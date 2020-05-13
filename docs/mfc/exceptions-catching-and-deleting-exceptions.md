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
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365521"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>例外狀況：攔截及刪除例外狀況

下列指示和範例示範如何攔截和刪除例外狀況。 有關**嘗試**、**捕捉**與**引發**關鍵字的詳細資訊,請參閱[現代C++異常和錯誤處理的最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)。

您的例外狀況處理常式必須刪除其所處理的例外狀況物件，因為每當程式碼攔截例外狀況時，若無法刪除例外狀況就會導致記憶體流失。

擷取**區塊**必須在以下情況刪除異常:

- **catch**塊將引發新的異常。

   當然，如果您再次擲回相同的例外狀況，則不得刪除例外狀況：

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 執行從**catch**塊內返回。

> [!NOTE]
> 刪除`CException`時`Delete`,使用成員函數刪除異常。 不要使用**delete**關鍵字,因為如果異常不在堆中,則該關鍵字可能會失敗。

#### <a name="to-catch-and-delete-exceptions"></a>攔截和刪除例外狀況

1. 使用**try**關鍵字設定**try**塊。 執行任何可能在**try**塊中引發異常的程式語句。

   使用**catch**關鍵字設置**catch**塊。 將異常處理代碼放在**catch**塊中。 僅當**try**塊中的代碼引發**catch**語句中指定的類型的異常時,才會執行**catch**塊中的代碼。

   以下骨架顯示了**嘗試**與**捕捉**區塊通常如何排列:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   引發異常時,控件將傳遞到其異常聲明與異常類型匹配的第一**個 catch**塊。 您可以有選擇地處理不同類型的異常,順序**CATCH**塊如下所示:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

有關詳細資訊,請參閱[異常:從 MFC 異常巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
