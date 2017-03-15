---
title: "控制列類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制列, 類別"
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 控制列類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制列附加到框架視窗。  它們包含按鈕、狀態窗格或是對話方塊範本。  自由浮動控制列，也稱為工具調色盤，您可以加入這些 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) 物件來實作。  
  
## Framework 控制列  
 這些控制項都是 MFC 架構的整數部分。  因為它們整合架構，所以它們比 Windows 控制列比較容易使用，且更強大。  大部分的 MFC 應用程式使用這些控制項列而不是使用 Window 控制列。  
  
 [CControlBar](../mfc/reference/ccontrolbar-class.md)  
 MFC 控制列的基底類別在此節中列出。  控制項列是視窗對齊至框架視窗的框線。  控制列包含 `HWND`\-根據 `HWND`未以子控制項或控制項為基礎，例如工具列按鈕。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 根據對話方塊樣板的控制列。  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 可以支援包含額外的子視窗以表單形式的工具列  
  
 [CToolbar](../mfc/reference/ctoolbar-class.md)  
 包含以 `HWND`沒有點陣圖命令按鈕的工具列控制項視窗。  大部分的 MFC 應用程式使用這個類別而不是 `CToolBarCtrl`。  
  
 [CStatusBar](../mfc/reference/cstatusbar-class.md)  
 狀態列控制項視窗的基底類別。  大部分的 MFC 應用程式使用這個類別而不是 `CStatusBarCtrl`。  
  
## Windows 控制項列  
 這些控制項則是對應的 Windows 控制項的細窄的包裝函式。  由於沒有整合架構，所以它們比先前所列的控制列難以使用。  大部分的 MFC 應用程式使用先前所列的控制列。  
  
 [CRebarCtrl](../mfc/reference/crebarctrl-class.md)  
 實作 `CRebar` 物件的內部控制項。  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 水平視窗，通常分為窗格，應用程式可能顯示狀態資訊。  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具列通用控制項的功能。  
  
## 相關類別  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 顯示說明工具的目的單行文字在應用程式的小型快顯視窗。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 處理控制列的停駐狀態資料之永續儲存。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)