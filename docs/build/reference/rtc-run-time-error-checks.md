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
ms.openlocfilehash: 49f0e4bace5f3dd199b58854e838204bd2cd5f3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222013"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (執行階段錯誤檢查)

用來啟用和停用執行階段錯誤檢查功能，並搭配[runtime_checks](../../preprocessor/runtime-checks.md) pragma。

## <a name="syntax"></a>語法

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>引數

**1**<br/>
**/Rtc**的對應項 `su` 。

**c**<br/>
當將值指派給較小的資料類型，並導致資料遺失時，就會報告。 例如，如果將類型的值 `short 0x101` 指派給類型的變數 **`char`** 。

此選項會報告您想要截斷的情況，例如，如果您想要傳回的前八位 **`int`** 做為 **`char`** 。 因為 **/RTC** `c` 當指派導致任何資訊遺失時，/rtc 會造成執行階段錯誤，您可以遮罩所需的資訊，以避免因為 **/rtc**而造成執行階段錯誤 `c` 。 例如：

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

**今日**<br/>
啟用堆疊框架執行階段錯誤檢查，如下所示：

- 將本機變數初始化為非零值。 這有助於識別在 debug 模式中執行時未顯示的 bug。 相較于發行組建，堆疊變數在 debug 組建中仍為零，因為在發行組建中，堆疊變數的編譯器優化。 當程式使用其堆疊的區域時，編譯器永遠不會將它重設為0。 因此，如果後續的未初始化堆疊變數使用相同的堆疊區域，則會傳回先前使用此堆疊記憶體的剩餘值。

- 偵測本機變數（例如陣列）的溢出和不足。 **/Rtc** `s`存取在結構內由編譯器填補所產生的記憶體時，不會偵測到溢出。 使用[align](../../cpp/align-cpp.md)、 [/Zp （結構成員對齊）](zp-struct-member-alignment.md)或[pack](../../preprocessor/pack.md)，或如果您以這種方式排序結構專案，以要求編譯器加入填補，就可能發生填補。

- 堆疊指標驗證，它會偵測堆疊指標損毀。 堆疊指標損毀可能是因為呼叫慣例不相符所造成。 例如，您可以使用函式指標來呼叫 DLL 中的函式，該函式會匯出為[__stdcall](../../cpp/stdcall.md) ，但您會將函式的指標宣告為[__cdecl](../../cpp/cdecl.md)。

**u**<br/>
在未初始化變數的情況下，報告使用。 例如，產生的指令 `C4701` 可能也會在 **/rtc**底下產生執行階段錯誤 `u` 。 任何會產生[編譯器警告（層級1和層級4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)的指令，都會在 **/rtc**底下產生執行階段錯誤 `u` 。

不過，請考慮下列程式碼片段：

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

如果變數可能已初始化，則不會在執行時間由 **/rtc**回報 `u` 。 例如，當變數透過指標進行別名處理之後，編譯器不會追蹤變數並報告未初始化的使用。 實際上，您可以藉由取得其位址來初始化變數。 在這種情況下，& 運算子的運作方式類似指派運算子。

## <a name="remarks"></a>備註

執行階段錯誤檢查是您在執行中的程式碼中找出問題的一種方式。如需詳細資訊，請參閱[如何：使用原生執行時間檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

如果您在命令列中使用任何 **/rtc**編譯器選項來編譯器，則在程式碼中的任何 pragma [optimize](../../preprocessor/optimize.md)指令都會以無訊息模式失敗。 這是因為在發行（優化）組建中，執行階段錯誤檢查無效。

您應該將 **/rtc**用於開發組建;您不應該將 **/rtc**用於零售組建。 **/Rtc**不能與編譯器優化搭配使用（[/O 選項（優化程式碼）](o-options-optimize-code.md)）。 以 **/rtc**建立的程式映射會稍微大一點，而且稍微慢于以 **/od**建立的映射（比 **/od**組建的速度高達5%）。

當您使用任何 **/rtc**選項或[/GZ](gz-enable-stack-frame-run-time-error-checking.md)時，將會定義 __MSVC_RUNTIME_CHECKS 預處理器指示詞。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [程式**代碼產生**] 屬性頁。

1. 修改下列一個或兩個屬性：**基本執行時間檢查**或**較小的類型檢查**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 屬性。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[如何：使用原生執行時間檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)
