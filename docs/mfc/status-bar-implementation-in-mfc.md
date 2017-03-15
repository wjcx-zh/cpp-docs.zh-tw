---
title: "MFC 中的狀態列實作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COldStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COldStatusBar 類別"
  - "CStatusBar 類別, 和 CStatusBarCtrl 類別"
  - "CStatusBar 類別, 和 MFC 狀態列"
  - "CStatusBarCtrl 類別, 和 CStatusBar 類別"
  - "CStatusBarCtrl 類別, 和 MFC 狀態列"
  - "狀態列, 和 CStatusBarCtrl 類別"
  - "狀態列, 回溯相容性"
  - "狀態列, 在 MFC 中實作"
  - "狀態列, COldStatusBar 類別中舊的"
  - "狀態列, Windows 95 實作"
  - "狀態指標"
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 中的狀態列實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CStatusBar](../mfc/reference/cstatusbar-class.md) 物件與文字輸出窗格中資料列的控制列。  輸出窗格通常做為訊息列和目前狀態表示。  範例包括簡短說明選取的功能表命令和指示器顯示 SCROLL LOCK、NUM LOCK 和其他按鍵狀態的功能表說明訊息行。  
  
 使用 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)類別，根據 MFC 4.0 版，狀態列會實作，封裝狀態列通用控制項。  如需回溯相容性，在 MFC 類別 **COldStatusBar**保留舊的狀態列實作。  MFC 舊版本的文件描述 **COldStatusBar**`CStatusBar`下。  
  
 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)成員函式，新的 MFC 4.0 中，可讓您利用 Windows 通用控制項支援狀態列自訂和其他功能。  `CStatusBar` 成員函式最給您 Windows 通用控制項的功能;不過，也就是說，當您呼叫 `GetStatusBarCtrl`時，您可以將狀態列狀態列的特性。  當您呼叫 `GetStatusBarCtrl`，則會傳回 `CStatusBarCtrl` 物件的參考。  您可以使用參考操作狀態列控制項。  
  
 下圖顯示數個指示器的狀態列。  
  
 ![狀態列](../mfc/media/vc37dy1.png "vc37DY1")  
一個狀態列  
  
 例如，工具列，在框架視窗時，狀態列物件在其父框架視窗內嵌和自動建構。  終結時，，，如同控制列，自動終結狀態列父框架。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [更新狀態列窗格文字](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   MFC 類別 [CStatusBar](../mfc/reference/cstatusbar-class.md) 和 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [控制列](../mfc/control-bars.md)  
  
-   [對話方塊列](../mfc/dialog-bars.md)  
  
-   [工具列 \(MFC 工具列實作\)](../mfc/mfc-toolbar-implementation.md)  
  
## 請參閱  
 [狀態列](../mfc/status-bars.md)