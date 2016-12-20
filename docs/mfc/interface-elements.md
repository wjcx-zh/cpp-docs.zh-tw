---
title: "介面項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "架構 [C++], MFC 功能套件"
  - "MFC 功能套件, 架構"
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
caps.latest.revision: 28
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 介面項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件說明在 [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] SP1 引入的介面項目，以及描述與舊版程式庫的差異。  
  
 下圖顯示使用新的介面項目，以建立的應用程式。  
  
 ![MFC 功能套件範例應用程式](../mfc/media/mfc_featurepack.png "MFC\_FeaturePack")  
  
## 視窗停駐  
 視窗停駐功能類似 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 圖形使用者介面使用的視窗停駐。  
  
## 控制列現在是窗格  
 控制列現在稱為窗格和衍生自 [CBasePane Class](../mfc/reference/cbasepane-class.md)。  在 MFC 舊版，控制項的基底類別是 `CControlBar`。  
  
 應用程式主框架視窗 \(由 [CFrameWndEx Class](../mfc/reference/cframewndex-class.md) 或 [CMDIFrameWndEx 類別](../mfc/reference/cmdiframewndex-class.md)通常表示。  主框架呼叫 *停駐位置*。  窗格可能已有三種類型之一:停駐網站、停駐列或小型框架視窗。  
  
 取得窗格的兩種型別:不可調整大小和可調整大小。  使用分隔器或滑桿，可調整大小的窗格，例如狀態列和工具列，可以調整大小。  可調整大小的窗格會形成容器 \(一個窗格可以停駐在其他窗格，在它們之間的分隔器\)。  不過，可調整大小的窗格無法附加 \(固定\) 內建列。  
  
 如果您的應用程式使用不可調整大小的窗格中，從 [CPane Class](../mfc/reference/cpane-class.md)衍生它們。如果您的應用程式使用可調整大小的窗格中，從 [CDockablePane Class](../mfc/reference/cdockablepane-class.md)衍生它們。  
  
## 固定網站  
 停駐位置 \(或主框架視窗\) 擁有所有窗格和小型框架視窗在應用程式。  停駐網站包含一個 [CDockingManager](../mfc/reference/cdockingmanager-class.md) 成員。  這個成員維護屬於停駐窗格所有網站的清單。  清單指令，以便建立窗格停駐在網站的外框在清單的開頭位置。  當架構重繪停駐網站時，會執行迴圈在這份清單並調整每個窗格配置包括停駐在網站的目前周框矩形。  您可以呼叫 `AdjustDockingLayout` 或 `RecalcLayout` ，在必須調整停駐配置時，因此，架構會將此呼叫重新導向至停駐管理員。  
  
## 停駐列  
 每個主框架視窗可以沿著邊界的停駐 *列* 。  停駐列是屬於 [CDockSite Class](../mfc/reference/cdocksite-class.md)的窗格。  停駐列可以接受衍生自 [CPane](../mfc/reference/cpane-class.md)的物件，例如工具列。  若要建立停駐列，當主框架視窗初始化時，請呼叫 `EnableDocking`。  若要啟用自動隱藏列，請呼叫 `EnableAutoHideBars`。  `EnableAutoHideBars` 建立 [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) 物件，並在每個停駐列旁邊放置。  
  
 每個停駐列分成停駐行為。  停駐行以 [CDockingPanesRow Class](../mfc/reference/cdockingpanesrow-class.md)表示。  每個資料行包含停駐工具列清單。  如果使用者停駐工具列或從一行移動工具列到另一個在同一個停駐列內，架構來建立新的資料列並據以調整停駐列，或是在現有資料列將工具列。  
  
## 小型框架視窗  
 浮動窗格位於小型框架視窗。  小型框架視窗由兩個類別代表:只能包含一個窗格\) 可以包含數個窗格\) 的 [CMDITabInfo Class](../mfc/reference/cmditabinfo-class.md) 和 [CMultiPaneFrameWnd Class](../mfc/reference/cmultipaneframewnd-class.md) 。  若要在一個窗格在程式碼中，呼叫 [CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md)。  在窗格之後浮動，架構會自動建立小型框架視窗，而且小型框架視窗變成浮動窗格的父。  當浮動窗格停駐時，架構會重設其父代，，而且浮動窗格變成停駐列 \(為工具列停駐\) 或網站 \(為可調整大小的窗格\)。  
  
## 窗格分割線  
 窗格分割線 \(也稱為滑桿或分隔器\) 以 [CPaneDivider Class](../mfc/reference/cpanedivider-class.md)表示。  當使用者停駐窗格時，這個架構窗格分割線，不論窗格是否停駐在停駐網站或另一個窗格。  當窗格停駐在停駐網站時，窗格分割線呼叫 *預設窗格分割線*。  預設窗格分割線對所有停駐窗格設定負責在停駐位置。  停駐管理員會維護預設窗格分割線清單和窗格清單。  停駐管理員負責所有停駐窗格配置。  
  
## 容器  
 任何可調整大小的窗格，，當互相停駐，在容器中維護。  容器以 [CPaneContainer Class](../mfc/reference/cpanecontainer-class.md)表示。  每個容器有指標到其左窗格、右窗格、左子容器、正確的子容器和分隔器左右在組件之間。\(*左右* 未參考的實體，而識別樹狀結構的分支\)。在我們可以建置窗格和分隔器樹狀結構也可以達到一起調整窗格的複雜配置。  `CPaneContainer` 類別維護容器樹狀結構;在這個樹狀結構的同時維護窗格兩份清單和滑桿。  窗格容器管理員通常會內嵌到傳送多窗格的預設滑桿和小型框架視窗。  
  
## 自動隱藏控制項。  
 根據預設，每個 `CDockablePane` 支援自動隱藏功能。  當使用者在 `CDockablePane`的標頭時按一下連接按鈕，架構會切換窗格自動隱藏模式。  想要處理按一下，架構建立 [CMFCAutoHideBar Class](../mfc/reference/cmfcautohidebar-class.md) 和 [CMFCAutoHideButton Class](../mfc/reference/cmfcautohidebutton-class.md) 相關聯的 `CMFCAutoHideBar` 物件。  架構在 [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)將新的 `CMFCAutoHideBar` 。  此架構也將 `CMFCAutoHideButton` 附加至工具列。  [CDockingManager Class](../mfc/reference/cdockingmanager-class.md) 維護 `CDockablePane`。  
  
## 索引標籤式控制列和 Outlook 功能區  
 [CMFCBaseTabCtrl Class](../mfc/reference/cmfcbasetabctrl-class.md) 實作成索引標籤式視窗的基本功能。可拆的選項。  若要使用 `CMFCBaseTabCtrl` 物件，請使用應用程式的 [CBaseTabbedPane 類別](../mfc/reference/cbasetabbedpane-class.md) 。  `CBaseTabbedPane` 衍生自 `CDockablePane` 並維護指標到 `CMFCBaseTabCtrl` 物件。  `CBaseTabbedPane` 可讓使用者修正和調整定位的控制列。  使用 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) 動態建立固定和定位的控制列。  
  
 Outlook 功能區控制項依據定位的列也。  [CMFCOutlookBar 類別](../mfc/reference/cmfcoutlookbar-class.md) 衍生自 `CBaseTabbedPane`。  如需如何使用 Outlook 功能區的詳細資訊，請參閱 [CMFCOutlookBar 類別](../mfc/reference/cmfcoutlookbar-class.md)。  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)