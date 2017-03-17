---
title: "CBasePane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBasePane
- AFXBASEPANE/CBasePane
- AFXBASEPANE/CBasePane::AccNotifyObjectFocusEvent
- AFXBASEPANE/CBasePane::AddPane
- AFXBASEPANE/CBasePane::AdjustDockingLayout
- AFXBASEPANE/CBasePane::AdjustLayout
- AFXBASEPANE/CBasePane::CalcFixedLayout
- AFXBASEPANE/CBasePane::CanAcceptPane
- AFXBASEPANE/CBasePane::CanAutoHide
- AFXBASEPANE/CBasePane::CanBeAttached
- AFXBASEPANE/CBasePane::CanBeClosed
- AFXBASEPANE/CBasePane::CanBeDocked
- AFXBASEPANE/CBasePane::CanBeResized
- AFXBASEPANE/CBasePane::CanBeTabbedDocument
- AFXBASEPANE/CBasePane::CanFloat
- AFXBASEPANE/CBasePane::CanFocus
- AFXBASEPANE/CBasePane::CopyState
- AFXBASEPANE/CBasePane::CreateDefaultMiniframe
- AFXBASEPANE/CBasePane::CreateEx
- AFXBASEPANE/CBasePane::DockPane
- AFXBASEPANE/CBasePane::DockPaneUsingRTTI
- AFXBASEPANE/CBasePane::DockToFrameWindow
- AFXBASEPANE/CBasePane::DoesAllowDynInsertBefore
- AFXBASEPANE/CBasePane::EnableDocking
- AFXBASEPANE/CBasePane::EnableGripper
- AFXBASEPANE/CBasePane::FloatPane
- AFXBASEPANE/CBasePane::get_accHelpTopic
- AFXBASEPANE/CBasePane::get_accSelection
- AFXBASEPANE/CBasePane::GetCaptionHeight
- AFXBASEPANE/CBasePane::GetControlBarStyle
- AFXBASEPANE/CBasePane::GetCurrentAlignment
- AFXBASEPANE/CBasePane::GetDockingMode
- AFXBASEPANE/CBasePane::GetDockSiteFrameWnd
- AFXBASEPANE/CBasePane::GetEnabledAlignment
- AFXBASEPANE/CBasePane::GetMFCStyle
- AFXBASEPANE/CBasePane::GetPaneIcon
- AFXBASEPANE/CBasePane::GetPaneRow
- AFXBASEPANE/CBasePane::GetPaneStyle
- AFXBASEPANE/CBasePane::GetParentDockSite
- AFXBASEPANE/CBasePane::GetParentMiniFrame
- AFXBASEPANE/CBasePane::GetParentTabbedPane
- AFXBASEPANE/CBasePane::GetParentTabWnd
- AFXBASEPANE/CBasePane::GetRecentVisibleState
- AFXBASEPANE/CBasePane::HideInPrintPreviewMode
- AFXBASEPANE/CBasePane::InsertPane
- AFXBASEPANE/CBasePane::IsAccessibilityCompatible
- AFXBASEPANE/CBasePane::IsAutoHideMode
- AFXBASEPANE/CBasePane::IsDialogControl
- AFXBASEPANE/CBasePane::IsDocked
- AFXBASEPANE/CBasePane::IsFloating
- AFXBASEPANE/CBasePane::IsHorizontal
- AFXBASEPANE/CBasePane::IsInFloatingMultiPaneFrameWnd
- AFXBASEPANE/CBasePane::IsMDITabbed
- AFXBASEPANE/CBasePane::IsPaneVisible
- AFXBASEPANE/CBasePane::IsPointNearDockSite
- AFXBASEPANE/CBasePane::IsResizable
- AFXBASEPANE/CBasePane::IsRestoredFromRegistry
- AFXBASEPANE/CBasePane::IsTabbed
- AFXBASEPANE/CBasePane::IsVisible
- AFXBASEPANE/CBasePane::LoadState
- AFXBASEPANE/CBasePane::MoveWindow
- AFXBASEPANE/CBasePane::OnAfterChangeParent
- AFXBASEPANE/CBasePane::OnBeforeChangeParent
- AFXBASEPANE/CBasePane::OnDrawCaption
- AFXBASEPANE/CBasePane::OnMovePaneDivider
- AFXBASEPANE/CBasePane::OnPaneContextMenu
- AFXBASEPANE/CBasePane::OnRemoveFromMiniFrame
- AFXBASEPANE/CBasePane::OnSetAccData
- AFXBASEPANE/CBasePane::PaneFromPoint
- AFXBASEPANE/CBasePane::RecalcLayout
- AFXBASEPANE/CBasePane::RemovePaneFromDockManager
- AFXBASEPANE/CBasePane::SaveState
- AFXBASEPANE/CBasePane::SelectDefaultFont
- AFXBASEPANE/CBasePane::SetControlBarStyle
- AFXBASEPANE/CBasePane::SetDockingMode
- AFXBASEPANE/CBasePane::SetPaneAlignment
- AFXBASEPANE/CBasePane::SetPaneStyle
- AFXBASEPANE/CBasePane::SetWindowPos
- AFXBASEPANE/CBasePane::ShowPane
- AFXBASEPANE/CBasePane::StretchPane
- AFXBASEPANE/CBasePane::UndockPane
- AFXBASEPANE/CBasePane::DoPaint
dev_langs:
- C++
helpviewer_keywords:
- get_accState method
- get_accHelp method
- CBasePane class
- accLocation method
- accHitTest method
- get_accDescription method
- get_accDefaultAction method
- get_accName method
- get_accFocus method
- get_accRole method
- get_accValue method
- get_accChild method
- accSelect method
- get_accKeyboardShortcut method
- get_accChildCount method
- Serialize method
- PreTranslateMessage method
- get_accParent method
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
caps.latest.revision: 43
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0444c0647d83a1e9b431dd0c5bdb369da213b91b
ms.lasthandoff: 02/24/2017

---
# <a name="cbasepane-class"></a>CBasePane 類別
在 MFC 中的所有窗格的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CBasePane : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CBasePane::CBasePane`|預設建構函式。|  
|`CBasePane::~CBasePane`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CBasePane::accHitTest`|由架構呼叫以擷取畫面中給定點的子項目或子物件。 (覆寫[CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest)。)|  
|`CBasePane::accLocation`|擷取目前畫面位置指定的物件架構呼叫。 (覆寫[CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation)。)|  
|[CBasePane::AccNotifyObjectFocusEvent](#accnotifyobjectfocusevent)|`CBasePane`不使用這個方法。|  
|`CBasePane::accSelect`|由架構呼叫以修改選取或移動指定物件的鍵盤焦點。 (覆寫[CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect)。)|  
|[CBasePane::AddPane](#addpane)|將連接管理員 窗格。|  
|[CBasePane::AdjustDockingLayout](#adjustdockinglayout)|重新導向停駐管理員呼叫，以調整停駐配置。|  
|[CBasePane::AdjustLayout](#adjustlayout)|當窗格應該調整其內部的版面配置時，由架構呼叫。|  
|[CBasePane::CalcFixedLayout](#calcfixedlayout)|計算將一種控制列的水平大小。|  
|[CBasePane::CanAcceptPane](#canacceptpane)|決定是否另一個窗格可以停駐窗格。|  
|[CBasePane::CanAutoHide](#canautohide)|判斷窗格是否支援自動隱藏模式。|  
|[CBasePane::CanBeAttached](#canbeattached)|判斷是否可以到另一個窗格停駐窗格。|  
|[CBasePane::CanBeClosed](#canbeclosed)|判斷是否可以關閉窗格。|  
|[CBasePane::CanBeDocked](#canbedocked)|判斷是否可以到另一個窗格停駐窗格。|  
|[CBasePane::CanBeResized](#canberesized)|判斷是否可以調整窗格的大小。|  
|[CBasePane::CanBeTabbedDocument](#canbetabbeddocument)|指定窗格是否可轉換為 MDI 索引標籤式文件。|  
|[CBasePane::CanFloat](#canfloat)|判斷是否可以浮動窗格。|  
|[CBasePane::CanFocus](#canfocus)|指定是否窗格可以接收焦點。|  
|[CBasePane::CopyState](#copystate)|將複製給定 窗格的狀態。|  
|[CBasePane::CreateDefaultMiniframe](#createdefaultminiframe)|如果可以浮動窗格，會建立的迷你框架視窗。|  
|[CBasePane::CreateEx](#createex)|建立窗格控制項。|  
|[CBasePane::DockPane](#dockpane)|另一個窗格或框架視窗停駐窗格。|  
|[CBasePane::DockPaneUsingRTTI](#dockpaneusingrtti)|停駐窗格在使用執行階段類型資訊。|  
|[CBasePane::DockToFrameWindow](#docktoframewindow)|可停駐窗格停駐於框架。|  
|[CBasePane::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|判斷是否可以此窗格與父框架間動態插入另一個窗格。|  
|[CBasePane::EnableDocking](#enabledocking)|啟用停駐窗格的主框架。|  
|[CBasePane::EnableGripper](#enablegripper)|啟用或停用移駐夾。 如果已啟用的移駐夾，使用者可以將它拖曳至窗格中重新調整位置。|  
|`CBasePane::FillWindowRect`|在內部使用。|  
|[CBasePane::FloatPane](#floatpane)|浮動窗格。|  
|`CBasePane::get_accChild`|由架構呼叫以擷取指定子系的 `IDispatch` 介面位址。 (覆寫[CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild)。)|  
|`CBasePane::get_accChildCount`|若要擷取此物件所屬的子系數目架構呼叫。 (覆寫[CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount)。)|  
|`CBasePane::get_accDefaultAction`|擷取字串，描述物件的預設動作的架構所呼叫。 (覆寫[CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction)。)|  
|`CBasePane::get_accDescription`|由架構呼叫以擷取含有指定物件的視覺外觀描述的字串。 (覆寫[CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription)。)|  
|`CBasePane::get_accFocus`|由架構呼叫以擷取具有鍵盤焦點的物件。 (覆寫[CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus)。)|  
|`CBasePane::get_accHelp`|要擷取之物件的說明屬性字串架構呼叫。 (覆寫[CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp)。)|  
|[CBasePane::get_accHelpTopic](#get_acchelptopic)|擷取與指定之物件相關聯的 WinHelp 檔案的完整路徑和檔案中的適當主題的識別項的架構所呼叫。 (覆寫[CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic)。)|  
|`CBasePane::get_accKeyboardShortcut`|若要擷取的物件指定的快速鍵架構呼叫。 (覆寫[CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut)。)|  
|`CBasePane::get_accName`|由架構呼叫以擷取指定物件的名稱。 (覆寫[CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname)。)|  
|`CBasePane::get_accParent`|要擷取架構呼叫`IDispatch`介面物件的父系。 (覆寫[CWnd::get_accParent](../../mfc/reference/cwnd-class.md#get_accparent)。)|  
|`CBasePane::get_accRole`|由架構呼叫以擷取含有指定物件的角色描述資訊。 (覆寫[CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole)。)|  
|[CBasePane::get_accSelection](#get_accselection)|由架構呼叫以擷取此物件的選取子物件。 (覆寫[CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection)。)|  
|`CBasePane::get_accState`|由架構呼叫以擷取指定物件的目前狀態。 (覆寫[CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate)。)|  
|`CBasePane::get_accValue`|由架構呼叫以擷取指定物件的值。 (覆寫[CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue)。)|  
|[CBasePane::GetCaptionHeight](#getcaptionheight)|傳回標題高度。|  
|[CBasePane::GetControlBarStyle](#getcontrolbarstyle)|傳回的控制列的樣式。|  
|[CBasePane::GetCurrentAlignment](#getcurrentalignment)|傳回目前窗格對齊方式。|  
|[CBasePane::GetDockingMode](#getdockingmode)|傳回目前停駐窗格的模式。|  
|[CBasePane::GetDockSiteFrameWnd](#getdocksiteframewnd)|傳回的視窗窗格的停駐位置的指標。|  
|[CBasePane::GetEnabledAlignment](#getenabledalignment)|傳回套用至 「 窗格 CBRS_ALIGN_ 樣式。|  
|[CBasePane::GetMFCStyle](#getmfcstyle)|傳回特定的窗格中的樣式至 MFC。|  
|[CBasePane::GetPaneIcon](#getpaneicon)|傳回窗格圖示的控制代碼。|  
|`CBasePane::GetPaneRect`|在內部使用。|  
|[CBasePane::GetPaneRow](#getpanerow)|傳回的指標[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)物件在停駐窗格。|  
|[CBasePane::GetPaneStyle](#getpanestyle)|傳回的窗格中的樣式。|  
|[CBasePane::GetParentDockSite](#getparentdocksite)|傳回父停駐位置的指標。|  
|[CBasePane::GetParentMiniFrame](#getparentminiframe)|傳回父迷你框架視窗的指標。|  
|[CBasePane::GetParentTabbedPane](#getparenttabbedpane)|傳回父索引標籤式窗格的指標。|  
|[CBasePane::GetParentTabWnd](#getparenttabwnd)|傳回的索引標籤內的父視窗的指標。|  
|[CBasePane::GetRecentVisibleState](#getrecentvisiblestate)|從封存還原窗格時，架構會呼叫這個方法。|  
|[CBasePane::HideInPrintPreviewMode](#hideinprintpreviewmode)|指定是否在預覽列印中隱藏窗格。|  
|[CBasePane::InsertPane](#insertpane)|連接管理員會向指定的窗格。|  
|[CBasePane::IsAccessibilityCompatible](#isaccessibilitycompatible)|指定窗格是否支援使用中的協助工具。|  
|[CBasePane::IsAutoHideMode](#isautohidemode)|決定是否自動隱藏模式中的窗格。|  
|[CBasePane::IsDialogControl](#isdialogcontrol)|指定的窗格是否對話方塊控制項。|  
|[CBasePane::IsDocked](#isdocked)|決定是否要停駐窗格。|  
|[CBasePane::IsFloating](#isfloating)|決定是否浮動窗格。|  
|[CBasePane::IsHorizontal](#ishorizontal)|決定是否要水平固定窗格。|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定是否在多窗格框架視窗窗格。|  
|[CBasePane::IsMDITabbed](#ismditabbed)|判斷是否已加入 MDI 子視窗做為索引標籤式文件 窗格。|  
|[CBasePane::IsPaneVisible](#ispanevisible)|指定是否`WS_VISIBLE`旗標設定窗格。|  
|[CBasePane::IsPointNearDockSite](#ispointneardocksite)|判斷指定的點是否停駐位置附近。|  
|[CBasePane::IsResizable](#isresizable)|判斷是否可以調整窗格的大小。|  
|[CBasePane::IsRestoredFromRegistry](#isrestoredfromregistry)|決定是否從登錄還原窗格。|  
|[CBasePane::IsTabbed](#istabbed)|判斷是否已插入的索引標籤式視窗索引標籤控制項 窗格。|  
|`CBasePane::IsTooltipTopmost`|在內部使用。|  
|[CBasePane::IsVisible](#isvisible)|決定窗格是否可見。|  
|[CBasePane::LoadState](#loadstate)|從登錄載入窗格狀態。|  
|[CBasePane::MoveWindow](#movewindow)|移動 [] 窗格。|  
|[CBasePane::OnAfterChangeParent](#onafterchangeparent)|在變更窗格的父代時，由架構呼叫。|  
|[CBasePane::OnBeforeChangeParent](#onbeforechangeparent)|窗格會變更其父視窗之前，由架構呼叫。|  
|[CBasePane::OnDrawCaption](#ondrawcaption)|繪製標題時，架構會呼叫這個方法。|  
|[CBasePane::OnMovePaneDivider](#onmovepanedivider)|目前未使用這個方法。|  
|[CBasePane::OnPaneContextMenu](#onpanecontextmenu)|建置功能表具有窗格的清單時，由架構呼叫。|  
|[CBasePane::OnRemoveFromMiniFrame](#onremovefromminiframe)|從其父迷你框架視窗中移除一個窗格時，由架構呼叫。|  
|[CBasePane::OnSetAccData](#onsetaccdata)|`CBasePane`不使用這個方法。|  
|`CBasePane::OnUpdateCmdUI`|在內部使用。|  
|[CBasePane::PaneFromPoint](#panefrompoint)|傳回包含指定的點的窗格。|  
|`CBasePane::PreTranslateMessage`|類別所使用的[CWinApp](../../mfc/reference/cwinapp-class.md)轉譯視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CBasePane::RecalcLayout](#recalclayout)|`CBasePane`不使用這個方法。|  
|[CBasePane::RemovePaneFromDockManager](#removepanefromdockmanager)|取消註冊 窗格，並將它從連接管理員清單移除。|  
|[CBasePane::SaveState](#savestate)|將窗格的狀態儲存至登錄。|  
|[CBasePane::SelectDefaultFont](#selectdefaultfont)|選取指定的裝置內容的預設字型。|  
|`CBasePane::Serialize`|從封存中讀取或寫入此物件。 (覆寫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CBasePane::SetControlBarStyle](#setcontrolbarstyle)|設定控制項的列樣式。|  
|[CBasePane::SetDockingMode](#setdockingmode)|設定停駐窗格的模式。|  
|`CBasePane::SetMDITabbed`|在內部使用。|  
|[CBasePane::SetPaneAlignment](#setpanealignment)|設定 [] 窗格中的對齊方式。|  
|`CBasePane::SetPaneRect`|在內部使用。|  
|[CBasePane::SetPaneStyle](#setpanestyle)|設定窗格的樣式。|  
|`CBasePane::SetRestoredFromRegistry`|在內部使用。|  
|[CBasePane::SetWindowPos](#setwindowpos)|變更大小、 位置和疊置順序的窗格。|  
|[CBasePane::ShowPane](#showpane)|顯示或隱藏窗格。|  
|[CBasePane::StretchPane](#stretchpane)|垂直或水平伸展窗格。|  
|[CBasePane::UndockPane](#undockpane)|移除停駐位置、 預設滑桿或目前固定的迷你框架視窗的窗格。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBasePane::DoPaint](#dopaint)|填滿 窗格的背景。|  
  
## <a name="remarks"></a>備註  
 如果您想要建立支援的 MFC 中的可用的擴充停駐功能窗格類別，您必須衍生從`CBasePane`或[CPane 類別](../../mfc/reference/cpane-class.md)。  
  
## <a name="customization-tips"></a>自訂秘訣  
 下列自訂秘訣屬於`CBasePane Class`以及任何從它繼承的類別︰  
  
-   當您建立一個窗格時，您可以套用數個新的樣式︰  
  
    - `AFX_CBRS_FLOAT`可讓窗格浮點數。  
  
    - `AFX_CBRS_AUTOHIDE`啟用自動隱藏模式。  
  
    - `AFX_CBRS_CLOSE`啟用 [關閉 （隱藏）] 窗格。  
  
     這些是您可以結合的位元 OR 運算的旗標。  
  
 `CBasePane`會實作下列虛擬布林方法，以反映這些旗標︰ [CBasePane::CanBeClosed](#canbeclosed)， [CBasePane::CanAutoHide](#canautohide)， [CBasePane::CanFloat](#canfloat)。 您可以在來自訂其行為的衍生類別中覆寫這些程式。  
  
-   您可以藉由覆寫自訂停駐行為[CBasePane::CanAcceptPane](#canacceptpane)。 傳回您窗格`FALSE`從這個方法，以防止停駐到另一個窗格。  
  
-   如果您想要建立靜態，不能浮動，這樣可防止任何其他窗格之前停駐的窗格 （類似於 outlook 功能區中 OutlookDemo 範例），其建立為非浮點數，並覆寫[CBasePane::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)傳回`FALSE`。 預設實作會傳回`FALSE`如果窗格建立不含`AFX_CBRS_FLOAT`樣式。  
  
-   建立識別碼為-1 以外所有窗格。  
  
-   若要判斷窗格可見性，請使用[CBasePane::IsVisible](#isvisible)。 它可正確處理的可見性狀態中的索引標籤，自動隱藏模式。  
  
-   如果您想要建立非浮點數的可調整大小 窗格中，建立不`AFX_CBRS_FLOAT`樣式和呼叫[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。  
  
-   若要排除配置停駐窗格或從其停駐列移除工具列，呼叫[CBasePane::UndockPane](#undockpane)。 請勿呼叫這個方法，自動隱藏模式窗格或存放在索引標籤式視窗索引標籤的窗格。  
  
-   如果您想要 float 或取消停駐窗格自動隱藏模式中，您必須呼叫[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)與`FALSE`做為第一個引數，才能呼叫[CBasePane::FloatPane](#floatpane)或[CBasePane::UndockPane](#undockpane)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CBasePane`類別。 此範例示範如何擷取從窗格`CFrameWndEx`類別以及如何設定停駐模式、 窗格對齊和窗格樣式。 程式碼是由[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&2;](../../mfc/reference/codesnippet/cpp/cbasepane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxbasepane.h  
  
##  <a name="accnotifyobjectfocusevent"></a>CBasePane::AccNotifyObjectFocusEvent  
 `CBasePane`不使用這個方法。  
  
```  
virtual void AccNotifyObjectFocusEvent(int);
```  
  
### <a name="parameters"></a>參數  
 [in] `int`  
 未使用。  
  
##  <a name="addpane"></a>CBasePane::AddPane  
 將連接管理員 窗格。  
  
```  
void AddPane(CBasePane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 窗格中，將指標。  
  
### <a name="remarks"></a>備註  
 這是很便利的方法，將窗格加入至停駐的管理員。 使用此方法，讓您不必撰寫程式碼，以分析父框架的類型。  
  
 如需詳細資訊，請參閱[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)和[CMDIFrameWndEx::AddPane](../../mfc/reference/cmdiframewndex-class.md#addpane)。  
  
##  <a name="adjustdockinglayout"></a>CBasePane::AdjustDockingLayout  
 重新導向停駐管理員呼叫，以調整停駐配置。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `hdwp`  
 此結構包含多個視窗位置控制代碼。  
  
### <a name="remarks"></a>備註  
 這是很便利的方法可調整的停駐配置。 使用此方法，讓您不必撰寫程式碼，以分析父框架的類型。  
  
 如需詳細資訊，請參閱[CDockingManager::AdjustDockingLayout](../../mfc/reference/cdockingmanager-class.md#adjustdockinglayout)  
  
##  <a name="adjustlayout"></a>CBasePane::AdjustLayout  
 若要調整窗格的內部配置架構呼叫。  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>備註  
 必須調整其內部的版面配置 窗格時，架構會呼叫這個方法。 基底實作，就沒有作用。  
  
##  <a name="calcfixedlayout"></a>CBasePane::CalcFixedLayout  
 計算將一種控制列的水平大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStretch`  
 指出軸是否應該自動縮放成框架的大小。 `bStretch`列 （不適用於停駐） 的停駐列並不是 0 停駐或浮動時 （適用於停駐） 時，參數為非零值。  
  
 [in] `bHorz`  
 指出軸是水平或垂直方向。 `bHorz`參數為非零，如果列是水平方向，而是 0，如果它是垂直方向。  
  
### <a name="return-value"></a>傳回值  
 控制列的大小，單位為像素的`CSize`物件。  
  
### <a name="remarks"></a>備註  
 請參閱 < 備註 > 一節中[CControlBar::CalcFixedLayout](../../mfc/reference/ccontrolbar-class.md#calcfixedlayout)  
  
##  <a name="canacceptpane"></a>CBasePane::CanAcceptPane  
 決定是否另一個窗格可以停駐窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要停駐窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以接受另一個窗格。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法之前所指定窗格停駐於`pBar`到目前的窗格。  
  
 使用這個方法和[CBasePane::CanBeDocked](#canbedocked)方法，以控制窗格將應用程式中的其他窗格的停駐。  
  
 預設實作會傳回 `FALSE`。  
  
##  <a name="canautohide"></a>CBasePane::CanAutoHide  
 判斷窗格是否支援自動隱藏模式。  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此窗格支援自動隱藏模式;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式可判斷窗格是否支援自動隱藏模式。  
  
 在建構期間，您可以設定這項功能，藉由傳遞`AFX_CBRS_AUTOHIDE`旗標設為[CBasePane::CreateEx](#createex)。  
  
 預設實作會檢查`AFX_CBRS_AUTOHIDE`旗標。 若要自訂此行為在衍生類別中的，這個方法會覆寫。  
  
##  <a name="canbeattached"></a>CBasePane::CanBeAttached  
 判斷是否可以到另一個窗格或框架視窗停駐窗格。  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果另一個窗格或框架視窗，停駐窗格，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 預設實作會傳回 `FALSE`。 這個方法來啟用或停用的功能，而不需呼叫停駐在衍生類別中覆寫[CBasePane::EnableDocking](#enabledocking)。  
  
##  <a name="canbeclosed"></a>CBasePane::CanBeClosed  
 判斷是否可以關閉窗格。  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以關閉窗格。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法來判斷是否可以關閉窗格。 如果此方法會傳回`TRUE`、**關閉**窗格的標題列中加入按鈕或 [] 窗格浮動窗格，窗格的 [自] 視窗的標題列。  
  
 在建構期間，您可以設定這項功能，藉由傳遞`AFX_CBRS_CLOSE`旗標設為[CBasePane::CreateEx](#createex)。  
  
 預設實作會檢查`AFX_CBRS_CLOSE`旗標。  
  
##  <a name="canbedocked"></a>CBasePane::CanBeDocked  
 判斷是否可以到另一個窗格停駐窗格。  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockBar`  
 指標，另一個窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此窗格可停駐到另一個窗格。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法之前所指定窗格停駐於`pDockBar`到目前的窗格。  
  
 使用這個方法和[CBasePane::CanAcceptPane](#canacceptpane)方法，以控制窗格將應用程式中的其他窗格的停駐。  
  
 預設實作會傳回 `FALSE`。  
  
##  <a name="canberesized"></a>CBasePane::CanBeResized  
 判斷是否可以調整窗格的大小。  
  
```  
virtual BOOL CanBeResized() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以調整窗格的大小;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會檢查`AFX_CBRS_RESIZE`旗標，指定預設`CBasePane::OnCreate`。 如果未指定這個旗標，停駐 manager 旗標，在內部為不可，而不是讓它停駐窗格。  
  
##  <a name="canbetabbeddocument"></a>CBasePane::CanBeTabbedDocument  
 指定窗格是否可轉換為 MDI 索引標籤式文件。  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格可以轉換為索引標籤式文件。否則， `FALSE`。 `CBasePane::CanBeTabbedDocument` 永遠傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 只有物件特定的`CBasePane`-衍生型別，例如[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)，可以轉換為索引標籤式文件。  
  
##  <a name="canfloat"></a>CBasePane::CanFloat  
 判斷是否可以浮動窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以浮動窗格。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法來判斷是否可以浮動窗格。  
  
 在建構期間，您可以設定這項功能，藉由傳遞`AFX_CBRS_FLOAT`旗標設為[CBasePane::CreateEx](#createex)。  
  
> [!NOTE]
>  架構會假設及非浮動窗格為靜態，且無法變更其停駐狀態。 因此，架構就不會儲存非浮動窗格的停駐狀態。  
  
 預設實作會檢查`AFX_CBRS_FLOAT`樣式。  
  
##  <a name="canfocus"></a>CBasePane::CanFocus  
 指定是否窗格可以接收焦點。  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格可以接收焦點。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法來控制焦點在衍生類別中。 例如，工具列不會收到焦點，因為這個方法會傳回`FALSE`當工具列物件上呼叫它。  
  
 架構會嘗試將輸入的焦點時停駐或浮動窗格。  
  
##  <a name="copystate"></a>CBasePane::CopyState  
 將複製給定 窗格的狀態。  
  
```  
virtual void CopyState(CBasePane* pOrgBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pOrgBar`  
 指標，另一個窗格。  
  
### <a name="remarks"></a>備註  
 這個方法會複製狀態從`pOrgBar`到這個窗格。  
  
##  <a name="createdefaultminiframe"></a>CBasePane::CreateDefaultMiniframe  
 如果可以浮動窗格，這個方法會為其建立的迷你框架視窗。  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectInitial`  
 指定迷你框架視窗的初始的座標。  
  
### <a name="return-value"></a>傳回值  
 新的迷你框架視窗的指標或`NULL`如果建立失敗。  
  
### <a name="remarks"></a>備註  
 當窗格切換為浮動狀態時，架構會呼叫這個方法。 方法會建立一個迷你框架視窗，並附加到這個視窗窗格。  
  
 預設實作會傳回 `NULL`。  
  
##  <a name="createex"></a>CBasePane::CreateEx  
 建立窗格控制項。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle=0,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwStyleEx`  
 延伸的樣式 (請參閱[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)如需詳細資訊)。  
  
 [in] `lpszClassName`  
 視窗類別名稱。  
  
 [in] `lpszWindowName`  
 視窗名稱。  
  
 [in] `dwStyle`  
 視窗樣式 (請參閱[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex))。  
  
 [in] `rect`  
 初始的矩形。  
  
 [in] `pParentWnd`  
 父視窗的指標。  
  
 [in] `nID`  
 指定窗格識別碼。 必須是唯一的。  
  
 [in] `dwControlBarStyle`  
 窗格的樣式旗標。  
  
 [in] `pContext`  
 指標`CcreateContext`  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功; 建立窗格否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 建立類別的視窗`lpszClassName`。 如果您指定`WS_CAPTION`，這個方法會清除`WS_CAPTION`樣式位元和集合`CBasePane::m_bHasCaption`至`TRUE`，因為程式庫不支援有標題的窗格。  
  
 您可以使用任何子視窗的樣式和 MFC 控制列 (CBRS_) 樣式的組合。  
  
 程式庫新增了數種新樣式 窗格。 下表說明新的樣式︰  
  
|樣式|描述|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|浮動窗格。|  
|`AFX_CBRS_AUTOHIDE`|[] 窗格支援自動隱藏模式|  
|`AFX_CBRS_RESIZE`|可以調整窗格的大小。 **重要事項︰**未實作此樣式。|  
|`AFX_CBRS_CLOSE`|可以關閉窗格。|  
|`AFX_CBRS_AUTO_ROLLUP`|當它會浮動窗格可彙總。|  
|`AFX_CBRS_REGULAR_TABS`|當一個窗格停駐於具有此樣式時的另一個窗格時，會建立一般的索引標籤式的視窗。 (如需詳細資訊，請參閱[CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)。)|  
|`AFX_CBRS_OUTLOOK_TABS`|當一個窗格停駐於具有此樣式時的另一個窗格時，會建立 Outlook 樣式索引標籤式的視窗。 (如需詳細資訊，請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。)|  
  
 若要使用新的樣式，指定在`dwControlBarStyle`。  
  
##  <a name="dockpane"></a>CBasePane::DockPane  
 另一個窗格或框架視窗停駐窗格。  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockBar`  
 指標，另一個窗格。  
  
 [in] `lpRect`  
 指定目的地矩形。  
  
 [in] `dockMethod`  
 指定的停駐的方法。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 停駐控制列，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可停駐窗格，另一個窗格或 停駐列 ( [CDockSite 類別](../../mfc/reference/cdocksite-class.md)) 所指定`pDockBar`，或主要畫面格如果`pDockBar`是`NULL`。  
  
 `dockMethod`指定如何停駐窗格。 請參閱[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)的可能值的清單。  
  
##  <a name="dockpaneusingrtti"></a>CBasePane::DockPaneUsingRTTI  
 停駐窗格在使用執行階段類型資訊。  
  
```  
void DockPaneUsingRTTI(BOOL bUseDockSite);
```  
  
### <a name="parameters"></a>參數  
 [in] `bUseDockSite`  
 如果`TRUE`，停駐到銜接站台。 如果`FALSE`，停駐於父框架。  
  
##  <a name="docktoframewindow"></a>CBasePane::DockToFrameWindow  
 可停駐窗格停駐於框架。  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 您想要停駐窗格的父框架端。  
  
 [in] `lpRect`  
 所需的大小。  
  
 [in] `dwDockFlags`  
 忽略。  
  
 [in] `pRelativeBar`  
 忽略。  
  
 [in] `nRelativeIndex`  
 忽略。  
  
 [in] `bOuterEdge`  
 如果`TRUE`和指定的側邊有其他可停駐窗格`dwAlignment`，窗格即停駐以外其他窗格，接近的父框架邊緣。 如果`FALSE`，窗格停駐在接近用戶端區域的中央。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果窗格分割線 ( [CPaneDivider 類別](../../mfc/reference/cpanedivider-class.md)) 無法建立。 否則，它一律傳回`TRUE`。  
  
##  <a name="doesallowdyninsertbefore"></a>CBasePane::DoesAllowDynInsertBefore  
 判斷是否可以此窗格與父框架間動態插入另一個窗格。  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果使用者可以插入另一個窗格。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法來判斷使用者是否可以動態插入此窗格前的一個窗格。  
  
 例如，假設您的應用程式，建立停駐在框架 （例如 outlook 功能區） 的左側的窗格。 若要防止使用者在停駐的第一個窗格左邊的另一個窗格，覆寫這個方法，並傳回`FALSE`。  
  
 我們建議您覆寫這個方法，並傳回`FALSE`非浮動窗格衍生自[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)。  
  
 預設實作會傳回 `TRUE`。  
  
##  <a name="dopaint"></a>CBasePane::DoPaint  
 填滿 窗格的背景。  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫目前的視覺管理員背景填滿 ( [CMFCVisualManager::OnFillBarBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillbarbackground))。  
  
##  <a name="enabledocking"></a>CBasePane::EnableDocking  
 啟用停駐窗格的主框架。  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 指定要啟用的停駐對齊。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來啟用停駐於主框架的對齊方式。 您可以傳遞多種`CBRS_ALIGN_`旗標 (如需詳細資訊，請參閱[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking))。  
  
 `EnableDocking`設定內部旗標`CBasePane::m_dwEnabledAlignment`和停駐窗格時，架構會檢查此旗標。  
  
 呼叫[CBasePane::GetEnabledAlignment](#getenabledalignment)判斷窗格的停駐對齊方式。  
  
##  <a name="enablegripper"></a>CBasePane::EnableGripper  
 啟用或停用移駐夾。 如果已啟用的移駐夾，使用者可以將它拖曳至窗格中重新調整位置。  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用移駐夾;`FALSE`停用它。  
  
### <a name="remarks"></a>備註  
 架構會使用這個方法來啟用移駐夾，而不是使用`WS_CAPTION`樣式。  
  
##  <a name="floatpane"></a>CBasePane::FloatPane  
 浮動窗格。  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod=DM_UNKNOWN,  
    bool bShow=true);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectFloat`  
 指定螢幕座標浮動窗格顯示的位置。  
  
 [in] `dockMethod`  
 指定要用於浮動窗格的停駐方法。  
  
 [in] `bShow`  
 指定浮動窗格是否可見 ( `TRUE`) 或隱藏 ( `FALSE`)。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 浮動窗格否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以浮動窗格，以在所指定的螢幕位置`rectFloat`。  
  
##  <a name="get_acchelptopic"></a>CBasePane::get_accHelpTopic  
 架構會呼叫這個方法，以擷取的完整路徑`WinHelp`與指定的物件和該檔案中的適當主題的識別項相關聯的檔案。  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>參數  
 [in] `pszHelpFile`  
 位址`BSTR`接收的完整路徑`WinHelp`相關聯檔案，以指定的物件，如果有的話。  
  
 [in] `varChild`  
 指定是否要擷取的 [說明] 主題的物件或其中一個物件的子元素。 這個參數可以是`CHILDID_SELF`（若要取得 [說明] 主題的物件） 或子識別碼 （若要取得 [說明] 主題的其中一個子物件的項目）。  
  
 [in] `pidTopic`  
 識別`Help`檔主題與指定的物件相關聯。  
  
### <a name="return-value"></a>傳回值  
 `CBasePane`不會實作這個方法。 因此，`CBasePane::get_accHelpTopic`一律會傳回`S_FALSE`。  
  
### <a name="remarks"></a>備註  
 此函式是在 MFC 中的使用中的協助工具支援的一部分。 覆寫這個函式在衍生類別提供物件的相關說明資訊。  
  
##  <a name="get_accselection"></a>CBasePane::get_accSelection  
 架構會呼叫這個方法來擷取此物件的所選子系。  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>參數  
 [in] `pvarChildren`  
 接收識別所選的子系的資訊。  
  
### <a name="return-value"></a>傳回值  
 `CBasePane`不會實作這個方法。 如果 `pvarChildren` 為 `NULL`，這個方法會傳回 `E_INVALIDARG`。 否則，這個方法會傳回`DISP_E_MEMBERNOTFOUND`。  
  
### <a name="remarks"></a>備註  
 此函式是在 MFC 中的使用中的協助工具支援的一部分。 如果您有無視窗的 ActiveX 控制項以外的非視窗型使用者介面項目，請覆寫這個函式在衍生類別中。  
  
##  <a name="getcaptionheight"></a>CBasePane::GetCaptionHeight  
 傳回標題高度。  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 標題高度。  
  
##  <a name="getcontrolbarstyle"></a>CBasePane::GetControlBarStyle  
 傳回的控制列的樣式。  
  
```  
virtual DWORD GetControlBarStyle() const 
```  
  
### <a name="return-value"></a>傳回值  
 AFX_CBRS_ 旗標的位元 OR 組合。  
  
### <a name="remarks"></a>備註  
 傳回值是以下的可能值的組合。  
  
|樣式|說明|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|可控制列浮點數。|  
|`AFX_CBRS_AUTOHIDE`|啟用自動隱藏模式。|  
|`AFX_CBRS_RESIZE`|可調整大小的控制列。 當設定這個旗標時，控制列可以放置在可停駐窗格。|  
|`AFX_CBRS_CLOSE`|啟用隱藏的控制列。|  
  
##  <a name="getcurrentalignment"></a>CBasePane::GetCurrentAlignment  
 傳回目前窗格對齊方式。  
  
```  
virtual DWORD GetCurrentAlignment() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制列目前的對齊方式。 下表顯示可能的值︰  
  
|值|對齊|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|靠左的對齊。|  
|`CBRS_ALIGN_RIGHT`|靠右對齊。|  
|`CBRS_ALIGN_TOP`|靠上對齊。|  
|`CBRS_ALIGN_BOTTOM`|靠下對齊。|  
  
##  <a name="getdockingmode"></a>CBasePane::GetDockingMode  
 傳回目前停駐窗格的模式。  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果拖曳窗格 DT_STANDARD 會以在螢幕上拖曳矩形。 DT_IMMEDIATE 如果拖曳窗格的內容。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法來判斷目前停駐窗格的模式。  
  
 如果`CBasePane::m_dockMode`是未定義 (DT_UNDEFINED)，然後停駐模式取自全域停駐模式 ( `AFX_GLOBAL_DATA::m_dockModeGlobal`)。  
  
 藉由設定`m_dockMode`或覆寫`GetDockingMode`您可以控制每個窗格的停駐模式。  
  
##  <a name="getdocksiteframewnd"></a>CBasePane::GetDockSiteFrameWnd  
 傳回的指標[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)物件在停駐窗格。  
  
```  
virtual CWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 窗格的停駐位置指標。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來擷取窗格的停駐位置的指標。 如果窗格浮動窗格停駐於主框架中，如果主框架視窗或迷你框架視窗可以是停駐位置。  
  
##  <a name="getenabledalignment"></a>CBasePane::GetEnabledAlignment  
 傳回套用至 「 窗格 CBRS_ALIGN_ 樣式。  
  
```  
virtual DWORD GetEnabledAlignment() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CBRS_ALIGN_ 樣式的組合。 下表顯示可能的樣式︰  
  
|旗標|已啟用的對齊方式|  
|----------|-----------------------|  
|`CBRS_ALIGN_LEFT`|左。|  
|`CBRS_ALIGN_RIGHT`|權限。|  
|`CBRS_ALIGN_TOP`|最上方。|  
|`CBRS_ALIGN_BOTTOM`|下方。|  
|`CBRS_ALIGN_ANY`|所有的旗標的組合。|  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷窗格的已啟用對齊方式。 已啟用的對齊表示側邊窗格停駐於主框架視窗。  
  
 使用啟用停駐對齊[CBasePane::EnableDocking](#enabledocking)。  
  
##  <a name="getmfcstyle"></a>CBasePane::GetMFCStyle  
 傳回特定 MFC 的窗格樣式。  
  
```  
virtual DWORD GetMFCStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 特定的程式庫 (AFX_CBRS_) 窗格樣式的組合。  
  
##  <a name="getpaneicon"></a>CBasePane::GetPaneIcon  
 傳回窗格圖示的控制代碼。  
  
```  
virtual HICON GetPaneIcon(BOOL bBigIcon);
```  
  
### <a name="parameters"></a>參數  
 [in] `bBigIcon`  
 指定 32 像素 32 像素圖示，如果`TRUE`; 指定 16 像素 16 像素圖示，如果`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 窗格圖示的控制代碼。 如果不成功，傳回`NULL`。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[CWnd::GetIcon](../../mfc/reference/cwnd-class.md#geticon)。  
  
##  <a name="getpanerow"></a>CBasePane::GetPaneRow  
 傳回的指標[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)物件在停駐窗格。  
  
```  
CDockingPanesRow* GetPaneRow();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CDockingPanesRow`停駐窗格中，如果或`NULL`如果它浮動窗格。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來存取資料列會在停駐窗格。 例如，若要排列窗格中的特定資料列，呼叫`GetPaneRow`，然後呼叫[CDockingPanesRow::ArrangePanes](../../mfc/reference/cdockingpanesrow-class.md#arrangepanes)。  
  
##  <a name="getpanestyle"></a>CBasePane::GetPaneStyle  
 傳回的窗格中的樣式。  
  
```  
virtual DWORD GetPaneStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制列的樣式 （包括 CBRS_ 樣式） 所設定的組合[CBasePane::SetPaneStyle](#setpanestyle)在建立時的方法。  
  
##  <a name="getparentdocksite"></a>CBasePane::GetParentDockSite  
 傳回父停駐位置的指標。  
  
```  
virtual CDockSite* GetParentDockSite() const;  
```  
  
### <a name="return-value"></a>傳回值  
 父停駐站台。  
  
##  <a name="getparentminiframe"></a>CBasePane::GetParentMiniFrame  
 傳回父迷你框架視窗的指標。  
  
```  
virtual CPaneFrameWnd* GetParentMiniFrame(BOOL bNoAssert=FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bNoAssert`  
 如果`TRUE`，這個方法不會檢查非有效的指標。 如果您在應用程式結束時呼叫這個方法，將此參數設定為`TRUE`。  
  
### <a name="return-value"></a>傳回值  
 父迷你框架視窗窗格浮動窗格; 如果有效的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取父迷你框架視窗的指標。 這個方法逐一查看所有父系，並檢查物件衍生自[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)。  
  
 使用`GetParentMiniFrame`來判斷是否浮動窗格。  
  
##  <a name="getparenttabbedpane"></a>CBasePane::GetParentTabbedPane  
 傳回父索引標籤式窗格的指標。  
  
```  
CBaseTabbedPane* GetParentTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果有的話，父索引標籤式窗格的指標否則`NULL`。  
  
##  <a name="getparenttabwnd"></a>CBasePane::GetParentTabWnd  
 傳回的索引標籤內的父視窗的指標。  
  
```  
CMFCBaseTabCtrl* GetParentTabWnd(HWND& hWndTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `hWndTab`  
 如果傳回的值不是`NULL`，這個參數會包含父索引標籤式視窗的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 父代的有效指標的索引標籤式視窗或`NULL`。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來擷取父索引標籤式視窗的指標。 有時並不足夠呼叫`GetParent`，因為窗格可能會在停駐的包裝函式 ( [CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md)) 或內部窗格配接器 ( [CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md))。 使用`GetParentTabWnd`能夠擷取有效的指標，在這些情況下 （假設父代索引標籤式的視窗）。  
  
##  <a name="getrecentvisiblestate"></a>CBasePane::GetRecentVisibleState  
 從封存還原窗格時，架構會呼叫這個方法。  
  
```  
virtual BOOL GetRecentVisibleState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`BOOL`指定最近的可見狀態。 如果`TRUE`，窗格會是可見時，序列化，而且應該是可見時還原。 如果`FALSE`，當序列化和還原時，應該隱藏時，已隱藏窗格。  
  
##  <a name="hideinprintpreviewmode"></a>CBasePane::HideInPrintPreviewMode  
 指定是否在預覽列印中隱藏窗格。  
  
```  
virtual BOOL HideInPrintPreviewMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格不會顯示在預覽列印。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 基底窗格不會顯示在預覽列印中。 因此，這個方法一律會傳回`TRUE`。  
  
##  <a name="insertpane"></a>CBasePane::InsertPane  
 連接管理員會向指定的窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 要插入窗格指標。  
  
 [in] `pTarget`  
 指標，相鄰的窗格。  
  
 [in] `bAfter`  
 如果`TRUE`，`pControlBar`後面插入`pTarget`。 如果`FALSE`，`pControlBar`之前，插入`pTarget`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功，`FALSE`否則。  
  
##  <a name="isaccessibilitycompatible"></a>CBasePane::IsAccessibilityCompatible  
 指定窗格是否支援使用中的協助工具。  
  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格支援使用中的存取範圍;否則， `FALSE`。  
  
##  <a name="isautohidemode"></a>CBasePane::IsAutoHideMode  
 決定是否自動隱藏模式中的窗格。  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格處於自動隱藏模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 基底窗格無法自動隱藏。 這個方法一律會傳回 `FALSE`。  
  
##  <a name="isdialogcontrol"></a>CBasePane::IsDialogControl  
 指定的窗格是否對話方塊控制項。  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格對話方塊控制項。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會使用這個方法，以確保所有窗格的版面配置一致性。  
  
##  <a name="isdocked"></a>CBasePane::IsDocked  
 決定是否要停駐窗格。  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格的父系不是迷你框架，或與另一個窗格; 的迷你框架中 窗格浮動否則， `FALSE`。  
  
##  <a name="isfloating"></a>CBasePane::IsFloating  
 決定是否浮動窗格。  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果浮動窗格;，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法傳回的相反值[CBasePane::IsDocked](#isdocked)。  
  
##  <a name="ishorizontal"></a>CBasePane::IsHorizontal  
 決定是否要水平固定窗格。  
  
```  
virtual BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格即停駐水平空間。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 預設實作會檢查目前的停駐對齊的`CBRS_ORIENT_HORZ`。  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CBasePane::IsInFloatingMultiPaneFrameWnd  
 指定是否在多窗格框架視窗窗格 ( [CMultiPaneFrameWnd 類別](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格中的多窗格框架視窗。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 多窗格在框架視窗中浮動只可停駐窗格。 因此，`CBasePane::IsInFloatingMultiPaneFrameWnd`一律會傳回`FALSE`。  
  
##  <a name="ismditabbed"></a>CBasePane::IsMDITabbed  
 判斷是否已加入 MDI 子視窗做為索引標籤式文件 窗格。  
  
```  
virtual BOOL IsMDITabbed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格加入至 MDI 子視窗做為索引標籤式文件。否則， `FALSE`。  
  
##  <a name="ispanevisible"></a>CBasePane::IsPaneVisible  
 指定是否`WS_VISIBLE`旗標設定窗格。  
  
```  
BOOL IsPaneVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`WS_VISIBLE`設定，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CBasePane::IsVisible](#isvisible)以判斷窗格可見性。  
  
##  <a name="ispointneardocksite"></a>CBasePane::IsPointNearDockSite  
 判斷指定的點是否停駐位置附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指定的點。  
  
 [輸出] `dwBarAlignment`  
 指定的點是附近的邊緣。 可能的值為`CBRS_ALIGN_LEFT`， `CBRS_ALIGN_RIGHT`， `CBRS_ALIGN_TOP`，並`CBRS_ALIGN_BOTTOM`  
  
 [輸出] `bOuterEdge`  
 `TRUE`如果點很近外框的停駐位置。`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果點附近的停駐位置。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 重點是停駐位置附近時中設定連接管理員中的敏感度。 預設區分大小寫為 15 像素。  
  
##  <a name="isresizable"></a>CBasePane::IsResizable  
 判斷是否可以調整窗格的大小。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果使用者，可以調整窗格的大小否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 窗格[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)可調整大小。  
  
 狀態列 ( [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)) 和停駐列 ( [CDockSite 類別](../../mfc/reference/cdocksite-class.md)) 無法調整大小。  
  
##  <a name="isrestoredfromregistry"></a>CBasePane::IsRestoredFromRegistry  
 決定是否從登錄還原窗格。  
  
```  
virtual BOOL IsRestoredFromRegistry() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格還原登錄。否則， `FALSE`。  
  
##  <a name="istabbed"></a>CBasePane::IsTabbed  
 判斷是否已插入的索引標籤式視窗索引標籤控制項 窗格。  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果控制列插入的索引標籤式視窗中，索引標籤否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法擷取直屬父的指標，並判斷是否在父系的執行階段類別[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
##  <a name="isvisible"></a>CBasePane::IsVisible  
 決定窗格是否可見。  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格是可見的。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法，以判斷窗格的可見性。 請勿使用`::IsWindowVisible`。  
  
 如果不索引標籤式窗格 (請參閱[CBasePane::IsTabbed](#istabbed))，這個方法會檢查`WS_VISIBLE`樣式。 如果索引標籤式窗格中，這個方法會檢查父索引標籤式視窗的可見性。 如果父視窗為可見，函式會檢查窗格 索引標籤使用的可見性[CMFCBaseTabCtrl::IsTabVisible](../../mfc/reference/cmfcbasetabctrl-class.md#istabvisible)。  
  
##  <a name="loadstate"></a>CBasePane::LoadState  
 從登錄載入窗格的狀態。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 設定檔名稱。  
  
 [in] `nIndex`  
 設定檔的索引。  
  
 [in] `uiID`  
 窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 載入窗格狀態否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以從登錄載入窗格狀態。 若要載入儲存的其他資訊在衍生類別中覆寫它[CBasePane::SaveState](#savestate)。  
  
##  <a name="movewindow"></a>CBasePane::MoveWindow  
 移動 [] 窗格。  
  
```  
virtual HDWP MoveWindow(
    CRect& rect,  
    BOOL bRepaint = TRUE,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 指定新的位置和大小 窗格的矩形。  
  
 [in] `bRepaint`  
 如果`TRUE`，窗格會重新繪製。 如果`FALSE`，不會重新繪製的窗格。  
  
 [in] `hdwp`  
 延後的視窗位置結構的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 延後的視窗位置結構的控制代碼或`NULL`。  
  
### <a name="remarks"></a>備註  
 如果您傳遞`NULL`為`hdwp`參數，這個方法通常移動的視窗。 如果您傳遞的控制代碼，這個方法會執行延遲的視窗移動。 您可以藉由呼叫中取得控制代碼[BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672)或儲存的先前呼叫這個方法傳回的值。  
  
##  <a name="onafterchangeparent"></a>CBasePane::OnAfterChangeParent  
 窗格的父變更之後，由框架呼叫。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndOldParent`  
 先前的父代指標。  
  
### <a name="remarks"></a>備註  
 窗格的父項目變更，通常是因為停駐或浮動作業之後，架構會呼叫這個方法。  
  
 預設實作不做任何動作。  
  
##  <a name="onbeforechangeparent"></a>CBasePane::OnBeforeChangeParent  
 窗格會變更其父視窗之前，由架構呼叫。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndNewParent`  
 新的父視窗的指標。  
  
 [in] `bDelay`  
 指定是否必須延遲版面配置調整。  
  
### <a name="remarks"></a>備註  
 架構之前呼叫這個方法只是窗格的父代的變更，通常是因為停駐、 浮動或自動隱藏 作業。  
  
 預設實作不做任何動作。  
  
##  <a name="ondrawcaption"></a>CBasePane::OnDrawCaption  
 繪製標題時，架構會呼叫這個方法。  
  
```  
virtual void OnDrawCaption();
```  
  
### <a name="remarks"></a>備註  
 這個方法沒有任何功能，如`CBasePane`類別。  
  
##  <a name="onmovepanedivider"></a>CBasePane::OnMovePaneDivider  
 目前未使用這個方法。  
  
```  
virtual void OnMovePaneDivider(CPaneDivider*);
```  
  
### <a name="parameters"></a>參數  
 [in] `CPaneDivider*`  
 未使用。  
  
##  <a name="onpanecontextmenu"></a>CBasePane::OnPaneContextMenu  
 建置功能表具有窗格的清單時，由架構呼叫。  
  
```  
virtual void OnPaneContextMenu(
    CWnd* pParentFrame,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentFrame`  
 父框架指標。  
  
 [in] `point`  
 指定的快顯功能表的位置。  
  
### <a name="remarks"></a>備註  
 `OnPaneContextMenu`呼叫停駐的管理員會維護屬於目前的框架視窗的窗格的清單。 這個方法將窗格的名稱加入至快顯功能表，並顯示它。 功能表命令顯示或隱藏個別的窗格。  
  
 覆寫這個方法，以自訂此行為。  
  
##  <a name="onremovefromminiframe"></a>CBasePane::OnRemoveFromMiniFrame  
 從其父迷你框架視窗中移除一個窗格時，由架構呼叫。  
  
```  
virtual void OnRemoveFromMiniFrame(CPaneFrameWnd* pMiniFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMiniFrame`  
 移除 [] 窗格的迷你框架視窗的指標。  
  
### <a name="remarks"></a>備註  
 從父迷你框架視窗 （因為停駐，比方說） 移除窗格時，架構會呼叫這個方法。  
  
 預設實作不做任何動作。  
  
##  <a name="onsetaccdata"></a>CBasePane::OnSetAccData  
 `CBasePane`不使用這個方法。  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>參數  
 [in] `lVal`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 這個方法一律會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="panefrompoint"></a>CBasePane::PaneFromPoint  
 傳回包含指定的點的窗格。  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 若要檢查的螢幕座標中指定點。  
  
 [in] `nSensitivity`  
 搜尋區域增加此數量。 如果指定的點落在增加區域中，窗格並符合搜尋準則。  
  
 [in] `bExactBar`  
 `TRUE`若要忽略`nSensitivity`參數，否則`FALSE`。  
  
 [in] `pRTCBarType`  
 如果不是`NULL`，該方法會搜尋窗格指定的型別。  
  
### <a name="return-value"></a>傳回值  
 `CBasePane`-衍生物件，其中包含指定的點或`NULL`如果找不到任何窗格。  
  
##  <a name="recalclayout"></a>CBasePane::RecalcLayout  
 `CBasePane`不使用這個方法。  
  
```  
virtual void RecalcLayout();
```  
  
##  <a name="removepanefromdockmanager"></a>CBasePane::RemovePaneFromDockManager  
 取消註冊 窗格，並將它從連接管理員清單移除。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pBar,  
    BOOL bDestroy = TRUE,  
    BOOL bAdjustLayout = FALSE,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 要移除的窗格指標。  
  
 [in] `bDestroy`  
 如果`TRUE`，終結已移除的窗格。  
  
 [in] `bAdjustLayout`  
 如果`TRUE`，立即調整停駐配置。  
  
 [in] `bAutoHide`  
 如果`TRUE`，停駐配置相關的自動隱藏列清單。 如果`FALSE`，停駐配置與一般窗格的清單。  
  
 [in] `pBarReplacement`  
 指標，會取代 [移除] 窗格的窗格。  
  
##  <a name="savestate"></a>CBasePane::SaveState  
 將窗格的狀態儲存至登錄。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 設定檔名稱。  
  
 [in] `nIndex`  
 設定檔的索引。  
  
 [in] `uiID`  
 窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果儲存的狀態已順利啟動。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 窗格的狀態儲存至登錄時，架構會呼叫這個方法。 覆寫`SaveState`儲存其他資訊在衍生類別中。  
  
##  <a name="selectdefaultfont"></a>CBasePane::SelectDefaultFont  
 選取指定的裝置內容的預設字型。  
  
```  
CFont* SelectDefaultFont(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容。  
  
### <a name="return-value"></a>傳回值  
 預設值的指標[CFont 類別](../../mfc/reference/cfont-class.md)物件。  
  
##  <a name="setcontrolbarstyle"></a>CBasePane::SetControlBarStyle  
 設定控制項的列樣式。  
  
```  
virtual void SetControlBarStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwNewStyle`  
 以下的可能值的位元 OR 組合。  
  
|樣式|說明|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|可控制列浮點數。|  
|`AFX_CBRS_AUTOHIDE`|啟用自動隱藏模式。|  
|`AFX_CBRS_RESIZE`|可調整大小的控制列。 當設定這個旗標時，控制列可以放置在可停駐窗格。|  
|`AFX_CBRS_CLOSE`|啟用隱藏的控制列。|  
  
##  <a name="setdockingmode"></a>CBasePane::SetDockingMode  
 設定停駐窗格的模式。  
  
```  
void SetDockingMode(AFX_DOCK_TYPE dockModeNew);
```  
  
### <a name="parameters"></a>參數  
 [in] `dockModeNew`  
 指定新的停駐模式的窗格。  
  
### <a name="remarks"></a>備註  
 架構支援兩種停駐模式︰ 標準和即時運算。  
  
 在標準停駐模式中，窗格和迷你框架視窗移動使用拖曳矩形。 在即時的停駐模式、 控制列和迷你框架視窗一起移動立即其內容。  
  
 一開始，停駐模式由全域定義[CDockingManager::m_dockModeGlobal](../../mfc/reference/cdockingmanager-class.md#m_dockmodeglobal)。 您可以設定個別使用每個窗格的停駐模式`SetDockingMode`方法。  
  
##  <a name="setpanealignment"></a>CBasePane::SetPaneAlignment  
 設定 [] 窗格中的對齊方式。  
  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 指定新的對齊方式。  
  
### <a name="remarks"></a>備註  
 通常，架構會呼叫這個方法窗格主框架的一端從停駐到另一個時。  
  
 下表顯示可能的值為`dwAlignment`:  
  
|值|對齊|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|靠左的對齊。|  
|`CBRS_ALIGN_RIGHT`|靠右對齊。|  
|`CBRS_ALIGN_TOP`|靠上對齊。|  
|`CBRS_ALIGN_BOTTOM`|靠下對齊。|  
  
##  <a name="setpanestyle"></a>CBasePane::SetPaneStyle  
 設定窗格的樣式。  
  
```  
virtual void SetPaneStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwNewStyle`  
 指定要設定的新樣式。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來設定任何在 afxres.h 中定義的 CBRS_ 樣式。 因為窗格樣式和窗格對齊方式儲存在一起，設定新的樣式結合目前的對齊，如下所示。  
  
 `pPane->SetPaneStyle (pPane->GetCurrentAlignment() | CBRS_TOOLTIPS);`  
  
##  <a name="setwindowpos"></a>CBasePane::SetWindowPos  
 變更大小、 位置和疊置順序的窗格。  
  
```  
virtual HDWP SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndInsertAfter`  
 識別`CWnd`物件前面這`CWnd`疊置順序的物件。 如需詳細資訊，請參閱[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 [in] `x`  
 指定視窗的左側位置。  
  
 [in] `y`  
 指定視窗頂端的位置。  
  
 [in] `cx`  
 指定視窗的寬度。  
  
 [in] `cy`  
 指定視窗的高度。  
  
 [in] `nFlags`  
 指定的大小和位置選項。 如需詳細資訊，請參閱[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 [in] `hdwp`  
 包含一個或多個視窗的大小和位置資訊的結構的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 更新後延後的視窗位置結構的控制代碼或`NULL`。  
  
### <a name="remarks"></a>備註  
 如果`pWndInsertAfter`是`NULL`，這個方法會呼叫[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。 如果`pWndInsertAfter`是非`NULL`，這個方法會呼叫`DeferWindowPos`。  
  
##  <a name="showpane"></a>CBasePane::ShowPane  
 顯示或隱藏窗格。  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 指定是否要顯示 ( `TRUE`) 或隱藏 ( `FALSE`) 窗格。  
  
 [in] `bDelay`  
 如果`TRUE`，重新計算停駐配置會延遲。  
  
 [in] `bActivate`  
 如果`TRUE`，窗格為作用中時顯示。  
  
### <a name="remarks"></a>備註  
 這個方法會顯示或隱藏窗格。 使用這個方法，而不是`ShowWindow`因為這個方法會通知相關的停駐管理員相關的變更窗格的可見性。  
  
 使用[CBasePane::IsVisible](#isvisible)以判斷目前的可見性 窗格。  
  
##  <a name="stretchpane"></a>CBasePane::StretchPane  
 垂直或水平伸展窗格。  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>參數  
 [in] `nLength`  
 用來拉長窗格長度。  
  
 [in] `bVert`  
 如果`TRUE`，垂直延伸 窗格。 如果`FALSE`，水平縮放的窗格。  
  
### <a name="return-value"></a>傳回值  
 [延伸] 窗格的大小。  
  
##  <a name="undockpane"></a>CBasePane::UndockPane  
 移除停駐位置、 預設滑桿或目前固定的迷你框架視窗的窗格。  
  
```  
virtual void UndockPane(BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bDelay`  
 如果為 TRUE，停駐配置時不會重新計算立即。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來操作窗格狀態，或排除的停駐配置的窗格。  
  
 如果您想要繼續使用此窗格中，呼叫[CBasePane::DockPane](#dockpane)或[CBasePane::FloatPane](#floatpane)之前呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)

