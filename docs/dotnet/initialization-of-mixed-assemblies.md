---
title: 混合組件的初始化
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 35dd47bd87c278d60fc616dca854bf843acc7c57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311772"
---
# <a name="initialization-of-mixed-assemblies"></a>混合組件的初始化

Windows 開發人員在期間`DllMain`執行程式碼時，一定要小心謹慎地載入器鎖定。 不過，在處理C++/clr 混合模式元件時，還有一些額外的問題需要考慮。

[DllMain](/windows/win32/Dlls/dllmain)內的程式碼不得存取 .Net Common Language RUNTIME （CLR）。 這表示`DllMain`不應直接或間接呼叫 managed 函式; 不應在中`DllMain`宣告或執行任何 managed 程式碼; 而且不應該`DllMain`在中進行垃圾收集或自動程式庫載入.

## <a name="causes-of-loader-lock"></a>載入器鎖定的原因

隨著 .NET 平臺的引進，載入執行模組（EXE 或 DLL）的方式有兩種：一個用於 Windows，一個用於非受控模組，另一個則用於載入 .NET 元件的 CLR。 混合 DLL 載入問題主要與 Microsoft Windows 作業系統載入器相關。

當您將只包含 .NET 建構的組件載入處理序時，CLR 載入器本身就能執行所有必要的載入和初始化工作。 不過，若是混合組件，因為它們可能包含機器碼和資料，所以還必須使用 Windows 載入器。

Windows 載入器可確保在初始化之前，程式碼不能存取該 DLL 中的程式碼或資料，而且程式碼在部分初始化時，不會重複載入 DLL。 若要這麼做，Windows 載入器會使用進程全域關鍵區段（通常稱為「載入器鎖定」），在模組初始化期間防止不安全的存取。 因此，載入程序很容易受到許多典型死結案例的危害。 若是混合組件，下列兩種案例會增加發生死結的風險：

- 首先，如果使用者在持有載入器鎖定時（例如從`DllMain`或在靜態初始化運算式中）嘗試執行編譯為 Microsoft 中繼語言（MSIL）的函式，則可能會造成鎖死。 請考慮 MSIL 函式參考尚未載入之元件中類型的情況。 CLR 會嘗試自動載入該組件，這可能需要 Windows 載入器對載入器鎖定進行封鎖。 發生鎖死的情況，因為呼叫順序中先前的程式碼已持有載入器鎖定。 不過，在載入器鎖定下執行 MSIL 並不保證會發生鎖死，這會使此案例難以診斷和修正。 在某些情況下，例如，當參考型別的 DLL 沒有包含原生結構，而且其所有相依性都不包含任何原生結構時，Windows 載入器不需要載入所參考類型的 .NET 元件。 此外，必要的組件或其混合的原生 (.NET) 相依性可能已由其他程式碼載入。 因此，死結的發生不僅很難預測，也會因目標電腦的組態而異。

- 第二，在 .NET Framework 的版本1.0 和1.1 中載入 Dll 時，CLR 會假設未持有載入器鎖定，並在載入器鎖定下執行數個不正確動作。 假設載入器鎖定並不是純粹 .NET Dll 的有效假設，但因為混合 Dll 會執行原生初始化常式，所以它們需要原生 Windows 載入器，因此載入器鎖定。 因此，即使開發人員未嘗試在 DLL 初始化期間執行任何 MSIL 函式，使用 .NET Framework 1.0 和 1.1 版還是有可能會出現不具決定性的死結 (但機率不高)。

在混合 DLL 載入程序中，所有不具決定性問題都已獲得解決。 這是使用下列變更來完成：

- 載入混合 DLL 時，CLR 不會再做出錯誤的假設。

- Unmanaged 和 Managed 初始化會在兩個獨立且相異的階段中執行。 未受管理的初始化會先進行（透過 DllMain），而 managed 初始化會在之後進行。支援`.cctor` NET 的結構。 除非使用 **/Zl** 或 **/NODEFAULTLIB** ，否則後者對於使用者是完全透明的。 如需詳細資訊，請參閱[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) 和 [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) 。

載入器鎖定仍然有可能發生，但現在能夠重現並偵測所發生的情況。 如果`DllMain`包含 MSIL 指令，編譯器會產生警告[編譯器警告（層級1） C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)。 此外，CRT 或 CLR 會嘗試偵測並回報在載入器鎖定下嘗試執行 MSIL。 CRT 偵測會產生執行階段診斷 C 執行階段錯誤 R6033。

本文件的其他部分將描述其他可以在載入器鎖定下執行 MSIL 的案例、每個案例所發生之問題的解決方法，以及偵錯技術。

## <a name="scenarios-and-workarounds"></a>案例和因應措施

在幾種不同的情況下，使用者程式碼可能會在載入器鎖定下執行 MSIL。 開發人員必須確保使用者程式碼實作在下列各種情況下都不會嘗試執行 MSIL 指令。 下列各節說明所有可能性，並討論如何解決最常見案例中的問題。

### <a name="dllmain"></a>DllMain

`DllMain`函數是 DLL 的使用者定義進入點。 除非使用者另外指定，否則每次處理序或執行緒附加至所包含的 DLL 或與其中斷連結時，都會叫用 `DllMain` 。 因為持有載入器鎖定時會發生此引動過程，所以使用者提供的 `DllMain` 函式不應該編譯為 MSIL。 此外，根目錄為 `DllMain` 的呼叫樹狀結構中的函式不可以編譯為 MSIL。 若要解決此處的問題，應該使用 #pragma `DllMain` 修改定義 `unmanaged`的程式碼區塊。 針對 `DllMain` 呼叫的每個函式，都應該執行相同的作業。

在某些情況下，這些函式必須呼叫要求其他呼叫內容有 MSIL 實作的函式，此時可以使用複製策略，以建立相同函式的 .NET 和原生版本。

或者，如果不需要 `DllMain` ，或不需要在載入器鎖定下執行，則可以移除使用者提供的 `DllMain` 實作，如此便可排除問題。

如果 DllMain 嘗試直接執行 MSIL，就會產生 [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 。 不過，如果是 DllMain 呼叫其他模組中的函式，進而嘗試執行 MSIL，編譯器就無法偵測到這些情況。

如需此案例的詳細資訊，請參閱[診斷的阻礙](#impediments-to-diagnosis)。

### <a name="initializing-static-objects"></a>初始化靜態物件

如果需要動態初始設定式，初始化靜態物件就可能會產生死結。 針對簡單的情況，例如將靜態變數指派給在編譯時期已知的值時，不需要動態初始化，因此不會有鎖死的風險。 不過，由函式呼叫、建構函式引動過程，或編譯期間無法評估的運算式所初始化的靜態變數，則要求在模組初始化期間執行程式碼。

下列程式碼示範需要動態初始化的靜態初始設定式：函式呼叫、物件建構和指標初始化 （這些範例不是靜態的，而是假設為全域範圍中所定義的，其效果相同）。

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

死結的風險取決於所包含的模組是否使用 **/clr** 進行編譯，以及是否會執行 MSIL。 具體來說，如果編譯靜態變數時不使用 **/clr** (或位於 #pragma `unmanaged` 區塊中)，而且初始化所需的動態初始設定式導致執行 MSIL 指令，則可能會發生死結。 這是因為針對未使用 **/clr**編譯的模組，會由 DllMain 執行靜態變數的初始化。 相反地，使用 **/clr**編譯的靜態變數會在未`.cctor`受管理的初始化階段完成，而且已釋放載入器鎖定之後，由初始化。

針對靜態變數的動態初始化所造成的死結，有幾個解決方案 (大致上依修正問題所需的時間順序排列)：

- 包含靜態變數的來源檔案，可使用 **/clr**進行編譯。

- 由靜態變數呼叫的所有函式可使用 #pragma `unmanaged` 指示詞編譯為機器碼。

- 以手動方式複製靜態變數所依賴的程式碼，並為 .NET 和原生版本指定不同的名稱。 接著，開發人員可從原生靜態初始設定式呼叫原生版本，並從別處呼叫 .NET 版本。

### <a name="user-supplied-functions-affecting-startup"></a>影響啟動的使用者提供函式

程式庫在啟動期間的初始化，會依賴數個使用者提供的函式。 例如， C++當全域多載運算子（例如`new`和`delete`運算子）時，使用者提供的版本會在任何地方使用，包括C++標準程式庫初始化和銷毀。 因此， C++標準程式庫和使用者提供的靜態初始化運算式會叫用這些運算子的任何使用者提供版本。

如果使用者提供的版本會編譯為 MSIL，則這些初始設定式會在持有載入器鎖定時嘗試執行 MSIL 指令。 使用者提供`malloc`的結果相同。 若要解決此問題，任何多載或使用者提供的定義，都必須使用 #pragma `unmanaged` 指示詞實作為機器碼。

如需此案例的詳細資訊，請參閱[診斷的阻礙](#impediments-to-diagnosis)。

### <a name="custom-locales"></a>自訂地區設定

如果使用者提供自訂的全域地區設定，則會使用此地區設定來初始化所有未來的 i/o 資料流程，包括靜態初始化的資料流程。 如果此全域地區設定物件會編譯為 MSIL，就可能在持有載入器鎖定時，叫用編譯為 MSIL 的地區設定物件成員函式。

有三個解決此問題的選項：

包含所有全域 I/O 資料流定義的來源檔案，可使用 **/clr** 選項進行編譯。 它會防止在載入器鎖定下執行其靜態初始化運算式。

自訂地區設定函式定義可使用 #pragma `unmanaged` 指示詞編譯為機器碼。

請等到釋放載入器鎖定之後，再將自訂地區設定設定為全域地區設定。 然後再明確設定初始化期間使用自訂地區設定建立的 I/O 資料流。

## <a name="impediments-to-diagnosis"></a>診斷的阻礙

在某些情況下，很容易偵測到鎖死的來源。 下列各節將討論這些案例及解決這些問題的方法。

### <a name="implementation-in-headers"></a>標頭中的實作

在選取的案例中，標頭檔內的函式實作可能會使診斷變得複雜。 內嵌函式和範本程式碼都要求必須在標頭檔中指定函式。  C++ 語言會指定「一個定義規則」，強制所有同名的函式實作在語意上相等。 因此，當合併的物件檔案具有指定函式的重複實作時，C++ 連結器不需要進行任何特殊的考量。

在 Visual Studio 2005 之前，連結器只會選擇這些語義上對等定義中的最大值，以容納向前宣告，以及針對不同的來源檔案使用不同優化選項的案例。 它會針對混合的 native/.NET Dll 建立問題。

因為啟用和停用 **/clr**的檔案可能C++會同時包含相同的標頭，或者 #include 可以`#pragma unmanaged`包裝在區塊內，所以可能會有 MSIL 和原生版本的函式，這些函式會在中提供實作為標題. MSIL 和原生實作針對在載入器鎖定下進行初始化有不同的語意，這實際上違反了「一個定義規則」。 因此，當連結器選擇最大的實作時，它可能會選擇 MSIL 版本的函式，即使在其他地方使用了 #pragma Unmanaged 指示詞明確編譯為機器碼亦然。 為確保不會在載入器鎖定下呼叫樣板或內嵌函式的 MSIL 版本，在載入器鎖定下呼叫的每個這類函數的每個`#pragma unmanaged`定義都必須使用指示詞進行修改。 如果標頭檔來自協力廠商，則進行這種變更最簡單的方式，就是在有問題`#pragma unmanaged`的標頭檔的 #include 指示詞前後，推送並彈出指示詞。 （如需範例，請參閱[受控、](../preprocessor/managed-unmanaged.md)不受管理）。不過，這項策略不適用於含有必須直接呼叫 .NET API 之其他程式碼的標頭。

為方便使用者處理載入器鎖定，若原生實作和 Managed 實作同時存在，連結器會優先選擇原生實作。 這個預設值會避免上述問題。 不過在這個版本中，因為編譯器有兩個尚未解決的問題，所以這項規則有兩個例外：

- 內嵌函式的呼叫是透過全域靜態函式指標。 這種情況很值得注意，因為虛擬函式是透過全域函式指標呼叫。 例如，套用至物件的

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

載入器鎖定問題的所有診斷都應該使用偵錯組建來完成。 發行組建可能不會產生診斷，而在發行模式中執行的最佳化可能會遮罩載入器鎖定情況下的部分 MSIL。

## <a name="how-to-debug-loader-lock-issues"></a>如何偵錯工具載入器鎖定問題

在叫用 MSIL 函式時，CLR 所產生的診斷會造成 CLR 暫停執行。 然後，這會導致視覺C++混合模式偵錯工具在進程中執行時，也會暫停。 不過，附加至進程時，無法使用混合偵錯工具來取得偵錯工具的 managed 呼叫堆疊。

若要識別在載入器鎖定下所呼叫的特定 MSIL 函式，開發人員應該完成下列步驟：

1. 確定可以使用 mscoree.dll 和 mscorwks.dll 的符號。

   您可以利用兩種方式來提供符號。 首先，您可以將 mscoree.dll 和 mscorwks.dll 的 PDB 加入符號搜尋路徑。 若要新增它們，請開啟 [符號搜尋路徑選項] 對話方塊。 （從 [**工具**] 功能表選擇 [**選項**]。 在 [**選項**] 對話方塊的左窗格中，開啟 [**調試**] 節點，然後選擇 [**符號**]）。將 mscoree.dll 和 mscorwks.dll PDB 檔案的路徑加入搜尋清單。 這些 PDB 會安裝到 %VSINSTALLDIR%\SDK\v2.0\symbols。 選擇 [確定]。

   其次，您可以從 Microsoft 符號伺服器下載 mscoree.dll 和 mscorwks.dll 的 PDB。 若要設定符號伺服器，請開啟 [symbol search path options] (符號搜尋路徑選項) 對話方塊。 （從 [**工具**] 功能表選擇 [**選項**]。 在 [**選項**] 對話方塊的左窗格中，開啟 [**調試**] 節點，然後選擇 [**符號**]）。將此搜尋路徑新增至搜尋清單： `https://msdl.microsoft.com/download/symbols`。 將符號快取目錄加入符號伺服器快取文字方塊。 選擇 [確定]。

1. 將偵錯工具模式設定為僅限原生模式。

   在方案中開啟啟始專案的 [**屬性**] 方格。 選取 [設定] [**屬性** > ] [**調試**]。 將 [**偵錯工具類型**] 設定為 [**僅限原生**]。

1. 啟動偵錯工具（F5）。

1. 產生 **/clr**診斷時，選擇 [**重試**]，然後選擇 [**中斷**]。

1. 開啟呼叫堆疊視窗 （在功能表列上，選擇 [ **Debug**  >  **Windows**  > **呼叫堆疊**]）。有問題`DllMain`的或靜態初始化運算式是以綠色箭號識別。 如果有未識別的違規函式，則必須採取下列步驟找到此函式。

1. 開啟 [即時**運算] 視窗**（在功能表列上，選擇 [ **Debug**  >  **Windows**  >  **Immediate**]）。

1. 在`.load sos.dll` [即時運算] 視窗中**輸入，以**載入 SOS 調試服務。

1. 在`!dumpstack` [即時**運算] 視窗中輸入，以**取得內部 **/clr**堆疊的完整清單。

1. 尋找任一 _CorDllMain （如果`DllMain`造成問題）或 _VTableBootstrapThunkInitHelperStub 或 GetTargetForVTableEntry （如果靜態初始化運算式造成問題）的第一個實例（最接近堆疊底部）。 此呼叫正下方的堆疊項目，會是在載入器鎖定下嘗試執行之 MSIL 實作函式的引動過程。

1. 移至在上一個步驟中識別的原始程式檔和行號，並使用案例一節中所述的案例和解決方案來更正問題。

## <a name="example"></a>範例

### <a name="description"></a>說明

下列範例示範如何透過將程式碼從`DllMain`移至全域物件的函式，以避免載入器鎖定。

在此範例中，有一個全域 managed 物件，其「函式」包含原本在中`DllMain`的 managed 物件。 這個範例的第二個部分會參考元件，並建立 managed 物件的實例，以叫用執行初始化的模組函式。

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
      printf_s("Test called so linker does not throw away unused object.\n");
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

這個範例會示範在初始化混合元件時的問題：

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

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
