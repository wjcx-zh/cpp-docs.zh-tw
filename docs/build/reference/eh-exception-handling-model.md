---
title: /EH (例外狀況處理模型)
description: Microsoft c + +/EH (例外狀況處理模型的參考指南) Visual Studio 中的編譯器選項。
ms.date: 08/25/2020
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
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 0d18d0f1d73b1de46b12262deecb2436c34e6176
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898387"
---
# <a name="eh-exception-handling-model"></a>`/EH` (例外狀況處理模型) 

指定編譯器所產生的例外狀況處理模型支援。 引數指定是否要將 `catch(...)` 語法套用至結構化和標準 c + + 例外狀況、是否假設** extern "C"** 程式碼為 throw 例外狀況，以及是否要將特定 **`noexcept`** 檢查優化。

## <a name="syntax"></a>語法

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>引數

**`a`**\
啟用標準 c + + 堆疊回溯。 當您使用語法時，會同時捕捉結構化 (非同步) 和 standard c + + (同步) 例外狀況 `catch(...)` 。 **`/EHa`** 覆寫 **`/EHs`** 和 **`/EHc`** 引數。

**`s`**\
啟用標準 c + + 堆疊回溯。 當您使用語法時，只會捕捉標準 c + + 例外狀況 `catch(...)` 。 除非 **`/EHc`** 另外指定，否則編譯器會假設宣告為** extern "C"** 的函式可能 throw 是 c + + 例外狀況。

**`c`**\
搭配使用時 **`/EHs`** ，編譯器會假設宣告為** extern "C"** 的函式永遠不 throw 是 c + + 例外狀況。 當與 (（也就是 **`/EHa`** 相當於) ）搭配使用時，它不會有任何作用 **`/EHca`** **`/EHa`** 。 **`/EHc`** 如果未指定或，則會忽略 **`/EHs`** **`/EHa`** 。

**`r`**\
告知編譯器一律針對所有函式產生執行時間終止檢查 **`noexcept`** 。 根據預設， **`noexcept`** 如果編譯器判斷函數只會呼叫非函式呼叫，則執行時間檢查可能會優化 throw 。 此選項提供嚴格的 c + + 一致性，但有一些額外程式碼的成本。 **`/EHr`** 如果未指定或，則會忽略 **`/EHs`** **`/EHa`** 。

**`-`**\
清除先前的選項引數。 例如， **`/EHsc-`** 會解讀為 **`/EHs /EHc-`** ，且相當於 **`/EHs`** 。

**`/EH`** 引數可依任何順序個別指定或合併。 如果指定了多個相同引數的實例，最後一個會覆寫任何先前的實例。  例如，與 **`/EHr- /EHc /EHs`** 相同 **`/EHscr-`** ，而且 **`/EHscr- /EHr`** 具有與相同的效果 **`/EHscr`** 。

## <a name="remarks"></a>備註

### <a name="default-exception-handling-behavior"></a>預設的例外狀況處理行為

編譯器一律會產生支援非同步結構化例外狀況處理 () 的程式碼 SEH 。 依預設 (也就是，如果 **`/EHsc`**) 未指定任何、 **`/EHs`** 或 **`/EHa`** 選項，編譯器會 SEH 在原生 c + + 子句中支援處理常式 `catch(...)` 。 不過，它也會產生僅部分支援 c + + 例外狀況的程式碼。 預設的例外狀況回溯程式碼不會在因例外狀況而超出範圍的區塊之外終結自動 c + + 物件 [`try`](../../cpp/try-throw-and-catch-statements-cpp.md) 。 當 c + + 例外狀況為 n 時，可能會導致資源流失和未定義的行為 throw 。

### <a name="standard-c-exception-handling"></a>標準 c + + 例外狀況處理

完整的編譯器支援標準 c + + 例外狀況處理模型，安全回溯堆疊物件需要 **`/EHsc`** (建議的) 、 **`/EHs`** 或 **`/EHa`** 。

如果您使用 **`/EHs`** 或 **`/EHsc`** ，則您的 `catch(...)` 子句不會 catch 非同步結構化例外狀況。 任何存取違規和受控例外狀況都會被無法攔截 <xref:System.Exception?displayProperty=fullName> 。 而且，即使程式碼處理非同步例外狀況，在發生非同步例外狀況時，範圍中的物件也不會損毀。 此行為是將結構化例外狀況保持未處理的引數。 相反地，請將這些例外狀況視為嚴重。

當您使用 **`/EHs`** 或時 **`/EHsc`** ，編譯器會假設例外狀況只能在 **`throw`** 語句或在函式呼叫中發生。 這項假設可讓編譯器消除追蹤許多 unwindable 物件存留期的程式碼，這可以大幅減少程式碼的大小。 如果您使用 **`/EHa`** ，您的可執行映射可能較大且較慢，因為編譯器不會 **`try`** 積極地優化區塊。 它也會保留在自動清除本機物件的例外狀況篩選準則中，即使編譯器沒有看到任何可能 throw 是 c + + 例外狀況的程式碼也一樣。

### <a name="structured-and-standard-c-exception-handling"></a>結構化和標準 c + + 例外狀況處理

**`/EHa`** 編譯器選項可針對非同步例外狀況和 c + + 例外狀況啟用安全堆疊回溯。 它支援使用原生 c + + 子句來處理標準 c + + 和結構化例外狀況 `catch(...)` 。 若要 SEH 在不指定 **`/EHa`** 的情況下執行，您可以使用 **`__try`** 、 **`__except`** 和 **`__finally`** 語法。 如需詳細資訊，請參閱 [結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)。

> [!IMPORTANT]
> 使用來指定 **`/EHa`** 和 try 處理所有例外狀況 `catch(...)` 可能會造成危險。 在大部分情況下，非同步例外狀況無法復原，因此應視為嚴重。 攔截這些例外狀況並繼續執行可能造成處理序損毀，因而導致難以找出並修正的 Bug。
>
> 雖然 Windows 和 Visual C++ 支援 SEH ，但強烈建議您使用 ISO 標準 c + + 例外狀況處理 (**`/EHsc`** 或 **`/EHs`**) 。 它讓您的程式碼更具可攜性和彈性。 SEH在舊版程式碼或特定類型的程式中，您可能仍需要使用。 例如，在編譯為支援 common language runtime () 的程式碼中，這是必要的 [`/clr`](clr-common-language-runtime-compilation.md) 。 如需詳細資訊，請參閱 [結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)。
>
> 我們建議您不要將使用編譯的目的檔連結 **`/EHa`** 至使用 **`/EHs`** 或 **`/EHsc`** 在相同可執行模組中編譯的物件檔案。 如果您必須使用模組中的任何位置來處理非同步例外狀況 **`/EHa`** ，請使用 **`/EHa`** 編譯模組中的所有程式碼。 您可以在與使用編譯的程式碼相同的模組中使用結構化例外狀況處理語法 **`/EHs`** 。 不過，您無法在相同的函式 SEH 中混用語法與 c + + **`try`** 、 **`throw`** 和 **`catch`** 。

**`/EHa`** 如果您想要例外狀況，而不 catch 是由以外的任何物件所引發，請使用 **`throw`** 。 此範例會產生 catch 結構化例外狀況，並進行 es：

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>/Clr 底下的例外狀況處理

**`/clr`** 選項意指 **`/EHa`** (也就是重複的 **`/clr /EHa`**) 。 如果 **`/EHs`** **`/EHsc`** 在之後使用或，則編譯器會產生錯誤 **`/clr`** 。 優化不會影響此行為。 攔截到例外狀況時，編譯器會針對與例外狀況相同範圍中的任何物件叫用類別析構函數。 如果未攔截到例外狀況，則不會執行這些析構函數。

如需下的例外狀況處理限制的相關資訊 **`/clr`** ，請參閱 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

### <a name="runtime-exception-checks"></a>執行時間例外狀況檢查

**`/EHr`** 選項會在所有具有屬性的函式中，強制執行執行時間終止檢查 **`noexcept`** 。 根據預設，如果編譯器後端判斷出函式只會呼叫 *非 throw * 函式呼叫，則執行時間檢查可能會優化。 非運算函式 throw 是指具有未指定例外狀況之屬性的任何函式都可能是 throw n。 這些函式包含標示為、、和的函式（ **`noexcept`** `throw()` `__declspec(nothrow)` 當指定時） **`/EHc`** **`extern "C"`** 。 非函數的函式 throw 也包含編譯器已判定為非 ing 的任何 throw 檢查。 您可以使用來明確設定預設行為 **`/EHr-`** 。

非 throw ing 屬性不保證函式的例外狀況不能是 throw n。 與函式的行為不同的是，MSVC 編譯器會將 **`noexcept`** 使用、或宣告的函式視為例外 throw 狀況 n 視為 `throw()` `__declspec(nothrow)` **`extern "C"`** 未定義的行為。 使用這三個宣告屬性的函式不會針對例外狀況強制執行執行時間終止檢查。 您可以使用 **`/EHr`** 選項來協助您找出這個未定義的行為，方法是強制編譯器針對未處理的例外狀況，產生可對函式進行 escape 檢查的執行時間檢查 **`noexcept`** 。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在 Visual Studio 或以程式設計方式設定選項

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取設定**屬性**  >  **C/c + +** 程式  >  **代碼產生**。

1. 修改 [啟用 C++ 例外狀況] **** 屬性。

   或者，將 [啟用 C++ 例外狀況] **** 設定為 [否] ****，然後在 [命令列] **** 屬性頁的 [其他選項] **** 方塊中，加入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>。

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)\
[錯誤和例外狀況處理](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[例外狀況規格 (throw) ](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
