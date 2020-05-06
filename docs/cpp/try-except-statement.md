---
title: try-except 陳述式
description: __Try 和 __except 結構化例外狀況處理語句的 Microsoft c + + 參考。
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
ms.openlocfilehash: d0471bbd50e07fccbf160e9e866de4c545cdeb7e
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825766"
---
# <a name="try-except-statement"></a>try-except 陳述式

**Try-except**語句是 Microsoft 擴充功能，可支援 c 和 c + + 語言的結構化例外狀況處理。 此延伸模組是**Microsoft 特有**的。

## <a name="syntax"></a>語法

> **\_\_次**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;受防護的程式碼 \
> }\
> except （ *expression* ） \ ** \_ \_ **
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;例外狀況處理常式代碼 \
> }

## <a name="remarks"></a>備註

**Try-except**語句是 C 和 c + + 語言的 Microsoft 擴充功能。 它可讓目標應用程式在發生通常會終止程式執行的事件時取得控制。 這類事件稱為*結構化例外*狀況，或簡稱*例外*狀況。 處理這些例外狀況的機制稱為*結構化例外狀況處理*（SEH）。

如需相關資訊，請參閱[try finally 語句](../cpp/try-finally-statement.md)。

例外狀況可能是以硬體為基礎或以軟體為基礎。 即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理也很有用。 SEH 可以顯示錯誤資訊，並將應用程式的內部狀態設為可協助診斷問題。 它特別適用于不容易重現的間歇性問題。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 c + + 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 針對 c + + 程式，建議您使用原生 c + + 例外狀況處理： [try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)語句。

**__Try**子句後面的複合陳述式是*主體*或*受保護*的區段。 **__Except**運算式也稱為「*篩選準則*運算式」。 其值會決定如何處理例外狀況。 **__Except**子句後面的複合陳述式是例外狀況處理常式。 如果在執行主體區段期間引發例外狀況，則處理常式會指定要採取的動作。 執行程序如下所示：

1. 執行保護的區段。

1. 如果在執行保護區段期間未發生任何例外狀況，則會在 **__except**子句後面的語句繼續執行。

1. 如果在執行保護的區段期間，或在受保護區段呼叫的任何常式中發生例外狀況，則會評估 **__except**運算式。 有三個可能的值：

   - `EXCEPTION_CONTINUE_EXECUTION`（-1）例外狀況已關閉。 在例外狀況發生的位置繼續執行。

   - `EXCEPTION_CONTINUE_SEARCH`（0）無法辨識例外狀況。 繼續搜尋堆疊中的處理常式，首先搜尋包含 **try-except** 陳述式，然後是具有次高優先順序的處理常式。

   - `EXCEPTION_EXECUTE_HANDLER`（1）識別出例外狀況。 藉由執行 **__except**複合陳述式，然後在 **__except**區塊之後繼續執行，以將控制權轉移給例外狀況處理常式。

**__Except**運算式會評估為 C 運算式。 其限制為單一值、條件運算式運算子或逗號運算子。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。

每個應用程式都有自己的例外狀況處理常式。

跳入 **__try**語句是有效的，但有效的是跳出其中一項。 如果進程在執行**try-catch**語句的過程中終止，則不會呼叫例外狀況處理常式。

為了與舊版相容，除非指定了編譯器選項[ \(/za 停用語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能，否則 **_try**、 **_except**和 **_leave**都是 **__try**、 **__except**和 **__leave**的同義字。

### <a name="the-__leave-keyword"></a>__leave 關鍵字

**__Leave**關鍵字僅適用于**try-except**語句的保護區段，而且其效果是跳至受保護區段的結尾。 然後在例外狀況處理常式之後的第一個陳述式繼續執行。

**Goto**語句也可以跳出保護的區段，而不會降低效能，如同在**try-catch**語句中所做的一樣。 這是因為堆疊回溯不會發生。 不過，我們建議您使用 **__leave**關鍵字，而不要使用**goto**語句。 原因是，如果保護的區段很大或很複雜，您就不太可能發生程式設計錯誤。

### <a name="structured-exception-handling-intrinsic-functions"></a>結構化例外狀況處理內建函式

結構化例外狀況處理提供兩個內建函式，可與**try-except**語句搭配使用： [GetExceptionCode](/windows/win32/Debug/getexceptioncode)和[GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)。

`GetExceptionCode`傳回例外狀況的程式碼（32位整數）。

內建函式`GetExceptionInformation`會傳回[EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers)結構的指標，其中包含例外狀況的其他相關資訊。 透過這個指標就可以存取發生硬體例外狀況當時的電腦狀態。 其結構如下所示：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

`PEXCEPTION_RECORD`指標類型`PCONTEXT`和定義于 include \<檔案中，>，而`_EXCEPTION_RECORD`和`_CONTEXT`則定義于 include 檔\<excpt.h 中>

您可以在`GetExceptionCode`例外狀況處理常式內使用。 不過，您只能在`GetExceptionInformation`例外狀況篩選條件運算式中使用。 它所指向的資訊通常是在堆疊上，而且當控制權轉移給例外狀況處理常式時，就無法再使用。

內建函式[AbnormalTermination](/windows/win32/Debug/abnormaltermination)可在終止處理常式中使用。 如果**try-catch**語句的主體順序終止，它會傳回0。 在所有其他情況下，它會傳回 1。

\<excpt.h> 會定義這些內建函式的一些替代名稱：

`GetExceptionCode`相當於`_exception_code`

`GetExceptionInformation`相當於`_exception_info`

`AbnormalTermination`相當於`_abnormal_termination`

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

## <a name="see-also"></a>請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
