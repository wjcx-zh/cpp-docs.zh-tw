---
title: "CDockSite Class | Microsoft Docs"
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
  - "CDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockSite class"
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 提供可將衍生自 [CPane Class](../../mfc/reference/cpane-class.md)的窗格排列成資料列集合的功能。  
  
## 語法  
  
```  
class CDockSite: public CBasePane  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDockSite::AddRow](../Topic/CDockSite::AddRow.md)||  
|[CDockSite::AdjustDockingLayout](../Topic/CDockSite::AdjustDockingLayout.md)|\(覆寫 [CBasePane::AdjustDockingLayout](../Topic/CBasePane::AdjustDockingLayout.md)。\)|  
|[CDockSite::AdjustLayout](../Topic/CDockSite::AdjustLayout.md)|\(覆寫 [CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)。\)|  
|[CDockSite::AlignDockSite](../Topic/CDockSite::AlignDockSite.md)||  
|[CDockSite::CalcFixedLayout](../Topic/CDockSite::CalcFixedLayout.md)|\(覆寫 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。\)|  
|[CDockSite::CanAcceptPane](../Topic/CDockSite::CanAcceptPane.md)|\(覆寫 [CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)。\)|  
|[CDockSite::CreateEx](../Topic/CDockSite::CreateEx.md)|\(覆寫 [CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)。\)|  
|[CDockSite::CreateRow](../Topic/CDockSite::CreateRow.md)||  
|[CDockSite::DockPane](../Topic/CDockSite::DockPane.md)|\(覆寫 [CBasePane::DockPane](../Topic/CBasePane::DockPane.md)。\)|  
|[CDockSite::DoesAllowDynInsertBefore](../Topic/CDockSite::DoesAllowDynInsertBefore.md)|\(覆寫 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)。\)|  
|[CDockSite::FindRowIndex](../Topic/CDockSite::FindRowIndex.md)||  
|[CDockSite::FixupVirtualRects](../Topic/CDockSite::FixupVirtualRects.md)||  
|[CDockSite::GetDockSiteID](../Topic/CDockSite::GetDockSiteID.md)||  
|[CDockSite::GetDockSiteRowsList](../Topic/CDockSite::GetDockSiteRowsList.md)||  
|[CDockSite::IsAccessibilityCompatible](../Topic/CDockSite::IsAccessibilityCompatible.md)|\(覆寫 `CBasePane::IsAccessibilityCompatible`。\)|  
|[CDockSite::IsDragMode](../Topic/CDockSite::IsDragMode.md)||  
|[CDockSite::IsLastRow](../Topic/CDockSite::IsLastRow.md)||  
|[CDockSite::IsRectWithinDockSite](../Topic/CDockSite::IsRectWithinDockSite.md)||  
|[CDockSite::IsResizable](../Topic/CDockSite::IsResizable.md)|\(覆寫 [CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)。\)|  
|[CDockSite::MovePane](../Topic/CDockSite::MovePane.md)||  
|[CDockSite::OnInsertRow](../Topic/CDockSite::OnInsertRow.md)||  
|[CDockSite::OnRemoveRow](../Topic/CDockSite::OnRemoveRow.md)||  
|[CDockSite::OnResizeRow](../Topic/CDockSite::OnResizeRow.md)||  
|[CDockSite::OnSetWindowPos](../Topic/CDockSite::OnSetWindowPos.md)||  
|[CDockSite::OnShowRow](../Topic/CDockSite::OnShowRow.md)||  
|[CDockSite::OnSizeParent](../Topic/CDockSite::OnSizeParent.md)||  
|[CDockSite::PaneFromPoint](../Topic/CDockSite::PaneFromPoint.md)|由給定參數指定時，傳回停駐於停駐位置的窗格。|  
|[CDockSite::DockPaneLeftOf](../Topic/CDockSite::DockPaneLeftOf.md)|將窗格停駐於另一個窗格的左邊。|  
|[CDockSite::FindPaneByID](../Topic/CDockSite::FindPaneByID.md)|傳回給定識別碼所識別的窗格。|  
|[CDockSite::GetPaneList](../Topic/CDockSite::GetPaneList.md)|傳回停駐於停駐位置的窗格清單。|  
|[CDockSite::RectSideFromPoint](../Topic/CDockSite::RectSideFromPoint.md)||  
|[CDockSite::RemovePane](../Topic/CDockSite::RemovePane.md)||  
|[CDockSite::RemoveRow](../Topic/CDockSite::RemoveRow.md)||  
|[CDockSite::ReplacePane](../Topic/CDockSite::ReplacePane.md)||  
|[CDockSite::RepositionPanes](../Topic/CDockSite::RepositionPanes.md)||  
|[CDockSite::ResizeDockSite](../Topic/CDockSite::ResizeDockSite.md)||  
|[CDockSite::ResizeRow](../Topic/CDockSite::ResizeRow.md)||  
|[CDockSite::ShowPane](../Topic/CDockSite::ShowPane.md)|顯示窗格。|  
|[CDockSite::ShowRow](../Topic/CDockSite::ShowRow.md)||  
|[CDockSite::SwapRows](../Topic/CDockSite::SwapRows.md)||  
  
## 備註  
 架構會在您呼叫 [CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md) 時自動建立 `CDockSite` 物件。  停駐位置視窗位於主框架視窗上用戶端區域的邊緣。  
  
 您通常不必呼叫停駐位置提供的服務，因為 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md) 會處理這些服務。  
  
## 範例  
 下列範例示範如何建立 `CDockSite` 類別的物件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/CPP/cdocksite-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## 需求  
 **標頭：**afxDockSite.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)