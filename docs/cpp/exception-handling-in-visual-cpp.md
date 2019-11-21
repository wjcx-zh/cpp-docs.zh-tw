---
title: Exception handling in MSVC
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246584"
---
# <a name="exception-handling-in-msvc"></a>Exception handling in MSVC

例外狀況是可能超出程式控制範圍的錯誤條件，它會使得程式無法繼續沿著其正常執行路徑進行。 即使您的程式正常執行，某些作業 (包括建立物件、檔案輸入/輸出以及其他模組發出的函式呼叫) 仍可能是例外狀況的來源。 穩定的程式碼會預測及處理例外狀況。 To detect logic errors, use assertions rather than exceptions (see [Using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Kinds of exceptions

The Microsoft C++ compiler (MSVC) supports three kinds of exception handling:

- [C++ exception handling](errors-and-exception-handling-modern-cpp.md)

   對於大部分 C++ 程式，您應該使用具備類型安全的 C++ 例外狀況處理，以確保在堆疊回溯期間叫用物件解構函式。

- [Structured exception handling](structured-exception-handling-c-cpp.md)

   Windows 提供自己的例外狀況機制，稱為 SEH。 不建議在 C++ 或 MFC 程式設計中使用這個機制。 Use SEH only in non-MFC C programs.

- [MFC exceptions](../mfc/exception-handling-in-mfc.md)

Use the [/EH](../build/reference/eh-exception-handling-model.md) compiler option to specify the type of exception handling to use in a project; C++ exception handling is the default. 請不要混用錯誤處理機制，例如，不要將 C++ 例外狀況與結構化例外狀況處理混用。 使用 C++ 例外狀況處理可讓您的程式碼更具可攜性，並可讓您處理任何類型的例外狀況。 For more information about the drawbacks of structured exception handling, see [Structured Exception Handling](structured-exception-handling-c-cpp.md). For advice about mixing MFC macros and C++ exceptions, see [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>本節內容

- [Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)

- [How to design for exception safety](how-to-design-for-exception-safety.md)

- [How to interface between exceptional and non-exceptional code](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [The try, catch, and throw Statements](try-throw-and-catch-statements-cpp.md)

- [Catch 區塊的評估方式](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions and Stack Unwinding](exceptions-and-stack-unwinding-in-cpp.md)

- [Exception Specifications](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未處理的 C++ 例外狀況](unhandled-cpp-exceptions.md)

- [混合 C (結構化) 和 C++ 例外狀況](mixing-c-structured-and-cpp-exceptions.md)

- [Structured Exception Handling (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>請參閱

[C++ 語言參考](cpp-language-reference.md)</br>
[x64 例外狀況處理](../build/exception-handling-x64.md)</br>
[Exception Handling (C++/CLI and C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
