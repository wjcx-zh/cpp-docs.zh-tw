---
title: 例外狀況： 攔截及刪除例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad6ad1c4d1d7d74f60acbd985ee549d708ae28f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074120"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>例外狀況：攔截及刪除例外狀況

下列指示和範例示範如何攔截和刪除例外狀況。 如需詳細資訊**嘗試**，**攔截**，並**擲回**關鍵字，請參閱[c + + 例外狀況處理](../cpp/cpp-exception-handling.md)。

您的例外狀況處理常式必須刪除其所處理的例外狀況物件，因為每當程式碼攔截例外狀況時，若無法刪除例外狀況就會導致記憶體流失。

您**攔截**區塊必須刪除例外狀況時：

- **攔截**區塊擲回新的例外狀況。

   當然，如果您再次擲回相同的例外狀況，則不得刪除例外狀況：

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 執行會返回內在**攔截**區塊。

> [!NOTE]
>  刪除時`CException`，使用`Delete`成員函式來刪除例外狀況。 請勿使用**刪除**關鍵字，因為它可能會失敗，如果例外狀況不是在堆積上。

#### <a name="to-catch-and-delete-exceptions"></a>攔截和刪除例外狀況

1. 使用**嘗試**關鍵字來設定**嘗試**區塊。 執行任何可能會擲回例外狀況中的程式陳述式**嘗試**區塊。

   使用**攔截**關鍵字來設定**攔截**區塊。 將例外狀況處理程式碼中的放置**攔截**區塊。 中的程式碼**攔截**才會執行的區塊內的程式碼**嘗試**區塊擲回例外狀況中指定之型別的**攔截**陳述式。

   下列的基本架構示範如何**嘗試**並**攔截**區塊的正常安排：

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   擲回例外狀況時，控制權會傳遞給第一個**攔截**的例外狀況宣告符合例外狀況類型的區塊。 您可以選擇性地處理不同類型的例外狀況和循序**攔截**封鎖，如下所示：

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

如需詳細資訊，請參閱 <<c0> [ 例外狀況： 從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)

