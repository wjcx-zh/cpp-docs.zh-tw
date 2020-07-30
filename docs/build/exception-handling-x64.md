---
title: x64 例外狀況處理
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 75658e2c86ffb1a75d5f66e873e0648a8ebae29e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224041"
---
# <a name="x64-exception-handling"></a>x64 例外狀況處理

概述結構化例外狀況處理和 c + + 例外狀況處理 x64 上的程式碼撰寫慣例和行為。 如需例外狀況處理的一般資訊，請參閱[Visual C++ 中的例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>例外狀況處理的回溯資料，偵錯工具支援

有數個資料結構是例外狀況處理和偵錯工具支援的必要項。

### <a name="struct-runtime_function"></a>struct RUNTIME_FUNCTION

以資料表為基礎的例外狀況處理需要一個資料表專案，適用于配置堆疊空間或呼叫另一個函式的所有函式（例如，非分葉函數）。 函數資料表專案的格式如下：

|||
|-|-|
|ULONG|函數起始位址|
|ULONG|函式結束位址|
|ULONG|回溯資訊位址|

RUNTIME_FUNCTION 結構必須在記憶體中對齊 DWORD。 所有位址都是相對的，也就是說，它們是包含函式資料表專案之影像起始位址的32位位移。 這些專案會進行排序，並放在 PE32 + 影像的 pdata 區段中。 針對動態產生的函式 [JIT 編譯程式]，支援這些函式的執行時間必須使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable，才能將這項資訊提供給作業系統。 若未這麼做，將導致不可靠的例外狀況處理和進程的偵錯工具。

### <a name="struct-unwind_info"></a>struct UNWIND_INFO

回溯資料資訊結構用來記錄函式在堆疊指標上的效果，以及將非靜態暫存器儲存在堆疊上的位置：

|||
|-|-|
|UBYTE：3|版本|
|UBYTE：5|Flags|
|UBYTE|初構的大小|
|UBYTE|回溯代碼的計數|
|UBYTE：4|畫面格暫存器|
|UBYTE：4|畫面格暫存器位移（已縮放）|
|USHORT \* n|回溯代碼陣列|
|變動|的格式可以是（1）或（2）以下|

（1）例外狀況處理常式

|||
|-|-|
|ULONG|例外狀況處理常式的位址|
|變動|語言特定處理常式資料（選擇性）|

（2）連鎖回溯資訊

|||
|-|-|
|ULONG|函數起始位址|
|ULONG|函式結束位址|
|ULONG|回溯資訊位址|

UNWIND_INFO 結構必須在記憶體中對齊 DWORD。 以下是每個欄位所代表的意義：

- **版本**

   回溯資料的版本號碼，目前為1。

- **旗標**

   目前已定義三個旗標：

   |旗標|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 函式具有例外狀況處理常式，應該在尋找需要檢查例外狀況的函數時呼叫。|
   |`UNW_FLAG_UHANDLER`| 函式具有終止處理常式，應在回溯例外狀況時呼叫。|
   |`UNW_FLAG_CHAININFO`| 這個回溯資訊結構不是程式的主要複本。 相反地，連鎖回溯資訊專案是先前 RUNTIME_FUNCTION 專案的內容。 如需相關資訊，請參閱連結的回溯[資訊結構](#chained-unwind-info-structures)。 如果已設定此旗標，則必須清除 [UNW_FLAG_EHANDLER] 和 [UNW_FLAG_UHANDLER] 旗標。 此外，[框架暫存器] 和 [固定堆疊配置] 欄位必須具有與主要回溯資訊中相同的值。|

- **初構的大小**

   函數初構的長度（以位元組為單位）。

- **回溯代碼的計數**

   回溯代碼陣列中的位置數目。 某些回溯程式碼（例如 UWOP_SAVE_NONVOL）在陣列中需要一個以上的位置。

- **畫面格暫存器**

   如果是非零值，則函式會使用框架指標（FP），而此欄位是用來做為框架指標的非靜態暫存器編號，使用 UNWIND_CODE 節點的 [作業資訊] 欄位的相同編碼方式。

- **畫面格暫存器位移（已縮放）**

   如果 [畫面格暫存器] 欄位為非零值，此欄位就是在建立時套用至 FP 暫存器的 RSP 的縮放位移。 實際的 FP 暫存器已設定為 RSP + 16 \* 這個數位，允許從0到240的位移。 此位移允許將 FP 暫存器指向動態堆疊框架的本機堆疊配置中間，透過較短的指示來提供更好的程式碼密度。 （也就是，其他指示可以使用8位帶正負號的位移形式）。

- **回溯代碼陣列**

   專案的陣列，說明初構在非靜態暫存器和 RSP 上的效果。 如需個別專案的意義，請參閱 UNWIND_CODE 的一節。 基於對齊目的，此陣列一律會有偶數的專案，而最終的專案可能未使用。 在這種情況下，陣列的長度比 [回溯程式碼計數] 欄位所表示的長。

- **例外狀況處理常式的位址**

   如果旗標 UNW_FLAG_CHAININFO 是明確的，且已設定其中一個旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER，則為函式的語言特定例外狀況或終止處理常式的影像相對指標。

- **語言特定處理常式資料**

   函數的語言特定例外狀況處理常式資料。 此資料的格式未指定，且完全由使用中的特定例外狀況處理常式決定。

- **連鎖回溯資訊**

   如果設定了旗標 UNW_FLAG_CHAININFO，則 UNWIND_INFO 結構會以三個 UWORDs 結束。  這些 UWORDs 代表連鎖回溯功能的 RUNTIME_FUNCTION 資訊。

### <a name="struct-unwind_code"></a>struct UNWIND_CODE

回溯程式碼陣列用來記錄初構中會影響非靜態暫存器和 RSP 的作業順序。 每個程式碼專案都有這種格式：

|||
|-|-|
|UBYTE|初構中的位移|
|UBYTE：4|回溯操作程式碼|
|UBYTE：4|作業資訊|

陣列會依照初構中的位移遞減順序來排序。

#### <a name="offset-in-prolog"></a>初構中的位移

執行這項作業之指令結尾的位移（從初構開始），加上1（也就是下一個指令開始的位移）。

#### <a name="unwind-operation-code"></a>回溯操作程式碼

注意：某些作業程式碼需要本機堆疊框架中值的不帶正負號位移。 這個位移來自開始，也就是固定堆疊配置的最低位址。 如果 UNWIND_INFO 中的 [框架暫存器] 欄位為零，則此位移是來自 RSP。 如果 [框架暫存器] 欄位為非零值，則此位移是從建立 FP 暫存器時的 .RSP 所在位置開始。 它等於 FP 暫存器減去 FP 暫存器位移（16在 \* UNWIND_INFO 中縮放的框架暫存器位移）。 如果使用 FP 暫存器，則任何採用位移的回溯程式碼都必須在初構中建立 FP 暫存器之後才使用。

對於除了和以外的所有 opcode `UWOP_SAVE_XMM128` `UWOP_SAVE_XMM128_FAR` ，位移一律是8的倍數，因為所有相關的堆疊值都會儲存在8位元組的界限上（堆疊本身一律會對齊16位元組）。 對於接受短位移的作業程式碼（小於512K），此程式碼之節點中的最後 USHORT 會將位移除以8。 對於採用長位移的作業程式碼（512K <= offset < 4 GB），此程式碼的最後兩個 USHORT 節點會保存位移（以位元組為單位的格式）。

對於作業碼 `UWOP_SAVE_XMM128` 和 `UWOP_SAVE_XMM128_FAR` ，位移一律是16的倍數，因為所有128位 XMM 作業都必須發生在16位元組對齊的記憶體上。 因此，調整因數16會用於 `UWOP_SAVE_XMM128` ，允許小於1百萬的位移。

回溯操作程式碼是下列其中一個值：

- `UWOP_PUSH_NONVOL`（0）1個節點

  推送非靜態整數暫存器，將 RSP 遞減8。 作業資訊是註冊的編號。 由於 epilogs 的條件約束，回溯程式 `UWOP_PUSH_NONVOL` 代碼必須先出現在初構中，並相對地，在回溯程式碼陣列中的最後一個。 這個相對順序會套用至以外的所有其他回溯代碼 `UWOP_PUSH_MACHFRAME` 。

- `UWOP_ALLOC_LARGE`（1）2或3個節點

  配置堆疊上的大型區域。 有兩種形式。 如果作業資訊等於0，則配置的大小除以8會記錄在下一個插槽中，允許配置最多 512K-8。 如果作業資訊等於1，則配置的未調整大小會以位元組由小到大的格式記錄在接下來的兩個位置，最多可達 4GB-8。

- `UWOP_ALLOC_SMALL`（2）1個節點

  配置堆疊上的小型區域。 配置的大小是作業資訊欄位 \* 8 + 8，允許從8到128個位元組的配置。

  堆疊配置的回溯程式碼應該一律使用最短的可能編碼方式：

  |**配置大小**|**回溯程式碼**|
  |-|-|
  |8到128個位元組|`UWOP_ALLOC_SMALL`|
  |136至 512K-8 個位元組|`UWOP_ALLOC_LARGE`，作業資訊 = 0|
  |512K 到 4G-8 個位元組|`UWOP_ALLOC_LARGE`，作業資訊 = 1|

- `UWOP_SET_FPREG`（3）1個節點

  將 [暫存器] 設定為目前 RSP 的某個位移，以建立框架指標暫存器。 位移等於 UNWIND_INFO 16 中的 [畫面格暫存器位移（縮放）] 欄位 \* ，允許從0到240的位移。 使用位移允許建立指向固定堆疊配置中間的框架指標，藉由允許更多存取權使用簡短的指令表單來協助程式碼密度。 [作業資訊] 欄位是保留的，不應使用。

- `UWOP_SAVE_NONVOL`（4）2個節點

  使用 MOV 而非 PUSH，將非靜態整數暫存器儲存在堆疊上。 此程式碼主要用於*壓縮包裝*，其中靜態暫存器會以先前配置的位置儲存至堆疊。 作業資訊是註冊的編號。 相應增加8的堆疊位移會記錄在下一個回溯操作程式碼位置中，如上面的注意事項中所述。

- `UWOP_SAVE_NONVOL_FAR`（5）3個節點

  使用 MOV 而非 PUSH，將非靜態整數暫存器儲存在具有長位移的堆疊上。 此程式碼主要用於*壓縮包裝*，其中靜態暫存器會以先前配置的位置儲存至堆疊。 作業資訊是註冊的編號。 未縮放的堆疊位移會記錄在接下來的兩個回溯作業程式碼位置中，如上面的注意事項所述。

- `UWOP_SAVE_XMM128`（8）2個節點

  將非靜態 XMM 暫存器的所有128位儲存在堆疊上。 作業資訊是註冊的編號。 相應放大的堆疊位移會記錄在下一個插槽中。

- `UWOP_SAVE_XMM128_FAR`（9）3個節點

  以長位移，將非靜態 XMM 暫存器的所有128位儲存在堆疊上。 作業資訊是註冊的編號。 無比例堆疊位移會記錄在接下來的兩個位置。

- `UWOP_PUSH_MACHFRAME`（10）1個節點

  推送電腦框架。  這個回溯程式碼是用來記錄硬體中斷或例外狀況的效果。 有兩種形式。 如果作業資訊等於0，則其中一個框架已推送至堆疊：

  |||
  |-|-|
  |.RSP + 32|SS|
  |RSP + 24|舊的 .RSP|
  |.RSP + 16|EFLAGS|
  |.RSP + 8|CS|
  |RSP|裂縫|

  如果作業資訊等於1，則表示其中一個框架已推送：

  |||
  |-|-|
  |.RSP + 40|SS|
  |.RSP + 32|舊的 .RSP|
  |RSP + 24|EFLAGS|
  |.RSP + 16|CS|
  |.RSP + 8|裂縫|
  |RSP|錯誤碼|

  這個回溯程式碼一律會出現在虛擬初構中，這實際上不會執行，而是會出現在中斷常式的實際進入點之前，而且只存在於提供一個位置來模擬機器框架的推送。 `UWOP_PUSH_MACHFRAME`記錄模擬，這表示電腦已在概念上完成此操作：

  1. Pop RIP 將位址從堆疊頂端傳回到*Temp*
  
  1. 推送 SS

  1. 推送舊的 .RSP

  1. 推送 EFLAGS

  1. Push CS

  1. 推送*暫存*

  1. 推播錯誤碼（如果 op 資訊等於1）

  模擬作業會將 `UWOP_PUSH_MACHFRAME` RSP 遞減40（op 資訊等於0）或48（op 資訊等於1）。

#### <a name="operation-info"></a>作業資訊

作業資訊位的意義取決於操作程式碼。 若要編碼一般用途（整數）暫存器，則會使用此對應：

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8至15|R8 至 R15|

### <a name="chained-unwind-info-structures"></a>連結的回溯資訊結構

如果已設定 UNW_FLAG_CHAININFO 旗標，則回溯資訊結構是次要的，而 [共用例外狀況-處理常式/連結資訊位址] 欄位包含主要回溯資訊。 這個範例程式碼會抓取主要回溯資訊，假設 `unwindInfo` 是已設定 UNW_FLAG_CHAININFO 旗標的結構。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

在兩種情況下，連鎖資訊很有用。 首先，它可以用於非連續的程式碼區段。 藉由使用連鎖資訊，您可以減少所需的回溯資訊大小，因為您不需要從主要回溯資訊複製回溯程式碼陣列。

您也可以使用連鎖資訊來分組 volatile 暫存器儲存。 編譯器可能會延遲儲存一些 volatile 暫存器，直到它位於函式進入初構之外。 您可以在群組程式碼之前讓函式部分的主要回溯資訊進行記錄，然後以非零的初構大小設定連結資訊，其中連鎖資訊中的回溯程式碼會反映非靜態暫存器的儲存。 在此情況下，回溯程式碼就是 UWOP_SAVE_NONVOL 的所有實例。 不支援使用推送來儲存非靜態暫存器，或使用額外的固定堆疊配置來修改 .RSP 暫存器的群組。

具有 UNW_FLAG_CHAININFO 集的 UNWIND_INFO 專案可以包含 UNWIND_INFO 專案也有 UNW_FLAG_CHAININFO 設定的 RUNTIME_FUNCTION 專案，有時也稱為*多個壓縮包裝*。 最後，連結的回溯資訊指標會到達已 UNW_FLAG_CHAININFO 清除的 UNWIND_INFO 專案。 這個專案是主要 UNWIND_INFO 專案，指向實際的程式進入點。

## <a name="unwind-procedure"></a>回溯程式

回溯程式碼陣列會依遞減順序排序。 發生例外狀況時，作業系統會將完整的內容儲存在內容記錄中。 接著會叫用例外狀況分派邏輯，這會重複執行這些步驟來尋找例外狀況處理常式：

1. 使用儲存在內容記錄中的目前 RIP，來搜尋描述連結 UNWIND_INFO 專案之目前函式（或函數部分）的 RUNTIME_FUNCTION 資料表專案。

1. 如果找不到函式資料表專案，則它會在分葉函式中，而 RSP 會直接定址傳回指標。 [.RSP] 的傳回指標儲存在更新的內容中，模擬的 RSP 會遞增8，而步驟1則重複。

1. 如果找不到函式資料表專案，則在初構或 c）中，在初構、b）中的 RIP 可以位於三個區域內，或在可能由例外狀況處理常式所涵蓋的程式碼中執行。

   - 案例 a）如果 RIP 在終的範圍內，控制項就會離開函式，此函式不能有與這個例外狀況相關聯的例外狀況處理常式，而且必須繼續計算呼叫端函式的內容。 若要判斷 RIP 是否在終解中，會檢查來自 RIP 的程式碼串流。 如果該程式碼串流可以與合法終解的尾端部分比對，則它會在終，而且會模擬終的剩餘部分，並在處理每個指令時更新內容記錄。 在此處理之後，會重複步驟1。

   - 案例 b）如果 RIP 位於序言內部，則 control 尚未進入函式，此函式不能有與這個例外狀況相關聯的例外狀況處理常式，而且必須復原初構的效果，以計算呼叫端函式的內容。 如果從函式開始到 RIP 的距離小於或等於回溯資訊中編碼的初構大小，RIP 就會在初構中。 針對第一個專案的回溯程式碼陣列（位移小於或等於函數 start 中的 RIP 位移）向前掃描，然後復原回溯程式碼陣列中所有剩餘專案的效果，就會展開初構的效果。 然後重複執行步驟1。

   - 案例 c）如果 RIP 不在初構或終解中，而且函式具有例外狀況處理常式（UNW_FLAG_EHANDLER 已設定），則會呼叫語言特定的處理常式。 處理常式會掃描其資料，並適當地呼叫篩選函數。 語言特定處理常式會傳回已處理的例外狀況，或是繼續進行搜尋。 它也可以直接起始回溯。

1. 如果語言特定處理常式傳回已處理的狀態，則會繼續使用原始內容記錄來執行。

1. 如果沒有任何語言特定的處理常式，或處理常式傳回「繼續搜尋」狀態，則必須將內容記錄展開至呼叫端的狀態。 其做法是處理所有回溯程式碼陣列元素，並復原每個專案的效果。 然後重複執行步驟1。

涉及連鎖的回溯資訊時，仍會遵循這些基本步驟。 唯一的差別在於，當您將回溯程式碼陣列回溯來回溯初構的效果時，一旦到達陣列結尾之後，它就會連結到父回溯資訊，而整個回溯程式碼陣列就會進行逐步解說。 此連結會繼續進行，直到到達沒有 UNW_CHAINED_INFO 旗標的回溯資訊，然後再完成其回溯程式碼陣列的流覽。

最小的回溯資料集為8個位元組。 這代表的函式只會配置128個位元組的堆疊（或更少），而且可能會儲存一個非靜態暫存器。 它也是不含回溯程式碼之零長度初構的連鎖回溯資訊結構大小。

## <a name="language-specific-handler"></a>語言特定處理常式

每當設定旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 時，UNWIND_INFO 中就會有語言特定處理常式的相對位址。 如上一節所述，特定語言的處理常式會在搜尋例外狀況處理常式或回溯的過程中呼叫。 它具有下列原型：

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord**會提供具有標準 Win64 定義之例外狀況記錄的指標。

**EstablisherFrame**是此函式之固定堆疊配置的基底位址。

**CoNtextRecord**會指向引發例外狀況（在例外狀況處理常式案例中）或目前「回溯」內容（在終止處理常式案例中）時的例外狀況內容。

**DispatcherCoNtext**會指向此函式的發送器內容。 它具有下列定義：

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc**是此函式內的 RIP 值。 這個值可以是例外狀況位址，或是控制項離開建立函數的位址。 RIP 用來判斷控制項是否在此函式內的部分受防護結構中，例如或的 `__try` 區塊 `__try` / **`__except`** `__try` / **`__finally`** 。

**Imagebase 設定**是包含此函式之模組的映射基底（載入位址），要加入函數專案和回溯資訊中用來記錄相對位址的32位位移。

**FunctionEntry**會提供 RUNTIME_FUNCTION 函式專案的指標，其中包含此函數的「函數」和「回溯資訊」影像基底相對位址。

**EstablisherFrame**是此函式之固定堆疊配置的基底位址。

**TargetIp**提供選用的指示位址，指定回溯的接續位址。 如果未指定**EstablisherFrame** ，則會忽略此位址。

**CoNtextRecord**會指向例外狀況內容，以供系統例外狀況分派/回溯程式碼使用。

**LanguageHandler**會指向所呼叫的語言特定語言處理常式常式。

**HandlerData**會指向此函式的語言特定處理常式資料。

## <a name="unwind-helpers-for-masm"></a>MASM 的回溯協助程式

為了撰寫適當的元件常式，有一組虛擬作業可以與實際的元件指令一併使用，以建立適當的 pdata 和. .xdata。 而且還有一組宏，可簡化虛擬作業的最常見用法。

### <a name="raw-pseudo-operations"></a>原始虛擬作業

|虛擬操作|說明|
|-|-|
|處理器框架 \[ ：*ehandler*]|讓 MASM 在. pdata 和回溯資訊中，為函式的結構化例外狀況處理回溯行為產生函數表專案。  如果*ehandler*存在，則會在 .xdata 中輸入此程式作為語言特定的處理常式。<br /><br /> 使用 FRAME 屬性時，其後面必須接著。ENDPROLOG 指示詞。  如果函式是分葉函式（如函式[類型](../build/stack-usage.md#function-types)中所定義），則不需要 FRAME 屬性，這是這些虛擬作業的其餘部分。|
|.PUSHREG *register*|使用序言中目前的位移，為指定的暫存器編號產生 UWOP_PUSH_NONVOL 回溯程式碼專案。<br /><br /> 請只將它與非靜態整數暫存器搭配使用。  對於 volatile 暫存器的推送，請使用。ALLOCSTACK 8，改為|
|.SETFRAME *register*， *offset*|使用指定的暫存器和位移，填入 [框架暫存器] 欄位和回溯資訊中的位移。 位移必須是16的倍數，且小於或等於240。 這個指示詞也會使用目前的序言位移，為指定的暫存器產生 UWOP_SET_FPREG 回溯程式碼專案。|
|.ALLOCSTACK*大小*|產生序言中目前位移之指定大小的 UWOP_ALLOC_SMALL 或 UWOP_ALLOC_LARGE。<br /><br /> *大小*運算元必須是8的倍數。|
|.SAVEREG *register*， *offset*|使用目前的序言位移，為指定的暫存器和位移產生 UWOP_SAVE_NONVOL 或 UWOP_SAVE_NONVOL_FAR 回溯程式碼專案。 MASM 會選擇最有效率的編碼方式。<br /><br /> *offset*必須是正數，而是8的倍數。 *offset*是相對於程式框架的基底，通常是在 RSP 中，或者，如果使用框架指標，則是未縮放的框架指標。|
|.SAVEXMM128 *register*， *offset*|使用目前的序言位移，為指定的 XMM 暫存器產生 UWOP_SAVE_XMM128 或 UWOP_SAVE_XMM128_FAR 回溯程式碼專案，以及位移。 MASM 會選擇最有效率的編碼方式。<br /><br /> *offset*必須是正數，而倍數則是16。  *offset*是相對於程式框架的基底，通常是在 RSP 中，或者，如果使用框架指標，則是未縮放的框架指標。|
|.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME 程式 \[ *代碼*]|產生 UWOP_PUSH_MACHFRAME 回溯程式碼專案。 如果指定了選擇性的程式*代碼*，則回溯程式碼專案會被賦予1的修飾詞。 否則修飾詞為0。|
|.ENDPROLOG|發出序言宣告結尾的信號。  必須發生在函式的前255個位元組。|

以下是範例函式初構，其中大部分的 opcode 都能正確使用：

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

如需有關終解範例的詳細資訊，請參閱[x64](prolog-and-epilog.md)初構和終解中的終解程式[代碼](prolog-and-epilog.md#epilog-code)。

### <a name="masm-macros"></a>MASM 宏

為了簡化[原始虛擬作業](#raw-pseudo-operations)的使用，有一組巨集定義在 ksamd64 中，可用於建立一般程式序言和結尾。

|巨集|說明|
|-|-|
|alloc_stack （n）|配置 n 個位元組的堆疊框架（使用 `sub rsp, n` ），併發出適當的回溯資訊（. allocstack n）|
|save_reg *reg*， *loc*|將非靜態暫存器*reg*儲存在 .rsp 位移*loc*的堆疊上，併發出適當的回溯資訊。 （. savereg reg，loc）|
|push_reg *reg*|將靜態暫存器*reg*推送至堆疊上，併發出適當的回溯資訊。 （. pushreg reg）|
|rex_push_reg *reg*|使用2個位元組的推送，將非靜態暫存器儲存在堆疊上，併發出適當的回溯資訊（. pushreg reg）。  如果 push 是函式中的第一個指令，請使用此宏，以確保函式為熱可修補。|
|save_xmm128 *reg*， *loc*|將非靜態 XMM 暫存器*reg*儲存在 .rsp 位移*loc*的堆疊上，併發出適當的回溯資訊（. savexmm128 reg，loc）|
|set_frame *reg*， *offset*|將畫面格暫存器*reg*設定為 RSP +*位移*（使用 `mov` 或 `lea` ），併發出適當的回溯資訊（. set_frame reg，offset）|
|push_eflags|使用指令推送 eflags `pushfq` ，併發出適當的回溯資訊（. alloc_stack 8）|

以下是搭配適當使用宏的範例函數初構：

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>C 中的回溯資料定義

以下是回溯資料的 C 描述：

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)
