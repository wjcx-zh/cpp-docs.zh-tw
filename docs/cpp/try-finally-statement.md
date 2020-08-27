---
title: try-finally 陳述式
description: __Try 和 __finally 結構化例外狀況處理語句的 Microsoft c + + 參考。
ms.date: 08/25/2020
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
ms.openlocfilehash: edabbbe35c86f0305e31f36584c4dfe01f2f88cd
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898649"
---
# <a name="try-finally-statement"></a>`try-finally` 陳述式

`try-finally`語句是**Microsoft 特定**的擴充功能，可支援 C 和 c + + 語言的結構化例外狀況處理。

## <a name="syntax"></a>語法

下列語法描述 `try-finally` 語句：

```cpp
    // . . .
    __try {
        // guarded code
    }
    __finally {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>文法

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

`try-finally`語句是 C 和 c + + 語言的 Microsoft 擴充功能，可讓目標應用程式在執行程式碼區塊中斷時，保證執行清除程式碼。 清除包含如取消配置記憶體、關閉檔案和釋放檔案控制代碼等工作。 `try-finally` 陳述式對於有多個地方要檢查可能會導致常式過早傳回的錯誤時會特別有用。

如需相關資訊和程式碼範例，請參閱[ `try-except` 語句](../cpp/try-except-statement.md)。 如需一般結構化例外狀況處理的詳細資訊，請參閱 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)。 如需使用 c + +/CLI 處理 managed 應用程式例外狀況的詳細資訊，請參閱底下的[例外狀況處理 `/clr` ](../extensions/exception-handling-cpp-component-extensions.md)。

> [!NOTE]
> 結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 若是 c + + 程式，建議您使用 c + + 例外狀況處理機制， ([ `try` 、 `catch` 和 `throw` ](../cpp/try-throw-and-catch-statements-cpp.md)語句) 。

子句後面的複合陳述式 **`__try`** 是受保護的區段。 子句後面的複合陳述式 **`__finally`** 是終止處理常式。 處理常式會指定一組當保護區段結束時執行的動作、是否因例外狀況 (異常終止) 而結束受保護的區段，或依標準 (正常終止) 。

藉 **`__try`** 由簡單的循序執行，將控制項傳遞至語句 (貫穿) 。 當控制項進入時 **`__try`** ，其相關聯的處理常式會變成作用中狀態。 如果控制流程到達 try 區塊的結尾，執行程序如下所示：

1. 已叫用終止處理常式。

1. 終止處理常式完成時，會在語句之後繼續執行 **`__finally`** 。 不過，受保護的區段會 (例如，透過 **`goto`** 超出防護主體或 **`return`** 語句) 來執行，終止處理常式會在控制流程移出保護區段 *之前* 執行。

   **`__finally`** 語句不會封鎖搜尋適當的例外狀況處理常式。

如果區塊中發生例外狀況 **`__try`** ，作業系統必須找到例外狀況的處理常式，否則程式將會失敗。 如果找到處理程式，則會執行任何和所有 **`__finally`** 區塊，並且在處理常式中繼續執行。

例如，假設有一系列的函式呼叫連結了函式 A 與函式 D，如下圖所示。 每個函式都具有一個終止處理常式。 如果例外狀況在函式 D 中引發，並在函式 A 中處理，則會在系統回溯堆疊時，依此順序呼叫終止處理常式：D、C、B。

![終止&#45;處理常式的執行順序](../cpp/media/vc38cx1.gif "終止&#45;處理常式的執行順序") <br/>
終止處理常式的執行順序

> [!NOTE]
> Try-catch 的行為不同于支援使用的其他語言 **`finally`** ，例如 c #。  單一 **`__try`** 可以有（但不是兩者）和兩者 **`__finally`** **`__except`** 。  如果要同時使用兩個，外層的 try-except 陳述式必須以引號括住內部 try-finally 陳述式。  指定的規則在每個區塊執行時也不同。

為了與舊版相容，、 **`_try`** 和 **`_finally`** **`_leave`** 都是、和的同義字， **`__try`** **`__finally`** **`__leave`** 除非指定了編譯器選項[ `/Za` (停用語言延伸模組) ](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="the-__leave-keyword"></a>__leave 關鍵字

**`__leave`** 關鍵字只有在語句的保護區段內才有效 `try-finally` ，而其效果是跳到受保護區段的結尾。 然後從終止處理常式中的第一個陳述式繼續執行。

**`goto`** 語句也可以跳出受保護的區段，但它會降低效能，因為它會叫用堆疊回溯。 **`__leave`** 語句會更有效率，因為它不會導致堆疊回溯。

## <a name="abnormal-termination"></a>異常終止

`try-finally`使用[longjmp](../c-runtime-library/reference/longjmp.md)執行時間函式結束語句會被視為異常終止。 跳到陳述並不合法 **`__try`** ，但要跳到其中一項是合法的。 **`__finally`** 在起飛點之間作用的所有語句 (區塊) 的正常終止 **`__try`** ，以及處理例外狀況) 的目的地 (**`__except`** 必須執行。 它稱為「 *本機*回溯」。

如果 **`__try`** 區塊因為任何原因而提前終止，包括跳出區塊，系統會在回溯堆疊的過程中執行相關聯的 **`__finally`** 區塊。 在這種情況下， [`AbnormalTermination`](/windows/win32/Debug/abnormaltermination) **`true`** 如果從區塊內呼叫，函數會傳回， **`__finally`** 否則會傳回 **`false`** 。

如果進程在執行語句的過程中終止，則不會呼叫終止處理常式 `try-finally` 。

**結束 Microsoft 專用**

## <a name="see-also"></a>請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[終止-處理常式語法](/windows/win32/Debug/termination-handler-syntax)
