---
title: "初始化混合的組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e7d192387131ff0eaa04fc366254d7f78a73dd52
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="initialization-of-mixed-assemblies"></a>混合組件的初始化
在 Visual Studio 2005 之前編譯的 Dll **/clr**載入時，可能不具決定性死結編譯器選項; 此問題稱為混合的 DLL 載入器鎖定問題。 在混合 DLL 載入程序中，幾乎所有不具決定性問題都已獲得解決。 不過還是有些情況可能會發生載入器鎖定問題 (具決定性)。
  
 [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) 內的程式碼不得存取 CLR。 這表示 `DllMain` 不應該直接或間接呼叫 Managed 函式；Managed 程式碼不應該在 `DllMain`中宣告或實作；而且 `DllMain`內不應該發生記憶體回收或自動程式庫載入。  
  
> [!NOTE]
>  Visual C++ 2003 提供了 _vcclrit.h 以加速 DLL 初始化，同時將發生死結的機會降到最低。 您不再需要使用 _vcclrit.h，一旦使用即會導致在編譯期間產生取代警告。 建議的策略是使用 [Removing Deprecated Header File _vcclrit.h](http://msdn.microsoft.com/en-us/7881993e-431d-43e9-8c6d-0d2285a4882d)中的步驟移除此檔案中的相依性。 較不理想的解決方案是在包含 _vcclrit.h 之前先定義 `_CRT_VCCLRIT_NO_DEPRECATE` 以隱藏警告，或直接忽略取代警告。  
  
## <a name="causes-of-loader-lock"></a>載入器鎖定的原因  
 採用 .NET 平台後，會有兩種不同的載入執行模組 (EXE 或 DLL) 機制：一種適用於 Windows，可用於 Unmanaged 模組；另一種適用 .NET Common Language Runtime (CLR)，可載入 .NET 組件。 混合 DLL 載入問題主要與 Microsoft Windows 作業系統載入器相關。  
  
 當您將只包含 .NET 建構的組件載入處理序時，CLR 載入器本身就能執行所有必要的載入和初始化工作。 不過，若是混合組件，因為它們可能包含機器碼和資料，所以還必須使用 Windows 載入器。  
  
 Windows 載入器可確保在 DLL 初始化之前，所有程式碼都無法存取 DLL 的程式碼或資料，而且在 DLL 部分初始化時，所有程式碼都無法重複載入 DLL。 為了達成此目的，Windows 載入器使用處理序全域關鍵區段 (通常稱為「載入器鎖定」)，以防止在模組初始化期間有不安全的存取。 因此，載入程序很容易受到許多典型死結案例的危害。 若是混合組件，下列兩種案例會增加發生死結的風險：  
  
-   首先，如果使用者在持有載入器鎖定時嘗試執行編譯為 Microsoft Intermediate Language (MSIL) 的函式 (例如從 `DllMain` 或在靜態初始設定式中)，這可能會造成死結。 假設 MSIL 函式參考尚未載入之組件中的類型。 CLR 會嘗試自動載入該組件，這可能需要 Windows 載入器對載入器鎖定進行封鎖。 因為稍早在呼叫序列中的程式碼就已經持有載入器鎖定，所以會產生死結。 不過，在載入器鎖定下執行 MSIL 不一定會發生死結，因此很難診斷及修正此案例。 在某些情況下 (例如參考類型的 DLL 及其所有相依性都未包含原生建構時)，不需要 Windows 載入器來載入參考類型的 .NET 組件。 此外，必要的組件或其混合的原生 (.NET) 相依性可能已由其他程式碼載入。 因此，死結的發生不僅很難預測，也會因目標電腦的組態而異。  
  
-   其次，在 .NET Framework 1.0 和 1.1 版中載入 DLL 時，CLR 會假設未持有載入器鎖定，並會在載入器鎖定下執行幾個無效的動作。 假設未持有載入器鎖定是針對完全是 .NET DLL 的有效假設，但因為混合 DLL 執行原生初始化常式，所以需要原生 Windows 載入器而導致載入器鎖定。 因此，即使開發人員未嘗試在 DLL 初始化期間執行任何 MSIL 函式，使用 .NET Framework 1.0 和 1.1 版還是有可能會出現不具決定性的死結 (但機率不高)。  
  
 在混合 DLL 載入程序中，所有不具決定性問題都已獲得解決。 這是透過下列變更所達成︰  
  
-   載入混合 DLL 時，CLR 不會再做出錯誤的假設。  
  
-   Unmanaged 和 Managed 初始化會在兩個獨立且相異的階段中執行。 會先進行 Unmanaged 初始化 (透過 DllMain)，然後再進行 Managed 初始化 (透過稱為 *.cctor*的 .NET 支援建構)。 除非使用 **/Zl** 或 **/NODEFAULTLIB** ，否則後者對於使用者是完全透明的。 如需詳細資訊，請參閱[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) 和 [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) 。  
  
 載入器鎖定仍然有可能發生，但現在能夠重現並偵測所發生的情況。 如果 DllMain 包含 MSIL 指令，編譯器會產生警告： [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)。 此外，CRT 或 CLR 會嘗試偵測並回報在載入器鎖定下嘗試執行 MSIL。 CRT 偵測會產生執行階段診斷 C 執行階段錯誤 R6033。  
  
 本文件的其他部分將描述其他可以在載入器鎖定下執行 MSIL 的案例、每個案例所發生之問題的解決方法，以及偵錯技術。  
  
## <a name="scenarios-and-workarounds"></a>案例和因應措施  
 在幾種不同的情況下，使用者程式碼可能會在載入器鎖定下執行 MSIL。 開發人員必須確保使用者程式碼實作在下列各種情況下都不會嘗試執行 MSIL 指令。 下列各節說明所有可能性，並討論如何解決最常見案例中的問題。  
  
-   `DllMain`  
  
-   靜態初始設定式  
  
-   影響啟動的使用者提供函式  
  
-   自訂地區設定  
  
### <a name="dllmain"></a>DllMain  
 `DllMain` 函式是使用者定義的 DLL 進入點。 除非使用者另外指定，否則每次處理序或執行緒附加至所包含的 DLL 或與其中斷連結時，都會叫用 `DllMain` 。 因為持有載入器鎖定時會發生此引動過程，所以使用者提供的 `DllMain` 函式不應該編譯為 MSIL。 此外，根目錄為 `DllMain` 的呼叫樹狀結構中的函式不可以編譯為 MSIL。 若要解決此處的問題，應該使用 #pragma `DllMain` 修改定義 `unmanaged`的程式碼區塊。 針對 `DllMain` 呼叫的每個函式，都應該執行相同的作業。  
  
 在某些情況下，這些函式必須呼叫要求其他呼叫內容有 MSIL 實作的函式，此時可以使用複製策略，以建立相同函式的 .NET 和原生版本。  
  
 或者，如果不需要 `DllMain` ，或不需要在載入器鎖定下執行，則可以移除使用者提供的 `DllMain` 實作，如此便可排除問題。  
  
 如果 DllMain 嘗試直接執行 MSIL，就會產生 [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 。 不過，如果是 DllMain 呼叫其他模組中的函式，進而嘗試執行 MSIL，編譯器就無法偵測到這些情況。  
  
 如需此案例的詳細資訊，請參閱＜診斷的阻礙＞。  
  
### <a name="initializing-static-objects"></a>初始化靜態物件  
 如果需要動態初始設定式，初始化靜態物件就可能會產生死結。 在簡單的情況下 (例如將靜態變數僅指派給編譯時間已知的值時)，不需要動態初始化，因此不會有發生死結的風險。 不過，由函式呼叫、建構函式引動過程，或編譯期間無法評估的運算式所初始化的靜態變數，則要求在模組初始化期間執行程式碼。  
  
 下列程式碼示範需要動態初始化的靜態初始設定式：函式呼叫、物件建構和指標初始化 (這些範例並非靜態，而是假設定義於全域範圍內，因此有相同的效果)。  
  
```  
// dynamic initializer function generated  
int a = init();  
CObject o(arg1, arg2);    
CObject* op = new CObject(arg1, arg2);  
```  
  
 死結的風險取決於所包含的模組是否使用 **/clr** 進行編譯，以及是否會執行 MSIL。 具體來說，如果編譯靜態變數時不使用 **/clr** (或位於 #pragma `unmanaged` 區塊中)，而且初始化所需的動態初始設定式導致執行 MSIL 指令，則可能會發生死結。 這是因為在未使用 **/clr**編譯的模組中，會由 DllMain 執行靜態變數的初始化。 相反地，使用 **/clr** 編譯的靜態變數則是在 Unmanaged 初始化階段完成並釋放載入器鎖定之後，由 .cctor 進行初始化。  
  
 針對靜態變數的動態初始化所造成的死結，有幾個解決方案 (大致上依修正問題所需的時間順序排列)：  
  
-   包含靜態變數的來源檔案，可使用 **/clr**進行編譯。  
  
-   由靜態變數呼叫的所有函式可使用 #pragma `unmanaged` 指示詞編譯為機器碼。  
  
-   以手動方式複製靜態變數所依賴的程式碼，並為 .NET 和原生版本指定不同的名稱。 接著，開發人員可從原生靜態初始設定式呼叫原生版本，並從別處呼叫 .NET 版本。  
  
### <a name="user-supplied-functions-affecting-startup"></a>影響啟動的使用者提供函式  
 程式庫在啟動期間的初始化，會依賴數個使用者提供的函式。 例如，當全域多載運算子，在 c + + 例如`new`和`delete`運算子，使用者提供的版本會使用於各處，包括在 c + + 標準程式庫初始化和解構。 如此一來，c + + 標準程式庫和使用者提供的靜態初始設定式會叫用這些運算子的任何使用者提供的版本。  
  
 如果使用者提供的版本會編譯為 MSIL，則這些初始設定式會在持有載入器鎖定時嘗試執行 MSIL 指令。 使用者提供的 malloc 會有相同的結果。 若要解決此問題，任何多載或使用者提供的定義，都必須使用 #pragma `unmanaged` 指示詞實作為機器碼。  
  
 如需此案例的詳細資訊，請參閱＜診斷的阻礙＞。  
  
### <a name="custom-locales"></a>自訂地區設定  
 如果使用者提供自訂全域地區設定，此地區設定就會用來初始化日後所有的 I/O 資料流，包括靜態初始化的資料流。 如果此全域地區設定物件會編譯為 MSIL，就可能在持有載入器鎖定時，叫用編譯為 MSIL 的地區設定物件成員函式。  
  
 有三個解決此問題的選項：  
  
 包含所有全域 I/O 資料流定義的來源檔案，可使用 **/clr** 選項進行編譯。 如此可防止在載入器鎖定下執行其靜態初始設定式。  
  
 自訂地區設定函式定義可使用 #pragma `unmanaged` 指示詞編譯為機器碼。  
  
 請等到釋放載入器鎖定之後，再將自訂地區設定設定為全域地區設定。 然後再明確設定初始化期間使用自訂地區設定建立的 I/O 資料流。  
  
## <a name="impediments-to-diagnosis"></a>診斷的阻礙  
 在某些情況下，很難偵測死結的來源。 下列各節將討論這些案例及解決這些問題的方法。  
  
### <a name="implementation-in-headers"></a>標頭中的實作  
 在選取的案例中，標頭檔內的函式實作可能會使診斷變得複雜。 內嵌函式和範本程式碼都要求必須在標頭檔中指定函式。  C++ 語言會指定「一個定義規則」，強制所有同名的函式實作在語意上相等。 因此，當合併的物件檔案具有指定函式的重複實作時，C++ 連結器不需要進行任何特殊的考量。  
  
 在 Visual Studio 2005 之前，連結器只會選擇這些語意相等的定義，以配合向前宣告，以及案例不同最佳化選項用於不同原始程式檔時的最大值。 這會產生混合的原生/.NET DLL 的問題。  
  
 因為啟用和停用 **/clr** 的 CPP 檔案都可能包含相同的標頭，或是 #include 可能包裝在 #pragma `unmanaged` 區塊內，所以可能會有 MSIL 和原生版本的函式同時在標頭中提供實作。 MSIL 和原生實作針對在載入器鎖定下進行初始化有不同的語意，這實際上違反了「一個定義規則」。 因此，當連結器選擇最大的實作時，它可能會選擇 MSIL 版本的函式，即使在其他地方使用了 #pragma Unmanaged 指示詞明確編譯為機器碼亦然。 為了確保在載入器鎖定下絕不會呼叫 MSIL 版本的範本或內嵌函式，您必須使用 #pragma `unmanaged` 指示詞，來修改在載入器鎖定下呼叫之這類函式的所有定義。 如果標頭檔來自協力廠商，要達到這個目的，最簡單的方法就是在違規標頭檔的 #include 指示詞附近，推入和彈出 #pragma Unmanaged 指示詞 (請參閱[managed、 unmanaged](../preprocessor/managed-unmanaged.md)的範例。)不過，這項策略不適用於含有必須直接呼叫 .NET API 之其他程式碼的標頭。  
  
 為方便使用者處理載入器鎖定，若原生實作和 Managed 實作同時存在，連結器會優先選擇原生實作。  這可避免上述問題。  不過在這個版本中，因為編譯器有兩個尚未解決的問題，所以這項規則有兩個例外：  
  
-   內嵌函式是透過全域靜態函式指標呼叫。  此案例特別值得注意，因為虛擬函式是透過全域函式指標呼叫。  例如，套用至物件的  
  
```  
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
  
-   當編譯目標為 Itanium 時，所有函式指標的實作都會發生錯誤。  在上述範例中，如果已在 during_loaderlock() 內本機定義 myObject_p，則呼叫可能也會解析成 Managed 實作。  
  
### <a name="diagnosing-in-debug-mode"></a>在偵錯模式中診斷  
 載入器鎖定問題的所有診斷都應該使用偵錯組建來完成。 發行組建可能不會產生診斷，而在發行模式中執行的最佳化可能會遮罩載入器鎖定情況下的部分 MSIL。  
  
## <a name="how-to-debug-loader-lock-issues"></a>如何偵錯載入器鎖定問題  
 在叫用 MSIL 函式時，CLR 所產生的診斷會造成 CLR 暫停執行。 而這會造成在同處理序執行偵錯項目時，Visual C++ 混合模式偵錯工具也會跟著暫停。 不過，在附加至處理序時，不可能使用混合模式偵錯工具取得偵錯項目的 Managed 呼叫堆疊。  
  
 若要識別在載入器鎖定下所呼叫的特定 MSIL 函式，開發人員應該完成下列步驟：  
  
1.  確定可以使用 mscoree.dll 和 mscorwks.dll 的符號。  
  
     有兩種方法可以達到這個目的： 首先，您可以將 mscoree.dll 和 mscorwks.dll 的 PDB 加入符號搜尋路徑。 若要這樣做，請開啟 [symbol search path options] (符號搜尋路徑選項) 對話方塊。 (從 [工具] 功能表按一下 [選項]。 在 [選項] 對話方塊的左窗格中，開啟 [偵錯] 節點，然後按一下 [符號])。將 mscoree.dll 和 mscorwks.dll PDB 檔案的路徑加入搜尋清單。 這些 PDB 會安裝到 %VSINSTALLDIR%\SDK\v2.0\symbols。 按一下 [確定]。  
  
     其次，您可以從 Microsoft 符號伺服器下載 mscoree.dll 和 mscorwks.dll 的 PDB。 若要設定符號伺服器，請開啟 [symbol search path options] (符號搜尋路徑選項) 對話方塊。 (從 [工具] 功能表按一下 [選項]。 在 [選項] 對話方塊的左窗格中，開啟 [偵錯] 節點，然後按一下 [符號])。將下列搜尋路徑加入搜尋清單︰http://msdl.microsoft.com/download/symbols。 將符號快取目錄加入符號伺服器快取文字方塊。 按一下 [確定]。  
  
2.  將偵錯工具模式設定為僅限原生模式。  
  
     若要這樣做，請在解決方案中開啟啟始專案的 [屬性] 格線。 在 [組態屬性] 樹狀子目錄下，選取 [偵錯節點]。 將 [偵錯工具類型] 欄位設定為 [僅限原生]。  
  
3.  啟動偵錯工具 (F5)。  
  
4.  在產生 **/clr** 診斷之後，依序按一下 [重試] 和 [中斷]。  
  
5.  開啟呼叫堆疊視窗 (從 [偵錯] 功能表按一下 [Windows]，然後按一下 [呼叫堆疊])。如果違反`DllMain`或靜態初始設定式以綠色箭頭識別。 如果有未識別的違規函式，則必須採取下列步驟找到此函式。  
  
6.  開啟即時運算視窗 (從 [偵錯] 功能表按一下 [Windows]，然後按一下 [即時運算])。  
  
7.  在即時運算視窗中輸入 .load sos.dll，以載入 SOS 偵錯服務。  
  
8.  在即時運算視窗中輸入 !dumpstack，以取得內部 **/clr** 堆疊的完整清單。  
  
9. 尋找 _CorDllMain (如果問題的原因是 `DllMain` )、_VTableBootstrapThunkInitHelperStub 或 GetTargetForVTableEntry (如果問題的原因是靜態初始設定式) 的第一個執行個體 (最接近堆疊底部)。  此呼叫正下方的堆疊項目，會是在載入器鎖定下嘗試執行之 MSIL 實作函式的引動過程。  
  
10. 移至步驟 9 所識別的來源檔案和行號，並使用＜案例＞一節中所述的案例和解決方案來修正問題。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例示範如何將程式碼從 DllMain 移到全域物件的建構函式中，以避免載入器鎖定。  
  
 在此範例中，有一個全域 Managed 物件，其建構函式包含了原來位在 DllMain 中的 Managed 物件。 此範例的第二個部分會參考此組件，並建立 Managed 物件的執行個體，以叫用模組建構函式進行初始化。  
  
### <a name="code"></a>程式碼  
  
```  
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
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
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
  
### <a name="output"></a>輸出  
  
```  
Module ctor initializing based on global instance of class.  
  
Test called so linker does not throw away unused object.  
```  
  
## <a name="see-also"></a>請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)