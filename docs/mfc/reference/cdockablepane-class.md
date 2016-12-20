---
title: "CDockablePane Class | Microsoft Docs"
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
  - "CDockablePane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockablePane class"
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockablePane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作可在索引窗格可停駐在網站或內包含的窗格。  
  
## 語法  
  
```  
class CDockablePane : public CPane  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDockablePane::CDockablePane](../Topic/CDockablePane::CDockablePane.md)|建構和 `CDockablePane` 初始化物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)|窗格附加至另一個窗格。  這會建立索引窗格。|  
|[CDockablePane::CalcFixedLayout](../Topic/CDockablePane::CalcFixedLayout.md)|傳回窗格矩形的大小。|  
|[CDockablePane::CanAcceptMiniFrame](../Topic/CDockablePane::CanAcceptMiniFrame.md)|判斷指定的是否微架構可以停駐窗格。|  
|[CDockablePane::CanAcceptPane](../Topic/CDockablePane::CanAcceptPane.md)|判斷其他窗格是否可以停駐在目前窗格。|  
|[CDockablePane::CanAutoHide](../Topic/CDockablePane::CanAutoHide.md)|判斷  窗格是否支援自動隱藏模式。  \(覆寫 [CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)\)。|  
|[CDockablePane::CanBeAttached](../Topic/CDockablePane::CanBeAttached.md)|判斷目前窗格是否可以停駐到另一個窗格。|  
|[CDockablePane::ConvertToTabbedDocument](../Topic/CDockablePane::ConvertToTabbedDocument.md)|轉換一個或多個可停駐窗格為 MDI 索引標籤式文件。|  
|[CDockablePane::CopyState](../Topic/CDockablePane::CopyState.md)|將可停駐窗格的狀態。|  
|[CDockablePane::Create](../Topic/CDockablePane::Create.md)|建立 Windows 控制項並將其附加至 `CDockablePane` 物件。|  
|[CDockablePane::CreateDefaultPaneDivider](../Topic/CDockablePane::CreateDefaultPaneDivider.md)|當控制項停駐至框架視窗，建立窗格的預設分割線。|  
|[CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md)|建立 Windows 控制項並將其附加至 `CDockablePane` 物件。|  
|[CDockablePane::CreateTabbedPane](../Topic/CDockablePane::CreateTabbedPane.md)|會從目前的  窗格中的索引窗格。|  
|[CDockablePane::DockPaneContainer](../Topic/CDockablePane::DockPaneContainer.md)|停駐容器至窗格。|  
|[CDockablePane::DockPaneStandard](../Topic/CDockablePane::DockPaneStandard.md)|您可以使用大綱 \(標準\)，內建的停駐窗格。|  
|`CDockablePane::DockToFrameWindow`|內部使用。  若要停駐窗格，請使用 [CPane::DockPane](../Topic/CPane::DockPane.md) 或 [CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md)。|  
|[CDockablePane::DockToRecentPos](../Topic/CDockablePane::DockToRecentPos.md)|停駐窗格為其儲存的最新的停駐位置。|  
|[CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md)|停駐在另一個停駐窗格的停駐窗格。|  
|[CDockablePane::EnableAutohideAll](../Topic/CDockablePane::EnableAutohideAll.md)|以其他窗格 \(可啟用或停用這個窗格的自動隱藏模式在容器中。|  
|[CDockablePane::EnableGripper](../Topic/CDockablePane::EnableGripper.md)|顯示或隱藏標題 \(移駐夾\)。|  
|[CDockablePane::GetAHRestoredRect](../Topic/CDockablePane::GetAHRestoredRect.md)|在自動隱藏模式指定窗格的位置，並可見。|  
|[CDockablePane::GetAHSlideMode](../Topic/CDockablePane::GetAHSlideMode.md)|擷取窗格的自動隱藏滑動方式。|  
|`CDockablePane::GetAutoHideButton`|內部使用。|  
|`CDockablePane::GetAutoHideToolBar`|內部使用。|  
|[CDockablePane::GetCaptionHeight](../Topic/CDockablePane::GetCaptionHeight.md)|傳回目前標題的高度。|  
|[CDockablePane::GetDefaultPaneDivider](../Topic/CDockablePane::GetDefaultPaneDivider.md)|傳回窗格的容器的預設窗格分割線。|  
|[CDockablePane::GetDockingStatus](../Topic/CDockablePane::GetDockingStatus.md)|判斷是否可停駐窗格會根據提供的指標位置。|  
|[CDockablePane::GetDragSensitivity](../Topic/CDockablePane::GetDragSensitivity.md)|傳回停駐窗格拖曳的敏感度。|  
|[CDockablePane::GetLastPercentInPaneContainer](../Topic/CDockablePane::GetLastPercentInPaneContainer.md)|擷取窗格在容器中佔用空間百分比。|  
|[CDockablePane::GetTabArea](../Topic/CDockablePane::GetTabArea.md)|擷取窗格的索引標籤區域。|  
|[CDockablePane::GetTabbedPaneRTC](../Topic/CDockablePane::GetTabbedPaneRTC.md)|傳回所建立的新索引標籤式視窗的執行階段類別資訊，而另一個窗格停駐到目前窗格時。|  
|[CDockablePane::HasAutoHideMode](../Topic/CDockablePane::HasAutoHideMode.md)|指定停駐窗格是否可以轉換成自動隱藏模式。|  
|[CDockablePane::HitTest](../Topic/CDockablePane::HitTest.md)|在使用者按一下滑鼠的窗格指定特定位置。|  
|`CDockablePane::IsAccessibilityCompatible`|內部使用。|  
|[CDockablePane::IsAutohideAllEnabled](../Topic/CDockablePane::IsAutohideAllEnabled.md)|指示停駐窗格和其他窗格在容器是否在自動隱藏模式可放置。|  
|[CDockablePane::IsAutoHideMode](../Topic/CDockablePane::IsAutoHideMode.md)|判斷是否在窗格自動隱藏模式。|  
|`CDockablePane::IsChangeState`|內部使用。|  
|[CDockablePane::IsDocked](../Topic/CDockablePane::IsDocked.md)|判斷目前是否停駐窗格。|  
|[CDockablePane::IsHideInAutoHideMode](../Topic/CDockablePane::IsHideInAutoHideMode.md)|請確定是自動隱藏模式窗格的行為，則可以呼叫 `ShowPane`顯示 \(或隱藏\)。|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](../Topic/CDockablePane::IsInFloatingMultiPaneFrameWnd.md)|指定窗格是否在多窗格框架視窗。|  
|[CDockablePane::IsResizable](../Topic/CDockablePane::IsResizable.md)|指定窗格是否可以調整大小。|  
|[CDockablePane::IsTabLocationBottom](../Topic/CDockablePane::IsTabLocationBottom.md)|指定索引標籤是否位於  窗格的頂端或底端。|  
|[CDockablePane::IsTracked](../Topic/CDockablePane::IsTracked.md)|指定窗格是否由使用者拖曳。|  
|[CDockablePane::IsVisible](../Topic/CDockablePane::IsVisible.md)|判斷目前窗格是否可見。|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/zh-tw/96110136-4f46-4764-8a76-3b4abaf77917)|內部使用。|  
|[CDockablePane::OnAfterChangeParent](../Topic/CDockablePane::OnAfterChangeParent.md)|呼叫框架，其在窗格的父代變更。  \(覆寫 [CPane::OnAfterChangeParent](../Topic/CPane::OnAfterChangeParent.md)\)。|  
|[CDockablePane::OnAfterDockFromMiniFrame](../Topic/CDockablePane::OnAfterDockFromMiniFrame.md)|呼叫框架，只有一個浮動停駐列停駐在框架視窗。|  
|[CDockablePane::OnBeforeChangeParent](../Topic/CDockablePane::OnBeforeChangeParent.md)|呼叫框架，其在窗格的父代會變更。  \(覆寫 [CPane::OnBeforeChangeParent](../Topic/CPane::OnBeforeChangeParent.md)\)。|  
|[CDockablePane::OnBeforeFloat](../Topic/CDockablePane::OnBeforeFloat.md)|呼叫框架時，窗格會浮動。  \(覆寫 [CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)\)。|  
|[CDockablePane::RemoveFromDefaultPaneDividier](../Topic/CDockablePane::RemoveFromDefaultPaneDividier.md)|在  窗格中，取消停駐時，架構會呼叫這個方法。|  
|[CDockablePane::ReplacePane](../Topic/CDockablePane::ReplacePane.md)|使用指定的窗格取代窗格。|  
|[CDockablePane::RestoreDefaultPaneDivider](../Topic/CDockablePane::RestoreDefaultPaneDivider.md)|在  窗格中，序列化還原預設窗格分割線，架構會呼叫這個方法。|  
|`CDockablePane::SaveState`|內部使用。|  
|`CDockablePane::Serialize`|序列化窗格。  \(覆寫 `CBasePane::Serialize`\)。|  
|[CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)|切換為可見和自動隱藏模式之間切換的停駐窗格。|  
|[CDockablePane::SetAutoHideParents](../Topic/CDockablePane::SetAutoHideParents.md)|設定 \[自動隱藏\] 按鈕和 \[自動隱藏\] 工具列上的  窗格中的。|  
|`CDockablePane::SetDefaultPaneDivider`|內部使用。|  
|[CDockablePane::SetLastPercentInPaneContainer](../Topic/CDockablePane::SetLastPercentInPaneContainer.md)|將窗格設定為可在容器中佔用空間百分比。|  
|`CDockablePane::SetResizeMode`|內部使用。|  
|[CDockablePane::SetRestoredDefaultPaneDivider](../Topic/CDockablePane::SetRestoredDefaultPaneDivider.md)|設定還原的預設窗格分割線。|  
|[CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md)|設定要建立的索引標籤式視窗的執行階段類別資訊，並在兩個窗格的停駐。|  
|[CDockablePane::ShowPane](../Topic/CDockablePane::ShowPane.md)|顯示或隱藏窗格。|  
|[CDockablePane::Slide](../Topic/CDockablePane::Slide.md)|顯示或隱藏具有滑動動畫的窗格哪些顯示只有在 \[自動隱藏模式時。|  
|[CDockablePane::ToggleAutoHide](../Topic/CDockablePane::ToggleAutoHide.md)|切換 \[自動隱藏模式。  \(覆寫 [CPane::ToggleAutoHide](../Topic/CPane::ToggleAutoHide.md) \)。|  
|[CDockablePane::UndockPane](../Topic/CDockablePane::UndockPane.md)|若要解除停駐主框架視窗或小型框架視窗容器的窗格。|  
|`CDockablePane::UnSetAutoHideMode`|內部使用。  若要設定自動隱藏模式，請使用 [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CDockablePane::CheckAutoHideCondition](../Topic/CDockablePane::CheckAutoHideCondition.md)|決定停駐窗格是否隱藏 \(在自動隱藏模式\)。|  
|[CDockablePane::CheckStopSlideCondition](../Topic/CDockablePane::CheckStopSlideCondition.md)|當自動隱藏停駐窗格應該停止滑動，決定。|  
|[CDockablePane::DrawCaption](../Topic/CDockablePane::DrawCaption.md)|繪製停駐窗格標題 \(移駐夾\)。|  
|[CDockablePane::OnPressButtons](../Topic/CDockablePane::OnPressButtons.md)|呼叫 `AFX_HTCLOSE` 除了和之外， `AFX_HTMAXBUTTON` 按鈕，當使用者按下的是標題按鈕。|  
|[CDockablePane::OnSlide](../Topic/CDockablePane::OnSlide.md)|呼叫由架構所呈現自動隱藏投影片效果時，窗格會顯示或隱藏。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDockablePane::m\_bDisableAnimation](../Topic/CDockablePane::m_bDisableAnimation.md)|指定可停駐窗格的自動隱藏動畫是否停用。|  
|[CDockablePane::m\_bHideInAutoHideMode](../Topic/CDockablePane::m_bHideInAutoHideMode.md)|在窗格中，自動隱藏模式時，判斷窗格的行為。|  
|[CDockablePane::m\_nSlideSteps](../Topic/CDockablePane::m_nSlideSteps.md)|會在自動隱藏模式時，顯示或隱藏，當指定窗格的動畫速度。|  
  
## 備註  
 `CDockablePane` 實作下列功能:  
  
-   停駐窗格加入至主框架視窗。  
  
-   切換窗格自動隱藏模式。  
  
-   附加一個窗格加入至索引標籤式視窗。  
  
-   浮動在小型框架視窗的窗格。  
  
-   停駐窗格為小型框架視窗浮動的另一個窗格。  
  
-   調整窗格。  
  
-   停駐窗格的載入和儲存狀態。  
  
    > [!NOTE]
    >  狀態資訊儲存在 Windows 登錄中。  
  
-   建立具有或不具有標頭的窗格。  標題可以有文字標籤，則可以填滿漸層色彩。  
  
-   拖曳  窗格中，在顯示窗格的內容時。  
  
-   拖曳  窗格中，在顯示拖曳矩形時。  
  
 若要使用停駐窗格在應用程式中，從 `CDockablePane` 類別衍生您的窗格的類別。  請將衍生物件到主框架視窗物件或物件拖曳至  視窗窗格控制您的執行個體。  然後，當您在主框架視窗時，的 `WM_CREATE` 訊息呼叫 [CDockablePane::Create](../Topic/CDockablePane::Create.md)[CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md) 方法或方法。  最後，呼叫 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)、 [CBasePane::DockPane](../Topic/CBasePane::DockPane.md)或 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)設定窗格物件。  
  
## 自訂秘訣  
 下列提示套用至 `CDockablePane` 物件:  
  
-   如果您呼叫非定位的兩個 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) ，可停駐窗格，指標至索引標籤式視窗在 `ppTabbedControlBar` 參數就會傳回。  您可以使用這個參數，您可以繼續加入索引標籤加入至索引標籤式視窗。  
  
-   由 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) 建立哪種索引標籤式窗格取決於 `pTabControlBarAttachTo` 參數的 `CDockablePane` 物件。  您可以呼叫 [CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md) 設定 `CDockablePane` 定義要建立的索引標籤式窗格。  當您第一次建立時， `CDockablePane`預設型別取決於 [CDockablePane::Create](../Topic/CDockablePane::Create.md)`dwTabbedStyle` 。  如果 `dwTabbedStyle` 是 AFX\_CBRS\_OUTLOOK\_TABS 預設型別為 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md);如果 `dwTabbedStyle` 是 AFX\_CBRS\_REGULAR\_TABS 預設型別為 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)。  
  
-   如果您要停駐的可停駐窗格至另一個，請呼叫方法。 [CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md) 才能呼叫這個方法之前，必須先修正原始窗格某處。  
  
-   成員變數 [CDockablePane::m\_bHideInAutoHideMode](../Topic/CDockablePane::m_bHideInAutoHideMode.md) 控制可停駐窗格如何在自動隱藏模式行為，當您呼叫 [CDockablePane::ShowPane](../Topic/CDockablePane::ShowPane.md)。  如果這個成員變數設定為 `TRUE`，可停駐窗格和它們的自動隱藏按鈕將會隱藏。  否則，會將它們簽入和將滑動。  
  
-   您可以設定 [CDockablePane::m\_bDisableAnimation](../Topic/CDockablePane::m_bDisableAnimation.md) 成員變數停用自動隱藏動畫至 `TRUE`。  
  
## 範例  
 您可以使用類別，在 `CDockablePane` 的各種方法。下列範例將示範如何設定 `CDockablePane` 物件。  範例示範如何啟用自動隱藏可停駐窗格的所有功能，可讓標題或移駐夾，起始自動隱藏模式，顯示 \[SQL\] 窗格將自動隱藏模式的窗格的動畫。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#27](../../mfc/codesnippet/CPP/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#28](../../mfc/codesnippet/CPP/cdockablepane-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## 需求  
 **標題:** afxDockablePane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)