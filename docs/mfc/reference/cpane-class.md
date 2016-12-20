---
title: "CPane Class | Microsoft Docs"
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
  - "CPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPane class"
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPane` 類別是 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)增強功能。  如果您要升級現有的 MFC 專案，以 `CPane`取代 `CControlBar` 的所有項目。  
  
## 語法  
  
```  
class CPane : public CBasePane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CPane::~CPane`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPane::AdjustSizeImmediate](../Topic/CPane::AdjustSizeImmediate.md)|立即重新計算窗格的配置。|  
|[CPane::AllocElements](../Topic/CPane::AllocElements.md)|配置儲存區供內部使用。|  
|[CPane::AllowShowOnPaneMenu](../Topic/CPane::AllowShowOnPaneMenu.md)|指定窗格是否在應用程式的窗格執行階段產生的清單中。|  
|[CPane::CalcAvailableSize](../Topic/CPane::CalcAvailableSize.md)|大小計算差異在指定的矩形和目前視窗的矩形之間。|  
|[CPane::CalcInsideRect](../Topic/CPane::CalcInsideRect.md)|計算窗格內的矩形，允許框線和移駐夾。|  
|[CPane::CalcRecentDockedRect](../Topic/CPane::CalcRecentDockedRect.md)|計算最近停駐的矩形。|  
|[CPane::CalcSize](../Topic/CPane::CalcSize.md)|計算窗格的大小。|  
|[CPane::CanBeDocked](../Topic/CPane::CanBeDocked.md)|判斷  窗格是否可以停駐在指定的主窗格中。|  
|[CPane::CanBeTabbedDocument](../Topic/CPane::CanBeTabbedDocument.md)|判斷窗格是否可以轉換為索引標籤式文件。|  
|[CPane::ConvertToTabbedDocument](../Topic/CPane::ConvertToTabbedDocument.md)|轉換可停駐窗格為索引標籤式文件。|  
|[CPane::CopyState](../Topic/CPane::CopyState.md)|複製  窗格中的狀態。  \(覆寫 [CBasePane::CopyState](../Topic/CBasePane::CopyState.md)\)。|  
|[CPane::Create](../Topic/CPane::Create.md)|建立控制項並將其附加至 `CPane` 物件。|  
|[CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md)|建立浮動窗格的小型框架視窗。|  
|[CPane::CreateEx](../Topic/CPane::CreateEx.md)|建立控制項並將其附加至 `CPane` 物件。|  
|`CPane::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CPane::DockByMouse](../Topic/CPane::DockByMouse.md)|您可以使用滑鼠停駐方法，停駐窗格。|  
|[CPane::DockPane](../Topic/CPane::DockPane.md)|內建浮動窗格加入基本的窗格。|  
|[CPane::DockPaneStandard](../Topic/CPane::DockPaneStandard.md)|您可以使用大綱 \(標準\)，內建的停駐窗格。|  
|[CPane::DockToFrameWindow](../Topic/CPane::DockToFrameWindow.md)|內建可停駐窗格至框架。  \(覆寫 `CBasePane::DockToFrameWindow`\)。|  
|[CPane::DoesAllowSiblingBars](../Topic/CPane::DoesAllowSiblingBars.md)|指示是否可停駐其他窗格目前窗格內建的相同的資料列。|  
|[CPane::FloatPane](../Topic/CPane::FloatPane.md)|浮動窗格。|  
|[CPane::GetAvailableExpandSize](../Topic/CPane::GetAvailableExpandSize.md)|傳回數量，以像素為單位\)，該窗格內含可展開。|  
|[CPane::GetAvailableStretchSize](../Topic/CPane::GetAvailableStretchSize.md)|傳回數量，以像素為單位\)，該窗格可以縮小。|  
|[CPane::GetBorders](../Topic/CPane::GetBorders.md)|傳回窗格的框線寬度。|  
|[CPane::GetClientHotSpot](../Topic/CPane::GetClientHotSpot.md)|傳回窗格的作用點。|  
|[CPane::GetDockSiteRow](../Topic/CPane::GetDockSiteRow.md)|傳回停駐窗格的停駐行為。|  
|[CPane::GetExclusiveRowMode](../Topic/CPane::GetExclusiveRowMode.md)|判斷  窗格是否在獨佔模式下執行。|  
|[CPane::GetHotSpot](../Topic/CPane::GetHotSpot.md)|會傳回在基礎 `CMFCDragFrameImpl` 物件中儲存的作用點。|  
|[CPane::GetMinSize](../Topic/CPane::GetMinSize.md)|擷取窗格的最小容許大小。|  
|[CPane::GetPaneName](../Topic/CPane::GetPaneName.md)|擷取窗格的標題。|  
|`CPane::GetResizeStep`|內部使用。|  
|`CPane::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CPane::GetVirtualRect](../Topic/CPane::GetVirtualRect.md)|擷取窗格的 *虛擬矩形*。|  
|[CPane::IsChangeState](../Topic/CPane::IsChangeState.md)|當窗格移動時，這個方法來分析窗格的位置 \(相對於其他窗格，內建的資料列和小型框架視窗並傳回適當的 `AFX_CS_STATUS` 值。|  
|[CPane::IsDragMode](../Topic/CPane::IsDragMode.md)|指定  窗格是否已經拖曳。|  
|[CPane::IsInFloatingMultiPaneFrameWnd](../Topic/CPane::IsInFloatingMultiPaneFrameWnd.md)|指定窗格是否在多窗格框架視窗。  \(覆寫 `CBasePane::IsInFloatingMultiPaneFrameWnd`\)。|  
|[CPane::IsLeftOf](../Topic/CPane::IsLeftOf.md)|判斷  窗格是否為向左 \(和以上\) 指定的矩形。|  
|[CPane::IsResizable](../Topic/CPane::IsResizable.md)|判斷窗格是否可以調整大小。  \(覆寫 [CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)\)。|  
|[CPane::IsTabbed](../Topic/CPane::IsTabbed.md)|判斷是否在窗格的索引標籤式視窗的索引標籤控制項會在此處。  \(覆寫 [CBasePane::IsTabbed](../Topic/CBasePane::IsTabbed.md)\)。|  
|[CPane::LoadState](../Topic/CPane::LoadState.md)|從登錄載入窗格的狀態。  \(覆寫 [CBasePane::LoadState](../Topic/CBasePane::LoadState.md)\)。|  
|[CPane::MoveByAlignment](../Topic/CPane::MoveByAlignment.md)|根據指定的數量來捲動窗格和虛擬矩形。|  
|[CPane::MovePane](../Topic/CPane::MovePane.md)|捲動窗格移至指定的矩形。|  
|[CPane::OnAfterChangeParent](../Topic/CPane::OnAfterChangeParent.md)|呼叫框架，其在窗格的父代變更。|  
|[CPane::OnBeforeChangeParent](../Topic/CPane::OnBeforeChangeParent.md)|呼叫框架，其在窗格的父代會變更。|  
|[CPane::OnPressCloseButton](../Topic/CPane::OnPressCloseButton.md)|呼叫框架，當使用者選取標頭的關閉按鈕的窗格。|  
|`CPane::OnProcessDblClk`|內部使用。|  
|[CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)|呼叫框架，其在特殊窗格功能表隨即顯示。|  
|[CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)|呼叫框架，其在特殊窗格功能表隨即顯示。|  
|`CPane::PrepareToDock`|內部使用。|  
|[CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)|重新計算窗格的組態資訊。  \(覆寫 [CBasePane::RecalcLayout](../Topic/CBasePane::RecalcLayout.md)\)。|  
|[CPane::SaveState](../Topic/CPane::SaveState.md)|儲存窗格的狀態變更登錄。  \(覆寫 [CBasePane::SaveState](../Topic/CBasePane::SaveState.md)\)。|  
|[CPane::SetActiveInGroup](../Topic/CPane::SetActiveInGroup.md)|旗標窗格為作用中。|  
|[CPane::SetBorders](../Topic/CPane::SetBorders.md)|將窗格的邊界值。|  
|[CPane::SetClientHotSpot](../Topic/CPane::SetClientHotSpot.md)|將窗格的作用點。|  
|[CPane::SetDockState](../Topic/CPane::SetDockState.md)|停駐窗格的還原檢視狀態資訊。|  
|[CPane::SetExclusiveRowMode](../Topic/CPane::SetExclusiveRowMode.md)|可啟用或停用專案 \[執行\] 模式。|  
|[CPane::SetMiniFrameRTC](../Topic/CPane::SetMiniFrameRTC.md)|設定預設小型框架視窗的執行階段類別資訊。|  
|[CPane::SetMinSize](../Topic/CPane::SetMinSize.md)|將窗格的最小容許大小。|  
|[CPane::SetVirtualRect](../Topic/CPane::SetVirtualRect.md)|將窗格設定為 *虛擬矩形*。|  
|[CPane::StretchPaneDeferWndPos](../Topic/CPane::StretchPaneDeferWndPos.md)|垂直延伸窗格或以水平停駐樣式。|  
|[CPane::ToggleAutoHide](../Topic/CPane::ToggleAutoHide.md)|切換 \[自動隱藏模式。|  
|[CPane::UndockPane](../Topic/CPane::UndockPane.md)|從目前停駐的內建網站、預設滑桿或小型框架視窗中移除窗格。  \(覆寫 [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)\)。|  
|[CPane::UpdateVirtualRect](../Topic/CPane::UpdateVirtualRect.md)|更新虛擬矩形。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CPane::OnAfterDock](../Topic/CPane::OnAfterDock.md)|呼叫框架，該窗格停駐。|  
|[CPane::OnAfterFloat](../Topic/CPane::OnAfterFloat.md)|呼叫框架，該窗格浮動的話。|  
|[CPane::OnBeforeDock](../Topic/CPane::OnBeforeDock.md)|呼叫框架，該窗格就停駐。|  
|[CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)|呼叫框架時，窗格會浮動。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPane::m\_bHandleMinSize](../Topic/CPane::m_bHandleMinSize.md)|啟用一致處理窗格的最小大小。|  
|[CPane::m\_recentDockInfo](../Topic/CPane::m_recentDockInfo.md)|包含最近停駐資訊。|  
  
## 備註  
 通常， `CPane` 物件不會直接具現化。  如果您需要使用停駐功能的窗格，請從 [CDockablePane](../../mfc/reference/cdockablepane-class.md)衍生物件。  如果您需要工具列功能，請從 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)衍生物件。  
  
 當您從 `CPane`時衍生類別時，它會在 [CDockSite](../../mfc/reference/cdocksite-class.md) 可以停駐，而在 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)可以浮動。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## 需求  
 **標題:** afxPane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)