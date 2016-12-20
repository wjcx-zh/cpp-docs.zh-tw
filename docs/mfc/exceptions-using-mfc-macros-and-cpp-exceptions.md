---
title: "例外狀況：使用 MFC 巨集和 C++ 例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "catch 區塊, 明確刪除其中的程式碼"
  - "catch 區塊, 混合"
  - "例外狀況處理, MFC"
  - "例外狀況處理, 混合語言"
  - "例外狀況物件"
  - "例外狀況物件, 刪除"
  - "例外狀況, MFC 巨集和 C++ 關鍵字比較"
  - "堆積損毀"
  - "記憶體遺漏, 未刪除的例外狀況物件"
  - "巢狀 catch 區塊"
  - "巢狀 try 區塊"
  - "try-catch 例外狀況處理, 混合 MFC 巨集和 C++ 關鍵字"
  - "try-catch 例外狀況處理, 巢狀 try 區塊"
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況：使用 MFC 巨集和 C++ 例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論的撰寫使用 MFC 例外狀況處理巨集和 C\+\+ 例外狀況處理關鍵字的程式碼的考量。  
  
 本文包括下列主題:  
  
-   [混合例外狀況關鍵字和巨集](#_core_mixing_exception_keywords_and_macros)  
  
-   [在 catch 區塊內 try 區塊](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> 混合例外狀況關鍵字和巨集  
 您可以混合 MFC 例外狀況在相同的巨集和 C\+\+ 例外狀況關鍵字程式。  但是，您無法使用 C\+\+ 在相同區塊中的例外狀況關鍵字混合 MFC 巨集，因為巨集會自動刪除例外狀況物件，以便在超出範圍時，反之，使用例外狀況處理關鍵字的程式碼沒有。  如需詳細資訊，請參閱文件 [例外狀況:攔截和刪除例外狀況。](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 巨集和關鍵字之間的主要差異在於巨集「自動刪除已攔截的例外狀況，當例外狀況超出範圍時。  使用關鍵字的程式碼不;必須明確地刪除在 catch 區塊攔截的例外狀況。  混合巨集和 C\+\+ 例外狀況關鍵字可能會導致記憶體遺漏例外狀況時，物件不會被刪除時，或者堆積損毀，當例外狀況兩次時刪除。  
  
 下列程式碼，例如，沒有例外狀況指標:  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 問題的發生，因為 `e` 會刪除，當執行傳入「內部」 **CATCH** 區塊。  使用而非 **THROW** 陳述式的 `THROW_LAST` 巨集會造成「extern」 **CATCH** 區塊接收有效的指標:  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> 在 catch 區塊內 try 區塊  
 您不能重新擲回目前的例外狀況是在 catch 區塊內 **try** 區塊內。  下列範例無效:  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 如需詳細資訊，請參閱 [例外狀況:要檢查的例外狀況內容](../mfc/exceptions-examining-exception-contents.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)