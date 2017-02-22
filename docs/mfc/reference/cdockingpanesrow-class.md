---
title: "CDockingPanesRow Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockingPanesRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockingPanesRow class"
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CDockingPanesRow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理與停駐位置位於相同水平或垂直列 \(欄\) 之窗格的清單。  
  
## 語法  
  
```  
class CDockingPanesRow : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CDockingPanesRow::CDockingPanesRow`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDockingPanesRow::AddPane](../Topic/CDockingPanesRow::AddPane.md)||  
|[CDockingPanesRow::AddPaneFromRow](../Topic/CDockingPanesRow::AddPaneFromRow.md)||  
|[CDockingPanesRow::ArrangePanes](../Topic/CDockingPanesRow::ArrangePanes.md)|根據指定的邊界和間距參數排列資料列中的窗格。|  
|[CDockingPanesRow::CalcFixedLayout](../Topic/CDockingPanesRow::CalcFixedLayout.md)||  
|[CDockingPanesRow::Create](../Topic/CDockingPanesRow::Create.md)||  
|[CDockingPanesRow::ExpandStretchedPanes](../Topic/CDockingPanesRow::ExpandStretchedPanes.md)||  
|[CDockingPanesRow::ExpandStretchedPanesRect](../Topic/CDockingPanesRow::ExpandStretchedPanesRect.md)||  
|[CDockingPanesRow::FixupVirtualRects](../Topic/CDockingPanesRow::FixupVirtualRects.md)||  
|[CDockingPanesRow::GetAvailableLength](../Topic/CDockingPanesRow::GetAvailableLength.md)||  
|[CDockingPanesRow::GetAvailableSpace](../Topic/CDockingPanesRow::GetAvailableSpace.md)||  
|[CDockingPanesRow::GetClientRect](../Topic/CDockingPanesRow::GetClientRect.md)||  
|[CDockingPanesRow::GetDockSite](../Topic/CDockingPanesRow::GetDockSite.md)||  
|[CDockingPanesRow::GetExtraSpace](../Topic/CDockingPanesRow::GetExtraSpace.md)||  
|[CDockingPanesRow::GetGroupFromPane](../Topic/CDockingPanesRow::GetGroupFromPane.md)||  
|[CDockingPanesRow::GetID](../Topic/CDockingPanesRow::GetID.md)||  
|[CDockingPanesRow::GetMaxPaneSize](../Topic/CDockingPanesRow::GetMaxPaneSize.md)||  
|[CDockingPanesRow::GetPaneCount](../Topic/CDockingPanesRow::GetPaneCount.md)||  
|[CDockingPanesRow::GetPaneList](../Topic/CDockingPanesRow::GetPaneList.md)||  
|[CDockingPanesRow::GetRowAlignment](../Topic/CDockingPanesRow::GetRowAlignment.md)||  
|[CDockingPanesRow::GetRowHeight](../Topic/CDockingPanesRow::GetRowHeight.md)||  
|[CDockingPanesRow::GetRowOffset](../Topic/CDockingPanesRow::GetRowOffset.md)||  
|[CDockingPanesRow::GetVisibleCount](../Topic/CDockingPanesRow::GetVisibleCount.md)||  
|[CDockingPanesRow::GetWindowRect](../Topic/CDockingPanesRow::GetWindowRect.md)||  
|[CDockingPanesRow::HasPane](../Topic/CDockingPanesRow::HasPane.md)||  
|[CDockingPanesRow::IsEmpty](../Topic/CDockingPanesRow::IsEmpty.md)||  
|[CDockingPanesRow::IsExclusiveRow](../Topic/CDockingPanesRow::IsExclusiveRow.md)||  
|[CDockingPanesRow::IsHorizontal](../Topic/CDockingPanesRow::IsHorizontal.md)||  
|[CDockingPanesRow::IsVisible](../Topic/CDockingPanesRow::IsVisible.md)||  
|[CDockingPanesRow::Move](../Topic/CDockingPanesRow::Move.md)||  
|[CDockingPanesRow::MovePane](../Topic/CDockingPanesRow::MovePane.md)||  
|[CDockingPanesRow::OnResizePane](../Topic/CDockingPanesRow::OnResizePane.md)||  
|[CDockingPanesRow::RedrawAll](../Topic/CDockingPanesRow::RedrawAll.md)||  
|[CDockingPanesRow::RemovePane](../Topic/CDockingPanesRow::RemovePane.md)||  
|[CDockingPanesRow::ReplacePane](../Topic/CDockingPanesRow::ReplacePane.md)||  
|[CDockingPanesRow::RepositionPanes](../Topic/CDockingPanesRow::RepositionPanes.md)||  
|[CDockingPanesRow::Resize](../Topic/CDockingPanesRow::Resize.md)||  
|[CDockingPanesRow::ResizeByPaneDivider](../Topic/CDockingPanesRow::ResizeByPaneDivider.md)||  
|[CDockingPanesRow::ScreenToClient](../Topic/CDockingPanesRow::ScreenToClient.md)||  
|[CDockingPanesRow::SetExtra](../Topic/CDockingPanesRow::SetExtra.md)||  
|[CDockingPanesRow::ShowDockSiteRow](../Topic/CDockingPanesRow::ShowDockSiteRow.md)||  
|[CDockingPanesRow::ShowPane](../Topic/CDockingPanesRow::ShowPane.md)||  
|[CDockingPanesRow::UpdateVisibleState](../Topic/CDockingPanesRow::UpdateVisibleState.md)||  
  
## 備註  
 `CDockingPanesRow` 物件會由固定站台物件在內部建立。  
  
## 範例  
 下列範例示範如何從 `CMFCAutoHideBar` 物件取得 `CDockingPanesRow` 物件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/CPP/cdockingpanesrow-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)  
  
## 需求  
 **標頭：**afxDockingPanesRow.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)