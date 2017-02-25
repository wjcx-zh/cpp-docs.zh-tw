---
title: "CPaneContainerManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneContainerManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneContainerManager class"
ms.assetid: 3d974c15-a62f-4648-bb5b-cc31ab7950af
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CPaneContainerManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPaneContainerManager` 類別處理目前停駐配置的儲存和顯示。  
  
## 語法  
  
```  
class CPaneContainerManager : public CObject  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPaneContainerManager::AddPane](../Topic/CPaneContainerManager::AddPane.md)||  
|[CPaneContainerManager::AddPaneContainerManager](../Topic/CPaneContainerManager::AddPaneContainerManager.md)||  
|[CPaneContainerManager::AddPaneContainerManagerToDockablePane](../Topic/CPaneContainerManager::AddPaneContainerManagerToDockablePane.md)||  
|[CPaneContainerManager::AddPanesToList](../Topic/CPaneContainerManager::AddPanesToList.md)||  
|[CPaneContainerManager::AddPaneToList](../Topic/CPaneContainerManager::AddPaneToList.md)||  
|[CPaneContainerManager::AddPaneToRecentPaneContainer](../Topic/CPaneContainerManager::AddPaneToRecentPaneContainer.md)||  
|[CPaneContainerManager::CalcRects](../Topic/CPaneContainerManager::CalcRects.md)||  
|[CPaneContainerManager::CanBeAttached](../Topic/CPaneContainerManager::CanBeAttached.md)||  
|[CPaneContainerManager::CheckAndRemoveNonValidPane](../Topic/CPaneContainerManager::CheckAndRemoveNonValidPane.md)||  
|[CPaneContainerManager::CheckForMiniFrameAndCaption](../Topic/CPaneContainerManager::CheckForMiniFrameAndCaption.md)||  
|[CPaneContainerManager::Create](../Topic/CPaneContainerManager::Create.md)||  
|[CPaneContainerManager::DoesAllowDynInsertBefore](../Topic/CPaneContainerManager::DoesAllowDynInsertBefore.md)||  
|[CPaneContainerManager::DoesContainFloatingPane](../Topic/CPaneContainerManager::DoesContainFloatingPane.md)||  
|[CPaneContainerManager::EnableGrippers](../Topic/CPaneContainerManager::EnableGrippers.md)||  
|[CPaneContainerManager::FindPaneContainer](../Topic/CPaneContainerManager::FindPaneContainer.md)||  
|[CPaneContainerManager::FindTabbedPane](../Topic/CPaneContainerManager::FindTabbedPane.md)||  
|[CPaneContainerManager::GetAvailableSpace](../Topic/CPaneContainerManager::GetAvailableSpace.md)||  
|[CPaneContainerManager::GetDefaultPaneDivider](../Topic/CPaneContainerManager::GetDefaultPaneDivider.md)||  
|[CPaneContainerManager::GetDockSiteFrameWnd](../Topic/CPaneContainerManager::GetDockSiteFrameWnd.md)||  
|[CPaneContainerManager::GetFirstPane](../Topic/CPaneContainerManager::GetFirstPane.md)||  
|[CPaneContainerManager::GetFirstVisiblePane](../Topic/CPaneContainerManager::GetFirstVisiblePane.md)||  
|[CPaneContainerManager::GetMinMaxOffset](../Topic/CPaneContainerManager::GetMinMaxOffset.md)||  
|[CPaneContainerManager::GetMinSize](../Topic/CPaneContainerManager::GetMinSize.md)||  
|[CPaneContainerManager::GetNodeCount](../Topic/CPaneContainerManager::GetNodeCount.md)||  
|[CPaneContainerManager::GetPaneContainerRTC](../Topic/CPaneContainerManager::GetPaneContainerRTC.md)||  
|[CPaneContainerManager::GetPaneCount](../Topic/CPaneContainerManager::GetPaneCount.md)||  
|[CPaneContainerManager::GetTotalRefCount](../Topic/CPaneContainerManager::GetTotalRefCount.md)||  
|[CPaneContainerManager::GetVisiblePaneCount](../Topic/CPaneContainerManager::GetVisiblePaneCount.md)||  
|[CPaneContainerManager::GetWindowRect](../Topic/CPaneContainerManager::GetWindowRect.md)||  
|[CPaneContainerManager::HideAll](../Topic/CPaneContainerManager::HideAll.md)||  
|[CPaneContainerManager::InsertPane](../Topic/CPaneContainerManager::InsertPane.md)||  
|[CPaneContainerManager::IsAutoHideMode](../Topic/CPaneContainerManager::IsAutoHideMode.md)||  
|[CPaneContainerManager::IsEmpty](../Topic/CPaneContainerManager::IsEmpty.md)||  
|[CPaneContainerManager::IsRootPaneContainerVisible](../Topic/CPaneContainerManager::IsRootPaneContainerVisible.md)||  
|[CPaneContainerManager::NotifyPaneDivider](../Topic/CPaneContainerManager::NotifyPaneDivider.md)||  
|[CPaneContainerManager::OnPaneDividerMove](../Topic/CPaneContainerManager::OnPaneDividerMove.md)||  
|[CPaneContainerManager::OnShowPane](../Topic/CPaneContainerManager::OnShowPane.md)||  
|[CPaneContainerManager::PaneFromPoint](../Topic/CPaneContainerManager::PaneFromPoint.md)||  
|[CPaneContainerManager::ReleaseEmptyPaneContainers](../Topic/CPaneContainerManager::ReleaseEmptyPaneContainers.md)||  
|[CPaneContainerManager::RemoveAllPanesAndPaneDividers](../Topic/CPaneContainerManager::RemoveAllPanesAndPaneDividers.md)||  
|[CPaneContainerManager::RemoveNonValidPanes](../Topic/CPaneContainerManager::RemoveNonValidPanes.md)||  
|[CPaneContainerManager::RemovePaneDivider](../Topic/CPaneContainerManager::RemovePaneDivider.md)||  
|[CPaneContainerManager::RemovePaneFromPaneContainer](../Topic/CPaneContainerManager::RemovePaneFromPaneContainer.md)||  
|[CPaneContainerManager::ReplacePane](../Topic/CPaneContainerManager::ReplacePane.md)||  
|[CPaneContainerManager::ResizePaneContainers](../Topic/CPaneContainerManager::ResizePaneContainers.md)||  
|[CPaneContainerManager::Serialize](../Topic/CPaneContainerManager::Serialize.md)|讀取或寫入這個物件從或其中的檔案。  \(覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。|  
|[CPaneContainerManager::SetDefaultPaneDividerForPanes](../Topic/CPaneContainerManager::SetDefaultPaneDividerForPanes.md)||  
|[CPaneContainerManager::SetPaneContainerRTC](../Topic/CPaneContainerManager::SetPaneContainerRTC.md)||  
|[CPaneContainerManager::SetResizeMode](../Topic/CPaneContainerManager::SetResizeMode.md)||  
|[CPaneContainerManager::StoreRecentDockSiteInfo](../Topic/CPaneContainerManager::StoreRecentDockSiteInfo.md)||  
  
### 備註  
 這個架構便會自動建立物件執行個體 `CPaneContainerManager` 並且內嵌到 [CPaneDivider Class](../../mfc/reference/cpanedivider-class.md) 物件或輸入 [CMultiPaneFrameWnd Class](../../mfc/reference/cmultipaneframewnd-class.md) 物件。  
  
 `CPaneContainerManager` 類別儲存指標從 [CPaneContainer](../../mfc/reference/cpanecontainer-class.md) 物件已建置二進位樹狀目錄的根目錄。  
  
## 範例  
 下列範例示範如何取得 `CPaneContainerManager` 物件的參考。  這個程式碼片段是 [將窗格大小範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_SetPaneSize#5](../../mfc/reference/codesnippet/CPP/cpanecontainermanager-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)  
  
## 需求  
 **標題:** afxpanecontainermanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)   
 [CPaneDivider Class](../../mfc/reference/cpanedivider-class.md)