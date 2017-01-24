---
title: "CMFCAutoHideBar Class | Microsoft Docs"
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
  - "CMFCAutoHideBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAutoHideToolBar class"
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAutoHideBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCAutoHideBar` 類別是實作自動隱藏功能的特殊工具列類別。  
  
## 語法  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](../Topic/CMFCAutoHideBar::CMFCAutoHideBar.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAutoHideBar::AddAutoHideWindow](../Topic/CMFCAutoHideBar::AddAutoHideWindow.md)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](../Topic/CMFCAutoHideBar::AllowShowOnPaneMenu.md)|\(覆寫 `CPane::AllowShowOnPaneMenu`。\)|  
|[CMFCAutoHideBar::CalcFixedLayout](../Topic/CMFCAutoHideBar::CalcFixedLayout.md)|\(覆寫 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。\)|  
|[CMFCAutoHideBar::Create](../Topic/CMFCAutoHideBar::Create.md)|建立控制列並將它附加至 [CPane](../../mfc/reference/cpane-class.md) 物件。  \(覆寫 [CPane::Create](../Topic/CPane::Create.md)。\)|  
|[CMFCAutoHideBar::GetFirstAHWindow](../Topic/CMFCAutoHideBar::GetFirstAHWindow.md)||  
|[CMFCAutoHideBar::GetVisibleCount](../Topic/CMFCAutoHideBar::GetVisibleCount.md)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](../Topic/CMFCAutoHideBar::OnShowControlBarMenu.md)|當特殊窗格功能表即將顯示時由架構呼叫。  \(覆寫 [CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)。\)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](../Topic/CMFCAutoHideBar::RemoveAutoHideWindow.md)||  
|[CMFCAutoHideBar::SetActiveInGroup](../Topic/CMFCAutoHideBar::SetActiveInGroup.md)|\(覆寫 [CPane::SetActiveInGroup](../Topic/CPane::SetActiveInGroup.md)。\)|  
|[CMFCAutoHideBar::SetRecentVisibleState](../Topic/CMFCAutoHideBar::SetRecentVisibleState.md)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](../Topic/CMFCAutoHideBar::ShowAutoHideWindow.md)||  
|[CMFCAutoHideBar::StretchPane](../Topic/CMFCAutoHideBar::StretchPane.md)|垂直或水平伸展窗格。  \(覆寫 [CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)。\)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](../Topic/CMFCAutoHideBar::UnSetAutoHideMode.md)||  
|[CMFCAutoHideBar::UpdateVisibleState](../Topic/CMFCAutoHideBar::UpdateVisibleState.md)||  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAutoHideBar::m\_nShowAHWndDelay](../Topic/CMFCAutoHideBar::m_nShowAHWndDelay.md)|當使用者將滑鼠游標置於 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md)上方，及在架構顯示相關聯的視窗之間的時間延遲。|  
  
## 備註  
 當使用者將停駐窗格切換為自動隱藏模式時，架構會自動建立 `CMFCAutoHideBar` 物件。  它也會建立必要的 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) 和 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) 物件。  每個 `CAutoHideDockSite` 物件與一個個別的 `CMFCAutoHideButton` 相關聯。  
  
 當使用者的滑鼠停留在 `CMFCAutoHideButton` 上方時，`CMFCAutoHideBar` 類別會實作 `CAutoHideDockSite` 的顯示。  當工具列收到 WM\_MOUSEMOVE 訊息時，`CMFCAutoHideBar` 會啟動計時器。  當計時器完成時，會將 WM\_TIMER 事件通知傳送給工具列。  工具列會藉由檢查滑鼠指標是否放置在相同的自動隱藏按鈕上方 \(在計時器啟動時所放置\)，以處理此事件。  如果是，則顯示附加的 `CAutoHideDockSite`。  
  
 您可以設定 `m_nShowAHWndDelay` 來控制計時器的延遲長度。  預設值為 400 毫秒。  
  
## 範例  
 下列範例示範如何建構 `CMFCAutoHideBar` 物件及使用其 `GetDockSiteRow` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/CPP/cmfcautohidebar-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## 需求  
 **標頭：**afxautohidebar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CAutoHideDockSite Class](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md)