---
title: 適用于推測性執行端通道的 c + + 開發人員指導方針
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 72dffd25eef847d1bdffe61c4a18a27d9cb33644
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842451"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>適用于推測性執行端通道的 c + + 開發人員指導方針

本文包含的指引可協助開發人員識別和緩和 c + + 軟體中的推測性執行端通道硬體弱點。 這些弱點可能會在信任界限之間洩漏機密資訊，而且可能會影響在處理器上執行的軟體，該軟體可支援推測、順序外的指令執行。 此類別的弱點是在2018年1月、及其他背景中說明，並可在 [Microsoft 的安全性諮詢](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)中找到。

本文所提供的指導方針，與所代表的弱點類別有關：

1. CVE-2017-5753，也稱為 Spectre variant 1。 此硬體弱點類別與可能由於條件式分支 misprediction 結果而產生的推測性執行有關的側邊通道相關。 Visual Studio 2017 (中的 Microsoft c + + 編譯器，從版本15.5.5 版開始) 包含對參數的支援，可 `/Qspectre` 針對一組有限的 CVE-2017-5753 相關可能易受攻擊的程式碼模式提供編譯時間緩和。 `/Qspectre`交換器也可在 Visual Studio 2015 Update 3 到[KB 4338871](https://support.microsoft.com/help/4338871)中取得。 旗標的檔會 [`/Qspectre`](../build/reference/qspectre.md) 提供其效果和使用方式的詳細資訊。

2. CVE-2018-3639，也稱為「 [預測存放區略過」 (SSB) ](https://aka.ms/sescsrdssb)。 此硬體弱點類別與可能發生的端通道相關，這是因為記憶體存取 misprediction 導致相依性存放區預先載入的結果。

您可以在標題為 [Spectre 和 Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) 的簡報中，找到有關推測性執行端通道弱點的可存取簡介，其中一種發現這些問題的研究團隊。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>什麼是推測性執行端通道硬體弱點？

新式 Cpu 藉由使用預測性和順向循序執行指示來提供更高程度的效能。 例如，通常是藉由預測分支的目標 (條件式和間接) 來達成，如此可讓 CPU 在預測的分支目標上開始推測式運算執行指令，藉此避免延遲到實際的分支目標解決為止。 如果 CPU 稍後發現 misprediction 發生，則會捨棄所有已計算推測式運算的機器狀態。 這可確保 mispredicted 推理沒有架構可見的效果。

雖然推測執行不會影響架構可見的狀態，但它可能會在非架構狀態中留下剩餘的追蹤，例如 CPU 所使用的各種快取。 這是可能導致端通路弱點的推測性執行的剩餘追蹤。 若要進一步瞭解這一點，請考慮下列程式碼片段，其中提供 CVE-2017-5753 (界限檢查略過) 的範例：

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

在此範例中， `ReadByte` 會提供緩衝區、緩衝區大小和索引到緩衝區。 由指定的索引參數 `untrusted_index` 是由較不具許可權的內容所提供，例如非系統管理進程。 如果 `untrusted_index` 小於 `buffer_size` ，則會從索引處讀取該索引的字元 `buffer` ，並用來編制索引至所參考之記憶體的共用區域 `shared_buffer` 。

從架構的觀點來看，這個程式碼順序完全安全，因為保證 `untrusted_index` 一律會小於 `buffer_size` 。 不過，在有推理執行的情況下，即使大於或等於，CPU 還是可能會錯估條件式分支並執行 if 語句的主體 `untrusted_index` `buffer_size` 。 如此一來，CPU 可能會推測式運算讀取超出 (界限的位元組， `buffer` 這可能是秘密) ，然後可以使用該位元組值來計算後續載入的位址 `shared_buffer` 。

CPU 最後會偵測到此 misprediction，而剩餘的副作用可能會留在 CPU 快取中，以顯示從界限讀取之位元組值的相關資訊 `buffer` 。 在系統上執行的較不具許可權的內容，可以偵測存取中每個快取行的速度，以偵測到這些副作用 `shared_buffer` 。 可以採取的步驟如下：

1. ** `ReadByte` `untrusted_index` 使用 `buffer_size` 小於來叫用多次**。 攻擊內容可能會導致犧牲者內容 `ReadByte` 叫用 (例如透過 RPC) ，因此不會將分支預測器定型為 `untrusted_index` 小於 `buffer_size` 。

2. **清除中的 `shared_buffer` 所有**快取行。 攻擊內容必須清除所參考之記憶體共用區域中的所有快取行 `shared_buffer` 。 因為記憶體區域是共用的，所以這是很簡單的，而且可以使用內建函式來完成（例如） `_mm_clflush` 。

3. ** `ReadByte` `untrusted_index` 使用 `buffer_size` 大於**的叫用。 攻擊內容會導致犧牲者內容叫用，使 `ReadByte` 其不正確地預測不會進行分支。 這會導致處理器推測式運算執行的 if 區塊主體 `untrusted_index` 大於 `buffer_size` ，因此會導致超出範圍的讀取 `buffer` 。 因此， `shared_buffer` 會使用讀取超出範圍的可能秘密值來編制索引，進而導致 CPU 載入個別的快取行。

4. **讀取中的每個 `shared_buffer` 快取行，以查看最快存取的快取行**。 攻擊內容可以讀取中的每個快取行 `shared_buffer` ，以及偵測到快載入的快取行比其他快取行快很多。 這是可能已在步驟3中導入的快取行。 因為此範例中的位元組值與快取行之間有1:1 的關聯性，所以這可讓攻擊者推斷讀取超出範圍之位元組的實際值。

上述步驟提供一個範例，說明如何使用稱為 FLUSH + 重載的技術，以及如何利用 CVE-2017-5753 的實例。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些軟體案例可能會受到影響？

使用 [安全性開發生命週期（例如安全性開發生命週期](https://www.microsoft.com/sdl/) ）來開發安全軟體 (SDL) 通常需要開發人員識別應用程式中存在的信任界限。 信任界限存在於應用程式可與較不受信任的內容（例如系統上的另一個進程）進行互動的位置，或在核心模式設備磁碟機的情況下，為非系統管理使用者模式進程。 涉及推測性執行端通道的新弱點類別，與現有軟體安全性模型中的許多信任界限相關，這些界限會在裝置上隔離程式碼和資料。

下表提供軟體安全性模型的摘要，開發人員可能需要關注這些弱點：

|信任邊界|描述|
|----------------|----------------|
|虛擬機器界限|在不同的虛擬機器中隔離工作負載的應用程式可能會有風險。|
|核心界限|從非系統管理使用者模式進程接收未受信任資料的核心模式設備磁碟機可能會有風險。|
|進程界限|從本機系統上執行的另一個進程接收不受信任資料的應用程式，例如透過遠端程序呼叫 (RPC) 、共用記憶體或其他處理序間通訊 (IPC) 機制可能會有風險。|
|記憶體保護區界限|在安全記憶體保護區中執行的應用程式 (例如，從記憶體保護區外部接收不受信任資料的 Intel SGX) 可能會有風險。|
|語言界限|解釋或及時 (JIT) 編譯和執行以較高層級語言撰寫之不受信任程式碼的應用程式可能會有風險。|

對上述任何信任界限公開受攻擊面的應用程式，應該查看受攻擊面上的程式碼，以找出並減輕可能的推測性執行端通道弱點實例。 請注意，暴露于遠端攻擊面的信任界限（例如遠端網路協定），尚未被示範為具有推測性執行端通道弱點的風險。

## <a name="potentially-vulnerable-coding-patterns"></a>可能易受攻擊的程式碼撰寫模式

推測性執行端通道弱點可能會因為多個程式碼撰寫模式而產生。 本節說明可能易受攻擊的程式碼撰寫模式，並提供每個模式的範例，但應能辨識出這些主題的變化可能存在。 因此，開發人員建議將這些模式做為範例，而不是所有可能易受攻擊的程式碼撰寫模式的詳盡清單。 目前可能存在於軟體中的相同記憶體安全性漏洞類別，也可能會隨著執行的推測和順序而存在，包括但不限於緩衝區溢位、超出界限的陣列存取、未初始化的記憶體使用、類型混淆等等。 攻擊者可用來利用架構路徑的記憶體安全性漏洞的相同基本專案，也可以套用至推測路徑。

一般情況下，當條件運算式對可由較不受信任的內容所控制或受影響的資料進行操作時，就可能會發生與條件式分支 misprediction 相關的推測性執行端通道。 例如，這可以包含用於 **`if`** 、 **`for`** 、 **`while`** 、 **`switch`** 或三元語句的條件運算式。 針對上述每個語句，編譯器可能會產生一個條件式分支，讓 CPU 在執行時間預測分支目標。

在每個範例中，會插入含有「推理關卡」片語的批註，讓開發人員可以在其中引入屏障作為緩和措施。 這在緩和措施一節中會更詳細地討論。

## <a name="speculative-out-of-bounds-load"></a>推測超出範圍的載入

這類的程式碼撰寫模式牽涉到一個條件式分支 misprediction，它會導致推測的超出範圍記憶體存取。

### <a name="array-out-of-bounds-load-feeding-a-load"></a>陣列超出界限的載入載入

這種編碼模式是最初描述的 CVE-2017-5753 (界限檢查略過) 的易受攻擊編碼模式。 本文的背景章節將詳細說明這種模式。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

同樣地，陣列超出範圍負載可能會與因 misprediction 而超過其終止條件的迴圈一起發生。 在此範例中，與運算式相關聯的條件分支 `x < buffer_size` 可能會錯估，而推測式運算則會在 **`for`** 大於或等於時執行迴圈的主體 `x` `buffer_size` ，進而導致推測的超出範圍載入。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>將間接分支饋送的陣列超出界限載入

這種程式碼撰寫模式牽涉到條件式分支 misprediction 可能會導致函式指標陣列的超出範圍存取，而這些指標接著會導致間接分支至讀取超出範圍的目標位址。 下列程式碼片段提供示範此的範例。

在此範例中，會透過參數提供未受信任的訊息識別碼給 DispatchMessage `untrusted_message_id` 。 如果 `untrusted_message_id` 小於，則 `MAX_MESSAGE_ID` 會使用它來索引至函式指標的陣列，並將分支加入至對應的分支目標。 這段程式碼在架構上是安全的，但如果 CPU 錯估數條件分支，它可能會在 `DispatchTable` `untrusted_message_id` 其值大於或等於時編制索引， `MAX_MESSAGE_ID` 進而導致超出界限的存取權。 這可能會導致從相依于陣列界限的分支目標位址產生推理執行，這可能會導致資訊洩漏，視執行推測式運算的程式碼而定。

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

如同陣列超出界限載入的情況下，另一個負載，此情況可能也會與因 misprediction 而超過其終止條件的迴圈一起發生。

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>將間接分支饋送的陣列超出範圍存放區

雖然先前的範例示範了推測的超出範圍負載如何影響間接分支目標，但超出範圍的存放區也可以修改間接分支目標，例如函數指標或傳回位址。 這可能會導致從攻擊者指定的位址推測執行。

在此範例中，會透過參數傳遞未受信任的索引 `untrusted_index` 。 如果 `untrusted_index` 小於陣列的元素計數 `pointers` (256 元素) ，則會將中提供的指標值 `ptr` 寫入 `pointers` 陣列中。 這段程式碼在架構上是安全的，但如果 CPU 錯估數條件分支，可能會導致 `ptr` 推測式運算寫出超過堆疊配置陣列的界限 `pointers` 。 這可能會導致的傳回位址的推測損毀 `WriteSlot` 。 如果攻擊者可以控制的值 `ptr` ，則可能會在以推測路徑傳回時，從任意位址產生推測的執行 `WriteSlot` 。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

同樣地，如果在堆疊上配置了名為的函式指標本機變數 `func` ，則在 `func` 發生條件式分支 misprediction 的情況下，可能可以推測式運算修改參考的位址。 當透過呼叫函式指標時，這可能會導致從任意位址執行推測。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

請注意，這兩個範例都牽涉到對堆疊配置間接分支指標的推測修改。 全域變數、堆積配置的記憶體，甚至是某些 Cpu 上的唯讀記憶體，也有可能發生推測修改。 針對堆疊配置的記憶體，Microsoft c + + 編譯器已採取步驟，讓推測式運算修改堆疊配置的間接分支目標變得更困難，例如重新排列區域變數，讓緩衝區在編譯器安全性功能中與安全性 cookie 相鄰 [`/GS`](../build/reference/gs-buffer-security-check.md) 。

## <a name="speculative-type-confusion"></a>推測型別混淆

此類別處理的程式碼模式，可能會讓推測的型別混淆。 在推測執行期間使用不正確的型別來存取記憶體時，就會發生這種情況。 條件式分支 misprediction 和推理存放區略過可能會導致推測型別混淆。

針對推測儲存區略過，這可能發生在編譯器針對多個類型的變數重複使用堆疊位置的情況下。 這是因為可能會略過型別變數的架構存放區 `A` ，因此在指派變數之前，允許將型別載入 `A` 推測式運算執行。 如果先前儲存的變數屬於不同的類型，則這可以建立推測型別混淆的條件。

在條件式分支 misprediction 中，下列程式碼片段將用來描述推測型別混淆可能帶來的不同條件。

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>推理型別混淆，導致超出範圍的負載

這種編碼模式牽涉到推測型別混淆的情況，可能會導致超出範圍或類型混淆的欄位存取，而載入的值會將後續的載入位址饋送。 這類似于陣列超出範圍的程式碼撰寫模式，但是它會透過替代的編碼順序來顯示，如上所示。 在此範例中，攻擊內容可能會導致犧牲者內容以 `ProcessType` 類型的物件（ `CType1` (`type` 欄位）等於) 來執行多次 `Type1` 。 這會讓第一個語句的條件式分支定型， **`if`** 而不會進行預測。 然後，攻擊內容就可以讓犧牲者內容以 `ProcessType` 類型的物件來執行 `CType2` 。 如果第一個語句的條件式分支 **`if`** 錯估數並執行語句的主體 **`if`** ，因而將類型的物件轉換為，則這可能會導致推測型別 `CType2` 混淆 `CType1` 。 由於小於 `CType2` `CType1` ，的記憶體存取 `CType1::field2` 會導致可能為秘密之資料的推測超出範圍載入。 然後，此值會用於 `shared_buffer` 可建立可觀察的副作用的負載，如同先前所述的陣列超出範圍範例。

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>導致間接分支的推測型別混淆

這種編碼模式牽涉到推測型別混淆的情況，可能會在推測執行期間導致不安全的間接分支。 在此範例中，攻擊內容可能會導致犧牲者內容以 `ProcessType` 類型的物件（ `CType2` (`type` 欄位）等於) 來執行多次 `Type2` 。 這將會對要執行的第一個 **`if`** 語句和不採用的語句定型條件分支的效果 `else if` 。 然後，攻擊內容就可以讓犧牲者內容以 `ProcessType` 類型的物件來執行 `CType1` 。 如果第一個語句的條件式分支 **`if`** 預測採用 `else if` ，而不採用語句，則執行的主體 `else if` 和將類型的物件轉換 `CType1` 為 `CType2` ，就會導致推測型別混淆。 因為 `CType2::dispatch_routine` 欄位與 **`char`** 陣列重迭，所以 `CType1::field1` 這可能會導致非預期分支目標的推測間接分支。 如果攻擊內容可以控制陣列中的位元組值 `CType1::field1` ，它們可能就可以控制分支目標位址。

## <a name="speculative-uninitialized-use"></a>推測未初始化的使用

這類的程式碼撰寫模式牽涉到可能會存取未初始化的記憶體，並使用它來饋送後續載入或間接分支的情節。 為了讓這些程式碼撰寫模式得以被利用，攻擊者必須能夠控制或有意義地影響所使用記憶體的內容，而不需由所用的內容進行初始化。

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>推理未初始化的使用會導致超出範圍的載入

推測未初始化的使用可能會導致使用受攻擊者控制值的超出範圍負載。 在下列範例中，的值 `index` 會指派給 `trusted_index` 所有架構路徑，並 `trusted_index` 假設為小於或等於 `buffer_size` 。 不過，根據編譯器所產生的程式碼而定，可能會出現可能會略過的推測存放區，以便讓從 `buffer[index]` 和相依運算式的載入在指派之前執行 `index` 。 如果發生這種情況，將會使用未初始化的值 `index` 做為的位移， `buffer` 讓攻擊者能夠讀取超出範圍的機密資訊，並透過的相依載入，在端通道之間傳遞 `shared_buffer` 。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>推理未初始化的使用會導致間接分支

推測未初始化的使用可能會導致間接分支，其中分支目標是由攻擊者控制。 在下列範例中， `routine` 會將指派給 `DefaultMessageRoutine1` 或（視的值而定） `DefaultMessageRoutine` `mode` 。 在架構路徑上，這會導致 `routine` 永遠在間接分支之前初始化。 不過，根據編譯器所產生的程式碼而定，可能會發生可略過的推測存放區，以便在 `routine` 指派給之前將間接分支推測式運算執行 `routine` 。 如果發生這種情況，攻擊者可以從任意位址推測式運算執行，假設攻擊者可以影響或控制的未初始化值 `routine` 。

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>緩和選項

您可以對原始程式碼進行變更，藉以減輕推測性執行端通道弱點。 這些變更可能牽涉到減輕弱點的特定實例，例如藉由新增 *推理關卡*，或對應用程式的設計進行變更，讓機密資訊無法存取推測的執行。

### <a name="speculation-barrier-via-manual-instrumentation"></a>透過手動檢測來推理障礙

開發人員可以手動插入 *推理關卡* ，以防止在非架構路徑中進行推測性執行。 例如，開發人員可以在條件式區塊主體中的危險編碼模式之前插入推理關卡， (條件式分支) 之後，或在第一個需要考慮的載入之前。 這會將執行序列化，以防止條件式分支 misprediction 在非架構路徑上執行危險程式碼。 依下表所述，「推測屏障」序列會依硬體架構而有所不同：

|架構|CVE 的推理屏障內建函式-2017-5753|CVE 的推理屏障內建函式-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence ( # A1|_mm_lfence ( # A1|
|ARM|目前無法使用|__dsb (0) |
|ARM64|目前無法使用|__dsb (0) |

例如，您可以使用內建來緩解下列程式碼模式， `_mm_lfence` 如下所示。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>透過編譯器時間檢測的推理關卡

Visual Studio 2017 (中的 Microsoft c + + 編譯器從15.5.5 版版開始，) 包含對參數的支援，該 `/Qspectre` 參數會自動針對一組有限的可能易受攻擊的程式碼模式（與 CVE-2017-5753 相關）插入推理關卡。 旗標的檔會 [`/Qspectre`](../build/reference/qspectre.md) 提供其效果和使用方式的詳細資訊。 請務必注意，此旗標不會涵蓋所有可能易受攻擊的程式碼撰寫模式，因此開發人員不應該依賴它來做為此類弱點的全面緩和措施。

### <a name="masking-array-indices"></a>遮罩陣列索引

在可能發生推測超出範圍負載的情況下，藉由新增明確系結陣列索引的邏輯，陣列索引可以在架構和非架構路徑上進行強式綁定。 例如，如果可以將陣列配置給對齊兩次冪的大小，則可以引進簡單的遮罩。 以下範例將說明這一點，假設它 `buffer_size` 是對齊二的乘冪。 這可確保 `untrusted_index` 一律小於 `buffer_size` ，即使條件式分支 misprediction 發生，而且傳入的 `untrusted_index` 值大於或等於 `buffer_size` 。

請注意，在這裡執行的索引遮罩可能會根據編譯器所產生的程式碼，以略過的略過存放區略過。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>從記憶體移除機密資訊

另一種可用來減輕推測性執行端通道弱點的技巧，就是從記憶體中移除機密資訊。 軟體發展人員可以尋找重構應用程式的機會，讓您無法在推測執行期間存取機密資訊。 這可以藉由重構應用程式的設計，將機密資訊隔離到個別的進程來完成。 例如，網頁瀏覽器應用程式可以嘗試將與每個 web 來源相關聯的資料隔離到個別的進程，藉此防止一個進程透過推測執行來存取跨原始來源的資料。

## <a name="see-also"></a>另請參閱

[減少推測性執行端通道弱點的指引](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[減少推測性執行端通道硬體弱點](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
