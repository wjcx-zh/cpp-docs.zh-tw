---
title: try-except 陳述式
description: __Try 和 __except 結構化例外狀況處理語句的 Microsoft c + + 參考。
ms.date: 08/25/2020
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
ms.openlocfilehash: 226c3a3df39f284d9c1267051114fc39db358f55
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898624"
---
# <a name="try-except-statement"></a>`try-except` 陳述式

`try-except`語句是**Microsoft 特定**的擴充功能，可支援 C 和 c + + 語言的結構化例外狀況處理。

```cpp
    // . . .
    __try {
        // guarded code
    }
    __except ( /* filter expression */ ) {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>文法

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

## <a name="remarks"></a>備註

`try-except`語句是 C 和 c + + 語言的 Microsoft 擴充功能。 它可讓目標應用程式在通常會終止程式執行的事件發生時，掌握控制權。 這類事件稱為 *結構化例外*狀況，或簡稱 *例外* 狀況。 處理這些例外狀況的機制稱為 *結構化例外狀況處理* ， (SEH) 。

如需相關資訊，請參閱 [try finally 語句](../cpp/try-finally-statement.md)。

例外狀況可能是以硬體為基礎或以軟體為基礎。 即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理仍很有用。 SEH 可以顯示錯誤資訊，並將應用程式的內部狀態設為可協助診斷問題。 它特別適用于不容易重現的間歇性問題。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 但是，它不是專為 c + + 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 針對 c + + 程式，建議您使用原生 c + + 例外狀況處理： [try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md) 語句。

子句後面的複合陳述式 **`__try`** 是 *主體* 或 *受保護* 的區段。 **`__except`** 運算式也稱為*篩選*運算式。 它的值會決定例外狀況的處理方式。 子句後面的複合陳述式 **`__except`** 是例外狀況處理常式。 如果在主體區段執行期間引發例外狀況，則處理常式會指定要採取的動作。 執行程序如下所示：

1. 執行保護的區段。

1. 如果在執行受保護區段期間未發生任何例外狀況，則會在子句之後的語句繼續執行 **`__except`** 。

1. 如果在執行受保護區段期間發生例外狀況，或在受保護區段呼叫的任何常式中發生例外狀況，則 **`__except`** 會評估運算式。 有三個可能的值：

   - `EXCEPTION_CONTINUE_EXECUTION` (-1) 例外狀況已關閉。 在例外狀況發生的位置繼續執行。

   - `EXCEPTION_CONTINUE_SEARCH` 無法辨識 (0) 例外狀況。 繼續搜尋堆疊中的處理常式，先針對包含 `try-except` 語句，然後針對具有下一個最高優先順序的處理常式。

   - `EXCEPTION_EXECUTE_HANDLER` (1) 例外狀況被辨識。 藉由執行複合陳述式來將控制權傳送至例外狀況處理常式 **`__except`** ，然後在區塊之後繼續執行 **`__except`** 。

**`__except`** 運算式會評估為 C 運算式。 它受限於單一值、條件運算式運算子或逗號運算子。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。

每個應用程式都有自己的例外狀況處理常式。

跳入語句是不正確 **`__try`** ，但有效的方式就是跳出一個語句。 如果進程在執行語句的中途結束，則不會呼叫例外狀況處理常式 `try-except` 。

為了與舊版相容， **_try**、 **_except**和 **_leave** 是、和的同義字 **`__try`** ， **`__except`** **`__leave`** 除非指定了編譯器選項 [/za \( 停用語言延伸模組) ](../build/reference/za-ze-disable-language-extensions.md) 。

### <a name="the-__leave-keyword"></a><a name="__leave"></a>`__leave`關鍵字

**`__leave`** 關鍵字只有在語句的保護區段內才有效 `try-except` ，而其效果是跳到受保護區段的結尾。 然後在例外狀況處理常式之後的第一個陳述式繼續執行。

**`goto`** 語句也可以跳出受保護的區段，而不會降低效能，就像在**try-catch**語句中所做的一樣。 這是因為堆疊回溯不會發生。 不過，我們建議您使用 **`__leave`** 關鍵字而不是 **`goto`** 語句。 原因是，如果受保護的區段很大或複雜，您較不可能犯程式設計錯誤。

### <a name="structured-exception-handling-intrinsic-functions"></a>結構化例外狀況處理內建函式

結構化例外狀況處理提供兩個可搭配語句使用的內建函式 `try-except` ： [GetExceptionCode](/windows/win32/Debug/getexceptioncode) 和 [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)。

`GetExceptionCode` 傳回例外狀況的32位整數) 的程式碼 (。

內建函式會傳回 `GetExceptionInformation` [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) 結構的指標，其中包含有關例外狀況的其他資訊。 透過這個指標就可以存取發生硬體例外狀況當時的電腦狀態。 其結構如下所示：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

指標類型 `PEXCEPTION_RECORD` 和 `PCONTEXT` 定義于 include 檔中，而且 \<winnt.h> `_EXCEPTION_RECORD` `_CONTEXT` 會定義于 include 檔中。 \<excpt.h>

您可以在 `GetExceptionCode` 例外狀況處理常式中使用。 不過，您只能在 `GetExceptionInformation` 例外狀況篩選條件運算式內使用。 它所指向的資訊通常是在堆疊上，而且當控制權轉移到例外狀況處理常式時，就無法再使用。

內建函式 [AbnormalTermination](/windows/win32/Debug/abnormaltermination) 可在終止處理常式中使用。 如果 **try-catch** 語句的主體依序終止，它會傳回0。 在所有其他情況下，它會傳回 1。

\<excpt.h> 定義這些內建函式的一些替代名稱：

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

## <a name="see-also"></a>請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
