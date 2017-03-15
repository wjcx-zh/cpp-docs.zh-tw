---
title: "控制列 | Microsoft Docs"
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
  - "CControlBar 類別, MFC 控制列"
  - "CDialogBar 類別, 控制列"
  - "命令列, 類型"
  - "控制列 [C++]"
  - "控制列 [C++], 類型"
  - "CStatusBar 類別, 控制列"
  - "CToolBar 類別, 控制列"
  - "對話方塊列, 控制列"
  - "MFC, 控制列"
  - "狀態列, 控制列"
  - "工具列 [C++], 控制列"
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 控制列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「控制列」是一般名稱工具列、狀態列和對話方塊列。  MFC 類別 `CToolBar`， `CStatusBar`， `CDialogBar`， `COleResizeBar`，因此 **CReBar** 從類別衍生自 [CControlBar](../mfc/reference/ccontrolbar-class.md)，實作它們通用功能。  
  
 控制列是顯示控制項的使用者可以選取選項執行命令，或者取得程式資訊的視窗。  控制列的類型包括工具列、對話方塊列和狀態列。  
  
-   工具列在 [CToolBar](../mfc/reference/ctoolbar-class.md)類別  
  
-   狀態列，在 [CStatusBar](../mfc/reference/cstatusbar-class.md)類別  
  
-   對話方塊，在 [CDialogBar](../mfc/reference/cdialogbar-class.md)類別  
  
-   Rebars，在 [CReBar](../mfc/reference/crebar-class.md)類別  
  
> [!IMPORTANT]
>  根據 MFC 4.0 版，工具列、狀態列和工具提示中實作會使用這個 comctl32.dll 實作的系統功能而不是目前實作特定對 MFC。  在 MFC 6.0 版， **CReBar**，也加入包裝 comctl32.dll 功能。  
  
 控制列型別簡介之後。  如需詳細資訊，請參閱下列連結。  
  
## 控制列  
 控制項會藉由提供快，進一步命令動作大幅提高程式的可用性。  `CControlBar` 類別提供所有工具列、狀態列和對話方塊列的通用功能。  `CControlBar` 為放置在其父框架視窗的控制列的功能。  由於一列控制項通常是父框架視窗的子視窗，則是「同層級」用戶端檢視或框架視窗的 MDI 用戶端。  控制列物件利用父視窗工作區矩形的資訊將自己當地語系化。  然後修改父的其他用戶端視窗矩形，讓用戶端檢視或 MDI 用戶端視窗填滿用戶端視窗的其餘部分。  
  
> [!NOTE]
>  如果在控制項中的按鈕沒有 **COMMAND** 和 **UPDATE\_COMMAND\_UI** 處理常式，架構會自動停用按鈕。  
  
## 工具列  
 工具列會顯示點陣圖按鈕執行命令的控制列。  按下工具列按鈕相當於選擇功能表項目相等;，如果該功能表項目 ID 和工具列按鈕相同，它會呼叫相同的處理常式對應至功能表項目。  您可以設定按鈕顯示和運作為按鈕、選項按鈕、核取方塊。  工具列在框架視窗頂端通常對齊，不過， MFC 工具列可以「固定」給它的父視窗或浮動的所有框在它的小型框架視窗。  工具列可能會「浮動」，而且您可以變更其大小和拖曳它的上方。  當使用者在工具列上的按鈕，工具列也會顯示工具提示。  工具提示是簡短描述按鈕的用途微小的快顯視窗。  
  
> [!NOTE]
>  根據 MFC 4.0 版，類別 [CToolBar](../mfc/reference/ctoolbar-class.md) 使用視窗工具列通用控制項。  `CToolBar` 包含 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)。  但是舊版的工具列，仍然支援。  請參閱本文件的 [工具列](../mfc/mfc-toolbar-implementation.md)。  
  
## 狀態列  
 狀態列會包含文字輸出窗格或「指示器的控制列」。輸出窗格通常做為訊息列和目前狀態表示。  訊息的範例包括簡短說明選取的功能表或工具列命令在 MFC 應用程式精靈建立的預設狀態列最左邊窗格的命令說明訊息行。  狀態的範例包括 SCROLL LOCK、NUM LOCK 和其他索引鍵。  狀態列通常會對齊框架視窗底端。  請參閱 [CStatusBar](../mfc/reference/cstatusbar-class.md) 類別和類別 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)。  
  
## 對話方塊列  
 關於對話方塊列是一列控制項，以對話方塊範本資源，以非強制回應對話方塊的功能。  對話方塊列可包含 Windows、自訂或 ActiveX 控制項。  在對話方塊，使用者可以在控制項中選取中。  對話方塊列可位於頂端，底端對齊，或是框架視窗右邊與它們在自己的框架視窗也會浮動。  請參閱 [CDialogBar](../mfc/reference/cdialogbar-class.md)類別。  
  
## Rebars  
 [rebar](../mfc/using-crebarctrl.md) 是提供 Rebar 控制的停靠、配置狀態和持續性資訊的控制列。  Rebar 物件可以包含各種子視窗，通常是其他控制項，包括編輯方塊、工具列和清單方塊。  Rebar 物件可以顯示在指定之點陣圖的子視窗。  它可以透過按一下或拖曳的移駐夾列自動或手動調整大小。  請參閱 [CReBar](../mfc/reference/crebar-class.md)類別。  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)