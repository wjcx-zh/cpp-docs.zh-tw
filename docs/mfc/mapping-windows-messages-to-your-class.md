---
title: "將 Windows 訊息對應到您的類別 | Microsoft Docs"
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
  - "對應, 訊息到對話方塊類別"
  - "訊息對應 [C++], 在對話方塊類別中"
  - "訊息對應 [C++], 將 Windows 訊息對應到類別"
  - "訊息到對話方塊類別"
  - "訊息到對話方塊類別, 對應"
  - "MFC 對話方塊, Windows 訊息"
  - "Windows 訊息 [C++], 對話方塊類別中的對應"
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 Windows 訊息對應到您的類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您需要自己的對話方塊處理 Windows 訊息，請覆寫適當的處理函式。  若要這麼做，請使用屬性視窗以 [對應訊息](../mfc/reference/mapping-messages-to-functions.md) 至對話方塊類別。  對於每個訊息寫入訊息對應項目並將訊息處理常式成員函式加入至類別。  使用 Visual C\+\+ 原始程式碼編輯器在訊息處理常式撰寫程式碼。  
  
 您也可以覆寫 [CDialog](../mfc/reference/cdialog-class.md) 的成員函式和它的基底類別，特別是 [CWnd](../mfc/reference/cwnd-class.md)。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
-   [常被覆寫的成員函式](../mfc/commonly-overridden-member-functions.md)  
  
-   [常加入的成員函式](../mfc/commonly-added-member-functions.md)  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)