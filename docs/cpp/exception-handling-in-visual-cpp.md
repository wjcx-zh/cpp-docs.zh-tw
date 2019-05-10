---
title: 在 MSVC 中處理的例外狀況
ms.date: 05/07/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 47443f1b7021aac7755d77f797a4f7b7410281f8
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222073"
---
# <a name="exception-handling-in-msvc"></a>在 MSVC 中處理的例外狀況

例外狀況是可能超出程式控制範圍的錯誤條件，它會使得程式無法繼續沿著其正常執行路徑進行。 即使您的程式正常執行，某些作業 (包括建立物件、檔案輸入/輸出以及其他模組發出的函式呼叫) 仍可能是例外狀況的來源。 穩定的程式碼會預測及處理例外狀況。

若要偵測單一程式或模組內的邏輯錯誤，請使用判斷提示，而不是例外狀況 (請參閱[使用判斷提示](/visualstudio/debugger/c-cpp-assertions))。

MicrosoftC++編譯器 (MSVC) 支援三種類型的例外狀況處理：

- [C++例外狀況處理](../cpp/cpp-exception-handling.md)

   對於大部分 C++ 程式，您應該使用具備類型安全的 C++ 例外狀況處理，以確保在堆疊回溯期間叫用物件解構函式。

- [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)

   Windows 提供自己的例外狀況機制，稱為 SEH。 不建議在 C++ 或 MFC 程式設計中使用這個機制。 只能在非 MFC C 程式中使用 SEH。

- [MFC 例外狀況](../mfc/exception-handling-in-mfc.md)

   從 3.0 版開始，MFC 使用了 C++ 例外狀況，但是仍支援舊有的例外狀況處理巨集，其形式類似 C++ 例外狀況。 雖然不建議新的程式設計使用這些巨集，但是仍然支援它們以提供回溯相容性。 在已經使用巨集的程式中，您也可以使用 C++ 例外狀況而不受限制。 在前置處理巨集評估例外狀況處理中的 MSVC 實作所定義的關鍵字C++自 Visual 的語言C++2.0 版。 在您開始使用 C++ 例外狀況時，可以保留現有的例外狀況巨集。

使用  [/EH](../build/reference/eh-exception-handling-model.md)編譯器選項以指定的例外狀況處理的專案中; 中使用的類型C++例外狀況處理是預設值。 請不要混用錯誤處理機制，例如，不要將 C++ 例外狀況與結構化例外狀況處理混用。 使用 C++ 例外狀況處理可讓您的程式碼更具可攜性，並可讓您處理任何類型的例外狀況。 結構化例外狀況處理的缺點的相關資訊，請參閱[Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md)。 如需有關混用 MFC 巨集的建議和C++例外狀況，請參閱[例外狀況：使用 MFC 巨集和C++例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

如需處理 CLR 應用程式中的例外狀況資訊，請參閱[例外狀況處理 (C++/CLI 和C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)。

如需有關在 x64 上處理的例外狀況資訊的處理器，請參閱[x64 例外狀況處理](../build/exception-handling-x64.md)。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)