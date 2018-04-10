---
title: -/RTC （執行階段錯誤檢查） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
dev_langs:
- C++
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8699a96dcd7c04bc1b2707e964afb4b68068147e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rtc-run-time-error-checks"></a>/RTC (執行階段錯誤檢查)
用來啟用和停用之執行階段錯誤檢查功能搭配[runtime_checks](../../preprocessor/runtime-checks.md) pragma。  
  
## <a name="syntax"></a>語法  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## <a name="arguments"></a>引數  
 `1`  
 對等**/RTC**`su`。  
  
 `c`  
 值時，報表會指派給較小的資料類型，會導致資料遺失。 例如，如果型別的值`short 0x101`指派給類型的變數`char`。  
  
 此選項將會報告在您想截斷，比方說，如果您想要的第一個八位元的情況下`int`當成`char`。 因為**/RTC** `c`會導致執行階段錯誤由於指派的緣故遺失任何資訊時，可以關閉您要避免發生可能是執行階段錯誤的資訊進行遮罩**/RTC** `c`. 例如:   
  
```  
#include <crtdbg.h>  
  
char get8bits(int value, int position) {  
   _ASSERT(position < 32);  
   return (char)(value >> position);  
   // Try the following line instead:  
   // return (char)((value >> position) & 0xff);  
}  
  
int main() {  
   get8bits(12341235,3);  
}  
```  
  
 `s`  
 啟用堆疊框架執行階段錯誤檢查，如下所示：  
  
-   為非零值的本機變數的初始化。 這有助於找出在偵錯模式中執行時不會出現的錯誤。 沒有機會堆疊變數仍會在相較於發行組建，因為編譯器最佳化的發行組建中的堆疊變數的偵錯組建中的零。 一旦程式使用其堆疊的區域，它會永遠不會重設為 0 編譯器。 因此，若要使用相同的堆疊區域，就可能發生的後續未初始化的堆疊變數可以傳回值中剩餘的先前使用這個堆疊記憶體。  
  
-   偵測滿溢和不足的本機變數，例如陣列。 **/RTC** `s`存取結果編譯器填補結構內的記憶體時，則不會偵測溢位。 發生填補可藉由使用[對齊](../../cpp/align-cpp.md)， [/Zp （結構成員對齊）](../../build/reference/zp-struct-member-alignment.md)，或[套件](../../preprocessor/pack.md)，或如果您在這種方式需要加入填補編譯器結構項目。  
  
-   堆疊指標驗證，它會偵測堆疊指標損毀。 堆疊指標損壞可能因呼叫慣例不相符。 例如，使用函式指標，您呼叫的函式中的 DLL 會匯出為[__stdcall](../../cpp/stdcall.md)但宣告為函式的指標[__cdecl](../../cpp/cdecl.md)。  
  
 `u`  
 報表時未經初始化就會使用變數。 例如，產生的指令`C4701`也可能會產生下的一個執行階段錯誤**/RTC**`u`。 會產生任何指令[編譯器警告 （層級 1 和層級 4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)會產生在執行階段錯誤**/RTC**`u`。  
  
 不過，請考慮下列程式碼片段：  
  
```cpp  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 如果變數可能已經過初始化，它將不會報告在執行階段**/RTC**`u`。 例如，變數是透過指標的別名之後，編譯器將會不追蹤變數及報告未初始化的使用。 作用中，您可以取得其位址來初始化變數。 & 運算子在這種情況下的作用就像是指派運算子。  
  
## <a name="remarks"></a>備註  
 執行階段錯誤檢查會讓您執行的程式碼; 中找出問題如需詳細資訊，請參閱[How to： 使用原生執行階段會檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。  
  
 如果您將編譯您的程式，在命令列使用任何**/RTC**編譯器選項、 任何 pragma[最佳化](../../preprocessor/optimize.md)指示程式碼中的將會以無訊息模式失敗。 這是因為執行階段錯誤檢查 （最佳化） 的發行組建中無效。  
  
 您應該使用**/RTC**開發組建。**/RTC**不應該用於零售版本。 **/RTC**不能與編譯器最佳化 ([/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md))。 使用建置程式映像**/RTC**會稍微大一點，比使用建置的映像稍微慢一點**/Od** (低於高達 5% **/Od**建置)。  
  
 將定義 __MSVC_RUNTIME_CHECKS 前置處理器指示詞，當您使用任何**/RTC**選項或[/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**程式碼產生**屬性頁。  
  
4.  修改一個或兩個下列屬性：**基本執行階段會檢查**或**較小類型檢查**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 屬性。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)