---
title: "框架視窗執行什麼功能 | Microsoft Docs"
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
  - "框架視窗, 關於框架視窗"
  - "框架視窗, 工作"
  - "MFC, 框架視窗"
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架視窗執行什麼功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了框架檢視以外，框架視窗停駐在協調架構所涉及的許多工作負責與其檢視及應用程式。  [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 和 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 繼承自 [CFrameWnd](../mfc/reference/cframewnd-class.md)，因此，它們有它們加入的 `CFrameWnd` 功能和新功能。  子視窗的範例包括檢視控制項，例如按鈕和清單方塊和控制列，包括工具列、狀態列和對話方塊列。  
  
 框架視窗要負責管理自己的子視窗配置。  在 MFC 架構，框架視窗放置所有控制列、檢視和其他子視窗在其工作區內。  
  
 框架視窗也傳送命令給其檢視，並回應來自控制項視窗的通知訊息。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [控制列 \(它們如何配合至框架視窗\)](../mfc/control-bars.md)  
  
-   [處理功能表、控制列和快速鍵 \(它們如何配合至框架視窗\)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [命令路由 \(從框架視窗至它的檢視和其他命令目標\)。](../mfc/command-routing.md)  
  
-   [文件\/檢視架構](../mfc/document-view-architecture.md)  
  
-   [控制列](../mfc/control-bars.md)  
  
-   [控制項](../mfc/controls-mfc.md)  
  
## 請參閱  
 [框架視窗](../mfc/frame-windows.md)