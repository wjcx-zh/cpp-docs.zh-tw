---
title: /EH (例外狀況處理模型)
description: Visual Studio 中 Microsoft C++ /EH(異常處理模型)編譯器選項的參考指南。
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
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396286"
---
# <a name="eh-exception-handling-model"></a>/EH (例外狀況處理模型)

指定編譯器生成的異常處理模型支援。 參數指定是否將語法應用於`catch(...)`結構化和標準C++異常、是否**extern假定"C"** 代碼throw為異常,以及是否優化**noexcept** 某些檢查。

## <a name="syntax"></a>語法

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>引數

**`a`**\
啟用標準C++堆疊展開。 使用`catch(...)`語法時,捕獲結構化(非同步)和標準C++(同步)異常。 **`/EHa`** 重寫和**`/EHs`****`/EHc`** 參數。

**`s`**\
啟用標準C++堆疊展開。 使用`catch(...)`語法時,僅捕獲標準C++異常。 除非**`/EHc`** 還指定,否則編譯器假定聲明為**extern「C」的**函throw數可能是 C++例外。

**`c`**\
當**`/EHs`** 與 中使用 時,編譯器假定聲明為**extern「C」的**函數永遠不會throw成為C++異常。 它與 (**`/EHa`****`/EHca`** 即等效**`/EHa`** 於 ) 一起使用時不起作用。 **`/EHc`** 如果**`/EHs`****`/EHa`** 或未指定,則忽略。

**`r`**\
告訴編譯器始終為所有**noexcept** 函數生成運行時終止檢查。 默認情況下,如果編譯器確定函數僅**noexcept** 調用非引發函數,則可能會優化其運行時檢查。 此選項提供嚴格的C++符合性,但代價是一些額外的代碼。 **`/EHr`** 如果**`/EHs`****`/EHa`** 或未指定,則忽略。

**`-`**\
清除上一個選項參數。 例如,**`/EHsc-`** 被解釋**`/EHs /EHc-`** 為與等效**`/EHs`** 於 。

**`/EH`** 參數可以按任何順序單獨指定或合併。 如果指定了同一參數的多個實例,則最後一個實例將覆蓋任何較早的實例。  **`/EHr- /EHc /EHs`** 例如,**`/EHscr-`** 與相同,**`/EHscr- /EHr`** 並且具有**`/EHscr`** 與的效果相同。

## <a name="remarks"></a>備註

### <a name="default-exception-handling-behavior"></a>預設例外處理行為

編譯器始終產生支援非同步結構化異常處理的代碼SEH。 預設情況下(**`/EHsc`** 即,如果沒有**`/EHs`****`/EHa`**, 或指定選項),編SEH譯器支援 本`catch(...)`機 C++ 子句中的處理程式。 但是,它還生成僅部分支援C++異常的代碼。 默認異常展開代碼不會銷毀由於異常而超出範圍的[try](../../cpp/try-throw-and-catch-statements-cpp.md)塊之外的自動C++物件。 引發C++異常時,可能會導致資源洩漏和未定義的行為。

### <a name="standard-c-exception-handling"></a>標準C++異常處理

對標準C++異常處理模型的完全編譯器支援,該模型安全展開堆疊物件**`/EHsc`** 需要(**`/EHs`** 建議**`/EHa`**)或 。

如果使用**`/EHs`****`/EHsc`** 或 ,`catch(...)`則子catch句不會 非同步結構化異常。 任何訪問衝突和管理<xref:System.Exception?displayProperty=fullName>異常都未捕獲。 而且,發生異步異常時作用域中的物件不會銷毀,即使代碼處理異步異常也是如此。 此行為是使結構化異常未處理的參數。 相反,請考慮這些異常是致命的。

使用**`/EHs`****`/EHsc`** 或 時,編譯器假定異常**throw** 只能在語句或函數調用中發生。 此假設允許編譯器消除用於跟蹤許多可展開物件的存留期的代碼,這可以顯著減小代碼大小。 如果使用**`/EHa`**,則可執行映射可能會更大、更慢,因為編譯器不會像那樣積極地**try** 優化 塊。 它還會在自動清理本地物件的異常篩選器中保留,即使編譯器看不到任何可以throwC++異常的代碼也是如此。

### <a name="structured-and-standard-c-exception-handling"></a>結構化和標準化式C++異常處理

編譯器**`/EHa`** 選項允許針對非同步異常和C++異常進行安全堆疊展開。 它支援使用本機C++`catch(...)`子句處理標準C++和結構化異常。 要實現SEH而不**`/EHa`** 指定 ,可以使用 **__try、__except****__except**和 **__finally**語法。 有關詳細資訊,請參閱[結構化異常處理](../../cpp/structured-exception-handling-c-cpp.md)。

> [!IMPORTANT]
> 使用**`/EHa`** 指定並嘗試處理所有`catch(...)`異常 可能很危險。 在大部分情況下，非同步例外狀況無法復原，因此應視為嚴重。 攔截這些例外狀況並繼續執行可能造成處理序損毀，因而導致難以找出並修正的 Bug。
>
> 即使 Windows 和SEHVisual C++ 支援,我們強烈建議您使用**`/EHsc`** ISO 標準 C++ 異常**`/EHs`** 處理 (或 )。 它使代碼更加便攜和靈活。 有時,您仍必須在舊代碼或特定SEH類型的程式中使用。 例如,在編譯的代碼中,它是必需的,以支援通用語言運行時[(/clr)。](clr-common-language-runtime-compilation.md) 有關詳細資訊,請參閱[結構化異常處理](../../cpp/structured-exception-handling-c-cpp.md)。
>
> 我們建議您切勿將使用編譯**`/EHa`** 的物件檔連結到**`/EHs`** 使用**`/EHsc`** 或 在同一可執行模組中編譯的物件檔。 如果必須使用**`/EHa`** 模組中的任意位置來處理非同步異常,請使用**`/EHa`** 編譯 模組中的所有代碼。 您可以在使用的相同模組中使用結構化異常處理語法,這些程式碼**`/EHs`** 使用 。 但是SEH,不能將語法與**try** C++**throw****catch** 和 在同一函數中混合。

如果要**`/EHa`**catch使用 由以外的內容引發**throw** 的異常 ,請使用 。 這個範例將會產生並攔截結構化例外狀況：

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

### <a name="exception-handling-under-clr"></a>/clr 下的異常處理

該**`/clr`** 選項**`/EHa`** 表示**`/clr /EHa`**(即冗餘)。 如果在**`/EHs`** 中使用**`/EHsc`** 或 後使用,**`/clr`** 編譯器 將生成錯誤。 優化不會影響此行為。 捕獲異常時,編譯器會為與異常位於同一作用域內的任何物件調用類析構函數。 如果未捕獲異常,則不運行這些析構函數。

有關**`/clr`** 下 例外處理限制的資訊,請參閱[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

### <a name="runtime-exception-checks"></a>執行時異常檢查

該**`/EHr`** 選項強制在**noexcept** 具有 屬性的所有函數中檢查運行時終止。 默認情況下,如果編譯器後端確定函數僅調用*非引發*函數,則運行時檢查可能會被優化。 非擲回函式是具有指定不會擲回任何例外狀況之屬性的任何函式。 它們**noexcept** 包括標記為`throw()`的`__declspec(nothrow)`函**`/EHc`** 數 ,和 ,指定時**extern,"C"** 函數。 非擲回函式也包含編譯器判定檢查不會擲回任何例外狀況的任何函式。 可以使用 顯示式設定預設**`/EHr-`** 行為 。

非引發屬性不能保證函數不能引發異常。 與**noexcept** 函數的行為不同,MSVC 編譯器將`throw()``__declspec(nothrow)`**extern** 使用 聲明的函數引發的異常視為未定義的行為。 使用這三個聲明屬性的函數不強制運行時終止檢查異常。 可以使用**`/EHr`** 該 選項通過強制編譯器為**noexcept** 轉義 函數的未處理異常生成運行時檢查來幫助標識此未定義的行為。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在可檢視化工作室中設定選項,或以程式設計方式設定選項

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**設定屬性** > **C/C++** > **程式碼產生**。

1. 修改 [啟用 C++ 例外狀況] **** 屬性。

   或者，將 [啟用 C++ 例外狀況] **** 設定為 [否] ****，然後在 [命令列] **** 屬性頁的 [其他選項] **** 方塊中，加入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)\
[錯誤與不正常處理](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[例外規格throw( )](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
