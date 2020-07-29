---
title: /EH (例外狀況處理模型)
description: Visual Studio 中 Microsoft c + +/EH （例外狀況處理模型）編譯器選項的參考指南。
ms.date: 04/14/2020
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
no-loc:
- ':::no-loc(SEH):::'
- ':::no-loc(try):::'
- ':::no-loc(catch):::'
- ':::no-loc(throw):::'
- ':::no-loc(extern):::'
- ':::no-loc(finally):::'
- ':::no-loc(noexcept):::'
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: f158e951d595d5934ff513254871710db5920bf1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232712"
---
# <a name="eh-exception-handling-model"></a>/EH (例外狀況處理模型)

指定編譯器所產生的例外狀況處理模型支援。 引數會指定是否要將 `:::no-loc(catch):::(...)` 語法套用至結構化和標準 c + + 例外狀況、是否將** :::no-loc(extern)::: "C"** 程式碼假設為 :::no-loc(throw)::: 例外狀況，以及是否要優化特定 **`:::no-loc(noexcept):::`** 檢查。

## <a name="syntax"></a>語法

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>引數

**`a`**\
啟用標準 c + + 堆疊回溯。 當您使用語法時，會同時捕捉結構化（非同步）和標準 c + + （同步）例外狀況 `:::no-loc(catch):::(...)` 。 **`/EHa`** 覆寫 **`/EHs`** 和 **`/EHc`** 引數。

**`s`**\
啟用標準 c + + 堆疊回溯。 當您使用語法時，只會捕捉標準 c + + 例外狀況 `:::no-loc(catch):::(...)` 。 除非 **`/EHc`** 也指定，否則編譯器會假設宣告為** :::no-loc(extern)::: "C"** 的函式可能 :::no-loc(throw)::: 是 c + + 例外狀況。

**`c`**\
與搭配使用時 **`/EHs`** ，編譯器會假設宣告為** :::no-loc(extern)::: "C"** 的函式永遠不會 :::no-loc(throw)::: 有 c + + 例外狀況。 搭配使用 **`/EHa`** （也就是 **`/EHca`** 相當於）時，它不會有任何作用 **`/EHa`** 。 **`/EHc`** 如果未指定或，則會忽略 **`/EHs`** **`/EHa`** 。

**`r`**\
告知編譯器一律產生所有函式的執行時間終止檢查 **`:::no-loc(noexcept):::`** 。 根據預設， **`:::no-loc(noexcept):::`** 如果編譯器判斷函數只呼叫非 ing 函數，則的執行時間檢查可能會優化 :::no-loc(throw)::: 。 此選項提供嚴格的 c + + 一致性，代價是一些額外的程式碼。 **`/EHr`** 如果未指定或，則會忽略 **`/EHs`** **`/EHa`** 。

**`-`**\
清除先前的 option 引數。 例如， **`/EHsc-`** 會被視為 **`/EHs /EHc-`** ，而相當於 **`/EHs`** 。

**`/EH`** 引數可以依任何順序個別指定或結合。 如果指定了同一個引數的多個實例，則最後一個會覆寫任何先前的。  例如，與 **`/EHr- /EHc /EHs`** 相同 **`/EHscr-`** ，而且與 **`/EHscr- /EHr`** 具有相同的效果 **`/EHscr`** 。

## <a name="remarks"></a>備註

### <a name="default-exception-handling-behavior"></a>預設的例外狀況處理行為

編譯器一律會產生支援非同步結構化例外狀況處理（）的程式碼 :::no-loc(SEH)::: 。 根據預設（亦即，如果未 **`/EHsc`** **`/EHs`** 指定、或 **`/EHa`** 選項），編譯器會支援 :::no-loc(SEH)::: 原生 c + + 子句中的處理常式 `:::no-loc(catch):::(...)` 。 不過，它也會產生僅部分支援 c + + 例外狀況的程式碼。 預設的例外狀況回溯程式碼不會損毀超出範圍的區塊以外的自動 c + + 物件 [:::no-loc(try):::](../../cpp/:::no-loc(try):::-:::no-loc(throw):::-and-:::no-loc(catch):::-statements-cpp.md) ，因為發生例外狀況。 當 c + + 例外狀況為 n 時，可能會導致資源流失和未定義的行為 :::no-loc(throw)::: 。

### <a name="standard-c-exception-handling"></a>Standard c + + 例外狀況處理

適用于安全回溯堆疊物件之標準 c + + 例外狀況處理模型的完整編譯器支援 **`/EHsc`** （建議）、 **`/EHs`** 或 **`/EHa`** 。

如果您使用 **`/EHs`** 或 **`/EHsc`** ，那麼您的子句就不會有 `:::no-loc(catch):::(...)` :::no-loc(catch)::: 非同步結構化例外狀況。 任何存取違規和 managed 例外狀況都會被攔截 <xref:System.Exception?displayProperty=fullName> 到。 而且，即使程式碼處理非同步例外狀況，在非同步例外狀況發生時，範圍中的物件也不會損毀。 這個行為是讓結構化例外狀況未處理的引數。 相反地，請將這些例外狀況視為嚴重。

當您使用 **`/EHs`** 或時 **`/EHsc`** ，編譯器會假設例外狀況只能在 **`:::no-loc(throw):::`** 語句或在函式呼叫中發生。 這項假設可讓編譯器排除用來追蹤許多 unwindable 物件之存留期的程式碼，這可能會大幅減少程式碼大小。 如果您使用 **`/EHa`** ，您的可執行映射可能會變得更大且速度較慢，因為編譯器不會 **`:::no-loc(try):::`** 積極地優化區塊。 它也會留在自動清除本機物件的例外狀況篩選準則，即使編譯器看不到任何可能會 :::no-loc(throw)::: 發生 c + + 例外狀況的程式碼。

### <a name="structured-and-standard-c-exception-handling"></a>結構化和標準 c + + 例外狀況處理

**`/EHa`** 編譯器選項可啟用非同步例外狀況和 c + + 例外狀況的安全堆疊回溯。 它支援使用原生 c + + 子句來處理標準 c + + 和結構化例外狀況 `:::no-loc(catch):::(...)` 。 若要在 :::no-loc(SEH)::: 不指定 **`/EHa`** 的情況下執行，您可以使用 **__ :::no-loc(try)::: **、 **`__except`** 和 **`__:::no-loc(finally):::`** 語法。 如需詳細資訊，請參閱[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)。

> [!IMPORTANT]
> **`/EHa`** 使用指定和 :::no-loc(try)::: 來處理所有例外狀況可能 `:::no-loc(catch):::(...)` 會造成危險。 在大部分情況下，非同步例外狀況無法復原，因此應視為嚴重。 攔截這些例外狀況並繼續執行可能造成處理序損毀，因而導致難以找出並修正的 Bug。
>
> 雖然 Windows 和 Visual C++ 支援 :::no-loc(SEH)::: ，但我們強烈建議您使用 ISO 標準 c + + 例外狀況處理（ **`/EHsc`** 或 **`/EHs`** ）。 它讓您的程式碼更具可攜性和彈性。 您可能還是需要 :::no-loc(SEH)::: 在舊版程式碼中使用，或針對特定類型的程式。 例如，編譯器代碼中的必須支援 common language runtime （[/clr](clr-common-language-runtime-compilation.md)）。 如需詳細資訊，請參閱[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)。
>
> 我們建議您不要將使用編譯的物件檔案連結 **`/EHa`** 至使用 **`/EHs`** 或 **`/EHsc`** 在相同可執行模組中編譯的檔案。 如果您必須在模組中的任何位置使用處理非同步例外狀況 **`/EHa`** ，請使用 **`/EHa`** 編譯模組中的所有程式碼。 您可以在與使用編譯的程式碼相同的模組中使用結構化例外狀況處理語法 **`/EHs`** 。 不過，您無法在相同的函式 :::no-loc(SEH)::: 中混用 c + + **`:::no-loc(try):::`** 、和語法 **`:::no-loc(throw):::`** **`:::no-loc(catch):::`** 。

如果您想要由以外的專案引發的例外狀況，請使用 **`/EHa`** :::no-loc(catch)::: **`:::no-loc(throw):::`** 。 這個範例會針對 :::no-loc(catch)::: 結構化例外狀況產生和：

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to :::no-loc(catch)::: it using :::no-loc(catch):::(...)
    :::no-loc(try):::
    {
        int i = 0, j = 1;
        j /= i;   // This will :::no-loc(throw)::: a SE (divide by zero).
        printf("%d", j);
    }
    :::no-loc(catch):::(...)
    {
        // :::no-loc(catch)::: block will only be executed under /EHa
        cout << "Caught an exception in :::no-loc(catch):::(...)." << endl;
    }
}

int main()
{
    __:::no-loc(try):::
    {
        fail();
    }

    // __except will only :::no-loc(catch)::: an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the :::no-loc(catch):::(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>/Clr 下的例外狀況處理

**`/clr`** 選項表示 **`/EHa`** （也就 **`/clr /EHa`** 是多餘的）。 如果 **`/EHs`** **`/EHsc`** 在之後使用或，則編譯器會產生錯誤 **`/clr`** 。 優化不會影響此行為。 攔截到例外狀況時，編譯器會針對與例外狀況位於相同範圍中的任何物件叫用類別的析構函數。 如果未攔截到例外狀況，則不會執行這些析構函數。

如需下的例外狀況處理限制的相關資訊 **`/clr`** ，請參閱[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

### <a name="runtime-exception-checks"></a>執行時間例外狀況檢查

**`/EHr`** 選項會在所有具有屬性的函式中強制執行執行時間終止檢查 **`:::no-loc(noexcept):::`** 。 根據預設，如果編譯器後端判斷函數只會呼叫*非 :::no-loc(throw)::: ing*函式，則執行時間檢查可能會優化。 非 :::no-loc(throw)::: ing 函式是具有指定無例外狀況之屬性的任何函數可能是 :::no-loc(throw)::: n。 其中包含標記 **`:::no-loc(noexcept):::`** 為、、和的函式（ `:::no-loc(throw):::()` `__declspec(no:::no-loc(throw):::)` 當 **`/EHc`** 指定了** :::no-loc(extern)::: "C"** 函式時）。 非 ing 函式 :::no-loc(throw)::: 也包含編譯器所判定的任何，而不是透過 :::no-loc(throw)::: 檢查來進行。 您可以使用明確地設定預設行為 **`/EHr-`** 。

非 :::no-loc(throw)::: ing 屬性不保證函式的例外狀況不能是 :::no-loc(throw)::: n。 不同于函式的行為 **`:::no-loc(noexcept):::`** ，MSVC 編譯器會 :::no-loc(throw)::: 將使用、或 "C" 宣告的函式視為例外狀況 n， `:::no-loc(throw):::()` `__declspec(no:::no-loc(throw):::)` 做為未定義的行為。 ** :::no-loc(extern)::: ** 使用這三個宣告屬性的函數不會強制執行例外狀況的執行時間終止檢查。 您可以使用 **`/EHr`** 選項來協助您識別這個未定義的行為，方法是強制編譯器針對已取消函式的未處理例外狀況產生執行時間檢查 **`:::no-loc(noexcept):::`** 。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在 Visual Studio 或以程式設計方式設定選項

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **C/c + +** 程式  >  **代碼產生**]。

1. 修改 [啟用 C++ 例外狀況] **** 屬性。

   或者，將 [啟用 C++ 例外狀況] **** 設定為 [否] ****，然後在 [命令列] **** 屬性頁的 [其他選項] **** 方塊中，加入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)\
[錯誤和例外狀況處理](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[例外狀況規格（ :::no-loc(throw)::: ）](../../cpp/exception-specifications-:::no-loc(throw):::-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
