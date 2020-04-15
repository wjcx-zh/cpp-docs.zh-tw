---
title: try-except 陳述式
description: Microsoft C++引用__try,__except結構化異常處理語句。
ms.date: 04/03/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: 132edf7cc9819637fafa3947686972d311924b99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366228"
---
# <a name="try-except-statement"></a>try-except 陳述式

**try-除了**語句是 Microsoft 擴展,支援 C 和 C++語言的結構化異常處理。 此擴展特定於**Microsoft。**

## <a name="syntax"></a>語法

> **\_\_嘗試**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;守衛代碼<br/>
> }<br/>
> ( 運算*expression*式**\_\_**)<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;例外處理程式碼<br/>
> }

## <a name="remarks"></a>備註

**try-除了**語句是 Microsoft 對 C 和 C++語言的擴展。 它使目標應用程式能夠在通常終止程式執行的事件發生時獲得控制。 此類事件稱為*結構化異常*,或簡稱*為例外*。 處理這些異常的機制稱為*結構化異常處理*(SEH)。

有關相關資訊,請參閱[嘗試最後語句](../cpp/try-finally-statement.md)。

例外情況可以是基於硬體的,也可以是基於軟體的。 即使應用程式無法從硬體或軟體異常中完全恢復,結構化異常處理也很有用。 SEH 能夠顯示錯誤資訊並捕獲應用程式的內部狀態,以幫助診斷問題。 它對於不易重現的間歇性問題特別有用。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 但是,它不是專門為C++設計的。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 對於C++程序,我們建議您使用本機C++異常處理:[嘗試、捕獲和引發](../cpp/try-throw-and-catch-statements-cpp.md)語句。

**__try**條款後的複合語句是*正文*或*受保護*部分。 **__except**表達式也稱為*篩選器*運算式。 其值確定如何處理異常。 **__except**子句之後的複合語句是異常處理程式。 處理程式指定在執行正文部分期間引發異常時要執行的操作。 執行程序如下所示：

1. 執行保護的區段。

1. 如果在執行受保護部分期間未發生異常,則在 **__except**子句之後的語句將繼續執行。

1. 如果在執行受保護節期間或在任何例程中發生異常,則計算 **__except**運算式。 有三個可能的值：

   - `EXCEPTION_CONTINUE_EXECUTION`(-1)異常將被駁回。 在例外狀況發生的位置繼續執行。

   - `EXCEPTION_CONTINUE_SEARCH`(0) 例外情況未識別。 繼續搜尋堆疊中的處理常式，首先搜尋包含 **try-except** 陳述式，然後是具有次高優先順序的處理常式。

   - `EXCEPTION_EXECUTE_HANDLER`(1) 確認例外情況。 通過執行 **__except**複合語句將控制件轉移到異常處理程式,然後在 **__except**塊之後繼續執行。

**__except**運算式被計算為 C 運算式。 它僅限於單個值、條件表達式運算符或逗號運算符。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。

每個應用程式都有自己的例外狀況處理常式。

跳入 **__try**語句無效,但跳出一個語句無效。 如果在執行**try-除外**語句的過程中終止進程,則不調用異常處理程式。

為了與以前的版本相容 **,_try、_except**和 **_except****_leave**是 **__except****__try、__except**和 **__leave**的同義詞,除非指定編譯器選項[/Za\(禁用語言擴展)。](../build/reference/za-ze-disable-language-extensions.md)

### <a name="the-__leave-keyword"></a>__leave 關鍵字

**__leave**關鍵字僅在**try-除了**語句的受保護部分內有效,其效果是跳轉到受保護部分的末尾。 然後在例外狀況處理常式之後的第一個陳述式繼續執行。

**goto**語句也可以跳出受保護的部分,並且它不會像**嘗試-最終**語句那樣降低性能。 這是因為不會進行堆疊展開。 但是,我們建議您使用 **__leave**關鍵字而不是**goto**語句。 原因是,如果受保護的部分很大或很複雜,則不太可能出現程式設計錯誤。

### <a name="structured-exception-handling-intrinsic-functions"></a>結構化例外狀況處理內建函式

結構化異常處理提供兩個可用於**try-除一**語句的固有函數:[取得 ExceptionCode](/windows/win32/Debug/getexceptioncode)和[Getexception 資訊](/windows/win32/Debug/getexceptioninformation)。

`GetExceptionCode`返回異常的代碼(32 位整數)。

內部函數`GetExceptionInformation`返回指向[EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers)結構的指標,其中包含有關異常的其他資訊。 透過這個指標就可以存取發生硬體例外狀況當時的電腦狀態。 其結構如下所示：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

`PEXCEPTION_RECORD`指標型態與`PCONTEXT`定義在 include\<檔案 winnt.h>,`_EXCEPTION_RECORD`並在`_CONTEXT`include 檔案\<excpt.h>

您可以在異常處理程式`GetExceptionCode`中使用。 但是,`GetExceptionInformation`只能在異常篩選器表達式中使用。 它指向的資訊通常位於堆疊上,當控件傳輸到異常處理程式時,這些資訊不再可用。

內在函數[異常終止](/windows/win32/Debug/abnormaltermination)在終止處理程式中可用。 如果**try-finally**語句的正文按順序終止,則返回 0。 在所有其他情況下，它會傳回 1。

\<excpt.h>定义这些内部函数的一些备用名称:

`GetExceptionCode`等效於`_exception_code`

`GetExceptionInformation`等效於`_exception_info`

`AbnormalTermination`等效於`_abnormal_termination`

## <a name="example"></a>範例

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>輸出

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

## <a name="see-also"></a>另請參閱

[編寫錯誤程式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
