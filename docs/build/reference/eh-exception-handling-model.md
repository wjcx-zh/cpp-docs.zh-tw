---
title: /EH (例外狀況處理模型)
ms.date: 08/14/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 8546b14995317afb57e4cc23a5d6f81c2172a1a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328287"
---
# <a name="eh-exception-handling-model"></a>/EH (例外狀況處理模型)

指定編譯器所使用的例外狀況處理類型、何時要繼續最佳化例外狀況檢查，以及是否要終結因例外狀況而超出範圍的 C++ 物件。 如果未指定 **/EH,** 編譯器將使代碼捕獲非同步結構化異常和C++異常,但不會銷毀由於異步異常而超出範圍C++物件。

## <a name="syntax"></a>語法

> **/EH****s**|=**a****-**=**c**=**r**= }

## <a name="arguments"></a>引數

**a**<br/>
通過使用C++`catch(...)`語法捕獲非同步(結構化)和同步(C++)異常的異常處理模型。

**s**<br/>
僅捕獲同步 (C++) 異常並告訴編譯器假定聲明為**外部「C」的**函數可能會引發異常的異常處理模型。

**C**<br/>
如果與**s** **(/EHsc**一起使用 ) 捕獲 C++個異常,並告訴編譯器假定聲明為**外部"C"的**函數永遠不會引發 C++異常。 **/EHca** 相當於 **/EHa**。

**R**<br/>
告訴編譯器始終生成所有**noa 函數**的運行時終止檢查。 默認情況下,如果編譯器確定函數僅調用非引發函數,則可能會優化**noa 的**運行時檢查。

## <a name="remarks"></a>備註

**/EHa** 編譯器選項可搭配原生 C++ `catch(...)` 子句，用來支援非同步結構化例外狀況處理 (SEH)。 要實現 SEH 而不指定 **/EHa,** 可以使用 **__try、__except**和 **__finally**語法。 **__except** 雖然 Windows 和 Visual C++ 支援 SEH，但強烈建議您使用 ISO 標準 C++ 例外狀況處理 (**/EHs** 或 **/EHsc**)，因為它可提升程式碼的可攜性和彈性。 但是,在現有代碼或特定類型的程式中(例如,為支援通用語言運行時[(/clr(通用語言運行時編譯)](clr-common-language-runtime-compilation.md)而編譯的代碼中),您仍可能仍必須使用 SEH。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。

使用 **/EHa** 指定 `catch(...)` 並嘗試處理所有例外狀況可能並不安全。 在大部分情況下，非同步例外狀況無法復原，因此應視為嚴重。 攔截這些例外狀況並繼續執行可能造成處理序損毀，因而導致難以找出並修正的 Bug。

如果您使用 **/EHs** 或 **/EHsc**，那麼您的 `catch(...)` 子句就不會攔截非同步結構化例外狀況。 存取違規和 Managed <xref:System.Exception?displayProperty=fullName> 例外狀況並不會遭到攔截，而產生非同步例外狀況時不會終結範圍內的物件，即使已處理非同步例外狀況也一樣。

如果使用 **/EHa,** 則映射可能更大,並且性能可能較差,因為編譯器不會像積極一樣優化**try**塊。 即使編譯器未發現任何可能擲回 C++ 例外狀況的程式碼，仍會在例外況狀中留下自動呼叫所有本機物件之解構函式的篩選。 這樣就能安全地回溯非同步例外狀況以及 C++ 例外狀況的堆疊。 使用 **/EHs**時,編譯器假定異常只能在**throw**語句或函數調用中發生。 這樣編譯器就能夠消除追蹤許多無法回溯物件之存留期的程式碼，進而大幅縮小程式碼。

我們建議您不要將使用 **/EHa**編譯的物件與在同一可執行模組中使用 **/EHs**或 **/EHsc**編譯的物件連結。 如果您必須在模組中的任何位置使用 **/EHa** 處理非同步例外狀況，請使用 **/EHa** 編譯模組中的所有程式碼。 您可以在使用 **/EHs**編譯的代碼的模組中使用結構化異常處理語法,但不能將 SEH 語法與**嘗試**,**引發**和**捕獲**混合在同一函數中。

如果要捕獲由**投擲**以外的內容引發的異常,請使用 **/EHa。** 這個範例將會產生並攔截結構化例外狀況：

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

**/EHc** 選項要求必須指定 **/EHs** 或 **/EHa** 。 **/clr**選項表示 **/EHa(** 即 **/clr** **/EHa**是冗餘的)。 如果在 **/EHs**或 **/EHsc**在 **/clr**之後使用,編譯器將生成錯誤。 最佳化作業不會影響這種行為。 攔截到例外狀況時，編譯器會叫用類別解構函式，或是與例外狀況位於相同範圍中的一個或多個物件的解構函式。 如果未攔截到例外狀況，則不會執行這些解構函式。

如需 **/clr**下的例外狀況處理限制的相關資訊，請參閱 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

可以使用符號**-** 清除該選項。 例如 **,/EHsc-** 被解釋為 **/EHs** **/EHc-** 並且等效於 **/EHs**。

**/EHr**編譯器選項強制在所有具有**nothe 屬性**的函數中檢查運行時終止。 根據預設，如果編譯器後端判斷函式只會呼叫 *「非擲回」* (Non-throwing) 函式，則可能會繼續最佳化執行階段檢查。 非擲回函式是具有指定不會擲回任何例外狀況之屬性的任何函式。 這包括標記為**noex**`throw()`的`__declspec(nothrow)`函數 ,和 ,指定 **/EHc**時,**外部"C"** 函數。 非擲回函式也包含編譯器判定檢查不會擲回任何例外狀況的任何函式。 您可以使用 **/EHr-** 明確地設定預設值。

不過，非擲回屬性並不保證函式不會擲回任何例外狀況。 與**noex 函數**的行為不同,MSVC 編`throw()`譯`__declspec(nothrow)`器將使用聲明的函數引發的異常,或**extern "C"** 視為未定義的行為。 使用這三種宣告屬性的函式，不會對例外狀況強制執行執行階段終止檢查。 您可以使用 **/EHr**選項來幫助標識此未定義的行為,為此,請強制編譯器為轉義**noexa**函數的未處理異常生成運行時檢查。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**設定屬性** > **C/C++** > **程式碼產生**。

1. 修改 [啟用 C++ 例外狀況] **** 屬性。

   或者，將 [啟用 C++ 例外狀況] **** 設定為 [否] ****，然後在 [命令列] **** 屬性頁的 [其他選項] **** 方塊中，加入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[錯誤和例外狀況處理](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
