---
title: "例外狀況： 攔截及刪除例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8496b5228fe4002bb1ca80f8fbe793fd5e16ca81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>例外狀況：攔截及刪除例外狀況
下列指示和範例示範如何攔截和刪除例外狀況。 如需有關**再試一次**，**攔截**，和`throw`關鍵字，請參閱[c + + 例外狀況處理](../cpp/cpp-exception-handling.md)。  
  
 您的例外狀況處理常式必須刪除其所處理的例外狀況物件，因為每當程式碼攔截例外狀況時，若無法刪除例外狀況就會導致記憶體流失。  
  
 您**攔截**區塊必須刪除例外狀況時：  
  
-   **攔截**區塊擲回新的例外狀況。  
  
     當然，如果您再次擲回相同的例外狀況，則不得刪除例外狀況：  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   執行會傳回從**攔截**區塊。  
  
> [!NOTE]
>  刪除時`CException`，使用**刪除**成員函式來刪除例外狀況。 請勿使用**刪除**關鍵字，因為它可能會失敗，如果例外狀況不是在堆積上。  
  
#### <a name="to-catch-and-delete-exceptions"></a>攔截和刪除例外狀況  
  
1.  使用**再試一次**關鍵字設定**再試一次**區塊。 執行任何可能會擲回例外狀況中的程式陳述式**再試一次**區塊。  
  
     使用**攔截**關鍵字設定**攔截**區塊。 將例外狀況處理程式碼中的放置**攔截**區塊。 中的程式碼**攔截**才會執行的區塊內的程式碼**再試一次**區塊擲回例外狀況中所指定型別的**攔截**陳述式。  
  
     下列基本架構顯示如何**再試一次**和**攔截**區塊的正常安排：  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     擲回例外狀況時，控制權會傳遞給第一個**攔截**其例外狀況宣告符合例外狀況類型的區塊。 您可以選擇性地處理不同類型的例外狀況的循序**攔截**封鎖如下所示：  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 如需詳細資訊，請參閱[例外狀況： 從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)

