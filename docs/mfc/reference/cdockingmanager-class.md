---
title: "CDockingManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockingManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockingManager class"
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: 37
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockingManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作該核心功能內建在框架視窗 \(Main Frame Window\) 的控制項配置。  
  
## 語法  
  
```  
class CDockingManager : public CObject  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDockingManager::AddDockSite](../Topic/CDockingManager::AddDockSite.md)|建立停駐窗格並將它加入至控制項的資料行清單。|  
|[CDockingManager::AddHiddenMDITabbedBar](../Topic/CDockingManager::AddHiddenMDITabbedBar.md)|將控制代碼列窗格加入至隱藏 MDI 索引標籤的分隔列窗格清單。|  
|[CDockingManager::AddMiniFrame](../Topic/CDockingManager::AddMiniFrame.md)|將框架加入至微架構清單。|  
|[CDockingManager::AddPane](../Topic/CDockingManager::AddPane.md)|註冊處理常式停駐的窗格。|  
|[CDockingManager::AdjustDockingLayout](../Topic/CDockingManager::AdjustDockingLayout.md)|重新計算並調整所有窗格配置在框架視窗中。|  
|[CDockingManager::AdjustPaneFrames](../Topic/CDockingManager::AdjustPaneFrames.md)|導致 `WM_NCCALCSIZE` 訊息傳送給所有窗格和 `CPaneFrameWnd` 視窗。|  
|[CDockingManager::AdjustRectToClientArea](../Topic/CDockingManager::AdjustRectToClientArea.md)|調整矩形的對齊方式。|  
|[CDockingManager::AlignAutoHidePane](../Topic/CDockingManager::AlignAutoHidePane.md)|在 autohide 模式重新調整停駐窗格，以便採用固定網站周圍框架的工作區的全形或高度。|  
|[CDockingManager::AutoHidePane](../Topic/CDockingManager::AutoHidePane.md)|建立 autohide 工具列。|  
|[CDockingManager::BringBarsToTop](../Topic/CDockingManager::BringBarsToTop.md)|會將具有指定的對齊頂端的內建的分隔列。|  
|[CDockingManager::BuildPanesMenu](../Topic/CDockingManager::BuildPanesMenu.md)|加入停駐窗格和工具列的名稱加入至功能表。|  
|[CDockingManager::CalcExpectedDockedRect](../Topic/CDockingManager::CalcExpectedDockedRect.md)|計算一個停駐視窗的預期的矩形。|  
|[CDockingManager::Create](../Topic/CDockingManager::Create.md)|建立的處理常式。|  
|[CDockingManager::DeterminePaneAndStatus](../Topic/CDockingManager::DeterminePaneAndStatus.md)|判斷包含指定的點和其狀態的停駐窗格。|  
|[CDockingManager::DisableRestoreDockState](../Topic/CDockingManager::DisableRestoreDockState.md)|啟用或停用停駐配置載入從登錄中。|  
|[CDockingManager::DockPane](../Topic/CDockingManager::DockPane.md)|停駐窗格加入至另一個窗格或到框架視窗。|  
|[CDockingManager::DockPaneLeftOf](../Topic/CDockingManager::DockPaneLeftOf.md)|在另一個窗格左邊的停駐窗格。|  
|[CDockingManager::EnableAutoHidePanes](../Topic/CDockingManager::EnableAutoHidePanes.md)|啟用窗格的停駐到主要畫面格，建立停駐窗格，並將它加入至控制項的資料行清單。|  
|[CDockingManager::EnableDocking](../Topic/CDockingManager::EnableDocking.md)|建立並啟用停駐窗格的停駐窗格為主要畫面格。|  
|[CDockingManager::EnableDockSiteMenu](../Topic/CDockingManager::EnableDockSiteMenu.md)|顯示開啟在所有停駐窗格的標題建立快顯功能表的另外一個按鈕。|  
|[CDockingManager::EnablePaneContextMenu](../Topic/CDockingManager::EnablePaneContextMenu.md)|呼叫程式庫會顯示含有應用程式工具列和停駐窗格中列出的特殊內容功能表，當使用者按一下滑鼠右鍵時，而程式庫 WM\_CONTEXTMENU 處理訊息。|  
|[CDockingManager::FindDockSite](../Topic/CDockingManager::FindDockSite.md)|擷取位於指定位置的，並具有指定的對齊的列窗格。|  
|[CDockingManager::FindDockSiteByPane](../Topic/CDockingManager::FindDockSiteByPane.md)|傳回具有目標列窗格的 ID 的列窗格。|  
|[CDockingManager::FindPaneByID](../Topic/CDockingManager::FindPaneByID.md)|由指定的控制項 ID. 發現窗格|  
|[CDockingManager::FixupVirtualRects](../Topic/CDockingManager::FixupVirtualRects.md)|認可目前所有工具列位置將虛擬矩形。|  
|[CDockingManager::FrameFromPoint](../Topic/CDockingManager::FrameFromPoint.md)|傳回包含指定點的框架。|  
|[CDockingManager::GetClientAreaBounds](../Topic/CDockingManager::GetClientAreaBounds.md)|取得包含工作區界限的矩形。|  
|[CDockingManager::GetDockingMode](../Topic/CDockingManager::GetDockingMode.md)|傳回目前的控制項。|  
|[CDockingManager::GetDockSiteFrameWnd](../Topic/CDockingManager::GetDockSiteFrameWnd.md)|取得指標父視窗框架。|  
|[CDockingManager::GetEnabledAutoHideAlignment](../Topic/CDockingManager::GetEnabledAutoHideAlignment.md)|傳回窗格中啟用對齊。|  
|[CDockingManager::GetMiniFrames](../Topic/CDockingManager::GetMiniFrames.md)|取得 miniframes 清單。|  
|[CDockingManager::GetOuterEdgeBounds](../Topic/CDockingManager::GetOuterEdgeBounds.md)|取得包含框架的外邊緣的矩形。|  
|[CDockingManager::GetPaneList](../Topic/CDockingManager::GetPaneList.md)|傳回屬於停駐管理員\] 窗格中的清單。  這包括所有浮動窗格。|  
|[CDockingManager::GetSmartDockingManager](../Topic/CDockingManager::GetSmartDockingManager.md)|擷取指標給智慧標籤的停駐處理常式。|  
|[CDockingManager::GetSmartDockingManagerPermanent](../Topic/CDockingManager::GetSmartDockingManagerPermanent.md)|擷取指標給智慧標籤的停駐處理常式。|  
|[CDockingManager::GetSmartDockingParams](../Topic/CDockingManager::GetSmartDockingParams.md)|傳回停駐管理員的智慧標籤的停駐參數。|  
|[CDockingManager::GetSmartDockingTheme](../Topic/CDockingManager::GetSmartDockingTheme.md)|傳回用來顯示主題智慧停駐標記的靜態方法。|  
|[CDockingManager::HideAutoHidePanes](../Topic/CDockingManager::HideAutoHidePanes.md)|隱藏在 autohide 模式的窗格。|  
|[CDockingManager::InsertDockSite](../Topic/CDockingManager::InsertDockSite.md)|建立一個停駐窗格並將它插入控制項的資料行清單中。|  
|[CDockingManager::InsertPane](../Topic/CDockingManager::InsertPane.md)|窗格控制項插入至控制項的清單。|  
|[CDockingManager::IsDockSiteMenu](../Topic/CDockingManager::IsDockSiteMenu.md)|指定快顯功能表是否在所有窗格的標題會顯示。|  
|[CDockingManager::IsInAdjustLayout](../Topic/CDockingManager::IsInAdjustLayout.md)|判斷是否要重新調整所有窗格配置。|  
|[CDockingManager::IsOLEContainerMode](../Topic/CDockingManager::IsOLEContainerMode.md)|指定停駐管理員是否位於 OLE 容器模式。|  
|[CDockingManager::IsPointNearDockSite](../Topic/CDockingManager::IsPointNearDockSite.md)|判斷指定的點是否包含在固定網站附近。|  
|[CDockingManager::IsPrintPreviewValid](../Topic/CDockingManager::IsPrintPreviewValid.md)|判斷預覽列印模式是否設定為。|  
|[CDockingManager::LoadState](../Topic/CDockingManager::LoadState.md)|從登錄載入停駐管理員的狀態。|  
|[CDockingManager::LockUpdate](../Topic/CDockingManager::LockUpdate.md)|鎖定特定視窗。|  
|[CDockingManager::OnActivateFrame](../Topic/CDockingManager::OnActivateFrame.md)|呼叫由架構，在框架視窗變成作用中或已停用。|  
|[CDockingManager::OnClosePopupMenu](../Topic/CDockingManager::OnClosePopupMenu.md)|呼叫框架，只有一個作用中的快顯功能表處理 WM\_DESTROY 訊息。|  
|[CDockingManager::OnMoveMiniFrame](../Topic/CDockingManager::OnMoveMiniFrame.md)|呼叫框架移動小型框架視窗。|  
|[CDockingManager::OnPaneContextMenu](../Topic/CDockingManager::OnPaneContextMenu.md)|呼叫由架構，在建立具有  窗格的清單中的功能表。|  
|[CDockingManager::PaneFromPoint](../Topic/CDockingManager::PaneFromPoint.md)|傳回包含指定點的窗格。|  
|[CDockingManager::ProcessPaneContextMenuCommand](../Topic/CDockingManager::ProcessPaneContextMenuCommand.md)|呼叫由架構選擇或清除指定之命令的核取方塊和重新計算一個顯示的  窗格中的設定。|  
|[CDockingManager::RecalcLayout](../Topic/CDockingManager::RecalcLayout.md)|計算控制項的內部配置目前在控制項的清單。|  
|[CDockingManager::ReleaseEmptyPaneContainers](../Topic/CDockingManager::ReleaseEmptyPaneContainers.md)|放開空格的窗格容器。|  
|[CDockingManager::RemoveHiddenMDITabbedBar](../Topic/CDockingManager::RemoveHiddenMDITabbedBar.md)|移除指定的隱藏列窗格。|  
|[CDockingManager::RemoveMiniFrame](../Topic/CDockingManager::RemoveMiniFrame.md)|從微架構清單中移除指定的框架。|  
|[CDockingManager::RemovePaneFromDockManager](../Topic/CDockingManager::RemovePaneFromDockManager.md)|將窗格與停駐管理員的清單中移除。|  
|[CDockingManager::ReplacePane](../Topic/CDockingManager::ReplacePane.md)|取代另一個窗格。|  
|[CDockingManager::ResortMiniFramesForZOrder](../Topic/CDockingManager::ResortMiniFramesForZOrder.md)|依賴微架構清單的框架。|  
|[CDockingManager::SaveState](../Topic/CDockingManager::SaveState.md)|儲存停駐管理員的狀態變更登錄。|  
|[CDockingManager::SendMessageToMiniFrames](../Topic/CDockingManager::SendMessageToMiniFrames.md)|傳送指定的訊息至所有微架構。|  
|[CDockingManager::Serialize](../Topic/CDockingManager::Serialize.md)|將檔案寫入停駐處理常式。  \(覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。|  
|[CDockingManager::SetAutohideZOrder](../Topic/CDockingManager::SetAutohideZOrder.md)|設定控制項的資料行和指定的窗格的大小、寬度和高度。|  
|[CDockingManager::SetDockingMode](../Topic/CDockingManager::SetDockingMode.md)|設定控制項。|  
|[CDockingManager::SetDockState](../Topic/CDockingManager::SetDockState.md)|設定控制項的資料行、微架構和 autohide 列停駐的狀態。|  
|[CDockingManager::SetPrintPreviewMode](../Topic/CDockingManager::SetPrintPreviewMode.md)|設定在預覽列印模式中顯示列的預覽列印模式。|  
|[CDockingManager::SetSmartDockingParams](../Topic/CDockingManager::SetSmartDockingParams.md)|設定定義智慧標籤的停駐行為的參數。|  
|[CDockingManager::ShowDelayShowMiniFrames](../Topic/CDockingManager::ShowDelayShowMiniFrames.md)|顯示或隱藏微架構的視窗。|  
|[CDockingManager::ShowPanes](../Topic/CDockingManager::ShowPanes.md)|顯示或隱藏控制項和 autohide 列的窗格。|  
|[CDockingManager::StartSDocking](../Topic/CDockingManager::StartSDocking.md)|依據智慧型的停駐管理員的對齊方式啟動指定之視窗的智慧標籤的停駐。|  
|[CDockingManager::StopSDocking](../Topic/CDockingManager::StopSDocking.md)|停止智慧停駐。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDockingManager::m\_bHideDockingBarsInContainerMode](../Topic/CDockingManager::m_bHideDockingBarsInContainerMode.md)|指定停駐管理員是否在 OLE 容器模式中隱藏窗格。|  
|[CDockingManager::m\_dockModeGlobal](../Topic/CDockingManager::m_dockModeGlobal.md)|指定全域停駐方式。|  
|[CDockingManager::m\_nDockSensitivity](../Topic/CDockingManager::m_nDockSensitivity.md)|指定停駐敏感度。|  
|[CDockingManager::m\_nTimeOutBeforeDockingBarDock](../Topic/CDockingManager::m_nTimeOutBeforeDockingBarDock.md)|在停駐窗格停駐在即時模式之前，固定長度 \(以毫秒為單位\)，指定。|  
|[CDockingManager::m\_nTimeOutBeforeToolBarDock](../Topic/CDockingManager::m_nTimeOutBeforeToolBarDock.md)|工具列停駐在主框架視窗之前，指定以毫秒為單位的時間。|  
  
## 備註  
 主框架視窗會自動建立和初始化這個類別。  
  
 停駐管理員物件鎖定在停駐配置所有窗格的清單中，以及屬於主框架視窗的所有 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) 視窗的清單。  
  
 `CDockingManager` 類別實作您可以使用  窗格或 `CPaneFrameWnd` 視窗的某些服務。  因為它們在主框架視窗物件封裝，您通常不會直接呼叫這些服務。  如需詳細資訊，請參閱 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)。  
  
## 自訂秘訣  
 下列提示套用至 `CDockingManager` 物件:  
  
-   [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) 支援這些控制項:  
  
    -   `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    -   `AFX_DOCK_TYPE::DT_STANDARD`  
  
    -   `AFX_DOCK_TYPE::DT_SMART`  
  
     這些控制項是由 [CDockingManager::m\_dockModeGlobal](../Topic/CDockingManager::m_dockModeGlobal.md) 定義和呼叫 [CDockingManager::SetDockingMode](../Topic/CDockingManager::SetDockingMode.md)設定。  
  
-   如果您想要建立非浮動，不可調整大小的窗格中， [CDockingManager::AddPane](../Topic/CDockingManager::AddPane.md) 呼叫方法。  這個方法會註冊處理常式停駐的窗格，負責窗格的配置。  
  
## 範例  
 下列範例會在 `CDockingManager` 類別會示範如何使用各種方法設定 `CDockingManager` 物件。  這個範例會示範如何開啟在所有停駐窗格的標題建立快顯功能表的其他按鈕和如何設定物件的控制項。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/CPP/cdockingmanager-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## 需求  
 **標題:** afxDockingManager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)