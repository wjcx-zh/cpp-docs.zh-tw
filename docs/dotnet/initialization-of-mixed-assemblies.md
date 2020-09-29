---
title: 混合組件的初始化
description: 處理載入和初始化混合元件期間可能發生的問題。
ms.date: 09/26/2020
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 6767e6087999138f8e62d3c5a58f972b4e2149ed
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413810"
---
# <a name="initialization-of-mixed-assemblies"></a>混合組件的初始化

在期間執行程式碼時，Windows 開發人員一定要小心載入載入器鎖定 `DllMain` 。 不過，在處理 c + +/CLI 混合模式元件時，需要考慮一些其他問題。

[DllMain](/windows/win32/Dlls/dllmain)內的程式碼不得存取 .Net Common Language RUNTIME (CLR) 。 這表示，不 `DllMain` 應該直接或間接呼叫 managed 函式; 不應該在中宣告或執行 managed 程式碼，也 `DllMain` 不應該在中進行垃圾收集或自動程式庫載入 `DllMain` 。

## <a name="causes-of-loader-lock"></a>載入器鎖定的原因

隨著 .NET 平臺的推出，有兩個不同的機制可將執行模組載入 (EXE 或 DLL) ：一個適用于非受控模組，另一個用於 CLR，它會載入 .NET 元件。 混合 DLL 載入問題主要與 Microsoft Windows 作業系統載入器相關。

當僅包含 .NET 結構的元件載入至進程時，CLR 載入器可以執行所有必要的載入和初始化工作本身。 不過，若要載入可包含機器碼和資料的混合元件，也必須使用 Windows 載入器。

Windows 載入器保證在初始化程式碼之前，沒有任何程式碼可以存取該 DLL 中的程式碼或資料。 也可確保程式碼在部分初始化時，不會重複載入 DLL。 若要這樣做，Windows 載入器會使用進程全域關鍵區段 (通常稱為「載入器鎖定」 ) ，可在模組初始化期間防止不安全的存取。 因此，載入程序很容易受到許多典型死結案例的危害。 若是混合組件，下列兩種案例會增加發生死結的風險：

- 首先，如果使用者嘗試執行編譯為 Microsoft 中繼語言的函式 (MSIL) 當載入器鎖定 (自 `DllMain` 或靜態初始化運算式（例如) ）時，它可能會造成鎖死。 請考慮 MSIL 函數在尚未載入的元件中參考型別的情況。 CLR 會嘗試自動載入該組件，這可能需要 Windows 載入器對載入器鎖定進行封鎖。 因為先前在呼叫順序中的程式碼已持有載入器鎖定，所以會發生鎖死。 不過，在載入器鎖定下執行 MSIL 不保證會發生鎖死。 這就是這種情況很難診斷和修正。 在某些情況下（例如，當參考型別的 DLL 未包含原生結構，而且其所有相依性不包含任何原生結構）時，不需要 Windows 載入器載入所參考型別的 .NET 元件。 此外，必要的組件或其混合的原生 (.NET) 相依性可能已由其他程式碼載入。 因此，死結的發生不僅很難預測，也會因目標電腦的組態而異。

- 第二，在 .NET Framework 的1.0 和1.1 版中載入 Dll 時，CLR 會假設載入器鎖定不會被保留，並且會在載入器鎖定下採取數個不正確動作。 假設未持有載入器鎖定是單純 .NET Dll 的有效假設。 但是由於混合 Dll 會執行原生初始化常式，因此需要原生的 Windows 載入器，因此也需要載入器鎖定。 因此，即使開發人員在 DLL 初始化期間未嘗試執行任何 MSIL 函數，在 .NET Framework 版本1.0 和1.1 中仍有很小的非決定性鎖死。

在混合 DLL 載入程序中，所有不具決定性問題都已獲得解決。 這項變更已完成，但有下列變更：

- 載入混合 DLL 時，CLR 不會再做出錯誤的假設。

- 非受控和受控初始化是在兩個不同的階段中完成。 非受控初始化會先 `DllMain` 透過) 進行 (，而且之後會透過來進行 managed 初始化。支援 NET 的 `.cctor` 結構。 除非使用或，否則後者對使用者而言是完全透明的 **`/Zl`** **`/NODEFAULTLIB`** 。 如需詳細資訊，請參閱[ `/NODEFAULTLIB` (忽略程式庫) ](../build/reference/nodefaultlib-ignore-libraries.md)和[ `/Zl` (省略預設程式庫名稱) ](../build/reference/zl-omit-default-library-name.md)。

載入器鎖定仍然有可能發生，但現在能夠重現並偵測所發生的情況。 如果 `DllMain` 包含 MSIL 指令，編譯器會產生警告 [編譯器警告 (層級 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)。 此外，CRT 或 CLR 會嘗試偵測並回報在載入器鎖定下嘗試執行 MSIL。 CRT 偵測會產生執行階段診斷 C 執行階段錯誤 R6033。

本文的其餘部分將說明可在載入器鎖定下執行 MSIL 的其餘案例。 它會示範如何解決每個案例的問題，以及偵錯工具的方法。

## <a name="scenarios-and-workarounds"></a>案例和因應措施

在幾種不同的情況下，使用者程式碼可能會在載入器鎖定下執行 MSIL。 開發人員必須確保使用者程式碼的執行不會在每一種情況下嘗試執行 MSIL 指令。 下列各節說明所有可能性，並討論如何解決最常見案例中的問題。

### <a name="dllmain"></a>DllMain

`DllMain`函數是 DLL 的使用者定義進入點。 除非使用者另外指定，否則每次處理序或執行緒附加至所包含的 DLL 或與其中斷連結時，都會叫用 `DllMain` 。 因為持有載入器鎖定時會發生此引動過程，所以使用者提供的 `DllMain` 函式不應該編譯為 MSIL。 此外，根目錄為 `DllMain` 的呼叫樹狀結構中的函式不可以編譯為 MSIL。 若要解決此問題，您應該使用修改定義的程式碼區塊 `DllMain` `#pragma unmanaged` 。 針對 `DllMain` 呼叫的每個函式，都應該執行相同的作業。

如果這些函式必須呼叫需要 MSIL 實作為其他呼叫內容的函式，您可以使用重複的策略，同時建立 .NET 和原生版本的相同函式。

或者，如果不需要 `DllMain` 執行，或不需要在載入器鎖定下執行，您可以移除使用者提供的 `DllMain` 執行，以排除問題。

如果 `DllMain` 嘗試直接執行 MSIL，則會產生 [編譯器警告 (層級 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 。 不過，編譯器無法偵測 `DllMain` 呼叫另一個模組中的函式，進而嘗試執行 MSIL 的情況。

如需此案例的詳細資訊，請參閱 [診斷的阻礙](#impediments-to-diagnosis)。

### <a name="initializing-static-objects"></a>初始化靜態物件

如果需要動態初始設定式，初始化靜態物件就可能會產生死結。 簡單的案例 (例如，當您將編譯時間已知的值指派給靜態變數時) 不需要動態初始化，因此不會有鎖死的風險。 不過，某些靜態變數會由函式呼叫、函式調用，或無法在編譯時期評估的運算式初始化。 這些變數都需要在模組初始化期間執行程式碼。

下列程式碼示範需要動態初始化的靜態初始設定式：函式呼叫、物件建構和指標初始化  (這些範例並不是靜態的，但假設有全域範圍中的定義，其效果也相同。 ) 

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

這種鎖死的風險取決於所包含的模組是否使用編譯 **`/clr`** ，以及是否會執行 MSIL。 具體而言，如果靜態變數未 **`/clr`** (或在區塊) 中進行編譯 `#pragma unmanaged` ，而將它初始化所需的動態初始化運算式導致執行 MSIL 指令，則可能會發生鎖死。 這是因為在不使用編譯的模組中，會 **`/clr`** 由 DllMain 執行靜態變數的初始化。 相反地，使用編譯的靜態變數 **`/clr`** 會在 `.cctor` 未受管理的初始化階段完成並釋放載入器鎖定之後，由初始化。

動態初始化靜態變數時，有許多因應鎖死的解決方案。 這些問題大約會依照修正問題所需的時間順序排列在此處：

- 包含靜態變數的來源檔案可以使用編譯 **`/clr`** 。

- 靜態變數所呼叫的所有函式都可以使用指示詞編譯為機器碼 `#pragma unmanaged` 。

- 以手動方式複製靜態變數所依賴的程式碼，並為 .NET 和原生版本指定不同的名稱。 接著，開發人員可從原生靜態初始設定式呼叫原生版本，並從別處呼叫 .NET 版本。

### <a name="user-supplied-functions-affecting-startup"></a>影響啟動的使用者提供函式

程式庫在啟動期間的初始化，會依賴數個使用者提供的函式。 例如，在 c + + 中全域多載運算子（例如 **`new`** 和 **`delete`** 運算子）時，使用者提供的版本會在所有地方使用，包括 c + + 標準程式庫初始化和銷毀。 因此，c + + 標準程式庫和使用者提供的靜態初始化運算式將會叫用這些運算子的任何使用者提供版本。

如果使用者提供的版本會編譯為 MSIL，則這些初始設定式會在持有載入器鎖定時嘗試執行 MSIL 指令。 使用者提供 `malloc` 的結果相同。 若要解決這個問題，您必須使用指示詞，將這些多載或使用者提供的定義實作為原生程式碼 `#pragma unmanaged` 。

如需此案例的詳細資訊，請參閱 [診斷的阻礙](#impediments-to-diagnosis)。

### <a name="custom-locales"></a>自訂地區設定

如果使用者提供自訂的全域地區設定，則會使用此地區設定來初始化所有未來的 i/o 資料流程，包括靜態初始化的資料流程。 如果此全域地區設定物件會編譯為 MSIL，就可能在持有載入器鎖定時，叫用編譯為 MSIL 的地區設定物件成員函式。

有三個解決此問題的選項：

包含所有全域 i/o 資料流程定義的來源檔案，可以使用選項進行編譯 **`/clr`** 。 它會防止在載入器鎖定下執行其靜態初始化運算式。

您可以使用指示詞，將自訂地區設定函式定義編譯成機器碼 `#pragma unmanaged` 。

請等到釋放載入器鎖定之後，再將自訂地區設定設定為全域地區設定。 然後再明確設定初始化期間使用自訂地區設定建立的 I/O 資料流。

## <a name="impediments-to-diagnosis"></a>診斷的阻礙

在某些情況下，很難偵測到鎖死的來源。 下列各節將討論這些案例及解決這些問題的方法。

### <a name="implementation-in-headers"></a>標頭中的實作

在選取的案例中，標頭檔內的函式實作可能會使診斷變得複雜。 內嵌函式和範本程式碼都要求必須在標頭檔中指定函式。  C++ 語言會指定「一個定義規則」，強制所有同名的函式實作在語意上相等。 因此，當合併的物件檔案具有指定函式的重複實作時，C++ 連結器不需要進行任何特殊的考量。

在 Visual Studio 2005 之前的 Visual Studio 版本中，連結器只會選擇這些語義相等定義的最大值。 這樣做的目的是為了配合向前宣告，以及針對不同的原始程式檔使用不同的優化選項時的案例。 它會為混合的原生和 .NET Dll 建立問題。

因為 c + + 檔案可以同時包含相同的標頭（ **`/clr`** 啟用和停用），或者 #include 可以包裝在 `#pragma unmanaged` 區塊內，所以可以有 MSIL 和原生版本的函式可在標頭中提供實作為。 MSIL 和原生實作為載入器鎖定下的初始化有不同的語法，這實際上違反了一個定義規則。 因此，當連結器選擇最大的實值時，它可能會選擇 MSIL 版本的函式，即使在其他地方使用指示詞明確地編譯成機器碼 `#pragma unmanaged` 。 為了確保不會在載入器鎖定下呼叫 MSIL 版本的範本或內嵌函式，在載入器鎖定下呼叫的每個這類函式的每個定義都必須使用指示詞來修改 `#pragma unmanaged` 。 如果標頭檔是來自協力廠商，則進行這項變更最簡單的方式就是在 `#pragma unmanaged` 有問題的標頭檔的 #include 指示詞周圍推送和 pop 指示詞。  (請參閱 [受控、非受控](../preprocessor/managed-unmanaged.md) 的範例。 ) 不過，此策略不適用於包含其他必須直接呼叫 .net api 之程式碼的標頭。

為方便使用者處理載入器鎖定，若原生實作和 Managed 實作同時存在，連結器會優先選擇原生實作。 此預設值可避免上述問題。 不過，在此版本中，這項規則有兩個例外狀況，因為編譯器有兩個未解決的問題：

- 內嵌函式的呼叫是透過全域靜態函式指標。 這個案例 isn'table 的原因是虛擬函式是透過全域函式指標呼叫。 例如，

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>在偵錯模式中診斷

載入器鎖定問題的所有診斷都應該使用偵錯組建來完成。 發行組建可能不會產生診斷。 此外，在發行模式中進行的優化，可能會在載入器鎖定案例下遮罩某些 MSIL。

## <a name="how-to-debug-loader-lock-issues"></a>如何偵錯工具載入器鎖定問題

在叫用 MSIL 函式時，CLR 所產生的診斷會造成 CLR 暫停執行。 接著也會在執行中的偵錯工具時，使 Visual C++ 混合模式偵錯工具暫停。 不過，當附加至進程時，it'sn't 可能會使用混合偵錯工具取得偵錯工具的 managed 呼叫堆疊。

若要識別在載入器鎖定下所呼叫的特定 MSIL 函式，開發人員應該完成下列步驟：

1. 確定可以使用 mscoree.dll 和 mscorwks.dll 的符號。

   您可以利用兩種方式來提供符號。 首先，您可以將 mscoree.dll 和 mscorwks.dll 的 PDB 加入符號搜尋路徑。 若要加入它們，請開啟 [符號搜尋路徑選項] 對話方塊。 從 [ **工具** ] 功能表 (，選擇 [ **選項**]。 在 [ **選項** ] 對話方塊的左窗格中，開啟 [ **調試** 程式] 節點，然後選擇 [ **符號**]。 ) 將 mscoree.dll 和 mscorwks.dll PDB 檔案的路徑新增至搜尋清單。 這些 PDB 會安裝到 %VSINSTALLDIR%\SDK\v2.0\symbols。 選擇 [確定]。

   其次，您可以從 Microsoft 符號伺服器下載 mscoree.dll 和 mscorwks.dll 的 PDB。 若要設定符號伺服器，請開啟 [symbol search path options] (符號搜尋路徑選項) 對話方塊。 從 [ **工具** ] 功能表 (，選擇 [ **選項**]。 在 [ **選項** ] 對話方塊的左窗格中，開啟 [ **調試** 程式] 節點，然後選擇 [ **符號**]。 ) 將此搜尋路徑新增至搜尋清單： `https://msdl.microsoft.com/download/symbols` 。 將符號快取目錄加入符號伺服器快取文字方塊。 選擇 [確定]。

1. 將偵錯工具模式設定為僅限原生模式。

   在方案中開啟啟始專案的 [ **屬性** ] 方格。 選取設定**屬性**  >  的**調試**。 將 [ **偵錯工具類型** ] 屬性設定為 [ **僅限原生**]。

1. 啟動偵錯工具 (F5) 。

1. 當 **`/clr`** 診斷產生時，請選擇 [ **重試** ]，然後選擇 [ **中斷**]。

1. 開啟呼叫堆疊視窗  (在功能表列上，選擇 [ **Debug**  >  **Windows**  >  **呼叫堆疊**]。 ) `DllMain` 有問題或靜態初始化運算式以綠色箭號識別。 如果未識別出違規的函式，則必須採取下列步驟來尋找它。

1. 開啟功能表列上的 [即時**運算視窗]** (，選擇 [ **Debug**  >  **Windows**  >  **immediate**]。 ) 

1. `.load sos.dll`在 [即時運算] 視窗中**輸入，** 以載入 SOS 調試服務。

1. 在 `!dumpstack` [即時**Immediate**運算] 視窗中輸入，以取得內部堆疊的完整清單 **`/clr`** 。

1. 尋找最接近) 堆疊最底部的第一個實例 (_CorDllMain (如果 `DllMain` 靜態初始化運算式造成問題) ，則 _VTableBootstrapThunkInitHelperStub 或 GetTargetForVTableEntry (。 此呼叫正下方的堆疊項目，會是在載入器鎖定下嘗試執行之 MSIL 實作函式的引動過程。

1. 移至在上一個步驟中識別的原始程式檔和行號，並使用案例一節中所述的案例和解決方案來修正問題。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示如何將程式碼從移 `DllMain` 至全域物件的函式，以避免載入器鎖定。

在此範例中，有一個全域 managed 物件，其函式包含原本在中的 managed 物件 `DllMain` 。 此範例的第二個部分會參考元件，並建立 managed 物件的實例來叫用執行初始化的模組函式。

### <a name="code"></a>程式碼

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker doesn't throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

此範例示範混合元件的初始化問題：

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

此程式碼會產生下列輸出：

```Output
Module ctor initializing based on global instance of class.

Test called so linker doesn't throw away unused object.
```

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 元件](../dotnet/mixed-native-and-managed-assemblies.md)
