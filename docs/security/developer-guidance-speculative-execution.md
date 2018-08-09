---
title: 理論式執行端通道的 c + + 開發人員指引 |Microsoft Docs
ms.custom: ''
ms.date: 07/10/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
author: mamillmsft
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: abf51432e5803de001610da07d97d5bad1796085
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018841"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>理論式執行端通道的 c + + 開發人員指引

本文包含可協助識別及緩和風險的理論式執行端通道硬體 c + + 軟體弱點的開發人員指導方針。 這些弱點可以將機密資訊洩漏跨越信任界限，而且可能影響支援推測性、 次序不對的指示執行的處理器上執行的軟體。 弱點的這個類別是 2018 年 1 月日中所述的第一個和其他背景資訊和指引可在[Microsoft 資訊安全摘要報告](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)。

這篇文章所提供的指引與相關弱點所代表的類別：

1. CVE-2017-5753，也稱為 Spectre 變異 1。 因為發生條件式分支 misprediction 的推測性執行而可能發生的側邊通道有關這個硬體的弱點可能會類別。 （從 15.5.5 版開始） 的 Visual Studio 2017 中 Visual c + + 編譯器支援`/Qspectre`CVE 2017-5753 的相關參數，可提供一組有限的可能有弱點的程式碼撰寫模式的編譯時期緩和措施。 文件[/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)旗標提供有關其效果與使用方式的詳細資訊。 

2. CVE-2018年-3639，也稱為[推測性存放區略過 (SSB)](https://aka.ms/sescsrdssb)。 可能發生因為相依的存放區，因為記憶體存取 misprediction 預先載入的推測性執行的側邊通道被與這個硬體的弱點可能會類別。

推測性執行端通道弱點的可存取簡介，請參閱標題為 「 簡報[案例的 Spectre 與 Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4)所探索到這些問題研究小組的其中一個。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>理論式執行端通道硬體弱點是什麼？

新型 Cpu 提供的效能較高程度的理論和出的順序執行指令的使用。 比方說，此移轉作業往往是預測的目標分支 （條件式和間接） 可讓 CPU 開始推測執行指示預測的分支目標，以避免延遲，直到實際分支目標判斷已解決。 CPU 稍後發現 misprediction 發生，就不會捨棄所有推測計算的機器狀態。 這可確保有錯估的推測沒有在架構上看到效果。

雖然推測性執行不會影響在架構上可見的狀態，它會將剩餘的追蹤保留非架構的狀態，例如 CPU 所使用的各種快取。 就這些殘差追蹤的側邊通道弱點可能會導致大量的推測性執行。 若要進一步了解，請考慮下列程式碼片段提供 CVE-2017-5753 （界限檢查略過） 的範例：

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

在此範例中，`ReadByte`是提供該緩衝區的緩衝區、 緩衝區大小和索引。 索引參數，所指定`untrusted_index`，提供的無特殊權限的內容，例如非系統管理程序。 如果`untrusted_index`是小於`buffer_size`，則該索引處的字元讀取`buffer`到共用記憶體所參考的區域用來索引和`shared_buffer`。 

從架構的觀點而言，此程式碼序列是完全安全必定`untrusted_index`一定會小於`buffer_size`。 不過，有風險的理論式執行時，就可以在 CPU 會錯估的條件式分支和執行在 if 的主體陳述式，即使`untrusted_index`大於或等於`buffer_size`。 如此一來，CPU 可以推測讀取一個位元組，它的界限`buffer`（這可能是密碼），接著可以使用該位元組的值來計算透過後續載入位址`shared_buffer`。 

雖然 CPU 最終將會偵測此 misprediction，剩餘的副作用可能會處於顯示資訊超出範圍，從已讀取的位元組值的 CPU 快取`buffer`。 這些副作用可以偵測到較低的系統上執行的方式快速探查的特殊權限的內容中的每個快取行`shared_buffer`存取。 若要這麼做可採取的步驟如下：

1. **叫用`ReadByte`多次`untrusted_index`正在小於`buffer_size`** 。 發動攻擊的內容可能會導致叫用的犧牲者內容`ReadByte`（例如，透過 RPC)，例如分支預測器是訓練是不被視為`untrusted_index`是小於`buffer_size`。

2. **排清中的所有快取行`shared_buffer`** 。 發動攻擊的內容必須排清所有記憶體所參考的共用區域中的快取行`shared_buffer`。 因為共用記憶體區域，這非常簡單，例如使用內建函式即可`_mm_clflush`。

3. **叫用`ReadByte`具有`untrusted_index`大於`buffer_size`** 。 發動攻擊的內容會導致叫用的犧牲者內容`ReadByte`使其不正確預測將不會採取的分支。 此處理器以推測執行在 if 的主體含有區塊的原因`untrusted_index`大於`buffer_size`，因此導致超出範圍的讀取權限的`buffer`。 因此，`shared_buffer`使用讀取超出範圍，因此會造成 CPU 所應載入的個別快取行的可能密碼值會編製索引。

4. **讀取中的每個快取行`shared_buffer`若要查看最快的速度存取哪一個**。 發動攻擊的內容可以讀取中的每個快取行`shared_buffer`和偵測的載入速度比其他的快取行。 這是可能已上線步驟 3 所快取行。 因為在此範例中的位元組值和快取行之間沒有 1:1 關聯性，這可讓攻擊者能夠推斷實際的值超出範圍讀取的位元組。

上述步驟將提供範例，使用稱為排清 + 重新載入，搭配 CVE 2017-5753 的執行個體的全部功能的技術。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些軟體情況可能會受到影響？

使用類似的程序的安全軟體開發[安全性開發生命週期](https://www.microsoft.com/en-us/sdl/)(SDL) 通常需要開發人員識別存在於其應用程式的信任界限。 信任界限存在於其中的應用程式可能會與低信任內容，例如在系統上的另一個處理序或在核心模式裝置驅動程式的情況下非系統管理使用者模式程序所提供的資料互動的地方。 涉及推測性執行端通道弱點的新類別是與許多現有的軟體安全性模型，找出程式碼，並且在裝置上的資料中的信任界限。 

下表提供開發人員可能要考慮發生這些弱點的軟體安全性模型的摘要：

|信任界限|描述|
|----------------|----------------|
|虛擬機器的界限|隔離在個別的虛擬機器，接收來自另一部虛擬機器不受信任的資料中的工作負載的應用程式可能會有風險。| 
|核心界限|接收來自非管理使用者模式程序不受信任的資料的核心模式裝置驅動程式可能會有風險。| 
|處理序界限|接收來自本機系統上執行的另一個處理序的未受信任的資料，例如透過遠端程序呼叫 (RPC)、 共用的記憶體或其他處理序間通訊 (IPC) 機制可能會有風險的應用程式。|
|Enclave 界限|接收從 enclave 之外的不受信任的資料的安全飛地 （例如 Intel SGX) 內執行的應用程式可能會有風險。|
|語言界限|解譯的應用程式或 Just-In-Time (JIT) 編譯並執行不受信任的程式碼撰寫的較高層級的語言可能會有風險。|

有受攻擊面公開至上述任一種信任界限應該檢閱受攻擊面，以識別和減緩的推測性執行端通道弱點的可能執行個體上的程式碼的應用程式。 請注意不具有已公開至遠端的受攻擊面，例如遠端網路通訊協定，信任界限示範可處於推測性執行端通道弱點的風險之中。

## <a name="potentially-vulnerable-coding-patterns"></a>可能有弱點的程式碼撰寫模式

由於多個程式碼撰寫模式，推測性執行端通道弱點可能會發生。 本章節描述可能有弱點的程式碼撰寫模式，並提供範例，針對每個，但應該識別這些佈景主題的變化可能存在。 因此，建議開發人員將需要這些模式做為範例，而不是所有可能有弱點的程式碼撰寫模式的完整清單。 現在可存在於軟體的記憶體安全弱點的相同的類別可能也會沿著推測性存在，且超出範圍的順序執行，包括但不是限於緩衝區溢位，路徑陣列的存取，未初始化的記憶體使用型別產生混淆，依此類推。 攻擊者可以利用記憶體安全性弱點，沿著架構路徑中使用的相同原始物件可能也適用於推測性的路徑。

一般情況下，可以控制或受到信任度較低的內容中的資料上操作的條件運算式時，可能會發生推測性執行端通道相關條件式分支 misprediction。 比方說，這可能包括用於條件運算式`if`， `for`， `while`， `switch`，或三元陳述式。 針對每個這些陳述式，編譯器可能會產生 CPU 可能會預測在執行階段的分支目標的條件式分支。

對於每個範例中，插入註解與片語"投機屏障 」 開發人員可能會造成屏障，以緩和措施。 這是一節中詳細討論上緩和措施。

## <a name="speculative-out-of-bounds-load"></a>超出範圍的理論式載入

這個類別的程式碼模式，牽涉到通往推測超出範圍的條件式分支 misprediction 記憶體存取。

### <a name="array-out-of-bounds-load-feeding-a-load"></a>超出範圍的陣列載入饋送負載

此程式碼撰寫模式是 CVE-2017-5753 （界限檢查略過） 原本描述易受攻擊程式碼撰寫模式。 這篇文章的背景一節說明此模式在詳細資料。

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

同樣地，陣列超出範圍時，負載可能會發生在超過其終止迴圈搭配條件因為 misprediction。 在此範例中，條件式分支相關聯`x < buffer_size`運算式可能會錯估，並推測執行主體`for`迴圈時`x`大於或等於`buffer_size`，因此產生的推測性超出範圍載入。

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

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>超出範圍的陣列載入饋送間接的分支

此程式碼撰寫模式牽涉到其中的條件式分支 misprediction 可能會導致案例然後因而間接分支至的目標位址的函式指標的陣列存取超出範圍讀取超出範圍。 下列程式碼片段提供範例，示範這項功能。 

在此範例中，不受信任的訊息識別項會提供透過 DispatchMessage`untrusted_message_id`參數。 如果`untrusted_message_id`是小於`MAX_MESSAGE_ID`，則它會使用對函式指標的陣列索引，以及分支到對應的分支目標。 此程式碼是在架構上，安全，但如果 CPU 錯估數的條件式分支，可能會造成`DispatchTable`檢索`untrusted_message_id`當其值為大於或等於`MAX_MESSAGE_ID`，而因此導致超出範圍的存取。 這可能會導致從衍生 překračuje meze 陣列，其中可能會導致資訊洩漏，根據推測執行的程式碼分支目標位址的推測性執行。

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

隨著與在超出範圍的陣列的案例負載提供另一個的負載，這種狀況可能也會發生與超出其結束的條件，因為 misprediction 迴圈搭配使用。

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>超出範圍的陣列儲存饋送間接的分支

雖然先前範例所示範的方式推測超出範圍負載可能會影響間接分支目標，也很可能超出範圍儲存修改的間接分支目標，例如函式指標或寄件地址。 這可能會導致推測性執行來自攻擊者指定的位址。

在此範例中，不受信任的索引會傳遞`untrusted_index`參數。 如果`untrusted_index`的項目計數少於`pointers`陣列 （256 個項目），則會在將提供的指標值`ptr`寫入`pointers`陣列。 此程式碼是在架構上，安全，但如果 CPU 錯估數的條件式分支，可能會造成`ptr`推測寫入 překračuje meze 堆疊配置`pointers`陣列。 這可能會導致推測性損毀的回覆地址`WriteSlot`。 如果攻擊者可以控制的值`ptr`，它們可能會導致從任意的推測性執行處理時`WriteSlot`推測性的路徑傳回。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

同樣地，如果函式指標名為區域變數`func`配置在堆疊上，則它可能可以推測修改地址，`func`指的是當條件式分支 misprediction，就會發生。 透過呼叫的函式指標時，這可能導致從任意地址的推測性執行。

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

請注意這兩個範例涉及推測性修改的堆疊配置間接分支指標。 可以推測性修改全域變數、 堆積配置的記憶體，和甚至是唯讀記憶體一些 Cpu 上也可能會發生。 堆疊配置的記憶體，針對 Visual c + + 編譯器已經採取步驟以讓它更難推測修改堆疊配置間接分支目標，例如透過重新排列本機變數，使得緩衝區會放在旁邊做為安全性 cookie屬於[/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check)編譯器的安全性功能。

## <a name="speculative-type-confusion"></a>理論式的型別混淆

此類別會處理程式碼可能會導致大量推測性的型別混淆的模式。 發生這種情況的風險的理論式執行期間使用非架構的路徑是正確類型來存取記憶體時。 條件式分支 misprediction 和推測性存放區略過可能會導致推測性的類型產生混淆。 

推測性存放區的許可，這可能會發生在案例中，編譯器會重複使用多個類型的變數的堆疊位置。 這是因為的架構類型的變數存放區`A`可能會略過，因此可允許的型別負載`A`推測執行之前已指派變數。 如果先前儲存的變數是不同的類型，這就可以建立理論式類型造成混淆的條件。

條件式分支 misprediction，如下列程式碼片段會用來描述不同的條件，讓理論式的型別混淆面對。

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>理論式的型別混淆導致超出範圍載入

此程式碼撰寫模式牽涉到其中的推測型別混淆可能會導致案例超出範圍或載入的值，摘要後續載入位址的類型產生混淆的欄位存取。 這是類似於陣列超出範圍的程式碼撰寫模式，但透過如上所示，撰寫程式碼順序的替代方法，它會顯示。 在此範例中，發動攻擊的內容可能會導致執行犧牲者內容`ProcessType`類型的物件使用多次`CType1`(`type`欄位等於`Type1`)。 這會造成影響訓練第一個條件式分支`if`預測不採用的陳述式。 發動攻擊的內容可能會犧牲者內容執行然後造成`ProcessType`型別的物件與`CType2`。 這會導致推測性的型別混淆如果條件式分支的前`if`錯估數陳述式，並執行的主體`if`陳述式，因此轉型別的物件`CType2`至`CType1`。 由於`CType2`小於`CType1`，記憶體存取`CType1::field2`會導致推測超出範圍載入的資料可能是祕密。 此值之後會用來從載入`shared_buffer`可以建立可預見的副作用，就如同陣列範例與先前說明的超出範圍。

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>理論式的型別混淆導致間接的分支

此程式碼撰寫模式牽涉到其中的推測型別混淆可能會導致不安全的間接分支理論式執行期間的情況。 在此範例中，發動攻擊的內容可能會導致執行犧牲者內容`ProcessType`類型的物件使用多次`CType2`(`type`欄位等於`Type2`)。 這會造成影響訓練第一個條件式分支`if`要採取的陳述式和`else if`不採取的陳述式。 發動攻擊的內容可能會犧牲者內容執行然後造成`ProcessType`型別的物件與`CType1`。 這會導致推測性的型別混淆如果條件式分支的第一個`if`陳述式來預測採取和`else if`陳述式來預測不採用，因此執行主體`else if`和轉型類型的物件`CType1`至`CType2`。 由於`CType2::dispatch_routine`欄位與重疊`char`陣列`CType1::field1`，這可能導致推測性的間接分支到非預期的分支目標。 如果發動攻擊的內容可以控制中的位元組值`CType1::field1`陣列，可能會讓它們能夠控制分支目標位址。

## <a name="speculative-uninitialized-use"></a>理論式未初始化的使用

這個類別的程式碼模式，牽涉到推測性執行可能會存取未初始化的記憶體並使用它來摘要後續載入或間接的分支。 這些是可利用來攻擊的程式碼撰寫模式，讓攻擊者必須能夠控制或有意義地影響它們的使用，而沒有它正在使用中的內容所要初始化的記憶體內容。

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>理論式未初始化的使用，導致超出範圍載入

理論式未初始化的使用可能會導致超出範圍使用的攻擊者所控制的值來載入。 在範例中的值以下`index`指派`trusted_index`架構的所有路徑上並`trusted_index`皆必須小於或等於`buffer_size`。 不過，根據編譯器所產生的程式碼，可能會推測性存放區略過可能會發生，可從負載`buffer[index]`和預先指派，以執行相依運算式`index`。 如果發生這種情況，未初始化的值，如`index`用作位移`buffer`這可讓攻擊者讀取超出範圍的敏感資訊，並透過側邊通道透過相依的負載傳達這`shared_buffer`.

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>理論式未初始化的使用，導致間接的分支

理論式未初始化的使用可能會導致間接的分支，攻擊者控制分支目標。 在下列範例中，`routine`指派給`DefaultMessageRoutine1`或是`DefaultMessageRoutine`的值而定`mode`。 在架構上的路徑，這會導致`routine`一定間接的分支之前初始化。 不過，編譯器所產生的程式碼，根據推測的存放區略過可能發生，可讓透過間接的分支`routine`推測執行預先指派給`routine`。 如果發生這種情況，攻擊者可以推測執行任意的地址，假設攻擊者可以影響或控制的未初始化的值`routine`。

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

對原始程式碼進行變更，就可以減輕風險的理論式執行端通道弱點。 這些變更可能是這類緩和的弱點，特定執行個體，藉由新增*投機屏障*，或藉由將機密資訊存取推測性應用程式的設計變更執行。

### <a name="speculation-barrier-via-manual-instrumentation"></a>透過手動檢測投機屏障

A*投機屏障*用手動方式插入由開發人員若要避免繼續進行非架構路徑的推測性執行。 比方說，開發人員可以插入投機屏障危險的程式碼撰寫模式之前的條件式區塊，在區塊開頭 （之後的條件式分支） 內或之前的考量是第一次載入。 這將導致無法執行非架構路徑的危險的程式碼，透過序列化執行條件式分支 misprediction。 硬體架構的推測屏障順序不同下, 表所述：

|架構|投機屏障 CVE 2017-5753 的內建函式|內建的 CVE-2018年-3639 投機屏障|
|----------------|----------------|----------------|
|x86 x64|_mm_lfence()|_mm_lfence()|
|ARM|目前無法使用|__dsb(0)|
|ARM64|目前無法使用|__dsb(0)|

例如，下列程式碼模式，可以減輕使用`_mm_lfence`如果內建函式，如下所示。

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>透過編譯器階段檢測投機屏障

（從 15.5.5 版開始） 的 Visual Studio 2017 中 Visual c + + 編譯器支援`/Qspectre`CVE 2017-5753 的相關參數，可自動插入投機屏障的一組有限的可能有弱點的程式碼撰寫模式。 文件[/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre)旗標提供有關其效果與使用方式的詳細資訊。 請務必請注意，這個旗標未涵蓋所有可能有弱點的程式碼撰寫模式，因此開發人員不應依賴它完整緩和這種弱點類別。

### <a name="masking-array-indices"></a>遮罩陣列索引

在位置推測超出範圍載入的情況下可能會發生，陣列索引可以強受到架構和非架構路徑上加入邏輯，以明確繫結的陣列索引。 例如，如果陣列可以配置為二乘冪對齊的大小，然後簡單遮罩可以導入。 下列範例，假設所示`buffer_size`靠二乘冪。 這可確保`untrusted_index`是一定小於`buffer_size`，即使發生條件式分支 misprediction 並`untrusted_index`傳遞的值大於或等於`buffer_size`。

請注意，在此執行之索引遮罩可能遭受推測性存放區根據編譯器所產生的程式碼的略過。

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

可用來減少推測性執行端通道弱點的另一個方法是移除記憶體中的機密資訊。 軟體開發人員可以尋找重構應用程式，使機密資訊不能存取理論式執行期間的機會。 這可透過重構來隔離到個別的程序的機密資訊的應用程式的設計。 例如，web 瀏覽器應用程式可以嘗試找出與每個 web 來源關聯到不同的處理序，因此導致其中一個處理序無法存取透過推測性執行的跨原始來源資料的資料。

## <a name="see-also"></a>另請參閱

[減少推測性執行旁路攻擊漏洞的指導方針](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)

[減少推測性執行側邊通道攻擊硬體漏洞](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)