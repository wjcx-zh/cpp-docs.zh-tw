---
title: try-except 陳述式
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- _except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
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
ms.openlocfilehash: af378f510f11e1fe7d08619b5f33efe92a13d7be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245167"
---
# <a name="try-except-statement"></a>try-except 陳述式

**Microsoft 特定的**

**Try-except**語句是 C 和C++語言的 Microsoft 擴充功能，可支援結構化例外狀況處理。

## <a name="syntax"></a>語法

> **\_\_試用**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//受防護程式碼<br/>
> }<br/>
> **\_\_除外**（ *expression* ）<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//例外狀況處理常式代碼<br/>
> }

## <a name="remarks"></a>備註

**Try-except**語句是 C 和C++語言的 Microsoft 擴充功能，可讓目標應用程式在發生通常會終止程式執行的事件時取得控制。 這類事件稱為*例外*狀況，而處理例外狀況的機制稱為*結構化例外狀況處理*（SEH）。

如需相關資訊，請參閱[try finally 語句](../cpp/try-finally-statement.md)。

例外狀況可能以硬體或軟體為主。 即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理仍可顯示錯誤資訊，並且對應用程式的內部狀態設陷，以協助診斷問題。 這在處理無法輕易重現的間歇性問題時特別有用。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 對於C++程式，建議您使用C++例外狀況處理機制（[try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)語句）。

**__Try**子句後面的複合陳述式是主體或受保護的區段。 **__Except**子句後面的複合陳述式是例外狀況處理常式。 如果在執行保護區段的主體時引發例外狀況，則處理常式會指定要採取的一組動作。 執行程序如下所示：

1. 執行保護的區段。

1. 如果在執行保護區段期間未發生任何例外狀況，則會在 **__except**子句後面的語句繼續執行。

1. 如果在執行保護的區段時或在保護區段所呼叫的任何常式中發生例外狀況，則會評估 **__except** *運算式*（稱為*篩選*運算式），而值會決定如何處理例外狀況。 可能的值有三個：

   - EXCEPTION_CONTINUE_EXECUTION （-1）例外狀況已關閉。 在例外狀況發生的位置繼續執行。

   - EXCEPTION_CONTINUE_SEARCH （0）無法辨識例外狀況。 繼續搜尋堆疊中的處理常式，首先搜尋包含 **try-except** 陳述式，然後是具有次高優先順序的處理常式。

   - 已辨識 EXCEPTION_EXECUTE_HANDLER （1）例外狀況。 藉由執行 **__except**複合陳述式，然後在 **__except**區塊之後繼續執行，以將控制權轉移給例外狀況處理常式。

因為 **__except**運算式會評估為 C 運算式，所以僅限於單一值、條件運算式運算子或逗號運算子。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。

每個應用程式都有自己的例外狀況處理常式。

跳入 **__try**語句是不正確，但有效的是跳到其中一個。 如果進程在執行**try-catch**語句的過程中終止，則不會呼叫例外狀況處理常式。

為了與舊版相容，除非指定了編譯器選項[/za __Except 停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_try**、 **_except**和 **_leave**都是 **__try**、 **__leave**和 **\(** 的同義字。

### <a name="the-__leave-keyword"></a>__leave 關鍵字

**__Leave**關鍵字僅適用于**try-except**語句的保護區段，而且其效果是跳至受保護區段的結尾。 然後在例外狀況處理常式之後的第一個陳述式繼續執行。

**Goto**語句也可以跳出保護的區段，而不會降低效能，因為它會在**try-catch**語句中執行，因為堆疊回溯不會發生。 不過，我們建議您使用 **__leave**關鍵字，而不要使用**goto**語句，因為如果保護的區段很大或複雜，則不太可能造成程式設計錯誤。

### <a name="structured-exception-handling-intrinsic-functions"></a>結構化例外狀況處理內建函式

結構化例外狀況處理提供兩個內建函式，可搭配**try-except**語句使用： `GetExceptionCode` 和 `GetExceptionInformation`。

`GetExceptionCode` 會傳回例外狀況的程式碼（32位整數）。

內建函式 `GetExceptionInformation` 會傳回結構的指標，其中包含例外狀況的其他相關資訊。 透過這個指標就可以存取發生硬體例外狀況當時的電腦狀態。 結構如下：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

`PEXCEPTION_RECORD` 和 `PCONTEXT` 的指標類型是在 include 檔中定義，\<winnt. h >，而 `_EXCEPTION_RECORD` 和 `_CONTEXT` 則定義于 include 檔案 \<excpt.h 中 >

您可以在例外狀況處理常式內使用 `GetExceptionCode`。 不過，您只能在例外狀況篩選條件運算式中使用 `GetExceptionInformation`。 它所指向的資訊通常位於堆疊上，而且在控制項傳送至例外狀況處理常式之後就不再提供。

內建函式 `AbnormalTermination` 可在終止處理常式中使用。 如果**try-catch**語句的主體順序終止，它會傳回0。 在所有其他情況下，它會傳回 1。

excpt.h 會定義這些內建函式的一些替代名稱：

`GetExceptionCode` 相當於 `_exception_code`

`GetExceptionInformation` 相當於 `_exception_info`

`AbnormalTermination` 相當於 `_abnormal_termination`

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
