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
ms.openlocfilehash: d05e1d113f4fc661cb6e2e2905fbd8c9dcdd7e2d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175916"
---
# <a name="try-finally-statement"></a>try-finally 陳述式

**Microsoft 專屬**

下列語法描述**try finally**陳述式：

> **\_\_請嘗試**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;受防護的程式碼<br/>
> }<br/>
> **\_\_最後**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;終止程式碼<br/>
> }<br/>

## <a name="grammar"></a>文法

*try-finally-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\_\_請嘗試***複合陳述式*  **\_\_最後***複合陳述式*

**Try finally**陳述式是 C 和 c + + 語言的 Microsoft 擴充功能，可讓目標應用程式來執行的程式碼區塊將會中斷時，保證會執行清除程式碼。 清除包含如取消配置記憶體、關閉檔案和釋放檔案控制代碼等工作。 **Try finally**陳述式是特別有用，有幾個地方，其中會進行檢查錯誤的可能會導致過早傳回常式。

如需相關的資訊和程式碼範例，請參閱[嘗試-try-except 陳述式](../cpp/try-except-statement.md)。 如需有關結構化例外狀況處理的詳細資訊，請參閱[Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md)。 如需有關如何處理在受管理的應用程式中的例外狀況的詳細資訊，請參閱[例外狀況處理在 /clr 下](../windows/exception-handling-cpp-component-extensions.md)。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 對於 c + + 程式，建議您使用 c + + 例外狀況處理機制 ([try、 catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)陳述式)。

後面的複合陳述式 **__try**子句是保護的區段。 後面的複合陳述式 **__finally**子句會終止處理常式。 處理常式會指定一組當保護區段結束時執行的動作，不管保護的區段是因例外狀況 (異常終止) 而結束，或是依標準的執行順序 (正常終止) 而結束。

控制項到達 **__try**經由簡單的循序執行 （正常執行） 的陳述式。 當控制項進入 **__try**，其相關聯的處理常式會變成作用中。 如果控制流程到達 try 區塊的結尾，執行程序如下所示：

1. 已叫用終止處理常式。

1. 當終止處理常式完成時之後, 會繼續執行 **__finally**陳述式。 不論如何保護區段結束 (例如，透過**goto**保護主體外部的或有**傳回**陳述式)，會執行終止處理常式*之前*控制流程移出保護區段。

   A **__finally**陳述式不會封鎖搜尋適當的例外狀況處理常式。

如果發生例外狀況 **__try**區塊中，作業系統必須尋找例外狀況處理常式或程式將會失敗。 如果處理常式找到，則所有 **__finally**區塊執行，並在處理常式繼續執行。

例如，假設有一系列的函式呼叫連結了函式 A 與函式 D，如下圖所示。 每個函式都具有一個終止處理常式。 如果例外狀況在函式 D 中引發，並在函式 A 中處理，則會在系統回溯堆疊時，依此順序呼叫終止處理常式：D、C、B。

![終止的順序&#45;處理常式執行](../cpp/media/vc38cx1.gif "順序終止&#45;處理常式執行") <br/>
終止處理常式的執行順序

> [!NOTE]
> Try-finally 的行為是不同於其他程式設計語言，支援使用**最後**，例如 C#。  單一 **__try**可能具有其中一個，但並非兩者的 **__finally**並 **__except**。  如果要同時使用兩個，外層的 try-except 陳述式必須以引號括住內部 try-finally 陳述式。  指定的規則在每個區塊執行時也不同。

為了與舊版中，相容性 **_finally**， **__identifier**，並 **_leave**同義 **__try**， **__最後**，並 **__leave**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)指定。

## <a name="the-leave-keyword"></a>__leave 關鍵字

**__Leave**關鍵字只在中是有效的保護區段**try finally**陳述式，而其作用是跳至保護區段的結尾。 然後從終止處理常式中的第一個陳述式繼續執行。

A **goto**陳述式也可以跳出保護的區段，但不是會降低效能，因為它會導致堆疊回溯。 **__Leave**陳述式會更有效率，因為它不會造成堆疊回溯的情形。

## <a name="abnormal-termination"></a>異常終止

結束**try finally**陳述式使用[longjmp](../c-runtime-library/reference/longjmp.md)執行階段函式會視為是異常終止。 它是不合法一頭栽進 **__try**陳述式，但是可以跳出一個。 所有 **__finally**起點之間有作用的陳述式 (的正常終止 **__try**區塊) 和目的地 ( **__except**區塊處理例外狀況） 必須執行。 這稱為區域回溯。

如果**嘗試**基於任何理由，包括跳出區塊已提前結束區塊，系統會執行相關聯**最後**回溯堆疊程序的一部分的區塊。 在此情況下， [AbnormalTermination](/windows/desktop/Debug/abnormaltermination)函式會傳回 **，則為 true**如果是從 內呼叫**最後**封鎖; 否則它會傳回**false**.

如果處理程序中間執行過程中終止，不會呼叫終止處理常式**try finally**陳述式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[終止處理常式語法](/windows/desktop/Debug/termination-handler-syntax)