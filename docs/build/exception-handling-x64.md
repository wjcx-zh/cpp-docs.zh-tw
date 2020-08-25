---
title: x64 例外狀況處理
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 3d973354f94ca8c9f2e0901e60f2a8009ac08cd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835047"
---
# <a name="x64-exception-handling"></a>x64 例外狀況處理

X64 上的結構化例外狀況處理和 c + + 例外狀況處理常式代碼撰寫慣例和行為的總覽。 如需例外狀況處理的一般資訊，請參閱 [Visual C++ 中的例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>例外狀況處理的回溯資料，偵錯工具支援

例外狀況處理和偵錯工具支援需要數個資料結構。

### <a name="struct-runtime_function"></a>struct RUNTIME_FUNCTION

以資料表為基礎的例外狀況處理需要所有配置堆疊空間的函式的資料表專案，或呼叫另一個函式 (例如，) 的非分葉函數。 函數資料表專案的格式如下：

|大小|值|
|-|-|
|ULONG|函數開始位址|
|ULONG|函數結束位址|
|ULONG|回溯資訊位址|

RUNTIME_FUNCTION 結構必須在記憶體中對齊 DWORD。 所有位址都是影像相對的，也就是說，它們是包含函式資料表專案之影像起始位址的32位位移。 這些專案會排序，並放在 PE32 + 影像的 .pdata 區段中。 若為動態產生的函式 [JIT 編譯程式]，支援這些函式的執行時間必須使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable，才能將這項資訊提供給作業系統。 若未這麼做，將會造成不可靠的例外狀況處理和處理常式。

### <a name="struct-unwind_info"></a>struct UNWIND_INFO

回溯資料資訊結構是用來記錄函式對堆疊指標的影響，而非靜態登錄儲存在堆疊上的位置：

|大小|值|
|-|-|
|UBYTE：3|版本|
|UBYTE：5|Flags|
|UBYTE|初構的大小|
|UBYTE|回溯程式碼的計數|
|UBYTE：4|畫面格暫存器|
|UBYTE：4|調整)  (框架暫存器位移|
|USHORT \* n|回溯代碼陣列|
|變動|的格式可以是 (1) 或 (2) 下方|

 (1) 例外狀況處理常式

|大小|值|
|-|-|
|ULONG|例外狀況處理常式的位址|
|變動|特定語言的處理常式資料 (選擇性) |

 (2) 連鎖的回溯資訊

|大小|值|
|-|-|
|ULONG|函數開始位址|
|ULONG|函數結束位址|
|ULONG|回溯資訊位址|

UNWIND_INFO 結構必須在記憶體中對齊 DWORD。 以下是每個欄位所代表的意義：

- **版本**

   回溯資料的版本號碼，目前為1。

- **旗標**

   目前已定義三個旗標：

   |旗標|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 在尋找需要檢查例外狀況的函式時，函式具有應呼叫的例外狀況處理常式。|
   |`UNW_FLAG_UHANDLER`| 函數具有終止處理常式，應在回溯例外狀況時呼叫。|
   |`UNW_FLAG_CHAININFO`| 此回溯資訊結構不是此程式的主要結構。 相反地，連鎖的回溯資訊專案是先前 RUNTIME_FUNCTION 專案的內容。 如需詳細資訊，請參閱連鎖的回溯 [資訊結構](#chained-unwind-info-structures)。 如果設定此旗標，則必須清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 旗標。 此外，[框架暫存器] 和 [固定堆疊配置] 欄位的值必須與主要回溯資訊中的值相同。|

- **初構的大小**

   函數初構的長度（以位元組為單位）。

- **回溯程式碼的計數**

   回溯程式碼陣列中的位置數目。 某些回溯程式碼（例如 UWOP_SAVE_NONVOL）在陣列中需要一個以上的位置。

- **畫面格暫存器**

   如果是非零值，則函式會使用框架指標 (FP) ，而此欄位是用來做為框架指標的非靜態登錄的數目，並針對 UNWIND_CODE 節點的作業資訊欄位使用相同的編碼方式。

- **調整)  (框架暫存器位移 **

   如果 [框架暫存器] 欄位為非零值，則此欄位是在建立時套用至 FP 註冊之 RSP 的縮放位移。 實際的 FP 暫存器設定為 RSP + 16 \* 這個數位，允許從0到240的位移。 此位移允許將 FP 登錄指向動態堆疊框架的本機堆疊配置，以提供更好的程式碼密度（透過較短的指示）。  (也就是說，更多的指示可以使用8位帶正負號的位移格式。 ) 

- **回溯代碼陣列**

   專案的陣列，說明在非靜態登錄和 RSP 上的初構效果。 如需個別專案的意義，請參閱 UNWIND_CODE 一節。 基於對齊目的，這個陣列一律會有偶數的專案，而最後一個專案則可能未使用。 在這種情況下，陣列的長度會比回溯程式碼欄位計數所表示的長一。

- **例外狀況處理常式的位址**

   如果清除旗標 UNW_FLAG_CHAININFO，且已設定其中一個旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER，則為函式的特定語言例外狀況或終止處理常式的影像相對指標。

- **特定語言的處理常式資料**

   函數的特定語言例外狀況處理常式資料。 這項資料的格式未指定，且完全由使用中的特定例外狀況處理常式所決定。

- **連鎖的回溯資訊**

   如果設定了旗標 UNW_FLAG_CHAININFO，則 UNWIND_INFO 結構會以三個 UWORDs 結尾。  這些 UWORDs 代表連鎖回溯函式的 RUNTIME_FUNCTION 資訊。

### <a name="struct-unwind_code"></a>struct UNWIND_CODE

回溯程式碼陣列用來記錄在初構中影響非靜態暫存器和 RSP 的作業順序。 每個程式碼專案都有此格式：

|大小|值|
|-|-|
|UBYTE|初構中的位移|
|UBYTE：4|回溯操作程式碼|
|UBYTE：4|作業資訊|

陣列會依初構中的位移遞減順序排序。

#### <a name="offset-in-prolog"></a>初構中的位移

位移 (從執行這項作業之指令的開頭初) 開始，再加上 1 (也就是下一個指令的開始位移) 。

#### <a name="unwind-operation-code"></a>回溯操作程式碼

注意：某些作業代碼需要本機堆疊框架值的不帶正負號位移。 此位移是從開始，也就是固定堆疊配置的最小位址。 如果 UNWIND_INFO 中的 [框架暫存器] 欄位為零，則此位移是來自 RSP。 如果畫面格暫存器欄位為非零值，則在建立 FP 暫存器時，這個位移會從 RSP 所在位置。 它等於 FP 登錄減去 FP 暫存器位移 (16 在 \* UNWIND_INFO) 中縮放的框架暫存器位移。 如果使用 FP 暫存器，則只有在初構中建立 FP 註冊之後，才需要使用任何採用位移的回溯程式碼。

除了和以外的所有操作碼 `UWOP_SAVE_XMM128` `UWOP_SAVE_XMM128_FAR` ，此位移一律為8的倍數，因為所有相關的堆疊值都儲存在8個位元組的界限上 (堆疊本身一律是16位元組對齊的) 。 針對取得短位移 (小於 512K) 的作業程式碼，此程式碼節點中的最後 USHORT 會保留位移除以8。 針對採用長位移 (512K <= 位移 < 4GB) 的作業碼，此程式碼的最後兩個 USHORT 節點會以位元組由大到小的格式來保存位移 (。

若為 opcode `UWOP_SAVE_XMM128` 和 `UWOP_SAVE_XMM128_FAR` ，則位移一律為16的倍數，因為所有128位 XMM 作業都必須發生在16位元組對齊的記憶體上。 因此，會使用縮放比例 16 `UWOP_SAVE_XMM128` ，允許小於1百萬的位移。

回溯作業程式碼是下列其中一個值：

- `UWOP_PUSH_NONVOL` (0) 1 個節點

  推送非靜態整數暫存器，並將 RSP 遞減8。 作業資訊是註冊的編號。 由於 epilogs 的條件約束，回溯程式 `UWOP_PUSH_NONVOL` 代碼必須先出現在初構中，並相對地出現在回溯程式碼陣列中。 除了以外，這個相對順序會套用至所有其他回溯代碼 `UWOP_PUSH_MACHFRAME` 。

- `UWOP_ALLOC_LARGE` (1) 2 或3個節點

  配置堆疊上的大尺寸區域。 有兩種形式。 如果作業資訊等於0，則配置的大小除以8會記錄在下一個插槽中，允許配置最多為 512K-8。 如果作業資訊等於1，則配置的未縮放大小會以位元組由小到大的格式記錄在接下來的兩個位置中，並允許配置高達 4GB-8。

- `UWOP_ALLOC_SMALL` (2) 1 節點

  配置堆疊上的小尺寸區域。 配置的大小是作業資訊欄位 \* 8 + 8，可允許從8到128個位元組的配置。

  堆疊配置的回溯程式碼應該一律使用可能最短的編碼：

  |**配置大小**|**回溯程式碼**|
  |-|-|
  |8到128位元組|`UWOP_ALLOC_SMALL`|
  |136至 512K-8 個位元組|`UWOP_ALLOC_LARGE`，操作資訊 = 0|
  |512K 至 4G-8 個位元組|`UWOP_ALLOC_LARGE`，操作資訊 = 1|

- `UWOP_SET_FPREG` (3) 1 節點

  藉由將暫存器設定為目前 RSP 的某個位移來建立框架指標暫存器。 位移等於框架暫存器位移， (在 UNWIND_INFO 16 中調整) 欄位 \* ，允許從0到240的位移。 使用位移可建立指向固定堆疊配置中間的框架指標，藉由允許更多的存取權來使用簡短的指令表單，以協助代碼濃度。 [作業資訊] 欄位是保留的，不應該使用。

- `UWOP_SAVE_NONVOL` (4) 2 個節點

  使用 MOV 而非 PUSH，將非靜態整數暫存器儲存在堆疊上。 這段程式碼主要用於 *縮減換行*，其中會以先前配置的位置將靜態登錄儲存至堆疊。 作業資訊是註冊的編號。 相應增加的堆疊位移會記錄在下一個回溯操作程式碼位置中，如上面的附注所述。

- `UWOP_SAVE_NONVOL_FAR` (5) 3 個節點

  使用 MOV 而非推播，在堆疊上將非靜態整數暫存器儲存于較長的位移。 這段程式碼主要用於 *縮減換行*，其中會以先前配置的位置將靜態登錄儲存至堆疊。 作業資訊是註冊的編號。 無比例的堆疊位移會記錄在接下來的兩個回溯作業程式碼位置中，如上面的附注所述。

- `UWOP_SAVE_XMM128` (8) 2 個節點

  將非靜態 XMM 註冊的所有128位儲存在堆疊上。 作業資訊是註冊的編號。 相應增加的堆疊位移會記錄在下一個插槽中。

- `UWOP_SAVE_XMM128_FAR` (9) 3 個節點

  使用長位移，將非靜態 XMM 暫存器的所有128位儲存在堆疊上。 作業資訊是註冊的編號。 無比例的堆疊位移會記錄在接下來的兩個插槽中。

- `UWOP_PUSH_MACHFRAME` (10) 1 節點

  推送電腦框架。  此回溯程式碼可用來記錄硬體中斷或例外狀況的效果。 有兩種形式。 如果作業資訊等於0，則會在堆疊上推入其中一個框架：

  |Location|值|
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|舊 RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|把|

  如果作業資訊等於1，則其中一個框架已推送：

  |Location|值|
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|舊 RSP|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|把|
  |RSP|錯誤碼|

  此回溯程式碼一律會出現在虛擬初構中，這項程式永遠不會實際執行，而是出現在插斷常式的實際進入點之前，而且只是為了提供位置來模擬電腦框架的推播。 `UWOP_PUSH_MACHFRAME` 記錄模擬，這表示機器已在概念上完成此操作：

  1. Pop 將位址從堆疊頂端傳回到 *Temp*
  
  1. Push SS

  1. 推送舊的 RSP

  1. 推送 EFLAGS

  1. 推送 CS

  1. 推送 *暫存*

  1. 如果 op 資訊等於 1) ，推送錯誤碼 (

  模擬作業會將 `UWOP_PUSH_MACHFRAME` RSP 遞減 40 (op 資訊等於 0) 或 48 (op 資訊等於 1) 。

#### <a name="operation-info"></a>作業資訊

作業資訊位的意義取決於作業程式碼。 若要將一般用途的 (整數編碼) register，請使用此對應：

|bit|註冊|
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8到15|R8 至 R15|

### <a name="chained-unwind-info-structures"></a>連鎖的回溯資訊結構

如果設定了 UNW_FLAG_CHAININFO 旗標，則回溯資訊結構會是次要的結構，而共用例外狀況處理常式/連鎖資訊位址欄位則包含主要的回溯資訊。 此範例程式碼會抓取主要的回溯資訊，假設它 `unwindInfo` 是已設定 UNW_FLAG_CHAININFO 旗標的結構。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

連結資訊在兩種情況下很有用。 首先，它可用於非連續的程式碼區段。 藉由使用連結資訊，您可以減少所需的回溯資訊大小，因為您不需要從主要回溯資訊複製回溯程式碼陣列。

您也可以使用連結資訊來群組 volatile 登錄的儲存。 編譯器可能會延遲儲存某些 volatile 暫存器，直到它在函式進入初構之外。 您可以藉由在分組程式碼之前的函式部分取得主要回溯資訊來記錄它們，然後以非零大小的初構設定連結資訊，其中連結資訊中的回溯程式碼反映了非靜態暫存器的儲存。 在此情況下，回溯程式碼是 UWOP_SAVE_NONVOL 的所有實例。 不支援使用 PUSH 來儲存非靜態暫存器，或使用其他固定堆疊配置來修改 RSP 登錄的群組。

具有 UNW_FLAG_CHAININFO 集的 UNWIND_INFO 專案可以包含 UNWIND_INFO 專案也有 UNW_FLAG_CHAININFO 設定的 RUNTIME_FUNCTION 專案，有時也稱為 *多個縮減換行*。 最後，連鎖的回溯資訊指標會抵達已 UNW_FLAG_CHAININFO 清除的 UNWIND_INFO 專案。 此專案是主要 UNWIND_INFO 專案，指向實際的程式進入點。

## <a name="unwind-procedure"></a>回溯程式

回溯程式碼陣列會依遞減順序排序。 發生例外狀況時，作業系統會在內容記錄中儲存完整的內容。 接著會叫用例外狀況分派邏輯，以重複執行這些步驟來尋找例外狀況處理常式：

1. 使用儲存在內容記錄中的目前 RIP 來搜尋 RUNTIME_FUNCTION 資料表專案，此專案會描述) 之連結 UNWIND_INFO 專案的目前函式 (或函數部分。

1. 如果找不到任何函式資料表專案，則它會在分葉函式中，而 RSP 直接定址傳回指標。 位於 [RSP] 的 return 指標儲存在更新的內容中，模擬的 RSP 會遞增8，而且步驟1會重複。

1. 如果找到函式資料表專案，則 RIP 可以位於三個區域內：在初構中的) 、在初構中為 b) ，或在例外狀況處理常式可能涵蓋的程式碼中使用 c) 。

   - 案例) 如果 RIP 在終解內，則控制權會離開函式，此函式不能有與這個例外狀況相關聯的例外狀況處理常式，而且必須繼續進行終解，以計算呼叫端函式的內容。 為了判斷 RIP 是否在終下，會檢查來自 RIP 的程式碼資料流程。 如果該程式碼資料流程可以與合法終的尾端部分進行比對，則它會在終，並模擬終的剩餘部分，並在處理每個指令時更新內容記錄。 在此處理之後，步驟1會重複。

   - 案例 b) 如果 RIP 位於序言中，則控制項尚未進入函式，此函式不能有與這個例外狀況相關聯的例外狀況處理常式，而且必須復原初構的結果，才能計算呼叫端函式的內容。 如果從函式開始到 RIP 的距離小於或等於回溯資訊中編碼的初構大小，則此 RIP 會在初構中。 針對第一個專案的回溯程式碼陣列進行向前掃描（位移小於或等於函數開頭的 RIP 位移），然後復原回溯程式碼陣列中所有其餘專案的效果，就會將初構的效果展開。 接著會重複步驟1。

   - 案例 c) 如果 RIP 不在初構或終解內，且函式具有例外狀況處理常式 (UNW_FLAG_EHANDLER 設定) ，則會呼叫語言特定處理常式。 處理常式會掃描其資料，並適當地呼叫篩選函數。 特定語言的處理常式可能會傳回已處理的例外狀況，或搜尋將繼續進行。 它也可以直接起始回溯。

1. 如果語言特定的處理常式傳回已處理的狀態，則會繼續使用原始內容記錄來執行。

1. 如果沒有任何語言特定的處理常式，或處理常式傳回「繼續搜尋」狀態，則內容記錄必須展開至呼叫端的狀態。 它是藉由處理所有回溯程式碼陣列元素來完成，並復原每個元素的效果。 接著會重複步驟1。

涉及連鎖的回溯資訊時，仍會遵循這些基本步驟。 唯一的差別在於，當您將回溯程式碼陣列回溯至初構的效果時，一旦到達陣列的結尾，就會連結到父項回溯資訊，而整個回溯程式碼陣列就會在此找到。 此連結會繼續進行，直到到達沒有 UNW_CHAINED_INFO 旗標的回溯資訊，然後再完成其回溯程式碼陣列。

最小的回溯資料集是8個位元組。 這代表的函式只會配置128個位元組的堆疊或更少，而且可能儲存一個非動態登錄。 它也是零長度初構（沒有回溯程式碼）的連鎖回溯資訊結構的大小。

## <a name="language-specific-handler"></a>語言特定處理常式

每當設定旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 時，就會在 UNWIND_INFO 中顯示特定語言處理常式的相對位址。 如上一節所述，系統會在搜尋例外狀況處理常式時，或做為回溯的一部分來呼叫特定語言的處理常式。 它具有下列原型：

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** 會提供包含標準 Win64 定義之例外狀況記錄的指標。

**EstablisherFrame** 是此函式之固定堆疊配置的基底位址。

**CoNtextRecord** 會指向例外狀況引發時的例外狀況內容 (在例外狀況處理常式案例中) 或終止處理常式案例中 (目前的「回溯」內容) 。

**DispatcherCoNtext** 會指向此函數的發送器內容。 它具有下列定義：

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

**ControlPc** 是此函數內的 RIP 值。 這個值可以是例外狀況位址或控制項離開建立函式的位址。 此 RIP 用來判斷控制項是否在此函式內的某個受防護結構內，例如， `__try` 或的區塊 `__try` / **`__except`** `__try` / **`__finally`** 。

**Imagebase 設定** 是映射基底 (載入位址) 包含此函式的模組），以新增至函式專案中所使用的32位位移，以及用來記錄相對位址的回溯資訊。

**FunctionEntry** 會提供指向 RUNTIME_FUNCTION 函式專案的指標，其中包含此函式的函式和回溯資訊影像基底相對位址。

**EstablisherFrame** 是此函式之固定堆疊配置的基底位址。

**TargetIp** 提供選擇性的指示位址，指定回溯的接續位址。 如果未指定 **EstablisherFrame** ，則會忽略此位址。

**CoNtextRecord** 會指向例外狀況內容，以供系統例外狀況分派/回溯程式碼使用。

**LanguageHandler** 指向要呼叫的語言特定語言處理常式常式。

**HandlerData** 指向此函式的語言特定處理常式資料。

## <a name="unwind-helpers-for-masm"></a>MASM 的回溯 helper

為了撰寫適當的元件常式，有一組虛擬作業可以與實際的元件指令平行使用，以建立適當的 .pdata 和. .xdata。 另外還有一組宏，可簡化對最常見用途之虛擬作業的使用。

### <a name="raw-pseudo-operations"></a>原始虛擬作業

|虛擬操作|描述|
|-|-|
|PROC FRAME \[ ：*ehandler*]|讓 MASM 在. .xdata 中產生函數資料表專案，以處理函式的結構化例外狀況處理回溯行為。  如果有 *ehandler* ，則會在 .xdata 中輸入此程式做為語言特定的處理常式。<br /><br /> 使用 FRAME 屬性時，其後必須接著。ENDPROLOG 指示詞。  如果函式是 (如函式 [類型](../build/stack-usage.md#function-types) 中所定義的分葉函數) 則不需要 FRAME 屬性，就像這些虛擬作業的其餘部分一樣。|
|.PUSHREG *註冊*|使用序言中的目前位移，為指定的登錄編號產生 UWOP_PUSH_NONVOL 的回溯程式碼專案。<br /><br /> 請勿將它用於非動態整數暫存器。  若為 volatile 暫存器的推送，請使用。ALLOCSTACK 8，改為|
|..SETFRAME *register*， *offset*|使用指定的暫存器和位移，填入框架暫存器欄位和回溯資訊中的位移。 位移必須是16的倍數，且小於或等於240。 這個指示詞也會使用目前的序言位移，針對指定的登錄產生 UWOP_SET_FPREG 的回溯程式碼專案。|
|.ALLOCSTACK *大小*|產生序言中目前位移之指定大小的 UWOP_ALLOC_SMALL 或 UWOP_ALLOC_LARGE。<br /><br /> *大小*運算元必須是8的倍數。|
|.SAVEREG *register*， *offset*|使用目前的序言位移，為指定的暫存器產生 UWOP_SAVE_NONVOL 或 UWOP_SAVE_NONVOL_FAR 回溯程式碼專案，以及位移。 MASM 選擇最有效率的編碼方式。<br /><br /> *位移* 必須是正數，以及8的倍數。 *位移* 會相對於程式框架的基底（通常是在 RSP 中），或者，如果使用框架指標，則是不縮放的框架指標。|
|.SAVEXMM128 *register*， *offset*|使用目前的序言位移，產生指定之 XMM 暫存器的 UWOP_SAVE_XMM128 或 UWOP_SAVE_XMM128_FAR 回溯程式碼專案，以及位移。 MASM 選擇最有效率的編碼方式。<br /><br /> *位移* 必須是正數，以及16的倍數。  *位移* 會相對於程式框架的基底（通常是在 RSP 中），或者，如果使用框架指標，則是不縮放的框架指標。|
|.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME 程式 \[ *代碼*]|產生 UWOP_PUSH_MACHFRAME 回溯程式碼專案。 如果指定了選擇性的程式 *代碼* ，則會為回溯程式碼專案提供1的修飾詞。 否則修飾詞為0。|
|.ENDPROLOG|發出序言宣告結尾的信號。  必須發生在函數的前255個位元組中。|

以下是範例函式初構，其中會正確使用大部分的操作碼：

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

為了簡化 [原始虛擬操作](#raw-pseudo-operations)的使用，有一組巨集定義在 ksamd64 中，可用來建立一般的程式序言和結尾。

|巨集|描述|
|-|-|
|alloc_stack (n) |使用) 配置 (n 個位元組的堆疊框架 `sub rsp, n` ，併發出適當的回溯資訊 (. allocstack n) |
|save_reg *reg*， *loc*|將靜態登錄 *reg* 儲存在堆疊上的 RSP 位移 *loc*，併發出適當的回溯資訊。  (。 savereg reg，loc) |
|push_reg *reg*|將非 *靜態登錄登錄* 推入堆疊，併發出適當的回溯資訊。  (. pushreg reg) |
|rex_push_reg *reg*|使用2個位元組的推送，將靜態登錄儲存在堆疊上，併發出適當的回溯資訊 ( pushreg reg) 。  如果推送是函數中的第一個指示，請使用這個宏，以確保函式是可修補的。|
|save_xmm128 *reg*， *loc*|將非靜態 XMM 緩存 *器登錄儲存在堆疊* 上的 RSP 位移 *loc*，併發出適當的回溯資訊 ( savexmm128 reg、loc) |
|set_frame *reg*， *offset*|使用、或) ，將框架暫存器登錄 *設定為 RSP* + *offset* (， `mov` 並將 `lea` 適當的回溯資訊發出 (。 set_frame reg，offset) |
|push_eflags|將 eflags 推入 `pushfq` 指令，併發出適當的回溯資訊 (。 alloc_stack 8) |

以下是具有適當使用宏的範例函數初構：

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
