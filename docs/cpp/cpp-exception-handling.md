---
title: C++ 例外狀況處理
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling
- Visual C++, exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
ms.openlocfilehash: b4eaab7d5bb352cccc612dd950572464b82b67e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392306"
---
# <a name="c-exception-handling"></a>C++ 例外狀況處理

C++ 語言內建擲回和攔截例外狀況支援。 使用 C++ 設計程式時，您應盡可能使用本節所述的內建 C++ 例外狀況支援。

若要啟用C++在您的程式碼，使用中處理的例外狀況[/EHsc](../build/reference/eh-exception-handling-model.md)。

## <a name="in-this-section"></a>本節內容

以下關於 C++ 例外狀況處理的討論包括：

- [Try、 catch 和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)

- [Catch 區塊的評估方式](../cpp/how-catch-blocks-are-evaluated-cpp.md)

- [例外狀況和堆疊回溯](../cpp/exceptions-and-stack-unwinding-in-cpp.md)

- [例外狀況規格](../cpp/exception-specifications-throw-cpp.md)

- [noexcept](../cpp/noexcept-cpp.md)

- [未處理的 C++ 例外狀況](../cpp/unhandled-cpp-exceptions.md)

- [混合 C (結構化) 和 C++ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)

## <a name="support-for-earlier-mfc-exceptions"></a>對於舊版 MFC 例外狀況的支援

從 4.0 版開始，MFC 開始使用 C++ 例外狀況處理機制。 雖然建議您在新的程式碼中使用 C++ 例外狀況處理，但 MFC 4.0 (含) 以後版本會保留舊版的 MFC 巨集，因此舊程式碼不會出現錯誤。 並且，您可以合併巨集和新的機制。 如需混合巨集的詳細資訊和C++例外狀況處理和轉換舊程式碼以使用新的機制，請參閱文章[例外狀況：使用 MFC 巨集和C++例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)並[例外狀況：從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。 如果您仍然使用舊版的 MFC 例外狀況巨集，它們會判斷值為 C++ 例外狀況關鍵字。 請參閱[例外狀況：變更為 3.0 版例外狀況巨集](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)