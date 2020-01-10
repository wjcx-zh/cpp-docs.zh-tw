---
title: MSVC 中的例外狀況處理
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
# <a name="exception-handling-in-msvc"></a>MSVC 中的例外狀況處理

例外狀況是可能超出程式控制範圍的錯誤條件，它會使得程式無法繼續沿著其正常執行路徑進行。 即使您的程式正常執行，某些作業 (包括建立物件、檔案輸入/輸出以及其他模組發出的函式呼叫) 仍可能是例外狀況的來源。 穩定的程式碼會預測及處理例外狀況。 若要偵測邏輯錯誤，請使用判斷提示，而不是例外狀況（請參閱[使用判斷](/visualstudio/debugger/c-cpp-assertions)提示）。

## <a name="kinds-of-exceptions"></a>例外狀況的種類

Microsoft C++編譯器（MSVC）支援三種例外狀況處理：

- [C++例外狀況處理](errors-and-exception-handling-modern-cpp.md)

   對於大部分 C++ 程式，您應該使用具備類型安全的 C++ 例外狀況處理，以確保在堆疊回溯期間叫用物件解構函式。

- [結構化例外狀況處理](structured-exception-handling-c-cpp.md)

   Windows 提供自己的例外狀況機制，稱為 SEH。 不建議在 C++ 或 MFC 程式設計中使用這個機制。 僅在非 MFC C 程式中使用 SEH。

- [MFC 例外狀況](../mfc/exception-handling-in-mfc.md)

使用[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項來指定要在專案中使用的例外狀況處理類型;C++例外狀況處理是預設值。 請不要混用錯誤處理機制，例如，不要將 C++ 例外狀況與結構化例外狀況處理混用。 使用 C++ 例外狀況處理可讓您的程式碼更具可攜性，並可讓您處理任何類型的例外狀況。 如需結構化例外狀況處理之缺點的詳細資訊，請參閱[結構化例外狀況處理](structured-exception-handling-c-cpp.md)。 如需混合 MFC 宏和C++例外狀況的相關建議，請參閱例外狀況[：使用 MFC 宏和C++例外](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)狀況。

## <a name="in-this-section"></a>本節內容

- [例外C++狀況和錯誤處理的現代化最佳做法](errors-and-exception-handling-modern-cpp.md)

- [如何針對例外狀況安全性進行設計](how-to-design-for-exception-safety.md)

- [如何在例外狀況和非例外狀況程式碼之間進行介面](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Try、catch 和 throw 語句](try-throw-and-catch-statements-cpp.md)

- [Catch 區塊的評估方式](how-catch-blocks-are-evaluated-cpp.md)

- [例外狀況和堆疊回溯](exceptions-and-stack-unwinding-in-cpp.md)

- [例外狀況規格](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未處理的 C++ 例外狀況](unhandled-cpp-exceptions.md)

- [混合 C (結構化) 和 C++ 例外狀況](mixing-c-structured-and-cpp-exceptions.md)

- [結構化例外狀況處理（SEH）（C++C/）](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>另請參閱

[C++ 語言參考](cpp-language-reference.md)</br>
[x64 例外狀況處理](../build/exception-handling-x64.md)</br>
[例外狀況處理C++（/Cli C++和/cx）](../extensions/exception-handling-cpp-component-extensions.md)
