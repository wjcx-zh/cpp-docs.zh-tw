---
title: 例外狀況：攔截及刪除例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 0142ffddfb391ae8da878d9e5fe34629cf16cb52
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246697"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>例外狀況：攔截及刪除例外狀況

下列指示和範例示範如何攔截和刪除例外狀況。 如需**try**、 **catch**和**throw**關鍵字的詳細資訊，請參閱[例外C++狀況和錯誤處理的現代化最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)。

您的例外狀況處理常式必須刪除其所處理的例外狀況物件，因為每當程式碼攔截例外狀況時，若無法刪除例外狀況就會導致記憶體流失。

當下列情況發生時，您的**catch**區塊必須刪除例外狀況：

- **Catch**區塊會擲回新的例外狀況。

   當然，如果您再次擲回相同的例外狀況，則不得刪除例外狀況：

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 執行會從**catch**區塊內傳回。

> [!NOTE]
>  刪除 `CException`時，請使用 `Delete` 成員函式來刪除例外狀況。 請勿使用**delete**關鍵字，因為如果例外狀況不在堆積上，它可能會失敗。

#### <a name="to-catch-and-delete-exceptions"></a>攔截和刪除例外狀況

1. 使用**try**關鍵字來設定**try**區塊。 執行可能會在**try**區塊內擲回例外狀況的任何程式語句。

   使用**catch**關鍵字來設定**catch**區塊。 將例外狀況處理常式代碼放在**catch**區塊中。 只有當**try**區塊內的程式碼擲回**catch**語句中所指定類型的例外狀況時，才會執行**catch**區塊中的程式碼。

   下列基本架構會顯示**try**和**catch**區塊的一般相片順序：

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   當擲回例外狀況時，控制權會傳遞給第一個**catch**區塊，其例外狀況宣告會符合例外狀況的類型。 您可以選擇性地使用連續**catch**區塊來處理不同類型的例外狀況，如下所示：

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

如需詳細資訊，請參閱[例外狀況：從 MFC 例外狀況宏轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
