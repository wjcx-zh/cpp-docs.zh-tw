---
title: 例外狀況：使用 MFC 巨集和 C++ 例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: 9e97eb545dedd3ac38dd93471f82aecc382717ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223170"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>例外狀況：使用 MFC 巨集和 C++ 例外狀況

本文討論撰寫同時使用 MFC 例外狀況處理宏和 c + + 例外狀況處理關鍵字之程式碼的考慮。

本文章涵蓋下列主題：

- [混合例外狀況關鍵字和宏](#_core_mixing_exception_keywords_and_macros)

- [在 catch 區塊內嘗試區塊](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>混合例外狀況關鍵字和宏

您可以在同一個程式中混合使用 MFC 例外狀況宏和 c + + 例外狀況關鍵字。 但是，您無法在相同的區塊中混合使用 c + + 例外狀況關鍵字的 MFC 宏，因為宏會在超出範圍時自動刪除例外狀況物件，而使用例外狀況處理關鍵字的程式碼則不會。 如需詳細資訊，請參閱[例外狀況：攔截及刪除例外](exceptions-catching-and-deleting-exceptions.md)狀況。

宏與關鍵字的主要差異在於，當例外狀況超出範圍時，宏會「自動」刪除攔截到的例外狀況。 使用關鍵字的程式碼不是;必須明確刪除 catch 區塊中攔截到的例外狀況。 混合宏和 c + + 例外狀況關鍵字可能會在未刪除例外狀況物件時造成記憶體流失，或在例外狀況刪除兩次時發生堆積損毀。

例如，下列程式碼會讓例外狀況指標失效：

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

發生此問題的原因 `e` 是，當執行超出「內部」 **CATCH**區塊時，就會刪除。 使用**THROW_LAST**宏而非**THROW**語句，會導致 "outer" **CATCH**區塊接收有效的指標：

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>在 Catch 區塊內嘗試區塊

您無法從 **`try`** **CATCH**區塊內的區塊中重新擲回目前的例外狀況。 下列範例無效：

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

如需詳細資訊，請參閱[例外狀況：檢查例外狀況內容](exceptions-examining-exception-contents.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
