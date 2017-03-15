---
title: "應用程式精靈所建立的框架視窗類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CMainFrame"
  - "CMainFrame::PreCreateWindow"
  - "CMainFrame.PreCreateWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式精靈 [C++], 由其所建立的框架視窗類別"
  - "CFrameWnd 類別, 框架視窗"
  - "類別 [C++], 框架視窗"
  - "CMainFrame 類別"
  - "CMDIChildWnd 類別, 框架視窗"
  - "CMDIFrameWnd 類別, 框架視窗"
  - "框架視窗類別, 由應用程式精靈建立的"
  - "視窗類別"
  - "視窗類別, 框架"
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式精靈所建立的框架視窗類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了應用程式、文件和檢視類別之外，當您使用 [應用程式精靈](../ide/creating-desktop-projects-by-using-application-wizards.md) 建立基本架構應用程式，，應用程式精靈建立應用程式的主框架視窗的衍生框架視窗類別。  預設類別呼叫，則為 `CMainFrame` ，並包含其檔案名稱為 MAINFRM.H 和 MAINFRM.CPP。  
  
 如果您的應用程式是 SDI，您的 `CMainFrame` 類別是從類別衍生自 [CFrameWnd](../mfc/reference/cframewnd-class.md)。  
  
 如果您的應用程式是 MDI，從 `CMainFrame` 類別衍生自 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)。  在此情況下 `CMainFrame` 實作主要畫面格，保留功能表、工具列和狀態列。  應用程式精靈不會取得您的新文件框架視窗類別。  相反地，它在 [CMDIChildWnd 類別](../mfc/reference/cmdichildwnd-class.md)使用預設實作。  MFC 架構建立子視窗包含可以屬於型別 `CScrollView`， `CEditView`， `CTreeView`， `CListView`的每一個檢視 \(等等\)，應用程式要求。  如果您需要自訂您的文件框架視窗，您可以建立新的文件框架視窗類別 \(請參閱 [加入類別](../ide/adding-a-class-visual-cpp.md)\)。  
  
 如果您選擇支援工具列，類別也會初始化型別 [CToolBar](../mfc/reference/ctoolbar-class.md) 和 [CStatusBar](../mfc/reference/cstatusbar-class.md) 成員的變數和 `OnCreate` 訊息處理函式兩個 [控制列](../mfc/control-bars.md)。  
  
 這些框架視窗類別運作所建立，不過，提高其功能，您必須加入成員變數和成員函式。  您也可以將視窗類別處理其他 Windows 訊息。  如需詳細資訊，請參閱 [變更 MFC 建立之視窗的樣式。](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。  
  
## 請參閱  
 [框架視窗類別](../mfc/frame-window-classes.md)   
 [MFC 程式或控制項原始程式檔和標頭檔](../ide/mfc-program-or-control-source-and-header-files.md)