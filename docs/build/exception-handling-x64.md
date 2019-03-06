---
title: x64 例外狀況處理
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 7dab7f3b6593bf4eaed1b8c804deb915677ccf5b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422971"
---
# <a name="x64-exception-handling"></a>x64 例外狀況處理

結構化例外狀況處理和 c + + 例外狀況處理程式碼撰寫慣例和行為在 x64 上的概觀。 一般例外狀況處理的詳細資訊，請參閱[的 Visual c + + 例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>回溯例外狀況處理，偵錯工具支援的資料

許多資料結構所需的例外狀況處理和偵錯支援。

### <a name="struct-runtimefunction"></a>struct RUNTIME_FUNCTION

以資料表為基礎的例外狀況處理的配置堆疊空間，或呼叫另一個函式 （例如，非分葉函式） 的所有函式需要資料表項目。 函式表項目具有格式：

|||
|-|-|
|ULONG|函式的起始位址|
|ULONG|函式結束位址|
|ULONG|回溯資訊位址|

RUNTIME_FUNCTION 結構必須是在記憶體中的對齊的 DWORD。 所有位址都是相對的映像，也就是它們與包含的函式表項目之映像的起始位址的 32 位元位移。 這些項目會經過排序，並放在 PE32 + 映像的.pdata 區段。 針對動態產生的函式 [JIT 編譯器]，執行階段支援這些函式必須使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 提供此資訊給作業系統。 若要這樣做會導致不可靠的例外狀況處理和偵錯的處理序。

### <a name="struct-unwindinfo"></a>struct UNWIND_INFO

回溯資料資訊結構用來記錄函式具有堆疊指標和靜態暫存器儲存在堆疊上的效果：

|||
|-|-|
|UBYTE:3|版本|
|UBYTE:5|旗標|
|UBYTE|初構的大小|
|UBYTE|回溯程式碼的計數|
|UBYTE:4|框架註冊|
|UBYTE:4|框架註冊位移 （調整）|
|USHORT \* n|回溯程式碼陣列|
|變數|可以是表單的 （1） 或 （2） 以下版本嗎|

（1） 例外狀況處理常式

|||
|-|-|
|ULONG|例外狀況處理常式的位址|
|變數|語言特有的處理常式資料 （選擇性）|

（2） 鏈結的回溯資訊

|||
|-|-|
|ULONG|函式的起始位址|
|ULONG|函式結束位址|
|ULONG|回溯資訊位址|

UNWIND_INFO 結構必須是在記憶體中的對齊的 DWORD。 以下是每個欄位的意義：

- **版本**

   回溯資料，目前 1 的版本號碼。

- **旗標**

   目前定義三個旗標：

   |旗標|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 函式有想要檢查例外狀況的函式時，應該呼叫例外狀況處理常式。|
   |`UNW_FLAG_UHANDLER`| 函式具有回溯例外狀況時，應該呼叫終止處理常式。|
   |`UNW_FLAG_CHAININFO`| 這樣的回溯資訊結構並不是主要程序。 相反地，鏈結的回溯資訊項目是先前的 RUNTIME_FUNCTION 項目的內容。 資訊，請參閱 < [Chained 回溯資訊結構](#chained-unwind-info-structures)。 如果設定此旗標，則必須先清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 旗標。 此外，框架登錄 」 以及 「 固定的堆疊配置欄位必須具有相同的值和主要的回溯資訊。|

- **初構的大小**

   函式初構，以位元組為單位的長度。

- **回溯程式碼的計數**

   回溯程式碼陣列中的位置數目。 部分回溯程式碼，例如 UWOP_SAVE_NONVOL，需要在陣列中的多個位置。

- **框架註冊**

   如果是非零值，然後此函數會使用框架指標 (FP)，且此欄位做為框架指標，使用相同的編碼方式和 UNWIND_CODE 節點的 [作業資訊] 欄位之靜態暫存器的數目。

- **框架註冊 （調整） 的位移**

   如果框架註冊欄位為非零值，這個欄位是從套用至 FP RSP 縮放的位移時建立就是註冊。 實際的 fp 暫存器設為 RSP + 16\*這個數字，允許從 0 到 240 的位移。 這個位移會允許指向中間以動態的堆疊框架，允許更好的程式碼密度，透過較短的指令 （詳細指示可以使用 8 位元帶正負號位移的形式） 的本機堆疊配置的 fp 暫存器。

- **回溯程式碼陣列**

   靜態暫存器和 RSP 說明效果的初構項目的陣列。 請參閱區段和 UNWIND_CODE 相關的個別項目的意義。 用於對齊用途，此陣列一律會有偶數數目的項目，而且最後一個項目可能未使用。 在此情況下，陣列是一個超過指出回溯程式碼欄位的計數。

- **例外狀況處理常式的位址**

   函式的語言特定的例外狀況或終止處理常式，如果 UNW_FLAG_CHAININFO 的旗標已清除，且其中一個旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 設定相對映像的指標。

- **語言特有的處理常式的資料**

   函式的特定語言的例外狀況處理常式的資料。 這些資料的格式是未指定，並完全取決於使用中的特定例外狀況處理常式。

- **鏈結的回溯資訊**

   如果設定旗標 UNW_FLAG_CHAININFO UNWIND_INFO 結構結尾三個 UWORDs。  這些 UWORDs 代表函式的鏈結的回溯 RUNTIME_FUNCTION 的資訊。

### <a name="struct-unwindcode"></a>struct UNWIND_CODE

回溯程式碼陣列用來記錄會影響到 RSP 與靜態暫存器的初構中的一系列的作業。 每個程式碼項目具有下列格式：

|||
|-|-|
|UBYTE|初構中的位移|
|UBYTE:4|回溯作業程式碼|
|UBYTE:4|作業資訊|

陣列是由初構中的位移的遞減順序排序。

#### <a name="offset-in-prolog"></a>初構中的位移

從執行這項作業，再加上 1 （也就是下一個指令開始的位移） 的指示結尾的初構開頭的位移。

#### <a name="unwind-operation-code"></a>回溯作業程式碼

注意:某些作業程式碼需要的不帶正負號的位移，在本機的堆疊框架中的值。 這個位移會從開始時，也就是固定的堆疊配置的最小位址。 如果框架註冊中的欄位 UNWIND_INFO 為零，此位移為 from RSP。 如果框架註冊 欄位為非零值，這會是從 RSP 所在 fp 暫存器建立時的位移。 此值等於減 FP 暫存器位移 fp 暫存器 (16\*縮放的框架註冊 UNWIND_INFO 中的位移)。 如果使用 fp 暫存器，然後採用位移任何回溯程式碼只能用於初構中建立的 FP 暫存器之後。

針對以外的所有作業碼`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`位移一律是 8 的倍數，因為所有堆疊 （堆疊本身是一律對齊 16 位元組） 的 8 位元組界限上儲存感興趣的值。 如需簡短的位移 (不超過 512 K) 的作業碼，最終的 USHORT 的節點，此程式碼中會保留除以 8 的位移。 針對需要較長的位移的作業程式碼 (512 K < = 位移 < 4 GB)，最後兩個 USHORT 節點，此程式碼會容納位移 （以位元組由小到大格式）。

針對 opcode`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`，位移永遠是倍數的 16 個，因為所有的 128 位元 XMM 作業必須發生在 16 位元組對齊的記憶體上。 因此，16 縮放比例就會用於`UWOP_SAVE_XMM128`，允許小於 1 百萬個的位移。

回溯作業程式碼是下列值之一：

- `UWOP_PUSH_NONVOL` (0) 1 個節點

  推送靜態整數暫存器，遞減 RSP 8。 作業資訊是暫存器的數目。 由於在終，限制`UWOP_PUSH_NONVOL`回溯程式碼必須出現在初構中的第一次，而同樣地，最後一個回溯程式碼陣列中。 此相對順序適用於所有其他回溯程式碼，除了`UWOP_PUSH_MACHFRAME`。

- `UWOP_ALLOC_LARGE` （1) 2 或 3 個節點

  配置堆疊上的大型區域。 有兩種形式。 如果作業資訊會等於 0，則除以配置的大小 8 會記錄到下一個位置，讓配置的上限為 512 K-8。 如果作業資訊會等於 1，則允許配置的位元組由小到大格式的下面兩個插槽中記錄的配置未縮放的大小達 4 GB-8。

- `UWOP_ALLOC_SMALL` （2) 1 個節點

  配置堆疊上的小型區域。 配置的大小是作業的 [資訊] 欄位\*8 + 8，允許從 8 到 128 個位元組的配置。

  堆疊配置的回溯程式碼應該一律使用最短的可能編碼方式：

  |**配置大小**|**回溯程式碼**|
  |-|-|
  |8 到 128 個位元組|`UWOP_ALLOC_SMALL`|
  |第 136 到 512-8 個位元組|`UWOP_ALLOC_LARGE`作業資訊 = 0|
  |512 K 到 4 G-8 個位元組|`UWOP_ALLOC_LARGE`作業資訊 = 1|

- `UWOP_SET_FPREG` （3) 1 個節點

  建立框架指標暫存器的目前 RSP 一些位移，以設定暫存器。 位移等於框架註冊位移 （縮放） 欄位中 UNWIND_INFO \* 16，允許從 0 到 240 的位移。 使用位移允許建立框架指標，指向 固定的堆疊配置，有助於藉由使用更多的存取，使用簡短的指令形式的程式碼的密度的中間。 [作業資訊] 欄位已保留，並不應該使用。

- `UWOP_SAVE_NONVOL` （4） 2 個節點

  將靜態整數暫存器儲存使用 MOV，而不推入堆疊上。 此程式碼主要用於*包裝*、 靜態暫存器儲存到先前配置的位置中的堆疊的位置。 作業資訊是暫存器的數目。 調整由-8 堆疊位移會記錄在下一個回溯作業程式碼位置，如以上所述。

- `UWOP_SAVE_NONVOL_FAR` （5） 3 個節點

  將靜態整數暫存器儲存長時間的位移，而不推播使用 MOV 與在堆疊上。 此程式碼主要用於*包裝*、 靜態暫存器儲存到先前配置的位置中的堆疊的位置。 作業資訊是暫存器的數目。 無縮放的堆疊會記錄在接下來兩個回溯作業程式碼位置，如以上所述。

- `UWOP_SAVE_XMM128` （8） 2 個節點

  將所有的 128 位元靜態 xmm 暫存器儲存在堆疊上。 作業資訊是暫存器的數目。 縮放 x 16 堆疊位移會記錄在下一個位置。

- `UWOP_SAVE_XMM128_FAR` （9） 3 個節點

  將所有的 128 位元靜態 xmm 暫存器儲存以長位移堆疊上。 作業資訊是暫存器的數目。 未縮放的堆疊會記錄在下面兩個位置。

- `UWOP_PUSH_MACHFRAME` （10) 1 個節點

  推播機器框架。  這用來記錄硬體插斷或例外狀況的影響。 有兩種形式。 如果作業資訊會等於 0，這些框架的其中一個已推入堆疊：

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|舊 RSP|
  |RSP+16|EFLAGS|
  |RSP+8|CS|
  |RSP|RIP|

  如果作業資訊會等於 1，然後這些框架的其中一個已推送：

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|舊 RSP|
  |RSP+24|EFLAGS|
  |RSP+16|CS|
  |RSP+8|RIP|
  |RSP|錯誤碼|

  此回溯程式碼永遠會出現在空的初構，永遠不會實際執行，但改為出現之前的插斷常式，實際的進入點和存在只是為了提供一個位置來模擬電腦畫面格的推播。 `UWOP_PUSH_MACHFRAME` 會記錄該模擬，表示電腦已在概念上完成這項作業：

  1. 快顯至堆疊的頂端 RIP 傳回位址*Temp*
  
  1. 推播 SS

  1. 推入舊 RSP

  1. 推播 EFLAGS

  1. 推播 CS

  1. 推播*Temp*

  1. 推入錯誤碼 （如果 op 資訊等於 1）

  模擬`UWOP_PUSH_MACHFRAME`40 的作業遞減 RSP （作業資訊會等於 0） 或 48 （作業資訊會等於 1）。

#### <a name="operation-info"></a>作業資訊

作業資訊位元的意義取決於作業程式碼。 若要編碼的一般用途 (integer) 暫存器，請使用此對應：

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
|8 到 15|R15 的 R8|

### <a name="chained-unwind-info-structures"></a>鏈結的回溯資訊結構

如果已設定 UNW_FLAG_CHAININFO 旗標，則回溯資訊結構是次要，並共用例外狀況處理常式/鏈結-資訊的地址欄位包含主要的回溯資訊。 此範例程式碼會擷取主要回溯的詳細資訊，但前提`unwindInfo`是結構，其 UNW_FLAG_CHAININFO 旗標設定。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

鏈結的資訊可用於兩種情況。 首先，它可以用於非連續的程式碼區段。 藉由使用鏈結的資訊，您可以減少必要的回溯資訊，因為您沒有重複的回溯程式碼陣列，從主要的回溯資訊。

您也可以將變動性的暫存器儲存使用鏈結的資訊。 編譯器可能會延遲儲存一些動態暫存器，直到它超出函式項目初構。 您可以將此資訊記錄讓主要的回溯資訊所屬的群組程式碼之前，此函式，然後設定鏈結與為非零的初構，其中的鏈結資訊中的回溯程式碼反映的靜態暫存器儲存大小的資訊。 在此情況下，回溯程式碼是 UWOP_SAVE_NONVOL 的所有執行個體。 不支援使用推入儲存靜態暫存器，或使用其他固定的堆疊配置來修改 RSP 暫存器群組。

UNWIND_INFO 項目有 UNW_FLAG_CHAININFO 集合，可包含其 UNWIND_INFO 項目也會有設定，UNW_FLAG_CHAININFO RUNTIME_FUNCTION 項目，有時也稱為*多個包裝*。 最後，鏈結的回溯資訊指標抵達可清除; UNW_FLAG_CHAININFO UNWIND_INFO 項目這是主要的 UNWIND_INFO 項目，它會指向實際的程序進入點。

## <a name="unwind-procedure"></a>回溯程序

回溯程式碼陣列是以遞減順序排序。 發生例外狀況時，完整的內容會儲存為內容記錄中的作業系統。 例外狀況分派邏輯會再叫用，它會重複執行下列步驟來尋找例外狀況處理常式：

1. 您可以使用目前的內容記錄中儲存的 RIP，搜尋 RUNTIME_FUNCTION 資料表項目，用來描述目前的函式 （或函式的部分，鏈結 UNWIND_INFO 項目）。

1. 如果找到任何函式表項目，它會在分葉函式，且 RSP 直接處理傳回的指標。 在 [RSP] 傳回的指標會儲存在已更新的內容、 模擬的 RSP 加 8，和會重複步驟 1。

1. 如果找到函式表項目，RIP 可以位於三個區域內： a） 在終解、 b） 在初構中，或 c） 在可能的例外狀況處理常式所涵蓋的程式碼。

   - 大小寫) 如果 RIP 是在終解，則控制項將離開函式可以有任何為此函式，此例外狀況相關聯的例外狀況處理常式，必須繼續終解效果，以計算呼叫端函式的內容。 若要判斷 RIP 是否在終解中，從擷取的程式碼資料流中，在檢查。 如果合法的終解中的尾端部分可符合該程式碼資料流處於終解中，然後模擬終解的其餘部分時，會處理與更新為每個指示的內容記錄。 在此之後，請重複步驟 1。

   - 案例 b） 如果 RIP 在序言，則控制項不進入函式可以有任何為此函式，此例外狀況相關聯的例外狀況處理常式，必須復原的初構效果，以計算呼叫端函式的內容。 RIP 是初構中，如果函式開始擷取之間的距離小於或等於初構大小，以回溯資訊編碼。 初構的效果是回溯掃描回溯程式碼陣列的位移小於或等於從函式開始時，RIP 位移的第一個項目，然後復原的回溯程式碼陣列中的所有剩餘項目的影響。 然後重複步驟 1。

   - 案例 c) 如果 RIP 不在初構和終解函式內 （設定 UNW_FLAG_EHANDLER） 的例外狀況處理常式，則會呼叫特定語言的處理常式。 處理常式會掃描其資料，並呼叫篩選為適當的函式。 語言特有的處理常式可以傳回已處理例外狀況，或搜尋是以繼續。 它也可以直接初始化回溯。

1. 如果語言特有的處理常式會傳回已處理的狀態，則執行會繼續使用原始的內容記錄。

1. 如果沒有任何語言特定處理常式或處理常式會傳回 「 繼續搜尋 」 的狀態，則內容記錄必須回溯至呼叫端的狀態。 這是藉由處理所有的回溯程式碼陣列項目，並復原每個作用中完成。 然後重複步驟 1。

當進行鏈結時回溯的相關資訊，還是會進行下列基本步驟。 唯一的差別是，雖然查核回溯初構的效果，一旦達到陣列結尾對回溯程式碼陣列，它會接著連結至父回溯資訊，並在那裡找到完整的回溯程式碼陣列便移動。 此連結會繼續直到到達不 UNW_CHAINED_INFO 旗標的回溯資訊問題，然後完成逐一查看其回溯程式碼陣列。

回溯資料以最小一組 8 個位元組。 這代表的函式只會配置 128 個位元組的堆疊或更少，並可能是儲存一個靜態暫存器。 這也是大小鏈結的回溯資訊結構的長度為零的初構沒有回溯程式碼使用。

## <a name="language-specific-handler"></a>語言特有的處理常式

每當設定旗標 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER UNWIND_INFO 中有語言特定處理常式的相對位址。 上一節所述，語言特有的處理常式稱為例外狀況處理常式中搜尋的一部分，或做為回溯的一部分。 其為這個原型：

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**Exception_record**提供例外狀況記錄，其具有標準 Win64 定義的指標。

**EstablisherFrame**是固定的堆疊配置，此函式的基底的位址。

**ContextRecord**點，以在引發例外狀況 （例外狀況處理常式案例中） 的時間或目前的例外狀況內容的 「 回溯 」 （在終止處理常式案例中） 的內容。

**DispatcherContext**指向此函式的發送器內容。 它擁有此定義：

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

**ControlPc** RIP 內此函式的值。 這個值會是例外狀況的地址或處控制保留建立的函式的位址。 擷取用來判斷控制項是否在某些受防護的建構內此函式，例如`__try`封鎖`__try` / `__except`或是`__try` / `__finally`。

**將 ImageBase**是映像基底 （載入位址） 的模組，其中包含此函式，新增至函式項目中所使用的 32 位元位移並回溯記錄相對位址的資訊。

**FunctionEntry**供應器的指標 RUNTIME_FUNCTION 函式保留函式的項目，並回溯此函式的資訊映像基底相對位址。

**EstablisherFrame**是固定的堆疊配置，此函式的基底的位址。

**TargetIp**提供選擇性的指令位址會指定回溯的接續位址。 如果，則會忽略這個地址**EstablisherFrame**未指定。

**ContextRecord**指向例外狀況的內容，以供系統例外狀況分派/回溯程式碼。

**LanguageHandler**指向特定語言的語言處理常式呼叫。

**HandlerData**指向此函式的語言特有的處理常式資料。

## <a name="unwind-helpers-for-masm"></a>MASM 的回溯 helper

若要撰寫適當的組件常式，沒有一組可用以平行方式，與實際組件的指示來建立適當的.pdata 和.xdata 的虛擬作業。 有一組提供的巨集也簡化了其最常見的用途的虛擬作業使用。

### <a name="raw-pseudo-operations"></a>未經處理的虛擬作業

|虛擬作業|描述|
|-|-|
|處理序框架\[:*ehandler*]|原因產生函式的 MASM 表項目中的.pdata 和回溯.xdata 中的資訊的函式的結構化例外狀況處理回溯行為。  如果*ehandler*已存在，此程序輸入中做為語言特定處理常式.xdata。<br /><br /> 使用框架屬性時，它必須後面。ENDPROLOG 指示詞。  如果函式的分葉函式 (如同[函式類型](../build/stack-usage.md#function-types)) 框架屬性是不必要的因為這些虛擬作業的其餘部分。|
|.PUSHREG *register*|產生使用目前的位移在序言中指定的暫存器編號 UWOP_PUSH_NONVOL 回溯程式碼項目。<br /><br /> 這應該只用於靜態整數暫存器。  動態暫存器的推播，使用。ALLOCSTACK 8，改為|
|.SETFRAME*註冊*，*位移*|在 框架填滿欄位位移在中註冊和使用指定的暫存器和位移的回溯資訊。 位移必須是 16 的倍數，且小於或等於 240。 這個指示詞也會產生使用目前的序言位移指定的暫存器的 UWOP_SET_FPREG 回溯程式碼項目。|
|.ALLOCSTACK*大小*|產生 UWOP_ALLOC_SMALL 或與目前的位移的指定大小的 UWOP_ALLOC_LARGE 序言中。<br /><br /> *大小*運算元必須是 8 的倍數。|
|.SAVEREG*註冊*，*位移*|產生 UWOP_SAVE_NONVOL 或指定的註冊和使用目前的序言位移的位移 UWOP_SAVE_NONVOL_FAR 回溯程式碼項目。 MASM 會選擇最有效率的編碼方式。<br /><br /> *位移*必須是正數且 8 的倍數。 *位移*相對於基底的程序的框架，通常是 RSP，或者，如果使用框架指標時，未調整的框架指標。|
|.SAVEXMM128*註冊*，*位移*|產生 UWOP_SAVE_XMM128 或使用目前的序言位移的位移與指定的 XMM 暫存器的 UWOP_SAVE_XMM128_FAR 回溯程式碼項目。 MASM 會選擇最有效率的編碼方式。<br /><br /> *位移*必須是正數且 16 的倍數。  *位移*相對於基底的程序的框架，通常是 RSP，或者，如果使用框架指標時，未調整的框架指標。|
|.PUSHFRAME \[*code*]|產生 UWOP_PUSH_MACHFRAME 回溯程式碼項目。 如果選擇性*程式碼*指定，則回溯程式碼項目指定為 1 的修飾詞。 否則修飾詞為 0。|
|.ENDPROLOG|結束的信號序言宣告。  必須存在於函式的第一個的 255 個位元組。|

以下是範例函式初構與大部分的作業碼的正確用法：

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
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>MASM 巨集

為了簡化使用[未經處理的虛擬作業](#raw-pseudo-operations)，沒有一組巨集，定義於 ksamd64.inc，可用來建立一般的程序序言和結尾。

|巨集|描述|
|-|-|
|alloc_stack(n)|N 個位元組的堆疊框架的配置 (使用`sub rsp, n`)，並發出適當的回溯資訊 (.allocstack n)|
|save_reg *reg*，*當地語系化*|將儲存靜態暫存器*reg* RSP 在堆疊上的位移*loc*，並發出適當的回溯資訊。 (.savereg reg，loc)|
|push_reg *reg*|將推入靜態暫存器*reg*在堆疊上，並發出適當的回溯資訊。 (.pushreg reg)|
|rex_push_reg *reg*|使用 2 位元組推入堆疊上儲存靜態暫存器，並會發出適當的回溯的資訊 (.pushreg reg)，這應該用於推播是以確保函式是經常性存取-可修補函式中的第一個指令。|
|save_xmm128 *reg*，*當地語系化*|將儲存靜態暫存的 xmm 暫存器*reg* RSP 在堆疊上的位移*loc*，並發出適當的回溯資訊 （.savexmm128 reg、 當地語系化）|
|set_frame *reg*，*位移*|設定框架註冊*reg*要 RSP +*位移*(使用`mov`，或有`lea`)，並發出適當的回溯資訊 （.set_frame reg、 位移）|
|push_eflags|推送與 eflags`pushfq`指令，並發出適當的回溯資訊 (.alloc_stack 8)|

以下是範例函式初構與巨集的正確用法：

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>中的回溯資料定義 C

以下是 C 描述的回溯資料：

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
