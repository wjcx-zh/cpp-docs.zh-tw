---
title: try-finally 陳述式
ms.date: 11/19/2018
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: 6234e8a2d2c18177a1e66475fff850c76f7ef73e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227071"
---
# <a name="try-finally-statement"></a>try-finally 陳述式

**Microsoft 特定的**

下列語法描述**try-catch**語句：

> **\_\_次**<br/>
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;受防護的程式碼 \
> }\
> **\_\_一點**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;終止代碼 \
> }

## <a name="grammar"></a>文法

*try-finally-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;** \_ \_ try** *複合陳述式* ** \_ \_ finally** *複合陳述式*

**Try finally**語句是 C 和 c + + 語言的 Microsoft 擴充功能，可讓目標應用程式在執行程式碼區塊中斷時，保證執行清除程式碼。 清除包含如取消配置記憶體、關閉檔案和釋放檔案控制代碼等工作。 在有多個位置的常式中，針對可能會導致常式提前傳回的錯誤進行檢查時， **try-catch**語句特別有用。

如需相關資訊和程式碼範例，請參閱[try-Except 語句](../cpp/try-except-statement.md)。 如需一般結構化例外狀況處理的詳細資訊，請參閱[結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)。 如需在 managed 應用程式中使用 c + +/CLI 處理例外狀況的詳細資訊，請參閱[/clr 下的例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 針對 c + + 程式，建議您使用 c + + 例外狀況處理機制（[try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)語句）。

**__Try**子句後面的複合陳述式是受保護的區段。 子句後面的複合陳述式 **`__finally`** 是終止處理常式。 處理常式會指定一組當保護區段結束時執行的動作，不管保護的區段是因例外狀況 (異常終止) 而結束，或是依標準的執行順序 (正常終止) 而結束。

Control 會透過簡單的連續執行（流經）來達到 **__try**的語句。 當控制項進入 **__try**時，其相關聯的處理常式會變成作用中狀態。 如果控制流程到達 try 區塊的結尾，執行程序如下所示：

1. 已叫用終止處理常式。

1. 當終止處理常式完成時，執行會在 **`__finally`** 語句之後繼續。 無論保護區段的結束方式為何（例如，透過 **`goto`** 受保護的主體或 **`return`** 語句），終止處理常式會在控制流程移出保護區段*之前*執行。

   **`__finally`** 語句不會封鎖搜尋適當的例外狀況處理常式。

如果 **__try**區塊中發生例外狀況，作業系統必須找出例外狀況的處理常式，否則程式將會失敗。 如果找到處理程式，則會執行任何和所有 **`__finally`** 區塊，並在處理常式中繼續執行。

例如，假設有一系列的函式呼叫連結了函式 A 與函式 D，如下圖所示。 每個函式都具有一個終止處理常式。 如果例外狀況在函式 D 中引發，並在函式 A 中處理，則會在系統回溯堆疊時，依此順序呼叫終止處理常式：D、C、B。

![終止&#45;處理常式執行的順序](../cpp/media/vc38cx1.gif "終止&#45;處理常式執行的順序") <br/>
終止處理常式的執行順序

> [!NOTE]
> Try-finally 的行為與支援使用**finally**的其他語言（例如 c #）不同。  單一 **__try**可能有和兩者，但不能同時有 **`__finally`** 兩者 **`__except`** 。  如果要同時使用兩個，外層的 try-except 陳述式必須以引號括住內部 try-finally 陳述式。  指定的規則在每個區塊執行時也不同。

為了與舊版相容， **_try**、 **_finally**和 **_leave**都是指定 **__try**、和的同義字， **`__finally`** **`__leave`** 除非已指定編譯器選項[/za 停用 \( 語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="the-__leave-keyword"></a>__leave 關鍵字

**`__leave`** 關鍵字僅適用于**try-catch**語句的保護區段，其作用是跳至受保護區段的結尾。 然後從終止處理常式中的第一個陳述式繼續執行。

**`goto`** 語句也可以跳出保護的區段，但它會降低效能，因為它會叫用堆疊回溯。 **`__leave`** 語句會更有效率，因為它不會導致堆疊回溯。

## <a name="abnormal-termination"></a>異常終止

使用[longjmp](../c-runtime-library/reference/longjmp.md)執行時間函式來結束**try-catch**語句，會被視為異常終止。 跳到 **__try**語句是不合法的，但從一開始就是合法的。 所有在 **`__finally`** 出發點（ **__try**區塊的正常終止）和目的地（處理例外狀況的區塊）之間作用的語句都 **`__except`** 必須執行。 這稱為區域回溯。

如果 **`try`** 區塊因任何原因而提前終止，包括跳出區塊，則系統會在回溯堆疊的過程中執行相關聯的**finally**區塊。 在這種情況下[AbnormalTermination](/windows/win32/Debug/abnormaltermination) ，如果是 **`true`** 從**finally**區塊內呼叫，AbnormalTermination 函式會傳回，否則會傳回 **`false`** 。

如果進程在執行**try-catch**語句的過程中終止，則不會呼叫終止處理常式。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[終止-處理常式語法](/windows/win32/Debug/termination-handler-syntax)
