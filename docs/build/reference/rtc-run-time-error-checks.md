---
title: /RTC (執行階段錯誤檢查)
ms.date: 07/31/2020
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
ms.openlocfilehash: eefec0956bebe9f72324f3cbc61fccbc5e2e24d7
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520534"
---
# <a name="rtc-run-time-error-checks"></a>`/RTC`（執行階段錯誤檢查）

用來啟用和停用執行階段錯誤檢查功能，並搭配[runtime_checks](../../preprocessor/runtime-checks.md) pragma。

## <a name="syntax"></a>語法

> **`/RTC1`**\
> **`/RTCc`**\
> **`/RTCs`**\
> **`/RTCu`**

## <a name="arguments"></a>引數

**`/RTC1`**<br/>
相當於 **`/RTCsu`** 。

**`/RTCc`**<br/>
當將值指派給較小的資料類型，並導致資料遺失時，就會報告。 例如，它會報告的 **`short`** 類型值 `0x0101` 是否已指派給類型的變數 **`char`** 。

此選項可以報告您想要截斷的情況。 例如，當您想要將的前8個位當做 **`int`** 傳回時 **`char`** 。 因為 **`/RTCc`** 會造成執行階段錯誤，如果指派導致遺失任何資訊，請先將您所需的資訊遮罩，以避免執行階段錯誤。 例如：

```C
#include <crtdbg.h>

char get8bits(unsigned value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

因為 **`/RTCc`** 會拒絕符合標準的程式碼，所以 c + + 標準程式庫不支援。 使用 **`/RTCc`** 和 c + + 標準程式庫的程式碼可能會導致編譯器錯誤[C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)。 您可以定義 `_ALLOW_RTCc_IN_STL` 將警告設為靜音，並使用 **`/RTCc`** 選項。

**`/RTCs`**<br/>
啟用堆疊框架執行階段錯誤檢查，如下所示：

- 將本機變數初始化為非零值。 這個選項有助於識別在 debug 模式中執行時未出現的 bug。 相較于發行組建，堆疊變數在 debug 組建中仍有零值的可能性更高。 這是因為在發行組建中，堆疊變數的編譯器優化。 當程式使用其堆疊的區域時，編譯器永遠不會將它重設為0。 這表示，如果任何未初始化的堆疊變數之後使用相同的堆疊區域，則會傳回先前使用此堆疊記憶體的剩餘值。

- 偵測本機變數（例如陣列）的溢出和不足。 **`/RTCs`** 當存取在結構內由編譯器填補所產生的記憶體時，不會偵測到溢出。 您可以使用 [`align`](../../cpp/align-cpp.md) 、 [ `/Zp` （結構成員對齊）](zp-struct-member-alignment.md)或 [`pack`](../../preprocessor/pack.md) ，或如果您將結構專案排序，以要求編譯器加入填補，則可能會發生填補。

- 堆疊指標驗證，它會偵測堆疊指標損毀。 堆疊指標損毀可能是因為呼叫慣例不相符所造成。 例如，使用函式指標時，您會在匯出為的 DLL 中呼叫函式， [`__stdcall`](../../cpp/stdcall.md) 但您會將函式的指標宣告為 [`__cdecl`](../../cpp/cdecl.md) 。

**`/RTCu`**<br/>
在未初始化變數的情況下，報告使用。 例如，產生警告 C4701 的指令可能也會在底下產生執行階段錯誤 **`/RTCu`** 。 任何會產生[編譯器警告（層級1和層級4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)的指令，都會在下產生執行階段錯誤 **`/RTCu`** 。

不過，請考慮下列程式碼片段：

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

如果變數可能已初始化，則在執行時間不會將其回報 **`/RTCu`** 。 例如，當變數透過指標進行別名處理之後，編譯器不會追蹤變數並報告未初始化的使用。 實際上，您可以藉由取得其位址來初始化變數。 **`&`** 在這種情況下，運算子的運作方式類似指派運算子。

## <a name="remarks"></a>備註

執行階段錯誤檢查是您在執行中的程式碼中找出問題的一種方式。如需詳細資訊，請參閱[如何：使用原生執行時間檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

您可以 **`/RTC`** 在命令列上指定一個以上的選項。 選項引數可能會合並;例如，與 **`/RTCcu`** 相同 **`/RTCc /RTCu`** 。

如果您在命令列使用任何編譯器選項來編譯您的程式 **`/RTC`** ，程式 [`optimize`](../../preprocessor/optimize.md) 代碼中的任何 pragma 指令都會以無訊息模式失敗。 這是因為執行階段錯誤檢查在發行（優化）組建中無效。

用於 **`/RTC`** 開發組建;不要 **`/RTC`** 針對發行組建使用。 **`/RTC`** 不能與編譯器優化搭配使用（[ `/O` 選項（優化程式碼）](o-options-optimize-code.md)）。 以建立的程式映射 **`/RTC`** 稍微大一點，而且稍微慢于建立的映射 **`/Od`** （速度比組建慢 5% **`/Od`** ）。

`__MSVC_RUNTIME_CHECKS`當您使用任何選項或時，將會定義預處理器指示詞 **`/RTC`** [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +** 程式**代碼產生**] 屬性頁。  

1. 修改下列一個或兩個屬性：**基本執行時間檢查**或**較小的類型檢查**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 屬性。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[如何：使用原生執行階段檢查](/visualstudio/debugger/how-to-use-native-run-time-checks)
