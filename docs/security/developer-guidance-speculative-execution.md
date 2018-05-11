---
title: 理論式執行側邊通道的 c + + 開發人員指引 |Microsoft 文件
ms.custom: ''
ms.date: 05/03/2018
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
ms.openlocfilehash: 0a7e7ddb51f07f7fe6be1da017d8feae9cc4919e
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>理論式執行側邊通道的 c + + 開發人員指引

本文將指導方針來協助識別及緩和推測執行側邊通道硬體的弱點可能會在 c + + 軟體開發人員。 這些弱點可能會將機密資訊洩漏跨信任界限，而且可能影響支援推測性、 次序不對的指示執行的處理器上執行的軟體。 弱點的這個類別是一月，2018年中所述的第一個和其他背景資訊和指引位於[Microsoft 安全性摘要報告](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)。

本文所提供的指導方針與相關的弱點可能會由 CVE-2017年-5753，也稱為 Spectre variant 1 類別。 由於理論執行因條件式分支 misprediction 而發生可能會發生的側邊通道與這個硬體的弱點可能會類別。 Visual c + + 編譯器，Visual Studio 2017 （起版本 15.5.5） 中的包含的支援`/Qspectre`交換器提供一組有限 CVE-2017年-5753 相關的程式碼撰寫模式可能有弱點的編譯時期防護功能。 文件[/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre)旗標提供有關其效果和用法的詳細資訊。 

標題為展示檔中可以找到可存取的簡介推測執行側邊通道攻擊[Spectre 案例和溶解](https://www.youtube.com/watch?v=_4O0zMW-Zu4)所探索到這些問題研究小組的其中一個。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>理論式執行側邊通道硬體的弱點可能會有哪些？

新型 Cpu 提供的效能較高程度，藉由使用理論和次序不對的指示執行。 例如，通常這是預測的分支 （條件和 indrect） 可讓 CPU 開始推測執行預測的分支目標，直到實際分支目標，因而避免拖延指示的目標判斷已解決。 CPU 稍後發現 misprediction 發生時，所有推測性地計算出來的機器狀態會被捨棄。 這可確保有估推測不在架構上顯示效果。

雖然理論式執行不會影響 architecturaly 可見狀態，它可以處於非架構的狀態，例如各種快取所使用的 CPU 保留剩餘的追蹤。 這些剩餘項目追蹤的側邊通道攻擊可能會導致大量的理論執行它。 若要深入了解，請考慮下列程式碼片段提供 CVE 2017 5753 （界限檢查略過） 的範例：

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

在此範例中，`ReadByte`會提供該緩衝區的緩衝區、 緩衝區大小和索引。 所指定的索引參數`untrusted_index`，由較不提供特殊權限的內容，例如非系統管理程序。 如果`untrusted_index`是小於`buffer_size`，則該索引處的字元讀取`buffer`和到記憶體所參考的區域中，共用用來索引`shared_buffer`。

架構的觀點而言，此程式碼序列是非常安全因為這樣會保證，`untrusted_index`一定會小於`buffer_size`。 不過，如果理論式執行時，存在很可能會 mispredict 條件式分支 CPU，並執行 if 主體陳述式，即使`untrusted_index`大於或等於`buffer_size`。 因此，CPU 推測可讀取的位元組，它的界限`buffer`（這可能是密碼），接著可以使用該位元組值來計算透過後續載入位址`shared_buffer`。 

CPU 最終將會偵測這個 misprediction，而剩餘的副作用可能會停留在超出範圍，從已讀取的位元組值的相關資訊會顯示 CPU 快取`buffer`。 這些副作用可以偵測無特殊權限的系統上執行的速度探查的內容中的每個快取一行`shared_buffer`存取。 若要完成這項作業時可採取的步驟如下：

1. **叫用`ReadByte`多次使用`untrusted_index`正在小於`buffer_size`** 。 攻擊的內容可能會導致叫用的犧牲者內容`ReadByte`（例如透過 RPC)，例如分支預測工具是定型是不被視為`untrusted_index`是小於`buffer_size`。

2. **排清中的所有快取行`shared_buffer`** 。 攻擊的內容必須清除快取中的程式共用的記憶體區域所參考的所有`shared_buffer`。 因為共用的記憶體區域，這很直接，而且可以使用內建函式，例如完成`_mm_clflush`。

3. **叫用`ReadByte`與`untrusted_index`大於`buffer_size`** 。 攻擊的內容會導致叫用的犧牲者內容`ReadByte`使其不正確預測不採用分支。 要推測執行 if 主體處理器區塊，這樣會導致`untrusted_index`大於`buffer_size`，而因此導致讀取超出範圍的`buffer`。 因此，`shared_buffer`編製索引使用密碼可能已讀取值超出範圍，因此會造成 cpu，載入個別的快取行。

4. **讀取中的每個快取行`shared_buffer`以查看最快速存取哪一個**。 攻擊的內容可以讀取中的每個快取行`shared_buffer`並偵測得比其他載入快取行。 這是可能已在步驟 3 所帶的快取行。 因為在此範例中的位元組值與快取行之間沒有 1:1 關聯性，這可讓攻擊者推斷實際的值超出範圍已讀取的位元組。

上述的步驟會提供使用 ant colony optimization 排清 + 重新載入，搭配高畫質視訊 CVE-2017年-5753 的執行個體的範例。

## <a name="what-software-scenarios-can-be-impacted"></a>哪些軟體案例可能會受到影響？

使用類似程序的安全軟體開發[安全性開發週期](https://www.microsoft.com/en-us/sdl/)(SDL) 通常需要開發人員以識別存在於其應用程式的信任界限。 信任界限存在於其中的應用程式可能會與無信任內容，例如系統上的另一個處理序或在核心模式裝置驅動程式的情況下非系統管理使用者模式程序所提供的資料互動的位置。 新的類別中的弱點可能會涉及推測執行側邊通道是適用於許多現有隔離程式碼和資料的裝置上的軟體安全性模型中的信任界限。

下表提供開發人員可能要考慮發生這些弱點相關資訊的軟體安全性模型的摘要：

|信任界限|描述|
|----------------|----------------|
|虛擬機器的界限|隔離在接收來自另一個虛擬機器不受信任的資料的個別虛擬機器中的工作負載的應用程式可能會有風險。|
|核心界限|接收來自非管理使用者模式程序不受信任的資料的核心模式裝置驅動程式可能會有風險。|
|處理序界限|從本機系統上執行的另一個處理序接收不受信任的資料，例如透過遠端程序呼叫 (RPC)、 共用的記憶體或其他處理序間通訊 (IPC) 機制可能會有風險的應用程式。|
|Enclave 界限|執行內安全 （例如 Intel SGX) enclave 將收到不受信任從 enclave 外部的資料可能會有風險的應用程式。|
|語言界限|解譯的應用程式或 Just-In-Time (JIT) 編譯和執行不受信任的程式碼撰寫的更高層級的語言可能會有風險。|

有受攻擊面公開任何上述信任界限應檢閱程式碼來識別及降低可能的執行個體推測執行側邊通道弱點的攻擊介面上的應用程式。 請注意不具有已公開給遠端攻擊的介面，例如遠端網路通訊協定，信任界限示範被推測執行側邊通道攻擊的風險。

## <a name="potentially-vulnerable-coding-patterns"></a>可能有弱點的程式碼撰寫模式

理論式執行側邊通道弱點可能會發生過多的程式碼撰寫模式。 本章節描述可能有弱點的程式碼撰寫模式，並提供範例，針對每個，但應該辨識可能存在這些佈景主題的變化。 因此，開發人員建議採取這些模式做為範例，而不是所有可能有弱點的程式碼撰寫模式的完整清單。

一般情況下，可以受到較不受信任的內容或控制的資料上操作的條件運算式時，可能會發生推測執行側邊通道相關的條件式分支 misprediction。 比方說，這可能包括條件式運算式中使用`if`， `for`， `while`， `switch`，或三元陳述式。 針對每個陳述式，編譯器可能會產生 CPU 可能會預測的分支目標，在執行階段的條件式分支。

對於每個範例中，插入註解與片語"推測屏障 」 開發人員可能會造成一條界線做為防護功能。 討論這一節中詳細說明上防護功能。

### <a name="speculative-out-of-bounds-load"></a>超出範圍的理論式載入

這個類別的程式碼撰寫模式牽涉到通往理論式超出範圍的條件式分支 misprediction 記憶體存取。

#### <a name="array-out-of-bounds-load-feeding-a-load"></a>超出範圍的陣列載入饋送負載

此編碼模式是原本描述容易遭受編碼模式 CVE 2017 5753 （界限檢查略過）。 這篇文章的背景一節說明此模式在詳細資料。

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

同樣地，陣列超出範圍負載可能會發生在超過其終止迴圈搭配條件由於 misprediction。 在此範例中，條件式分支相關聯`x < buffer_size`運算式可能 mispredict 和推測執行主體`for`迴圈時`x`大於或等於`buffer_size`，因此產生的推測性超出範圍載入。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

#### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>超出範圍的陣列載入饋送間接的分支

此編碼模式牽涉到的案例，其中條件式分支 misprediction 可能會導致超出範圍存取哪些然後負責人間接的分支到目標位址的函式指標的陣列已超出範圍。 下列程式碼片段提供的範例，示範這項處理。 

在此範例中，不受信任的訊息識別項可透過 DispatchMessage`untrusted_message_id`參數。 如果`untrusted_message_id`是小於`MAX_MESSAGE_ID`，則它用來在函式指標的陣列中的索引及分支到對應的分支目標。 此程式碼是安全的架構上，但如果 CPU 錯估數的條件式分支，它可能會導致`DispatchTable`檢索`untrusted_message_id`當其值為大於或等於`MAX_MESSAGE_ID`，而因此導致超出範圍的存取。 這可能導致推測執行從衍生超出陣列界限的這會導致資訊洩漏，根據推測所執行的程式碼分支目標位址。

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

隨著超出陣列的大小寫與負載填入其他負載，可能也會搭配超過 misprediction 由於其終止條件在迴圈中發生這種狀況。

### <a name="speculative-type-confusion"></a>理論式型別混淆

這個類別的程式碼撰寫模式牽涉到條件式分支 misprediction 通往推測類型產生混淆。 下列範例程式碼會參考這一節的程式碼撰寫模式。

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

#### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>理論式型別混淆導致超出範圍載入

此編碼模式涉及的看到其中推測類型混淆可能會導致超出範圍或位置載入的值摘要後續載入地址類型產生混淆的欄位存取權。 這是類似陣列超出範圍的程式碼撰寫模式，但是它會顯示透過替代編碼如上所示的順序。 在此範例中，攻擊的內容可能會造成犧牲者內容執行`ProcessType`多次使用型別的物件`CType1`(`type`欄位等於`Type1`)。 這會影響定型的第一個條件分支的`if`預測不採用的陳述式。 攻擊的內容則會導致犧牲者內容執行`ProcessType`類型的物件與`CType2`。 這會導致根據類型產生混淆如果條件式分支的第一個`if`錯估數陳述式，並執行的主體`if`陳述式，因此轉型別的物件`CType2`至`CType1`。 因為`CType2`小於`CType1`，記憶體存取`CType1::field2`會導致理論式超出範圍載入的可能是機密的資料。 此值接著用於從載入`shard_buffer`如同陣列建立可觀察的副作用，範例先前描述的超出範圍。

#### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>理論式型別混淆導致間接的分支

此程式碼撰寫模式涉及其中推測類型混淆可能會導致不安全的間接分支理論式執行期間的情況。 在此範例中，攻擊的內容可能會造成犧牲者內容執行`ProcessType`多次使用型別的物件`CType2`(`type`欄位等於`Type2`)。 這會影響定型的第一個條件分支的`if`所要採取的陳述式和`else if`不採取的陳述式。 攻擊的內容則會導致犧牲者內容執行`ProcessType`類型的物件與`CType1`。 這會導致根據類型產生混淆如果條件式分支的第一個`if`陳述式來預測採取和`else if`陳述式來預測不採用，因此會執行的主體`else if`和轉型別的物件`CType1`至`CType2`。 因為`CType2::dispatch_routine`欄位與重疊`char`陣列`CType1::field1`，這可能導致推測間接分支到非預期的分支目標。 如果攻擊的內容可以控制中的位元組值`CType1::field1`陣列，可能會讓它們能夠控制分支目標位址。

## <a name="mitigation-options"></a>降低選項

理論式執行側邊通道弱點可減輕對原始程式碼進行變更。 這些變更可能是緩和特定執行個體的安全性漏洞，例如，藉由新增*推測屏障*，或藉由讓機密資訊無法存取推測性應用程式的設計變更執行。

### <a name="speculation-barrier-via-manual-instrumentation"></a>透過手動檢測推測屏障

A*推測屏障*用手動方式插入由開發人員為了避免推測從非架構路徑後再繼續執行。 比方說，開發人員可以在區塊的開頭 （之後的條件式分支） 的條件式區塊的主體中插入推測屏障之前危險的程式碼撰寫模式或之前是考量的第一個載入。 如此可防止從非架構路徑上的危險的程式碼執行的序列化執行條件式分支 misprediction。 下表所述的硬體架構不同推測屏障順序：

|架構|推測屏障|
|----------------|----------------|
|x86/x64|_mm_lfence()|
|ARM|目前無法使用|
|ARM64|目前無法使用|


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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>透過編譯器時間檢測推測屏障

Visual c + + 編譯器，Visual Studio 2017 （起版本 15.5.5） 中的包含的支援`/Qspectre`CVE-2017年-5753 相關參數，會自動插入推測屏障的一組有限的可能有弱點的程式碼撰寫模式。 文件[/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre)旗標提供有關其效果和用法的詳細資訊。 請務必請注意，此旗標未涵蓋所有可能有弱點的程式碼撰寫模式，因此開發人員不應依賴它做為防護弱點的這個類別的完整功能。

### <a name="removing-sensitive-information-from-memory"></a>從記憶體移除機密資訊

可用來降低推測執行側邊通道弱點的另一種技術是從記憶體移除機密資訊。 軟體開發人員可以尋找重構他們的應用程式，使機密資訊不能存取理論式執行期間的機會。 這可以透過重構應用程式隔離到個別的程序的機密資訊的設計。 例如，web 瀏覽器應用程式可以嘗試找出與每個 web 來源關聯到不同的處理序，以防止一個處理序能夠存取透過推測執行跨原始資料的資料。

## <a name="see-also"></a>另請參閱

[若要減輕推測執行側邊通道的弱點可能會指引](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)

[緩和推測執行側邊通道硬體弱點](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
