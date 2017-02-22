---
title: "例外狀況：攔截及刪除例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AND_CATCH 巨集"
  - "catch 區塊, 攔截及刪除例外狀況"
  - "例外狀況處理, 攔截及刪除例外狀況"
  - "例外狀況, 刪除"
  - "執行, 從 catch 區塊內傳回"
  - "try-catch 例外狀況處理, 攔截及刪除例外狀況"
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 例外狀況：攔截及刪除例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列指示和範例會示範如何攔截和刪除例外狀況。  如需 **try**， **catch**和 `throw` 關鍵字，請參閱 [C\+\+ 例外狀況處理。](../cpp/cpp-exception-handling.md)。  
  
 每當程式碼攔截例外狀況時，被處理的例外狀況處理常式必須刪除例外狀況物件，因為無法刪除例外狀況就會造成記憶體遺漏 \(Memory Leak\)。  
  
 您的 **catch** 區塊必須刪除例外狀況，當:  
  
-   **catch** 區塊擲回新的例外狀況。  
  
     當然，如果您再擲回相同的例外狀況，您不能刪除例外狀況:  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   會從**catch**區塊內傳回。  
  
> [!NOTE]
>  當刪除 `CException`時，請使用 **Delete** 成員函式刪除例外狀況。  不要使用 **delete** 關鍵字，因為如果例外狀況不在堆積的話，它會失敗。  
  
#### 攔截和刪除例外狀況。  
  
1.  使用 **try** 關鍵字設定 **try** 區塊。  執行可能會擲回在 **try** 區塊中例外狀況的任何程式陳述式。  
  
     使用 **catch** 關鍵字設定 **catch**區塊。  位在 **catch** 區塊的例外處理程式碼。  只有在 **try** 區塊中的程式碼擲回在 **catch**陳述式，指定之型別的例外狀況**catch** 區塊中的程式碼執行。  
  
     下列基本架構顯示如何定期安排 **try** 和 **catch** 區塊:  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     當例外狀況擲回時，將控制項傳遞給例外狀況宣告符合的例外狀況型別的第一個 **catch**區塊。  您可以選擇性地處理例外狀況的不同類型與執行中 **catch** 區塊的如如下所列:  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 如需詳細資訊，請參閱 [例外狀況:轉換從 MFC 例外狀況巨集](../mfc/exceptions-converting-from-mfc-exception-macros.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)