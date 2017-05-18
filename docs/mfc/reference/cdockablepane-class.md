---
title: "CDockablePane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePane
- AFXDOCKABLEPANE/CDockablePane
- AFXDOCKABLEPANE/CDockablePane::CDockablePane
- AFXDOCKABLEPANE/CDockablePane::AttachToTabWnd
- AFXDOCKABLEPANE/CDockablePane::CalcFixedLayout
- AFXDOCKABLEPANE/CDockablePane::CanAcceptMiniFrame
- AFXDOCKABLEPANE/CDockablePane::CanAcceptPane
- AFXDOCKABLEPANE/CDockablePane::CanAutoHide
- AFXDOCKABLEPANE/CDockablePane::CanBeAttached
- AFXDOCKABLEPANE/CDockablePane::ConvertToTabbedDocument
- AFXDOCKABLEPANE/CDockablePane::CopyState
- AFXDOCKABLEPANE/CDockablePane::Create
- AFXDOCKABLEPANE/CDockablePane::CreateDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::CreateEx
- AFXDOCKABLEPANE/CDockablePane::CreateTabbedPane
- AFXDOCKABLEPANE/CDockablePane::DockPaneContainer
- AFXDOCKABLEPANE/CDockablePane::DockPaneStandard
- AFXDOCKABLEPANE/CDockablePane::DockToRecentPos
- AFXDOCKABLEPANE/CDockablePane::DockToWindow
- AFXDOCKABLEPANE/CDockablePane::EnableAutohideAll
- AFXDOCKABLEPANE/CDockablePane::EnableGripper
- AFXDOCKABLEPANE/CDockablePane::GetAHRestoredRect
- AFXDOCKABLEPANE/CDockablePane::GetAHSlideMode
- AFXDOCKABLEPANE/CDockablePane::GetCaptionHeight
- AFXDOCKABLEPANE/CDockablePane::GetDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::GetDockingStatus
- AFXDOCKABLEPANE/CDockablePane::GetDragSensitivity
- AFXDOCKABLEPANE/CDockablePane::GetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::GetTabArea
- AFXDOCKABLEPANE/CDockablePane::GetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::HasAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::HitTest
- AFXDOCKABLEPANE/CDockablePane::IsAutohideAllEnabled
- AFXDOCKABLEPANE/CDockablePane::IsAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsDocked
- AFXDOCKABLEPANE/CDockablePane::IsHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsInFloatingMultiPaneFrameWnd
- AFXDOCKABLEPANE/CDockablePane::IsResizable
- AFXDOCKABLEPANE/CDockablePane::IsTabLocationBottom
- AFXDOCKABLEPANE/CDockablePane::IsTracked
- AFXDOCKABLEPANE/CDockablePane::IsVisible
- AFXDOCKABLEPANE/CDockablePane::OnAfterChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnAfterDockFromMiniFrame
- AFXDOCKABLEPANE/CDockablePane::OnBeforeChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnBeforeFloat
- AFXDOCKABLEPANE/CDockablePane::RemoveFromDefaultPaneDividier
- AFXDOCKABLEPANE/CDockablePane::ReplacePane
- AFXDOCKABLEPANE/CDockablePane::RestoreDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideParents
- AFXDOCKABLEPANE/CDockablePane::SetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::SetRestoredDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::ShowPane
- AFXDOCKABLEPANE/CDockablePane::Slide
- AFXDOCKABLEPANE/CDockablePane::ToggleAutoHide
- AFXDOCKABLEPANE/CDockablePane::UndockPane
- AFXDOCKABLEPANE/CDockablePane::CheckAutoHideCondition
- AFXDOCKABLEPANE/CDockablePane::CheckStopSlideCondition
- AFXDOCKABLEPANE/CDockablePane::DrawCaption
- AFXDOCKABLEPANE/CDockablePane::OnPressButtons
- AFXDOCKABLEPANE/CDockablePane::OnSlide
- AFXDOCKABLEPANE/CDockablePane::m_bDisableAnimation
- AFXDOCKABLEPANE/CDockablePane::m_bHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::m_nSlideSteps
dev_langs:
- C++
helpviewer_keywords:
- CDockablePane class
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dea1f1ce66c0e9bedbe83109ab62055a4af2ebce
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdockablepane-class"></a>CDockablePane Class
實作可以停駐在固定位置或包含於索引標籤式窗格的窗格。  
  
## <a name="syntax"></a>語法  
  
```  
class CDockablePane : public CPane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDockablePane::CDockablePane](#cdockablepane)|建構並初始化 `CDockablePane` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDockablePane::AttachToTabWnd](#attachtotabwnd)|附加到另一個窗格的窗格。 這會建立索引標籤式的窗格。|  
|[CDockablePane::CalcFixedLayout](#calcfixedlayout)|傳回窗格矩形的大小。|  
|[CDockablePane::CanAcceptMiniFrame](#canacceptminiframe)|判斷是否為指定的迷你框架可以停駐窗格。|  
|[CDockablePane::CanAcceptPane](#canacceptpane)|判斷另一個窗格是否可停駐到目前的窗格。|  
|[CDockablePane::CanAutoHide](#canautohide)|判斷窗格是否支援自動隱藏模式。 (覆寫[CBasePane::CanAutoHide](../../mfc/reference/cbasepane-class.md#canautohide)。)|  
|[CDockablePane::CanBeAttached](#canbeattached)|判斷目前窗格是否可停駐到另一個窗格。|  
|[CDockablePane::ConvertToTabbedDocument](#converttotabbeddocument)|MDI 索引標籤式文件會將一或多個可停駐窗格。|  
|[CDockablePane::CopyState](#copystate)|複製可停駐窗格的狀態。|  
|[CDockablePane::Create](#create)|建立 Windows 控制項並將它附加`CDockablePane`物件。|  
|[CDockablePane::CreateDefaultPaneDivider](#createdefaultpanedivider)|建立框架視窗的停駐窗格的預設分割線。|  
|[CDockablePane::CreateEx](#createex)|建立 Windows 控制項並將它附加`CDockablePane`物件。|  
|[CDockablePane::CreateTabbedPane](#createtabbedpane)|從目前的窗格中建立索引標籤式的窗格。|  
|[CDockablePane::DockPaneContainer](#dockpanecontainer)|到窗格停駐容器。|  
|[CDockablePane::DockPaneStandard](#dockpanestandard)|使用大綱 （標準） 的停駐停駐窗格。|  
|`CDockablePane::DockToFrameWindow`|在內部使用。 若要停駐窗格，請使用[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)或[CDockablePane::DockToWindow](#docktowindow)。|  
|[CDockablePane::DockToRecentPos](#docktorecentpos)|窗格停駐於其預存的最新的停駐位置。|  
|[CDockablePane::DockToWindow](#docktowindow)|一個停駐窗格停駐於另一個停駐窗格。|  
|[CDockablePane::EnableAutohideAll](#enableautohideall)|啟用或停用此窗格，以及在容器中的其他窗格的 自動隱藏模式。|  
|[CDockablePane::EnableGripper](#enablegripper)|顯示或隱藏標題 （移駐夾）。|  
|[CDockablePane::GetAHRestoredRect](#getahrestoredrect)|指定窗格時自動隱藏模式中顯示的位置。|  
|[CDockablePane::GetAHSlideMode](#getahslidemode)|擷取窗格的 [自動隱藏投影片] 模式。|  
|`CDockablePane::GetAutoHideButton`|在內部使用。|  
|`CDockablePane::GetAutoHideToolBar`|在內部使用。|  
|[CDockablePane::GetCaptionHeight](#getcaptionheight)|傳回目前的標題高度。|  
|[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)|傳回預設窗格分割線，窗格的容器。|  
|[CDockablePane::GetDockingStatus](#getdockingstatus)|決定所提供的指標位置為基礎的停駐窗格的能力。|  
|[CDockablePane::GetDragSensitivity](#getdragsensitivity)|傳回停駐窗格拖曳的敏感度。|  
|[CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)|擷取其容器中的窗格所佔用的空間百分比。|  
|[CDockablePane::GetTabArea](#gettabarea)|擷取窗格 索引標籤區域。|  
|[CDockablePane::GetTabbedPaneRTC](#gettabbedpanertc)|傳回目前窗格停駐於另一個窗格時，會建立索引標籤式視窗的執行階段類別資訊。|  
|[CDockablePane::HasAutoHideMode](#hasautohidemode)|指定是否停駐窗格，即可切換自動隱藏模式。|  
|[CDockablePane::HitTest](#hittest)|在使用者按一下滑鼠的位置 窗格中指定的特定位置。|  
|`CDockablePane::IsAccessibilityCompatible`|在內部使用。|  
|[CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)|指出是否停駐窗格和其他容器中的所有窗格可以放在 自動隱藏模式。|  
|[CDockablePane::IsAutoHideMode](#isautohidemode)|決定是否自動隱藏模式中的窗格。|  
|`CDockablePane::IsChangeState`|在內部使用。|  
|[CDockablePane::IsDocked](#isdocked)|決定是否要停駐 [目前] 窗格。|  
|[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)|決定窗格處於自動隱藏模式中，如果它是顯示 （或隱藏） 藉由呼叫的行為`ShowPane`。|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定是否在多窗格框架視窗窗格。|  
|[CDockablePane::IsResizable](#isresizable)|指定是否可調整大小的窗格。|  
|[CDockablePane::IsTabLocationBottom](#istablocationbottom)|指定是否位於頂端或底部窗格的索引標籤。|  
|[CDockablePane::IsTracked](#istracked)|指定是否要由使用者拖曳窗格。|  
|[CDockablePane::IsVisible](#isvisible)|判斷目前窗格是否可見。|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917)|在內部使用。|  
|[CDockablePane::OnAfterChangeParent](#onafterchangeparent)|架構變更窗格的父代時呼叫。 (覆寫[CPane::OnAfterChangeParent](../../mfc/reference/cpane-class.md#onafterchangeparent)。)|  
|[CDockablePane::OnAfterDockFromMiniFrame](#onafterdockfromminiframe)|在框架視窗停駐浮動的停駐列時，由架構呼叫。|  
|[CDockablePane::OnBeforeChangeParent](#onbeforechangeparent)|架構 [] 窗格中的父代變更時呼叫。 (覆寫[CPane::OnBeforeChangeParent](../../mfc/reference/cpane-class.md#onbeforechangeparent)。)|  
|[CDockablePane::OnBeforeFloat](#onbeforefloat)|窗格即將浮點數時，由架構呼叫。 (覆寫[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|  
|[CDockablePane::RemoveFromDefaultPaneDividier](#removefromdefaultpanedividier)|窗格會被取消時，架構會呼叫這個方法。|  
|[CDockablePane::ReplacePane](#replacepane)|取代指定的窗格中的窗格。|  
|[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)|還原預設窗格分割線的窗格是還原序列化，架構會呼叫這個方法。|  
|`CDockablePane::SaveState`|在內部使用。|  
|`CDockablePane::Serialize`|將序列化的窗格。 (覆寫 `CBasePane::Serialize`。)|  
|[CDockablePane::SetAutoHideMode](#setautohidemode)|切換之間顯示停駐窗格和 自動隱藏模式。|  
|[CDockablePane::SetAutoHideParents](#setautohideparents)|設定自動隱藏] 按鈕和窗格的 [自動隱藏工具列。|  
|`CDockablePane::SetDefaultPaneDivider`|在內部使用。|  
|[CDockablePane::SetLastPercentInPaneContainer](#setlastpercentinpanecontainer)|設定容器中 窗格會佔用的空間的百分比。|  
|`CDockablePane::SetResizeMode`|在內部使用。|  
|[CDockablePane::SetRestoredDefaultPaneDivider](#setrestoreddefaultpanedivider)|設定 還原的預設窗格分割線。|  
|[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)|設定兩個窗格停駐在一起時，會建立索引標籤式視窗的執行階段類別資訊。|  
|[CDockablePane::ShowPane](#showpane)|顯示或隱藏窗格。|  
|[CDockablePane::Slide](#slide)|顯示或隱藏窗格中的，並顯示 窗格處於自動隱藏模式時，才滑動動畫。|  
|[CDockablePane::ToggleAutoHide](#toggleautohide)|切換自動隱藏模式。 (覆寫[CPane::ToggleAutoHide](../../mfc/reference/cpane-class.md#toggleautohide) 。)|  
|[CDockablePane::UndockPane](#undockpane)|取消停駐這些窗格中的，從主框架視窗或自視窗容器。|  
|`CDockablePane::UnSetAutoHideMode`|在內部使用。 若要設定自動隱藏模式，請使用[CDockablePane::SetAutoHideMode](#setautohidemode)|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDockablePane::CheckAutoHideCondition](#checkautohidecondition)|決定是否要停駐窗格隱藏 （在 自動隱藏模式）。|  
|[CDockablePane::CheckStopSlideCondition](#checkstopslidecondition)|決定何時自動隱藏停駐窗格應該停止滑動。|  
|[CDockablePane::DrawCaption](#drawcaption)|繪製停駐窗格標題 （移駐夾）。|  
|[CDockablePane::OnPressButtons](#onpressbuttons)|當使用者按下標題按鈕以外的其他呼叫`AFX_HTCLOSE`和`AFX_HTMAXBUTTON`按鈕。|  
|[CDockablePane::OnSlide](#onslide)|當要呈現的自動隱藏投影片效果 窗格顯示或隱藏架構呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)|指定是否要停用可停駐窗格的 自動隱藏動畫。|  
|[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)|[] 窗格處於自動隱藏模式時，請決定窗格的行為。|  
|[CDockablePane::m_nSlideSteps](#m_nslidesteps)|當它已經被指定動畫速度窗格的顯示或隱藏在自動隱藏模式中。|  
  
## <a name="remarks"></a>備註  
 `CDockablePane`會實作下列功能︰  
  
-   主框架視窗的停駐窗格。  
  
-   切換為 自動隱藏模式的窗格。  
  
-   附加為索引標籤式視窗的窗格。  
  
-   浮點自視窗中的窗格。  
  
-   到浮點自視窗中的另一個窗格的停駐窗格。  
  
-   調整窗格的大小。  
  
-   載入及儲存的停駐窗格的狀態。  
  
    > [!NOTE]
    >  狀態資訊會儲存至 Windows 登錄中。  
  
-   建立窗格，或沒有標題。 標題可以有文字標籤，並填入漸層色彩。  
  
-   在顯示窗格的內容時拖曳窗格  
  
-   同時顯示拖曳矩形拖曳窗格。  
  
 若要使用的停駐窗格在應用程式中，衍生您窗格類別從`CDockablePane`類別。 到主框架視窗物件或控制項的執行個體窗格的視窗物件，或是內嵌衍生的物件。 然後呼叫[CDockablePane::Create](#create)方法或[CDockablePane::CreateEx](#createex)方法，當您處理`WM_CREATE`主框架視窗中的訊息。 最後，設定窗格中的物件，藉由呼叫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)， [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane)，或[CDockablePane::AttachToTabWnd](#attachtotabwnd)。  
  
## <a name="customization-tips"></a>自訂秘訣  
 下列秘訣適用於`CDockablePane`物件︰  
  
-   如果您呼叫[CDockablePane::AttachToTabWnd](#attachtotabwnd)兩個非索引標籤，可停駐窗格的索引標籤式視窗的指標會傳回在`ppTabbedControlBar`參數。 您可以繼續使用這個參數，將索引標籤新增至索引標籤式視窗。  
  
-   所建立的索引標籤式窗格種[CDockablePane::AttachToTabWnd](#attachtotabwnd)取決於`CDockablePane`物件存放至`pTabControlBarAttachTo`參數。 您可以呼叫[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)若要設定的索引標籤式窗格類型`CDockablePane`會建立。 預設類型取決於`dwTabbedStyle`的[CDockablePane::Create](#create)當您第一次建立`CDockablePane`。 如果`dwTabbedStyle`是預設的類型是的 AFX_CBRS_OUTLOOK_TABS [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md); 如果`dwTabbedStyle`是預設的類型是的 AFX_CBRS_REGULAR_TABS [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)。  
  
-   如果您想要一個可停駐窗格固定到另一個，呼叫[CDockablePane::DockToWindow](#docktowindow)方法。 [原始] 窗格中，必須停駐地方之前呼叫這個方法。  
  
-   成員變數[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)控制項如何可停駐窗格行為中自動隱藏模式當您呼叫[CDockablePane::ShowPane](#showpane)。 如果這個成員變數設定為`TRUE`，將隱藏可停駐窗格和其自動隱藏按鈕。 否則，它們將投影片和縮小。  
  
-   您可以藉由設定停用自動隱藏動畫[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)成員變數來`TRUE`。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定`CDockablePane`使用各種方法的物件`CDockablePane`類別。 此範例說明如何啟用自動隱藏可停駐窗格的所有功能、 都啟用標題或移駐夾、 都啟用自動隱藏模式、 顯示窗格中，以及製作動畫的自動隱藏模式中的窗格。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&27;](../../mfc/codesnippet/cpp/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo #&28;](../../mfc/codesnippet/cpp/cdockablepane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxDockablePane.h  
  
##  <a name="attachtotabwnd"></a>CDockablePane::AttachToTabWnd  
 將目前窗格附加至目標窗格中，建立索引標籤式的窗格。  
  
```  
virtual CDockablePane* AttachToTabWnd(
    CDockablePane* pTabControlBarAttachTo,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bSetActive= TRUE,  
    CDockablePane** ppTabbedControlBar = NULL);  
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pTabControlBarAttachTo`  
 指定目前的窗格會將附加至 [目標] 窗格。 [目標] 窗格中必須是可停駐窗格。  
  
 [in] `dockMethod`  
 指定的停駐的方法。  
  
 [in] `bSetActive`  
 `TRUE`若要啟用索引標籤式的窗格之後附加作業。否則， `FALSE`。  
  
 [輸出] `ppTabbedControlBar`  
 包含附加作業所產生的索引標籤式的窗格。  
  
### <a name="return-value"></a>傳回值  
 指向目前窗格中，如果不是索引標籤式的窗格。否則附加作業所產生的索引標籤式窗格的指標。 傳回值是`NULL`如果無法連接目前的窗格，或如果發生錯誤。  
  
### <a name="remarks"></a>備註  
 一個可停駐窗格附加到另一個窗格，使用此方法時，發生下列情況︰  
  
1.  Framework 檢查是否目標窗格`pTabControlBarAttachTo`一般停駐窗格或它衍生自[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)。  
  
2.  如果目標是索引標籤式的窗格，架構就會將目前的窗格，以索引標籤。  
  
3.  如果目標是規則的停駐窗格，架構會建立索引標籤式的窗格。  
  
    -   這個架構會呼叫`pTabControlBarAttachTo->CreateTabbedPane`。 新的索引標籤式窗格的樣式取決於`m_pTabbedControlBarRTC`成員。 根據預設，這個成員會設定執行階段類別的[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)。 如果您傳遞`AFX_CBRS_OUTLOOK_TABS`樣式為`dwTabbedStyle`參數[CDockablePane::Create](#create)方法中，設定執行階段類別物件的執行階段類別為[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)。 您可以隨時變更新窗格的樣式來變更這個成員。  
  
    -   當這個方法會建立索引標籤式的窗格時，架構會取代指標`pTabControlBarAttachTo`（如果窗格處於停駐或浮動多自視窗） 與新的索引標籤式窗格的指標。  
  
    -   架構就會將`pTabControlBarAttachTo`做為第一個索引標籤的索引標籤式窗格的窗格。 然後架構就會將目前的窗格與第二個索引標籤。  
  
4.  如果目前的窗格衍生自`CBaseTabbedPane`，所有的索引標籤移到`pTabControlBarAttachTo`目前窗格則會損毀。 因此，請務必小心時呼叫這個方法，因為方法傳回時，[目前] 窗格的指標可能不正確。  
  
 如果建置停駐配置時，您可以附加至另一個的其中一個窗格，設定`dockMethod`到`DM_SHOW`。  
  
 您連接的另一個窗格之前，應該停駐的第一個窗格。  
  
##  <a name="calcfixedlayout"></a>CDockablePane::CalcFixedLayout  
 傳回窗格矩形的大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStretch`  
 未使用。  
  
 [in] `bHorz`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含窗格矩形的大小。  
  
##  <a name="canacceptminiframe"></a>CDockablePane::CanAcceptMiniFrame  
 判斷指定的迷你框架是否可以停駐窗格。  
  
```  
virtual BOOL CanAcceptMiniFrame(CPaneFrameWnd* pMiniFrame) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pMiniFrame`  
 指向 `CPaneFrameWnd` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`pMiniFrame`可停駐窗格，否則`FALSE`。  
  
##  <a name="canacceptpane"></a>CDockablePane::CanAcceptPane  
 判斷另一個窗格是否可停駐到目前的窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 指定目前窗格停駐窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以停駐此窗格中，指定的窗格，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法之前窗格即停駐到目前的窗格。  
  
 若要啟用或停用特定窗格停駐在衍生類別中的這個函式會覆寫。  
  
 根據預設，這個方法會傳回`TRUE`如果`pBar`或其父代為類型`CDockablePane`。  
  
##  <a name="canautohide"></a>CDockablePane::CanAutoHide  
 決定是否窗格可以顯示 自動隱藏。  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格可以顯示 自動隱藏。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 `CDockablePane::CanAutoHide`傳回`FALSE`在下列情況下︰  
  
-   窗格就會有沒有父代。  
  
-   連接管理員不允許自動隱藏的窗格。  
  
-   未停駐窗格。  
  
##  <a name="canbeattached"></a>CDockablePane::CanBeAttached  
 判斷目前窗格是否可停駐到另一個窗格。  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果另一個窗格或主框架視窗中，可以停駐可停駐窗格，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，此方法一律傳回`TRUE`。 若要啟用或停用停駐而不需呼叫衍生類別中的，這個方法會覆寫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="cdockablepane"></a>CDockablePane::CDockablePane  
 建構並初始化[CDockablePane](../../mfc/reference/cdockablepane-class.md)物件。  
  
```  
CDockablePane();
```  
  
### <a name="remarks"></a>備註  
 建構可停駐窗格物件之後，請呼叫[CDockablePane::Create](#create)或[CDockablePane::CreateEx](#createex)來建立它。  
  
##  <a name="converttotabbeddocument"></a>CDockablePane::ConvertToTabbedDocument  
 MDI 索引標籤式文件會將一或多個可停駐窗格。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActiveTabOnly`  
 當您轉換`CTabbedPane`，指定`TRUE`轉換作用中索引標籤。 指定`FALSE`轉換在窗格中的所有索引標籤。  
  
##  <a name="checkautohidecondition"></a>CDockablePane::CheckAutoHideCondition  
 決定是否停駐窗格為隱藏狀態 （也稱為自動隱藏模式）。  
  
```  
virtual BOOL CheckAutoHideCondition();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果隱藏條件符合時，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會使用計時器定期檢查是否隱藏自動隱藏可停駐窗格。 方法會傳回`TRUE`時不在使用中 窗格、 窗格不正在調整大小，將滑鼠指標不透過窗格。  
  
 如果符合所有先前的條件，架構會呼叫[CDockablePane::Slide](#slide)隱藏窗格。  
  
##  <a name="checkstopslidecondition"></a>CDockablePane::CheckStopSlideCondition  
 決定何時自動隱藏停駐窗格應該停止滑動。  
  
```  
virtual BOOL CheckStopSlideCondition(BOOL bDirection);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDirection`  
 `TRUE`如果窗格是可見的。`FALSE`如果隱藏的窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果符合的停止條件。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 時可停駐窗格設定為 自動隱藏模式時，架構會使用滑動效果顯示或隱藏窗格。 滑動窗格時，架構會呼叫此函式。 `CheckStopSlideCondition`傳回`TRUE`完全顯示 窗格時，或完全隱藏時。  
  
 覆寫這個方法在衍生類別來實作自訂的自動隱藏效果。  
  
##  <a name="copystate"></a>CDockablePane::CopyState  
 複製可停駐窗格的狀態。  
  
```  
virtual void CopyState(CDockablePane* pOrgBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pOrgBar`  
 指標，可停駐窗格。  
  
### <a name="remarks"></a>備註  
 `CDockablePane::CopyState`將複製的狀態`pOrgBar`到目前的窗格，藉由呼叫下列方法︰  
  
- [CPane::CopyState](../../mfc/reference/cpane-class.md#copystate)  
  
- [CDockablePane::GetAHRestoredRect](#getahrestoredrect)  
  
- [CDockablePane::GetAHSlideMode](#getahslidemode)  
  
- [CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)  
  
- [CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)  
  
##  <a name="create"></a>CDockablePane::Create  
 建立 Windows 控制項並將它附加[CDockablePane](../../mfc/reference/cdockablepane-class.md)物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);

 
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    CSize sizeDefault,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle = WS_CHILD|WS_VISIBLE|CBRS_TOP|CBRS_HIDE_INPLACE,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszCaption`  
 指定的視窗名稱。  
  
 [in][out]`pParentWnd`  
 指定父視窗。  
  
 [in] `rect`  
 在用戶端座標中指定的大小和位置 視窗中， `pParentWnd`。  
  
 [in] `bHasGripper`  
 `TRUE`若要建立窗格標題。否則， `FALSE`。  
  
 [in] `nID`  
 指定的子視窗的識別碼。 此值必須是唯一，如果您想要儲存此停駐窗格的停駐狀態。  
  
 [in] `dwStyle`  
 指定的視窗樣式屬性。  
  
 [in] `dwTabbedStyle`  
 指定使用者在此窗格的標題拖曳窗格時，會建立索引標籤式視窗的索引標籤式的樣式。  
  
 [in] `dwControlBarStyle`  
 指定其他的樣式屬性。  
  
 [in][out]`pContext`  
 指定建立視窗的內容。  
  
 [in] `lpszWindowName`  
 指定的視窗名稱。  
  
 [in] `sizeDefault`  
 指定視窗的大小。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功建立可停駐窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 建立 Windows 窗格並將它附加`CDockablePane`物件。  
  
 如果`dwStyle`視窗樣式`CBRS_FLOAT_MULTI`自視窗可以浮動旗標，與其他窗格內 [自] 視窗。 根據預設，停駐窗格可以只浮動個別。  
  
 如果`dwTabbedStyle`參數`AFX_CBRS_OUTLOOK_TABS`指定旗標，窗格建立 Outlook 樣式索引標籤式窗格，另一個窗格已附加至使用此窗格[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法。 根據預設，可停駐窗格建立類型的一般索引標籤式的窗格[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)。  
  
##  <a name="createdefaultpanedivider"></a>CDockablePane::CreateDefaultPaneDivider  
 建立框架視窗的停駐窗格的預設分割線。  
  
```  
static CPaneDivider* __stdcall CreateDefaultPaneDivider(
    DWORD dwAlignment,  
    CWnd* pParent,  
    CRuntimeClass* pSliderRTC = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 指定目標停駐窗格的主框架的端。 如果`dwAlignment`包含`CBRS_ALIGN_LEFT`或`CBRS_ALIGN_RIGHT`旗標，這個方法會建立垂直 ( `CPaneDivider::SS_VERT`) 分割線; 否則這個方法會建立水平 ( `CPaneDivider::SS_HORZ`) 分隔。  
  
 [in] `pParent`  
 父框架指標。  
  
 [in] `pSliderRTC`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 新建立的分割線，此方法傳回的指標或`NULL`如果分割線建立失敗。  
  
### <a name="remarks"></a>備註  
 `dwAlignment`可以是下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|框架視窗的工作區頂端所停駐窗格。|  
|`CBRS_ALIGN_BOTTOM`|框架視窗的工作區的底部所停駐窗格。|  
|`CBRS_ALIGN_LEFT`|正在停駐窗格的框架視窗工作區左緣。|  
|`CBRS_ALIGN_RIGHT`|框架視窗的用戶端區域的右側所停駐窗格。|  
  
##  <a name="createex"></a>CDockablePane::CreateEx  
 建立 Windows 控制項並將它附加[CDockablePane](../../mfc/reference/cdockablepane-class.md)物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwStyleEx`  
 指定新視窗的延伸的樣式屬性。  
  
 [in] `lpszCaption`  
 指定的視窗名稱。  
  
 [in][out]`pParentWnd`  
 指定父視窗。  
  
 [in] `rect`  
 在用戶端座標中指定的大小和位置 視窗中， `pParentWnd`。  
  
 [in] `bHasGripper`  
 `TRUE`若要建立窗格標題。否則， `FALSE`。  
  
 [in] `nID`  
 指定的子視窗的識別碼。 此值必須是唯一，如果您想要儲存此停駐窗格的停駐狀態。  
  
 [in] `dwStyle`  
 指定的視窗樣式屬性。  
  
 [in] `dwTabbedStyle`  
 指定使用者在此窗格的標題拖曳窗格時，會建立索引標籤式視窗的索引標籤式的樣式。  
  
 [in] `dwControlBarStyle`  
 指定的其他樣式屬性。  
  
 [in][out]`pContext`  
 指定建立視窗的內容。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功建立可停駐窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 建立 Windows 窗格並將它附加`CDockablePane`物件。  
  
 如果`dwStyle`視窗樣式`CBRS_FLOAT_MULTI`自視窗可以浮動旗標，與其他窗格內 [自] 視窗。 根據預設，停駐窗格可以只浮動個別。  
  
 如果`dwTabbedStyle`參數`AFX_CBRS_OUTLOOK_TABS`指定旗標，窗格建立 Outlook 樣式索引標籤式窗格，另一個窗格已附加至使用此窗格[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法。 根據預設，可停駐窗格建立類型的一般索引標籤式的窗格[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)。  
  
##  <a name="createtabbedpane"></a>CDockablePane::CreateTabbedPane  
 從目前的窗格中建立索引標籤式的窗格。  
  
```  
virtual CTabbedPane* CreateTabbedPane();
```  
  
### <a name="return-value"></a>傳回值  
 新的索引標籤式的窗格中，或`NULL`建立作業失敗。  
  
### <a name="remarks"></a>備註  
 建立索引標籤式的窗格來取代此窗格時，架構會呼叫這個方法。 如需詳細資訊，請參閱[CDockablePane::AttachToTabWnd](#attachtotabwnd)。  
  
 覆寫衍生的類別，即可自訂如何索引標籤式的窗格中，這個方法會建立並初始化。  
  
 索引標籤式的窗格根據儲存在執行階段類別資訊建立`m_pTabbedControlBarRTC`成員，這由初始化[CDockablePane::CreateEx](#createex)方法。  
  
##  <a name="dockpanecontainer"></a>CDockablePane::DockPaneContainer  
 到窗格停駐容器。  
  
```  
virtual BOOL DockPaneContainer(
    CPaneContainerManager& barContainerManager,  
    DWORD dwAlignment,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in] `barContainerManager`  
 容器管理員停駐容器的參考。  
  
 [in] `dwAlignment`  
 `DWORD`指定的容器會停駐的窗格的側邊。  
  
 [in] `dockMethod`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果容器已順利停駐窗格。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 `dwAlignment`可以是下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|容器是被停駐窗格的頂端。|  
|`CBRS_ALIGN_BOTTOM`|窗格的底部所停駐容器。|  
|`CBRS_ALIGN_LEFT`|容器是停駐窗格的左邊。|  
|`CBRS_ALIGN_RIGHT`|容器是停駐窗格的右邊。|  
  
##  <a name="dockpanestandard"></a>CDockablePane::DockPaneStandard  
 使用大綱 （標準） 的停駐停駐窗格。  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>參數  
 [in] `bWasDocked`  
 方法傳回時，這個值包含`TRUE`窗格已順利停駐; 否則如果它包含`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 如果索引標籤式視窗中，已停駐窗格或建立索引標籤式的視窗停駐的結果，這個方法會傳回索引標籤式視窗的指標。 如果窗格卻成功停駐，則這個方法會傳回`this`指標。 如果連接失敗，則這個方法會傳回`NULL`。  
  
##  <a name="docktorecentpos"></a>CDockablePane::DockToRecentPos  
 窗格停駐於其預存的停駐位置。  
  
```  
BOOL CDockablePane::DockToRecentPos();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功停駐窗格。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 可停駐窗格最近停駐資訊儲存在[CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)物件。  
  
##  <a name="docktowindow"></a>CDockablePane::DockToWindow  
 一個停駐窗格停駐於另一個停駐窗格。  
  
```  
virtual BOOL DockToWindow(
    CDockablePane* pTargetWindow,  
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pTargetWindow`  
 指定停駐此窗格可停駐窗格。  
  
 [in] `dwAlignment`  
 指定 [] 窗格的停駐對齊方式。 可能是其中一個 CBRS_ALIGN_LEFT、 CBRS_ALIGN_TOP、 CBRS_ALIGN_RIGHT、 CBRS_ALIGN_BOTTOM 或 CBRS_ALIGN_ANY。 （在 afxres.h 中定義）。  
  
 [in] `lpRect`  
 指定停駐窗格的矩形。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 停駐窗格，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，將停駐窗格的另一個窗格具有所指定的對齊方式`dwAlignment`。  
  
##  <a name="drawcaption"></a>CDockablePane::DrawCaption  
 繪製標題的停駐窗格 （也稱為 「 移駐夾 」）。  
  
```  
virtual void DrawCaption(
    CDC* pDC,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 表示用於繪圖的裝置內容。  
  
 [in] `rectCaption`  
 指定週框窗格的標題。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以繪製可停駐窗格的標題。  
  
 覆寫這個方法在衍生類別來自訂標題的外觀。  
  
##  <a name="enableautohideall"></a>CDockablePane::EnableAutohideAll  
 啟用或停用自動隱藏模式針對此窗格和其他容器中的窗格。  
  
```  
void EnableAutohideAll(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用自動隱藏所有的功能，可停駐窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當使用者與保留`Ctrl`索引鍵並按一下 固定 按鈕以切換至 自動隱藏模式中，相同的容器中所有其他窗格的窗格也會切換成 自動隱藏模式。  
  
 呼叫這個方法時`bEnable`設`FALSE`停用此功能，為特定的窗格。  
  
##  <a name="enablegripper"></a>CDockablePane::EnableGripper  
 顯示或隱藏標題 （也稱為 「 移駐夾 」）。  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用標題。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當此架構會建立可停駐窗格時，並沒有**WS_STYLE**即使指定的視窗樣式。 這表示窗格的標題是架構，由非工作區，但此區域不同於標準的視窗標題。  
  
 您可以顯示或隱藏標題在任何時間。 當面板會加入成為的索引標籤，為索引標籤式視窗或窗格浮動自視窗中，架構會隱藏標題。  
  
##  <a name="getahrestoredrect"></a>CDockablePane::GetAHRestoredRect  
 指定在自動隱藏模式中窗格的位置。  
  
```  
CRect GetAHRestoredRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CRect`物件，其中包含窗格的位置，自動隱藏模式中時。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getahslidemode"></a>CDockablePane::GetAHSlideMode  
 擷取窗格的 自動隱藏投影片模式。  
  
```  
virtual UINT GetAHSlideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`UINT`指定窗格的 自動隱藏投影片模式。 傳回值可以是`AFX_AHSM_MOVE`或`AFX_AHSM_STRETCH`，但只會使用實作`AFX_AHSM_MOVE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcaptionheight"></a>CDockablePane::GetCaptionHeight  
 傳回高度，單位為像素目前的標題。  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 標題，單位為像素的高度。  
  
### <a name="remarks"></a>備註  
 標題高度為 0，如果已隱藏標題[CDockablePane::EnableGripper](#enablegripper)方法，或如果窗格沒有標題。  
  
##  <a name="getdefaultpanedivider"></a>CDockablePane::GetDefaultPaneDivider  
 傳回預設窗格分割線，窗格的容器。  
  
```  
CPaneDivider* GetDefaultPaneDivider() const;  
```  
  
### <a name="return-value"></a>傳回值  
 有效[CPaneDivider](../../mfc/reference/cpanedivider-class.md)可停駐窗格停駐於主框架視窗中，如果物件或`NULL`可停駐窗格未停駐或浮動。  
  
### <a name="remarks"></a>備註  
 如需窗格分割線的詳細資訊，請參閱[CPaneDivider 類別](../../mfc/reference/cpanedivider-class.md)。  
  
##  <a name="getdockingstatus"></a>CDockablePane::GetDockingStatus  
 決定所提供的指標位置為基礎的停駐窗格的能力。  
  
```  
virtual AFX_CS_STATUS GetDockingStatus(
    CPoint pt,  
    int nSensitivity);
```  
  
### <a name="parameters"></a>參數  
 [in] `pt`  
 螢幕座標中指標的位置。  
  
 [in] `nSensitivity`  
 距離，單位為像素矩形邊緣指標必須在啟用停駐。  
  
### <a name="return-value"></a>傳回值  
 其中一個狀態如下︰  
  
|`AFX_CS_STATUS` 值|意義|  
|---------------------------|-------------|  
|`CS_NOTHING`|指標不是透過停駐位置。 架構不會不停駐窗格。|  
|`CS_DOCK_IMMEDIATELY`|滑鼠指標位於停駐位置中的即時模式 ([] 窗格中會使用`DT_IMMEDIATE`停駐模式)。 架構立即停駐窗格。|  
|`CS_DELAY_DOCK`|指標是透過與另一個停駐窗格或主要畫面格的邊緣的停駐位置。 架構的延遲之後停駐窗格。 請參閱 < 備註 > 一節，如需有關這個延遲現象。|  
|`CS_DELAY_DOCK_TO_TAB`|透過停駐在索引標籤式視窗中，窗格會停駐位置位於指標。 會發生這種情況是當滑鼠指標位於，另一個停駐窗格的標題或索引標籤式窗格的索引標籤區域上。|  
  
### <a name="remarks"></a>備註  
 架構會呼叫此方法以處理停駐浮動窗格。  
  
 浮動工具列或停駐窗格使用`DT_IMMEDIATE`停駐模式下，架構會延遲停駐命令，讓使用者移動超出工作區的父框架的視窗停駐發生之前。 延遲的時間長度以毫秒為單位，並且受到[CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock)資料成員... 預設值的[CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock)為 200。 此行為模擬的停駐行為[!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)]2007年。  
  
 用於延遲停駐狀態 (`CS_DELAY_DOCK`和`CS_DELAY_DOCK_TO_TAB`)，此架構不會執行停駐直到使用者放開滑鼠按鈕。 如果使用窗格`DT_STANDARD`停駐模式下，架構會顯示矩形投影停駐位置。 如果使用窗格`DT_SMART`停駐模式下，架構會顯示智慧停駐標記與半透明矩形投影停駐位置。 若要指定您窗格停駐的模式，請呼叫[CBasePane::SetDockingMode](../../mfc/reference/cbasepane-class.md#setdockingmode)方法。 如需智慧停駐的詳細資訊，請參閱[CDockingManager::GetSmartDockingParams](../../mfc/reference/cdockingmanager-class.md#getsmartdockingparams)。  
  
##  <a name="getdragsensitivity"></a>CDockablePane::GetDragSensitivity  
 傳回停駐窗格拖曳的敏感度。  
  
```  
static const CSize& GetDragSensitivity();
```  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含的寬度和高度，單位為像素矩形拖曳點為中心。 才滑鼠指標移到這個矩形之外，會開始拖曳作業。  
  
##  <a name="getlastpercentinpanecontainer"></a>CDockablePane::GetLastPercentInPaneContainer  
 擷取在其容器中 窗格會佔用的空間百分比 ( [CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md))。  
  
```  
int GetLastPercentInPaneContainer() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `int` ，指定在其容器中 窗格會佔用的空間百分比。  
  
### <a name="remarks"></a>備註  
 容器會調整它的版面配置時，會使用這個方法。  
  
##  <a name="gettabarea"></a>CDockablePane::GetTabArea  
 擷取窗格 索引標籤區域。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `rectTabAreaTop`  
 `GetTabArea`如果索引標籤位於頂端的窗格中填入索引標籤區域此變數。 如果索引標籤底端的窗格中，此變數會填入空的矩形。  
  
 [in] `rectTabAreaBottom`  
 `GetTabArea`如果索引標籤位於底部窗格中填入索引標籤區域此變數。 如果索引標籤頂端的窗格中，此變數會填入空的矩形。  
  
### <a name="remarks"></a>備註  
 這個方法只能用於類別衍生自`CDockablePane`和有索引標籤。 如需詳細資訊，請參閱[CTabbedPane::GetTabArea](../../mfc/reference/ctabbedpane-class.md#gettabarea)和[CMFCOutlookBar::GetTabArea](../../mfc/reference/cmfcoutlookbar-class.md#gettabarea)。  
  
##  <a name="gettabbedpanertc"></a>CDockablePane::GetTabbedPaneRTC  
 傳回目前窗格停駐於另一個窗格時，會建立索引標籤式視窗的執行階段類別資訊。  
  
```  
CRuntimeClass* GetTabbedPaneRTC() const;  
```  
  
### <a name="return-value"></a>傳回值  
 可停駐窗格執行階段類別資訊。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取以動態方式建立的索引標籤式窗格的執行階段類別資訊。 這可能是當使用者將一個窗格拖曳到另一個窗格中，標題，或如果您呼叫[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法來以程式設計方式建立從兩個可停駐窗格的 索引標籤式的窗格。  
  
 您可以藉由呼叫設定執行階段類別資訊[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)方法。  
  
##  <a name="hasautohidemode"></a>CDockablePane::HasAutoHideMode  
 指定是否停駐窗格，即可切換自動隱藏模式。  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以切換自動隱藏模式，可停駐窗格否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 若要停用特定的可停駐窗格的 自動隱藏模式的衍生類別中，這個方法會覆寫。  
  
##  <a name="hittest"></a>CDockablePane::HitTest  
 在使用者按一下滑鼠的位置 窗格中指定的位置。  
  
```  
virtual int HitTest(
    CPoint point,  
    BOOL bDetectCaption = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指定要測試的點。  
  
 [in] `bDetectCaption`  
 `TRUE`如果`HTCAPTION`應該傳回點是否在窗格的標題; 否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
- `HTNOWHERE`如果`point`不是處於可停駐窗格。  
  
- `HTCLIENT`如果`point`可停駐窗格的工作區中。  
  
- `HTCAPTION`如果`point`可停駐窗格的標題區域中。  
  
- `AFX_HTCLOSE`如果`point`是 [關閉] 按鈕。  
  
- `HTMAXBUTTON`如果`point`上釘選按鈕。  
  
##  <a name="isautohideallenabled"></a>CDockablePane::IsAutohideAllEnabled  
 指出是否停駐窗格和容器中的所有其他窗格，即可切換自動隱藏模式。  
  
```  
virtual BOOL IsAutohideAllEnabled() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可停駐窗格中，並在容器中，所有其他窗格，即可切換自動隱藏模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用者按一下 [停駐的 pin] 按鈕時保留啟用自動隱藏模式**Ctrl**金鑰  
  
 若要啟用或停用此行為，請呼叫[CDockablePane::EnableAutohideAll](#enableautohideall)方法。  
  
##  <a name="isautohidemode"></a>CDockablePane::IsAutoHideMode  
 決定是否自動隱藏模式中的窗格。  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可停駐窗格處於自動隱藏模式;否則， `FALSE`。  
  
##  <a name="isdocked"></a>CDockablePane::IsDocked  
 決定是否要停駐 [目前] 窗格。  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可停駐窗格不屬於自視窗，或在另一個窗格自視窗中浮動。 `FALSE`如果窗格是自視窗的子系，而且不屬於 [自] 視窗中的其他窗格。  
  
### <a name="remarks"></a>備註  
 若要判斷是否停駐於主框架視窗的窗格中，呼叫[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)。 如果此方法會傳回非 NULL 指標，窗格即停駐於主框架視窗中。  
  
##  <a name="ishideinautohidemode"></a>CDockablePane::IsHideInAutoHideMode  
 決定窗格處於自動隱藏模式中，如果它是顯示 （或隱藏） 藉由呼叫的行為[CDockablePane::ShowPane](#showpane)。  
  
```  
virtual BOOL IsHideInAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果應該在 自動隱藏模式，隱藏可停駐窗格，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 自動隱藏模式中可停駐窗格時，其行為方式當您呼叫`ShowPane`來隱藏或顯示 窗格。 這種行為會受到靜態成員[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)。 如果這個成員是`TRUE`，可停駐窗格及其相關的自動隱藏工具列或自動隱藏 按鈕會隱藏或顯示當您呼叫`ShowPane`。 否則，可停駐窗格是啟用或停用，而且其相關的自動隱藏工具列或 [自動隱藏] 按鈕一律會顯示。  
  
 若要變更個別窗格的預設行為的衍生類別中，這個方法會覆寫。  
  
 `m_bHideInAutoHideMode` 的預設值為 `FALSE`。  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CDockablePane::IsInFloatingMultiPaneFrameWnd  
 指定是否在多窗格框架視窗窗格 ( [CMultiPaneFrameWnd 類別](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格中的多窗格框架視窗。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isresizable"></a>CDockablePane::IsResizable  
 指定是否可調整大小的窗格。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果是可調整大小;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 預設情況下，可停駐窗格都是可調整大小。 若要避免重新調整大小，這個方法在衍生類別中的覆寫，並傳回`FALSE`。 請注意，`FALSE`值會導致失敗`ASSERT`中[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)。 使用[CDockingManager::AddPane](../../mfc/reference/cdockingmanager-class.md#addpane)改為停駐在父範圍內的窗格。  
  
 無法調整大小的窗格可以兩者都不浮動，也不輸入自動隱藏模式，都位於父框架的外部邊緣。  
  
##  <a name="istablocationbottom"></a>CDockablePane::IsTabLocationBottom  
 指定是否位於頂端或底部窗格的索引標籤。  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果在底部窗格中，位於索引標籤`FALSE`如果索引標籤位於窗格的頂端。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CTabbedPane::IsTabLocationBottom](../../mfc/reference/ctabbedpane-class.md#istablocationbottom)。  
  
##  <a name="istracked"></a>CDockablePane::IsTracked  
 指定使用者是否正在移動的窗格。  
  
```  
BOOL IsTracked() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果正在移動的窗格。否則， `FALSE`。  
  
##  <a name="isvisible"></a>CDockablePane::IsVisible  
 判斷目前窗格是否可見。  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可停駐窗格是可見的。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷可停駐窗格是否可見。 您可以使用這個方法，而不是呼叫[CWnd::IsWindowVisible](../../mfc/reference/cwnd-class.md#iswindowvisible)或測試`WS_VISIBLE`樣式。 傳回的可見性狀態取決於是否啟用或停用自動隱藏模式以及值[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)屬性。  
  
 如果可停駐窗格處於自動隱藏模式和`IsHideInAutoHideMode`傳回`FALSE`的可見性狀態永遠是`FALSE`。  
  
 如果可停駐窗格處於自動隱藏模式和`IsHideInAutoHideMode`傳回`TRUE`的可見性狀態相關的自動隱藏工具列的可見性狀態而定。  
  
 如果可停駐窗格不是自動隱藏模式中，有的可見性狀態由[CBasePane::IsVisible](../../mfc/reference/cbasepane-class.md#isvisible)方法。  
  
##  <a name="m_bdisableanimation"></a>CDockablePane::m_bDisableAnimation  
 指定是否要停用自動隱藏動畫的可停駐窗格。  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableAnimation;  
```  
  
##  <a name="m_bhideinautohidemode"></a>CDockablePane::m_bHideInAutoHideMode  
 [] 窗格處於自動隱藏模式時，請決定窗格的行為。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideInAutoHideMode;  
```  
  
### <a name="remarks"></a>備註  
 這個值會影響應用程式中的所有停駐窗格。  
  
 如果您將這個成員設定為`TRUE`，隱藏或顯示相關的自動隱藏工具列與按鈕，當您呼叫可停駐窗格[CDockablePane::ShowPane](#showpane)。  
  
 如果您將這個成員設定為`FALSE`，可停駐窗格會啟用或停用當您呼叫[CDockablePane::ShowPane](#showpane)。  
  
##  <a name="m_nslidesteps"></a>CDockablePane::m_nSlideSteps  
 自動隱藏模式中時，請指定窗格的動畫速度。  
  
```  
AFX_IMPORT_DATA static int m_nSlideSteps;  
```  
  
### <a name="remarks"></a>備註  
 更快速的動畫效果，請降低此值。 較慢的動畫效果，增加此值。  
  
##  <a name="onafterchangeparent"></a>CDockablePane::OnAfterChangeParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndOldParent`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onafterdockfromminiframe"></a>CDockablePane::OnAfterDockFromMiniFrame  
 在框架視窗停駐浮動的停駐列時，由架構呼叫。  
  
```  
virtual void OnAfterDockFromMiniFrame();
```  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法沒有作用。  
  
##  <a name="onbeforechangeparent"></a>CDockablePane::OnBeforeChangeParent  
 變更窗格的父之前，架構會呼叫這個方法。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndNewParent`  
 新的父視窗的指標。  
  
 [in] `bDelay`  
 `BOOL`指定是否要延遲重新計算停駐配置，如果未停駐窗格。 如需詳細資訊，請參閱[CDockablePane::UndockPane](#undockpane)。  
  
### <a name="remarks"></a>備註  
 如果窗格即停駐和停駐不允許新的父項，這個方法可以卸除 窗格。  
  
 如果窗格正在轉換為索引標籤式文件時，這個方法會儲存其最新的停駐位置。 架構會使用最新的停駐位置停駐狀態轉換時，還原窗格的位置。  
  
##  <a name="onbeforefloat"></a>CDockablePane::OnBeforeFloat  
 架構之前呼叫這個方法窗格轉換成浮動狀態。  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectFloat`  
 處於浮動狀態時，指定的位置和大小的窗格。  
  
 [in] `dockMethod`  
 指定的停駐的方法。 請參閱[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)的可能值的清單。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以浮動窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 窗格即將浮點數時，架構會呼叫這個方法。 如果您想要執行任何處理之前會浮動在窗格中，您可以覆寫這個方法在衍生類別中。  
  
##  <a name="onpressbuttons"></a>CDockablePane::OnPressButtons  
 當使用者按下標題按鈕以外的其他呼叫`AFX_HTCLOSE`和`AFX_HTMAXBUTTON`按鈕。  
  
```  
virtual void OnPressButtons(UINT nHit);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHit`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
 如果您將自訂按鈕加入可停駐窗格的標題，覆寫這個方法，以接收通知，當使用者按下按鈕時。  
  
##  <a name="onslide"></a>CDockablePane::OnSlide  
 以動畫顯示 窗格中自動隱藏模式時架構呼叫。  
  
```  
virtual void OnSlide(BOOL bSlideOut);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSlideOut`  
 `TRUE`若要顯示窗格。`FALSE`隱藏窗格。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別來實作自訂的自動隱藏效果。  
  
##  <a name="removefromdefaultpanedividier"></a>CDockablePane::RemoveFromDefaultPaneDividier  
 窗格會被取消時，架構會呼叫這個方法。  
  
```  
void RemoveFromDefaultPaneDividier();
```  
  
### <a name="remarks"></a>備註  
 這個方法設定為預設的窗格分割線`NULL`並移除其容器的窗格。  
  
##  <a name="replacepane"></a>CDockablePane::ReplacePane  
 取代指定的窗格中的窗格。  
  
```  
BOOL ReplacePane(
    CDockablePane* pBarToReplaceWith,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bRegisterWithFrame = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBarToReplaceWith`  
 指標，可停駐窗格。  
  
 [in] `dockMethod`  
 未使用。  
  
 [in] `bRegisterWithFrame`  
 如果`TRUE`，新窗格向之父系的舊窗格停駐的管理員。 舊窗格窗格停駐的管理員所維護的清單中的索引處插入新的窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果取代成功。否則， `FALSE`。  
  
##  <a name="restoredefaultpanedivider"></a>CDockablePane::RestoreDefaultPaneDivider  
 窗格會還原序列化時，架構會呼叫這個方法，以還原預設窗格分割線。  
  
```  
void RestoreDefaultPaneDivider();
```  
  
### <a name="remarks"></a>備註  
 還原的預設窗格分割線取代目前的預設窗格分割線，如果存在的話。  
  
##  <a name="setautohidemode"></a>CDockablePane::SetAutoHideMode  
 切換之間顯示停駐窗格和 自動隱藏模式。  
  
```  
virtual CMFCAutoHideBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMode`  
 `TRUE`若要啟用自動隱藏模式;`FALSE`來啟用規則的停駐模式。  
  
 [in] `dwAlignment`  
 指定要建立 [自動隱藏] 窗格的對齊方式。  
  
 [in][out]`pCurrAutoHideBar`  
 目前的自動隱藏工具列指標。 可以是`NULL`。  
  
 [in] `bUseTimer`  
 指定是否要使用自動隱藏效果，當使用者切換到 自動隱藏模式的窗格，或是立即隱藏窗格。  
  
### <a name="return-value"></a>傳回值  
 自動隱藏工具列切換為 自動隱藏模式已建立或`NULL`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，當使用者按一下 [固定] 按鈕，切換到自動隱藏模式或一般停駐模式的可停駐窗格。  
  
 呼叫這個方法來以程式設計方式切換自動隱藏模式可停駐窗格。 窗格必須可停駐於主框架視窗 ( [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)必須傳回有效指標[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。  
  
##  <a name="setautohideparents"></a>CDockablePane::SetAutoHideParents  
 設定自動隱藏] 按鈕和窗格的 [自動隱藏工具列。  
  
```  
void SetAutoHideParents(
    CMFCAutoHideBar* pToolBar,  
    CMFCAutoHideButton* pBtn);
```  
  
### <a name="parameters"></a>參數  
 [in] `pToolBar`  
 自動隱藏工具列的指標。  
  
 [in] `pBtn`  
 自動隱藏 按鈕的指標。  
  
##  <a name="setlastpercentinpanecontainer"></a>CDockablePane::SetLastPercentInPaneContainer  
 設定在其容器中 窗格會佔用的空間百分比。  
  
```  
void SetLastPercentInPaneContainer(int n);
```  
  
### <a name="parameters"></a>參數  
 [in] `n`  
 `int` ，指定在其容器中 窗格會佔用的空間百分比。  
  
### <a name="remarks"></a>備註  
 架構會調整窗格，即可使用新的值，重新計算配置。  
  
##  <a name="setrestoreddefaultpanedivider"></a>CDockablePane::SetRestoredDefaultPaneDivider  
 設定 還原的預設窗格分割線。  
  
```  
void SetRestoredDefaultPaneDivider(HWND hRestoredSlider);
```  
  
### <a name="parameters"></a>參數  
 [in] `hRestoredSlider`  
 窗格分割線 （滑桿） 控制代碼。  
  
### <a name="remarks"></a>備註  
 窗格會還原序列化時，會獲得還原的預設的窗格分割線。 如需詳細資訊，請參閱[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)。  
  
##  <a name="settabbedpanertc"></a>CDockablePane::SetTabbedPaneRTC  
 設定兩個窗格停駐在一起時，會建立索引標籤式視窗的執行階段類別資訊。  
  
```  
void SetTabbedPaneRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pRTC`  
 索引標籤式窗格執行階段類別資訊。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來設定動態建立的索引標籤式窗格的執行階段類別資訊。 這可能是當使用者將一個窗格拖曳到另一個窗格中，標題，或如果您呼叫[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法來以程式設計方式建立從兩個可停駐窗格的 索引標籤式的窗格。  
  
 根據設定的預設執行階段類別`dwTabbedStyle`參數[CDockablePane::Create](#create)和[CDockablePane::CreateEx](#createex)。 若要自訂新的索引標籤式的窗格，請從下列類別之一來衍生您的類別︰  
  
- [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)  
  
- [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)  
  
- [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 然後，呼叫這個方法時對其執行階段類別資訊的指標。  
  
##  <a name="showpane"></a>CDockablePane::ShowPane  
 顯示或隱藏窗格。  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 `TRUE`若要顯示窗格。`FALSE`隱藏窗格。  
  
 [in] `bDelay`  
 `TRUE`若要延遲調整停駐的版面配置。`FALSE`立即調整停駐配置。  
  
 [in] `bActivate`  
 `TRUE`若要啟動窗格時顯示。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，而不是[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)時顯示或隱藏可停駐窗格。  
  
##  <a name="slide"></a>CDockablePane::Slide  
 動畫處於自動隱藏模式的窗格。  
  
```  
virtual void Slide(
    BOOL bSlideOut,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSlideOut`  
 `TRUE`若要顯示窗格。`FALSE`隱藏窗格。  
  
 [in] `bUseTimer`  
 `TRUE`若要顯示或隱藏窗格中的，使用 [自動隱藏] 效果;`FALSE`以顯示或隱藏窗格立即。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以動畫顯示處於自動隱藏模式的窗格。  
  
 這個方法會使用`CDockablePane::m_nSlideDefaultTimeOut`值，以判斷投影片效果的逾時。 逾時的預設值為 1。 如果您自訂的自動隱藏演算法，修改此成員以變更逾時的時間。  
  
##  <a name="toggleautohide"></a>CDockablePane::ToggleAutoHide  
 顯示的 之間一定窗格和 自動隱藏模式切換。  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>備註  
 這個方法會切換窗格的 自動隱藏模式藉由呼叫[CDockablePane::SetAutoHideMode](#setautohidemode)。  
  
##  <a name="undockpane"></a>CDockablePane::UndockPane  
 取消停駐這些窗格中的，從主框架視窗或自視窗容器。  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDelay`  
 `TRUE`若要延遲計算停駐的版面配置。`FALSE`立即重新計算停駐配置。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來取消停駐窗格的主框架視窗或從多個自視窗容器 （在單一自視窗與其他窗格浮動窗格）。  
  
 執行不會執行的任何外部作業之前，您必須卸除窗格[CDockingManager](../../mfc/reference/cdockingmanager-class.md)。 例如，您必須卸除它以程式設計方式從某個位置移到另一個窗格。  
  
 架構會自動取消停駐這些窗格之前終結。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane 類別](../../mfc/reference/cpane-class.md)

