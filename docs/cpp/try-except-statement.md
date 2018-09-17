---
title: 請嘗試-try-except 陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2780697c1a50e15e170f2096a2841e2c50d844a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724681"
---
# <a name="try-except-statement"></a>try-except 陳述式

**Microsoft 專屬**

**嘗試-除了**陳述式是 C 的 Microsoft 擴充功能，以及 c + + 語言的支援結構化例外狀況處理。  

## <a name="syntax"></a>語法  
  
> **__try**   
> {  
>    受防護的程式碼  
> }  
> **__except** (*運算式*)  
> {  
>    例外狀況處理常式程式碼  
> }  

## <a name="remarks"></a>備註

**嘗試-除了**陳述式是 C 的 Microsoft 擴充功能，並讓目標應用程式，以取得 c + + 語言可讓您控制通常會終止程式執行的事件發生時。 這類事件稱為*例外狀況*，並處理例外狀況的機制稱為*結構化例外狀況處理*(SEH)。

如需相關資訊，請參閱[try-finally 陳述式](../cpp/try-finally-statement.md)。

例外狀況可能以硬體或軟體為主。 即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理仍可顯示錯誤資訊，並且對應用程式的內部狀態設陷，以協助診斷問題。 這在處理無法輕易重現的間歇性問題時特別有用。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 對於 c + + 程式，建議您使用 c + + 例外狀況處理機制 ([try、 catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)陳述式)。

後面的複合陳述式 **__try**子句是主體或保護的區段。 後面的複合陳述式 **__except**子句是例外狀況處理常式。 如果在執行保護區段的主體時引發例外狀況，則處理常式會指定要採取的一組動作。 執行程序如下所示：

1. 執行保護的區段。

2. 如果沒有發生例外狀況執行保護區段期間，在之後的陳述式會繼續執行 **__except**子句。  

3. 如果執行保護區段期間發生的例外狀況，或在任何受保護的區段所呼叫常式， **__except** *運算式*(稱為*篩選*運算式)評估和值會決定如何處理例外狀況。 共有三個值：

   EXCEPTION_CONTINUE_EXECUTION (-1) 例外狀況已解除。 在例外狀況發生的位置繼續執行。

   無法辨識 EXCEPTION_CONTINUE_SEARCH (0) 的例外狀況。 繼續搜尋堆疊中的處理常式，首先搜尋包含 **try-except** 陳述式，然後是具有次高優先順序的處理常式。

   辨識 EXCEPTION_EXECUTE_HANDLER (1) 例外狀況。 藉由執行將控制權轉移到例外狀況處理常式 **__except**複合陳述式，則之後繼續執行 **__except**區塊。

因為 **__except**運算式以 C 運算式求值，長度限制為單一值、 條件運算式運算子或逗號運算子。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。

每個應用程式都有自己的例外狀況處理常式。

不是有效一頭栽進 **__try**陳述式，但是可以跳出一個。 如果執行中期終止處理程序，不會呼叫例外狀況處理常式**嘗試-除了**陳述式。  
  
如需詳細資訊，請參閱知識庫文件 Q315937：＜如何：對 Visual C++ 應用程式中的堆疊溢位設陷＞(機器譯文)。  
  
## <a name="the-leave-keyword"></a>__leave 關鍵字

**__Leave**關鍵字只在中是有效的保護區段**嘗試-除了**陳述式，而其作用是跳至保護區段的結尾。 然後在例外狀況處理常式之後的第一個陳述式繼續執行。

A **goto**陳述式也可以跳出保護的區段中，而且它不會不會降低效能中一樣**try finally**陳述式因為堆疊回溯不會發生。 不過，我們建議您改用 **__leave**關鍵字而非**goto**陳述式因為您不太可能進行保護的區段是否大型或複雜的程式設計錯誤。

### <a name="structured-exception-handling-intrinsic-functions"></a>結構化例外狀況處理內建函式

結構化例外狀況處理提供兩個內建函式可搭配**嘗試-除了**陳述式：`GetExceptionCode`和`GetExceptionInformation`。

`GetExceptionCode` 傳回例外狀況的程式碼 （32 位元整數）。

內建函式`GetExceptionInformation`傳回結構，包含例外狀況的其他資訊的指標。 透過這個指標就可以存取發生硬體例外狀況當時的電腦狀態。 結構如下所示：

```cpp  
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS; 
```  

指標類型`PEXCEPTION_RECORD`和`PCONTEXT`include 檔中定義\<winnt.h >，和`_EXCEPTION_RECORD`並`_CONTEXT`include 檔中定義\<excpt.h >

您可以使用`GetExceptionCode`例外狀況處理常式內。 不過，您可以使用`GetExceptionInformation`只有在例外狀況篩選條件運算式內。 它所指向的資訊通常位於堆疊上，而且在控制項傳送至例外狀況處理常式之後就不再提供。

內建函式`AbnormalTermination`終止處理常式內可供使用。 它會傳回 0，如果主體**try finally**循序陳述式會終止。 在所有其他情況下，它會傳回 1。

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
  
## <a name="output"></a>輸出  
  
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

**結束 Microsoft 專屬**  

## <a name="see-also"></a>另請參閱
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化的例外處理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)