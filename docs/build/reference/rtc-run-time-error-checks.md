---
title: /RTC (執行階段錯誤檢查)
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
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
ms.openlocfilehash: 77dc97ee07499b7df37a115dafafddd71acb7bb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654996"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (執行階段錯誤檢查)

用來啟用和停用執行階段錯誤檢查功能，搭配[runtime_checks](../../preprocessor/runtime-checks.md) pragma。

## <a name="syntax"></a>語法

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>引數

**1**<br/>
對等 **/RTC**`su`。

**C**<br/>
報告的值時指派給較小的資料類型，而導致資料遺失。 例如，如果型別的值`short 0x101`指派給類型的變數`char`。

此選項會報告在您想要截斷，比方說，如果您想要的第一個八位元的情況下`int`傳回為`char`。 因為 **/RTC** `c`會造成執行階段錯誤因指派而遺失任何資訊時，您可以關閉遮罩，您必須避免執行階段錯誤的資訊 **/RTC** `c`. 例如: 

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

**s**<br/>
啟用堆疊框架執行階段錯誤檢查，如下所示：

- 為非零值的本機變數的初始化。 這有助於找出不會出現在 偵錯模式中執行時的錯誤。 沒有更高的機率堆疊變數仍然會在偵錯組建，因為編譯器最佳化的發行組建中的堆疊變數相較於發行組建中的零。 一旦程式已使用其堆疊的區域，永遠不會重設為 0 的編譯器。 因此，碰巧使用相同的堆疊區域的後續的、 未初始化堆疊變數會傳回剩餘的先前使用這個堆疊記憶體的值。

- 偵測溢位等情況不足，例如陣列的本機變數。 **/RTC** `s`存取產生的編譯器與邊框距離在結構中的記憶體時，則不會偵測溢位。 填補可能是使用[對齊](../../cpp/align-cpp.md)， [/Zp （結構成員對齊）](../../build/reference/zp-struct-member-alignment.md)，或[pack](../../preprocessor/pack.md)，或如果您需要編譯器加上邊框間距的方式排序結構項目。

- 堆疊指標驗證時，它會偵測堆疊指標損毀。 堆疊指標損毀可能因呼叫慣例不相符。 比方說，使用函式指標，您呼叫函式中做為匯出的 DLL [__stdcall](../../cpp/stdcall.md)但宣告為函式的指標[__cdecl](../../cpp/cdecl.md)。

**u**<br/>
當未經初始化就會使用變數時報告。 比方說，產生的指令`C4701`可能也會產生執行階段錯誤之下 **/RTC**`u`。 會產生任何指令[編譯器警告 （層級 1 和層級 4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)會產生在執行階段錯誤 **/RTC**`u`。

不過，請考慮下列程式碼片段：

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

如果變數可能已經過初始化，它將不會報告在執行階段 **/RTC**`u`。 例如，變數是透過指標的別名之後，編譯器不會追蹤變數和報告未初始化的使用。 作用中，您可以取得其位址來初始化變數。 & 運算子在這種情況下的作用就像是指派運算子。

## <a name="remarks"></a>備註

執行階段錯誤檢查是在您執行的程式碼; 中找出問題的方式如需詳細資訊，請參閱 <<c0> [ 如何： 使用原生的執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

如果您編譯您的程式，在命令列使用任一 **/RTC**編譯器選項、 任何 pragma[最佳化](../../preprocessor/optimize.md)中您的程式碼指示將會以無訊息模式失敗。 這是因為執行階段錯誤檢查 （最佳化） 的發行組建中無效。

您應該使用 **/RTC**開發組建;**/RTC**不應該用於零售組建。 **/RTC**不能使用的編譯器最佳化 ([/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md))。 以建置程式映像 **/RTC**會稍微大一點，比以建置映像稍微慢一點 **/Od** (低於最多 5% **/Od**建置)。

當您使用任何時，將會定義 __MSVC_RUNTIME_CHECKS 前置處理器指示詞 **/RTC**選項或[/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **程式碼產生**屬性頁。

1. 修改一或兩個下列屬性：**基本執行階段會檢查**或是**較小類型檢查**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 屬性。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)