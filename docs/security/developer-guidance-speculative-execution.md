---
title: 理論式執行端通道的 c + + 開發人員指導方針
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: d0b9faf0bd11892c05e25e981e8cd729cb623dd4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219322"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>理論式執行端通道的 c + + 開發人員指導方針

本文包含的指引可讓開發人員協助識別和緩和 c + + 軟體中的理論式執行端通道硬體弱點。 這些弱點可以在信任界限之間洩漏機密資訊，而且可能會影響在支援理論式、循序執行指示的處理器上執行的軟體。 這個類別的弱點第一次是在2018年1月，還有其他背景和指導方針，可以在[Microsoft 的安全性諮詢](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)中找到。

本文所提供的指導方針與所代表的弱點類別有關：

1. CVE-2017-5753，也稱為 Spectre variant 1。 這個硬體弱點類別與可能因為條件式分支 misprediction 而發生的理論性執行而產生的端通道相關。 Visual Studio 2017 中的 Microsoft c + + 編譯器（從版本15.5.5 版開始）包含對參數的支援， `/Qspectre` 針對一組有限的可能易受攻擊程式碼模式（與 CVE-2017-5753 相關）提供編譯時間緩和功能。 `/Qspectre`Visual Studio 2015 Update 3 到[KB 4338871](https://support.microsoft.com/help/4338871)也提供此參數。 [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)旗標的檔會提供其效果和使用方式的詳細資訊。

2. CVE-2018-3639，也稱為[推測存放區略過（SSB）](https://aka.ms/sescsrdssb)。 這個硬體弱點類別與可能因為記憶體存取 misprediction 而在相依存放區前的負載而產生的端通道相關。

如需可存取的理論式執行端通道弱點的簡介，請參閱標題為[Spectre 和 Meltdown 的案例](https://www.youtube.com/watch?v=_4O0zMW-Zu4)，這是由探索到這些問題的其中一名研究團隊所組成。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>什麼是推測性執行端通道硬體弱點？

新式 Cpu 藉由使用指示的推測和循序執行，來提供更高的效能。 例如，這通常是藉由預測分支的目標（條件式和間接）來完成，這可讓 CPU 開始在預測的分支目標上推測式運算執行指令，藉此避免在實際分支目標解決前的延遲。 當 CPU 稍後發現發生 misprediction 時，就會捨棄所有已計算推測式運算的機器狀態。 這可確保 mispredicted 推理沒有架構可見的效果。

雖然推測性執行不會影響架構可見狀態，但是它可能會在非結構化狀態下留下剩餘的追蹤，例如 CPU 使用的各種快取。 這是可能會導致並行通路弱點的理論性執行追蹤。 若要進一步瞭解這一點，請考慮下列程式碼片段，其中提供 CVE-2017-5753 （界限略過）的範例：

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

在此範例中，會在緩衝區中 `ReadByte` 提供緩衝區、緩衝區大小和索引。 所指定的索引參數 `untrusted_index` 是由許可權較低的內容所提供，例如非系統管理的進程。 如果 `untrusted_index` 小於，則 `buffer_size` 該索引處的字元會從讀取， `buffer` 並用於索引至所參考之記憶體的共用區域 `shared_buffer` 。

從架構的觀點來看，這個程式碼序列是完全安全的，因為保證一定 `untrusted_index` 會小於 `buffer_size` 。 不過，在有理論執行的情況下，CPU 可能會錯估條件分支，並執行 if 語句的主體，即使 `untrusted_index` 大於或等於也一樣 `buffer_size` 。 因此，CPU 可能會推測式運算從超出界限 `buffer` （可能是秘密）讀取一個位元組，然後使用該位元組值來計算後續負載的位址 `shared_buffer` 。

雖然 CPU 最後會偵測到此 misprediction，但剩餘的副作用可能會留在 CPU 快取中，以顯示從範圍外讀取之位元組值的相關資訊 `buffer` 。 在系統上執行的許可權較少的內容，可以藉由探查中每個快取行的存取速度，偵測到這些副作用 `shared_buffer` 。 完成此動作所能採取的步驟如下：

1. ** `ReadByte` `untrusted_index` 使用 `buffer_size` 小於**的多次叫用。 攻擊內容可能會導致犧牲者內容 `ReadByte` 叫用（例如透過 RPC），讓分支預測的定型不會被視為 `untrusted_index` 小於 `buffer_size` 。

2. **清除中的 `shared_buffer` 所有**快取行。 攻擊內容必須在所參考之記憶體的共用區域中，清除所有快取行 `shared_buffer` 。 因為記憶體區域是共用的，所以這很簡單，而且可以使用內建函式來完成，例如 `_mm_clflush` 。

3. ** `ReadByte` `untrusted_index` 以 `buffer_size` 大於的方式叫用**。 攻擊內容會導致犧牲者內容叫 `ReadByte` 用，這樣會不正確地預測不會採用分支。 這會導致處理器推測式運算執行 if 區塊的主體 `untrusted_index` ，其大於 `buffer_size` ，因而導致超出範圍的讀取 `buffer` 。 因此， `shared_buffer` 會使用超出範圍的可能秘密值來編制索引，因而導致 CPU 載入個別的快取行。

4. **讀取中的每個 `shared_buffer` 快取行，以查看最快速存取的那一行**。 攻擊內容可以讀取中的每個快取行 `shared_buffer` ，並偵測快取行的載入速度明顯比其他緩存程式快。 這是可能已由步驟3引入的快取行。 因為在此範例中，位元組值和快取行之間有1:1 關聯性，所以這可讓攻擊者推斷超出範圍讀取之位元組的實際值。

上述步驟提供一個範例，說明如何搭配使用一種稱為 FLUSH + RELOAD 的技術，並利用 CVE-2017-5753 的實例。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些軟體案例可能會受到影響？

使用[安全性開發生命週期](https://www.microsoft.com/sdl/)（SDL）之類的程式開發安全軟體，通常需要開發人員識別存在於其應用程式中的信任界限。 信任界限存在於應用程式可能與較不受信任的內容（例如系統上的另一個進程），或在核心模式設備磁碟機的情況下為非管理使用者模式進程進行互動的位置。 與理論式執行端通道相關的新弱點類別，與現有軟體安全性模型中的許多信任界限有關，可隔離裝置上的程式碼和資料。

下表提供軟體安全性模型的摘要，其中開發人員可能需要擔心這些弱點發生的情況：

|信任邊界|說明|
|----------------|----------------|
|虛擬機器界限|在不同的虛擬機器中隔離工作負載的應用程式，會從另一個虛擬機器接收不受信任的資料，可能會有風險。|
|核心界限|從非系統管理使用者模式進程接收不受信任資料的核心模式設備磁碟機可能會有風險。|
|進程界限|從本機系統上執行的另一個進程接收不受信任資料的應用程式，例如透過遠端程序呼叫（RPC）、共用記憶體或其他處理序間通訊（IPC）機制，可能會有風險。|
|記憶體保護區界限|在安全記憶體保護區（例如 Intel SGX）內執行的應用程式，會從記憶體保護區外部接收不受信任的資料，可能會有風險。|
|語言界限|用來解讀或及時（JIT）編譯和執行以較高層級語言撰寫之不受信任程式碼的應用程式可能會有風險。|

具有暴露于上述任何信任界限之受攻擊面的應用程式，應該查看受攻擊面上的程式碼，以找出並緩和可能的推測執行端通道弱點實例。 請注意，暴露于遠端攻擊介面的信任界限（例如遠端網路協定）尚未被示範為推測執行端通道弱點的風險。

## <a name="potentially-vulnerable-coding-patterns"></a>可能易受攻擊的程式碼撰寫模式

推測的執行端通道弱點可能會因為多個編碼模式而引發。 本節說明可能易受攻擊的程式碼撰寫模式，並提供各項的範例，但是應該辨識出這些主題的變化可能存在。 因此，開發人員建議採用這些模式作為範例，而不是所有可能受到攻擊的程式碼撰寫模式的完整清單。 現今軟體中可能存在的相同記憶體安全弱點類別，可能也會隨著執行的推測和順序而存在，包括但不限於緩衝區溢位、超出範圍的陣列存取、未初始化的記憶體使用、類型混淆等等。 攻擊者可以用來利用架構路徑來入侵記憶體安全性漏洞的相同基本專案，也可能適用于理論上的路徑。

一般而言，當條件運算式操作的資料可以受到較不信任的內容控制或影響時，就可能會發生與條件式分支 misprediction 相關的推測執行端通道。 例如，這可以包含在 **`if`** 、 **`for`** 、 **`while`** 、 **`switch`** 或三元語句中使用的條件運算式。 編譯器可能會針對每個語句產生條件式分支，讓 CPU 在執行時間預測分支目標。

針對每個範例，會插入含有「推測屏障」片語的批註，而開發人員可能會在其中引進屏障作為緩和措施。 這會在緩和措施一節中更詳細地討論。

## <a name="speculative-out-of-bounds-load"></a>推測的超出範圍負載

此類別的編碼模式牽涉到條件式分支 misprediction，而這會導致可預測的超出範圍記憶體存取。

### <a name="array-out-of-bounds-load-feeding-a-load"></a>陣列超出範圍的負載已載入

這種編碼模式是原本描述的 CVE-2017-5753 （限制範圍略過）的易受攻擊編碼模式。 本文的「背景」一節會詳細說明此模式。

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

同樣地，陣列超出範圍的負載可能會與因 misprediction 而超過其終止條件的迴圈一起發生。 在此範例中，與運算式相關聯的條件式分支 `x < buffer_size` 可能會錯估，而推測式運算會 **`for`** 在大於或等於時執行迴圈的主體 `x` `buffer_size` ，因而導致推測的超出範圍負載。

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

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>陣列超出範圍的載入會將間接分支饋送

這種編碼模式牽涉到條件式分支 misprediction 會導致對函式指標陣列進行超出範圍存取的情況，然後將間接分支導向超出範圍讀取的目標位址。 下列程式碼片段提供示範這項的範例。

在此範例中，會透過參數提供不受信任的訊息識別碼給 DispatchMessage `untrusted_message_id` 。 如果 `untrusted_message_id` 小於，則 `MAX_MESSAGE_ID` 會使用它來編制函式指標陣列和分支至對應分支目標的索引。 這段程式碼在架構上是安全的，但如果 CPU 錯估數條件式分支，則可能會在 `DispatchTable` `untrusted_message_id` 其值大於或等於時編制索引， `MAX_MESSAGE_ID` 因而導致超出範圍的存取權。 這可能會導致從衍生超出陣列界限的分支目標位址執行推測，而這可能會導致資訊洩漏，視執行推測式運算的程式碼而定。

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

就如同陣列超出範圍的負載會載入另一個負載，這種情況也可能會伴隨因 misprediction 而超過其終止條件的迴圈一起引發。

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>陣列超出範圍的存放區已為間接分支饋送

雖然先前的範例示範了推測的超出範圍負載如何影響間接分支目標，但超出範圍的存放區也可能會修改間接分支目標，例如函式指標或傳回位址。 這可能會導致從攻擊者指定的位址執行推測。

在此範例中，會透過參數傳遞不受信任的索引 `untrusted_index` 。 如果 `untrusted_index` 小於陣列的元素計數 `pointers` （256元素），則中提供的指標值 `ptr` 會寫入至 `pointers` 陣列。 這段程式碼在架構上是安全的，但如果 CPU 錯估數條件式分支，可能會導致 `ptr` 推測式運算寫出超過堆疊配置陣列的界限 `pointers` 。 這可能會導致的傳回位址的推測損毀 `WriteSlot` 。 如果攻擊者可以控制的值 `ptr` ，則在沿著理論路徑傳回時，它們可能會導致來自任意位址的推測性執行 `WriteSlot` 。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

同樣地，如果已在堆疊上配置名為的函式指標區域變數，則在 `func` `func` 發生條件式分支 misprediction 時，可能會推測式運算修改參考的位址。 當透過呼叫函式指標時，這可能會導致來自任意位址的推測性執行。

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

請注意，這兩個範例都牽涉到對堆疊配置的間接分支指標進行的推測修改。 可能也會對全域變數、堆積配置的記憶體，甚至某些 Cpu 上的唯讀記憶體進行推測性修改。 對於堆疊配置的記憶體，Microsoft c + + 編譯器已經採取步驟，使其更難以推測式運算修改堆疊配置的間接分支目標，例如，藉由重新排序區域變數，讓緩衝區與安全性 cookie 相鄰，做為[/gs](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check)編譯器安全性功能的一部分。

## <a name="speculative-type-confusion"></a>推測型別混淆

此類別處理的編碼模式可能會使推測的類型產生混淆。 在理論執行期間使用不正確的型別和非架構路徑來存取記憶體時，就會發生這種情況。 條件式分支 misprediction 和推測存放區略過，可能會導致推測的類型混淆。

針對理論式存放區略過，當編譯器重複使用多個類型變數的堆疊位置時，就會發生這種情況。 這是因為類型變數的架構存放區 `A` 可能會被略過，因此在指派變數之前，允許將類型的載入 `A` 推測式運算執行。 如果先前儲存的變數屬於不同的類型，則這可以建立推測類型混淆的條件。

針對條件式分支 misprediction，下列程式碼片段將用來描述推測型別混淆可能會增加的不同條件。

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>導致超出範圍負載的推測型別混淆

這種編碼模式牽涉到推測型別混淆的情況，可能會導致超出界限或類型困惑的欄位存取，其中載入的值會將後續的載入位址饋送。 這與陣列超出範圍的編碼模式類似，但它是透過如上所述的替代編碼順序來列出。 在此範例中，攻擊內容可能會導致犧牲者內容以 `ProcessType` 類型的物件 `CType1` （ `type` 欄位等於）多次執行 `Type1` 。 這會讓第一個語句的條件式分支定型， **`if`** 以預測不採用。 然後，攻擊內容就可以讓犧牲者內容以 `ProcessType` 類型的物件來執行 `CType2` 。 如果第一個語句的條件式分支 **`if`** 錯估數並執行語句的主體 **`if`** ，因而將類型的物件轉換為，這可能會造成推測型別混淆 `CType2` `CType1` 。 因為小於 `CType2` ，所以 `CType1` 的記憶體存取會導致理論上的 `CType1::field2` 超出範圍的資料載入可能是秘密。 然後，此值會用於 `shared_buffer` 可以建立可觀察副作用的負載，如同先前所述的陣列超出範圍的範例。

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>導致間接分支的推測型別混淆

這種編碼模式牽涉到在理論上執行時，推測型別混淆可能會導致不安全間接分支的情況。 在此範例中，攻擊內容可能會導致犧牲者內容以 `ProcessType` 類型的物件 `CType2` （ `type` 欄位等於）多次執行 `Type2` 。 這將會影響用於定型第一個語句的條件式分支 **`if`** ，以及 `else if` 未採取的語句。 然後，攻擊內容就可以讓犧牲者內容以 `ProcessType` 類型的物件來執行 `CType1` 。 如果第一個語句的條件式分支進行 **`if`** 預測，而語句預測不採用，這會導致理論型別混淆 `else if` ，因而執行的主體， `else if` 並將類型的物件轉換 `CType1` 為 `CType2` 。 由於 `CType2::dispatch_routine` 欄位與 **`char`** 陣列重迭，因此 `CType1::field1` 這可能會導致非預期的分支目標有推測間接分支。 如果攻擊內容可以控制陣列中的位元組值 `CType1::field1` ，它們可能就能夠控制分支目標位址。

## <a name="speculative-uninitialized-use"></a>推測未初始化的使用

此類別的編碼模式牽涉到，理論執行可能會存取未初始化的記憶體，並使用它來饋送後續的負載或間接分支。 為了讓這些程式碼撰寫模式能夠被利用，攻擊者必須能夠控制或有意義地影響所使用的記憶體內容，而不需要由它在中使用的內容來初始化。

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>推測未初始化的使用導致超出範圍的負載

理論上未初始化的使用可能會使用攻擊者控制的值，而導致超出範圍的負載。 在下列範例中，的值 `index` 會指派給 `trusted_index` 所有架構路徑，並 `trusted_index` 假設小於或等於 `buffer_size` 。 不過，視編譯器所產生的程式碼而定，可能會發生理論存放區略過，讓載入來源 `buffer[index]` 和相依運算式能夠在指派之前執行 `index` 。 如果發生這種情況，將會使用未初始化的值 `index` 做為的位移， `buffer` 使其可以讓攻擊者讀取超出範圍的機密資訊，並透過的相依負載在端通道中傳遞 `shared_buffer` 。

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>推測未初始化的使用，導致間接分支

推測未初始化的使用可能會導致間接分支，其中分支目標是由攻擊者所控制。 在下列範例中， `routine` 會 `DefaultMessageRoutine1` `DefaultMessageRoutine` 根據的值指派給或 `mode` 。 在架構路徑上，這會導致 `routine` 永遠在間接分支之前初始化。 不過，視編譯器所產生的程式碼而定，可能會發生理論存放區略過，讓間接分支能夠在 `routine` 指派之前推測式運算執行 `routine` 。 如果發生這種情況，攻擊者可能能夠從任意位址推測式運算執行，假設攻擊者可以影響或控制未初始化的值 `routine` 。

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

藉由對原始程式碼進行變更，可以降低推測的執行端通道弱點。 這些變更可能牽涉到降低弱點的特定實例，例如新增*推測屏障*，或變更應用程式的設計，使敏感性資訊無法被推測的執行。

### <a name="speculation-barrier-via-manual-instrumentation"></a>透過手動檢測的推測屏障

開發人員可以手動插入「*推理屏障*」，以避免在非架構路徑上進行理論式執行。 例如，開發人員可以在條件式區塊主體中的危險編碼模式之前插入推理屏障，不論是在區塊開頭（條件式分支之後），或是在考慮的第一個載入之前。 這會讓條件式分支 misprediction 無法藉由序列化執行，而在非架構路徑上執行危險的程式碼。 「推測屏障」序列與硬體架構不同，如下表所述：

|架構|CVE-2017-5753 的推理屏障內建函式|CVE-2018-3639 的推理屏障內建函式|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence （）|_mm_lfence （）|
|ARM|目前無法使用|__dsb （0）|
|ARM64|目前無法使用|__dsb （0）|

例如，您可以使用內建來減輕下列程式碼模式，如下 `_mm_lfence` 所示。

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>透過編譯器時間檢測的推測屏障

Visual Studio 2017 中的 Microsoft c + + 編譯器（從版本15.5.5 版開始）包含參數的支援， `/Qspectre` 它會自動為一組有限的可能易受攻擊程式碼模式（與 CVE-2017-5753 相關）插入推理屏障。 [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)旗標的檔會提供其效果和使用方式的詳細資訊。 請務必注意，此旗標不會涵蓋所有可能易受攻擊的程式碼撰寫模式，因此，這類開發人員不應依賴它做為此類別弱點的全面緩和。

### <a name="masking-array-indices"></a>遮罩陣列索引

在可能發生推測超出範圍負載的情況下，藉由新增邏輯以明確系結陣列索引，陣列索引可以是架構和非架構路徑的強式綁定。 例如，如果陣列可以配置為與兩者的乘冪對齊的大小，就可以引進簡單的遮罩。 這會在下列範例中說明，其假設 `buffer_size` 對齊兩者的乘冪。 這可確保 `untrusted_index` 永遠小於 `buffer_size` ，即使發生條件式分支 misprediction，而且傳入的 `untrusted_index` 值大於或等於 `buffer_size` 。

請注意，此處所執行的索引遮罩可能會根據編譯器所產生的程式碼而受到推測的存放區略過。

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

另一種可用來減輕理論式執行端通道弱點的技巧，就是從記憶體中移除機密資訊。 軟體發展人員可以尋找重構其應用程式的機會，使敏感性資訊無法在推測執行期間存取。 這可以透過重構應用程式的設計，將機密資訊隔離到不同的進程來完成。 例如，網頁瀏覽器應用程式可以嘗試將與每個 web 原點相關聯的資料隔離成不同的進程，藉此防止某個進程能夠透過理論式執行來存取跨原始來源的資料。

## <a name="see-also"></a>另請參閱

[緩解理論式執行端通道弱點的指引](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[緩和推測性執行端通道硬體弱點](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
