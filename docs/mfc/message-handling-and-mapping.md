---
title: "訊息處理和對應 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "訊息處理"
  - "訊息對應"
  - "MFC, 訊息"
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息處理和對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此文章系列描述 MFC 架構如何處理訊息和命令以及如何連接至其處理函式。  
  
 在 Windows 中的傳統的程式， Windows 訊息由視窗程序的大型 switch 陳述式來處理。  MFC 使用 [訊息對應](../mfc/message-categories.md) 直接對應訊息至不同類別成員函式。  訊息對應在這個目的較虛擬函式更有效率，而且允許訊息由最適當的 C\+\+ 物件—應用程式、文件、檢視等等處理。  您可以對應單一訊息或訊息的範圍、命令 ID 或控制項 ID。  
  
 **WM\_COMMAND** 訊息—通常由功能表、工具列按鈕或快速鍵產生──也使用訊息對應機制。  MFC 定義命令訊息標準的 [路由](../mfc/command-routing.md) 在在您的程式的應用程式、框架視窗、檢視和現用文件中。  如果需要，您可以覆寫這個路由。  
  
 訊息對應也提供了更新使用者介面物件 \(例如功能表和工具列按鈕\)，啟用或停用它們成為目前內容。  
  
 如需 Windows 訊息和訊息佇列的一般資訊，請參閱 [訊息和訊息佇列](http://msdn.microsoft.com/library/windows/desktop/ms632590) 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [架構如何呼叫訊息處理常式](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)  
  
-   [將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [如何在狀態列中顯示命令資訊](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [使用者介面物件的動態更新](../mfc/how-to-update-user-interface-objects.md)  
  
-   [如何：建立樣板類別的訊息對應](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [CWnd 類別](../mfc/reference/cwnd-class.md)   
 [CCmdTarget Class](../mfc/reference/ccmdtarget-class.md)