---
title: "CMFCAutoHideBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAutoHideBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideToolBar class
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
caps.latest.revision: 35
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
ms.openlocfilehash: db15fc9fa3925230e372b6e13368f455dcfbb1a9
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar 類別
`CMFCAutoHideBar` 類別是實作自動隱藏功能的特殊工具列類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|  
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(覆寫[CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|  
|[CMFCAutoHideBar::Create](#create)|建立一種控制列，並將它附加[CPane](../../mfc/reference/cpane-class.md)物件。 (覆寫[CPane::Create](../../mfc/reference/cpane-class.md#create)。)|  
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||  
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|當特殊窗格功能表即將顯示時由架構呼叫。 (覆寫[CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||  
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(覆寫[CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)。)|  
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||  
|[CMFCAutoHideBar::StretchPane](#stretchpane)|垂直或水平伸展窗格。 (覆寫[CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane)。)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||  
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|當使用者將滑鼠游標置於目前的時間間隔[CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)和目前的架構時顯示的相關聯的視窗。|  
  
## <a name="remarks"></a>備註  
 當使用者將停駐窗格切換為自動隱藏模式時，架構會自動建立 `CMFCAutoHideBar` 物件。 它也會建立所需之[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)物件。 每個 `CAutoHideDockSite` 物件與一個個別的 `CMFCAutoHideButton` 相關聯。  
  
 當使用者的滑鼠停留在 `CMFCAutoHideButton` 上方時，`CMFCAutoHideBar` 類別會實作 `CAutoHideDockSite` 的顯示。 當工具列收到 WM_MOUSEMOVE 訊息時，`CMFCAutoHideBar` 會啟動計時器。 當計時器完成時，會將 WM_TIMER 事件通知傳送給工具列。 工具列會藉由檢查滑鼠指標是否放置在相同的自動隱藏按鈕上方 (在計時器啟動時所放置)，以處理此事件。 如果是，則顯示附加的 `CAutoHideDockSite`。  
  
 您可以設定 `m_nShowAHWndDelay` 來控制計時器的延遲長度。 預設值為 400 毫秒。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構 `CMFCAutoHideBar` 物件及使用其 `GetDockSiteRow` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&26;](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxautohidebar.h  
  
##  <a name="a-nameaddautohidewindowa--cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow  
 將功能加入 `CDockablePane` 視窗以自動隱藏該功能。  
  
```  
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>參數  
 [in] `pAutoHideWnd`  
 您要隱藏的視窗。  
  
 [in] `dwAlignment`  
 指定自動隱藏按鈕與應用程式視窗之對齊方式的值。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 `dwAlignment` 參數表示自動隱藏按鈕在應用程式中的位置。 這個參數可以是下列任何一個值：  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="a-nameallowshowonpanemenua--cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowOnPaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecalcfixedlayouta--cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecmfcautohidebara--cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar  
 建構 CMFCAutoHideBar 物件。  
  
```  
CMFCAutoHideBar();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecreatea--cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHideBar::Create  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszClassName`  
 [in] `dwStyle`  
 [in] `rect`  
 [in] `pParentWnd`  
 [in] `nID`  
 [in] `dwControlBarStyle`  
 [in] `pContext`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetfirstahwindowa--cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow  
 傳回應用程式中第一個自動隱藏視窗的指標。  
  
```  
CDockablePane* GetFirstAHWindow();
```  
  
### <a name="return-value"></a>傳回值  
 應用程式中的第一個自動隱藏視窗，或如果沒有，則為 NULL。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetvisiblecounta--cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount  
 取得可見的自動隱藏按鈕數目。  
  
```  
int GetVisibleCount();
```  
  
### <a name="return-value"></a>傳回值  
 傳回可見的自動隱藏按鈕數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemnshowahwnddelaya--cmfcautohidebarmnshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay  
 當使用者將滑鼠游標置於目前的時間間隔[CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)和目前的架構時顯示的相關聯的視窗。  
  
```  
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;  
```  
  
### <a name="remarks"></a>備註  
 當使用者將滑鼠游標置於`CMFCAutoHideButton`，架構會顯示相關聯的視窗之前，會稍微延遲。 這個參數會決定該延遲，以毫秒為單位的長度。  
  
##  <a name="a-nameonshowcontrolbarmenua--cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>參數  
 [in] `CPoint`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameremoveautohidewindowa--cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow  
 移除和終結自動隱藏視窗。  
  
```  
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```  
  
### <a name="parameters"></a>參數  
 CDockablePane *`pAutoHideWnd`  
 要移除的自動隱藏視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetactiveingroupa--cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup  
 將自動隱藏列標幟為作用中。  
  
```  
virtual void SetActiveInGroup(BOOL bActive);  
```  
  
### <a name="parameters"></a>參數  
 [in]BOOL`bActive`  
 TRUE 表示要設定為作用中，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 請參閱[CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)。  
  
##  <a name="a-namesetrecentvisiblestatea--cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetRecentVisibleState(BOOL bState);
```  
  
### <a name="parameters"></a>參數  
 [in] `bState`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameshowautohidewindowa--cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow  
 顯示自動隱藏視窗。  
  
```  
BOOL ShowAutoHideWindow(
        CDockablePane* pAutoHideWnd,  
        BOOL bShow,  
        BOOL bDelay);  
```  
  
### <a name="parameters"></a>參數  
 [in]CDockablePane *`pAutoHideWnd`  
 [in]BOOL`bShow`  
 TRUE 表示要顯示視窗。  
  
 [in]BOOL`bDelay`  
 這個參數已忽略。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namestretchpanea--cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFCAutoHideBar::StretchPane  
 將摺疊狀態的自動隱藏列調整成適合 `CMFCAutoHideButton` 物件的大小。  
  
```  
virtual CSize StretchPane(
    int nLength,   
    BOOL bVert);
```  
  
### <a name="parameters"></a>參數  
 [in] `nLength`  
 這是基底實作中未使用的值。 在衍生實作中，這個值可用來表示已調整窗格的長度。  
  
 [in] `bVert`  
 這是基底實作中未使用的值。 在衍生的實作中，使用`TRUE`以處理的情況，[自動隱藏] 列會摺疊垂直和`FALSE`案例，其中 [自動隱藏] 列會摺疊水平的。  
  
### <a name="return-value"></a>傳回值  
 產生的已調整窗格大小。  
  
### <a name="remarks"></a>備註  
 衍生類別可以覆寫這個方法以自訂行為。  
  
##  <a name="a-nameunsetautohidemodea--cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode  
 停用自動隱藏列群組的自動隱藏模式。  
  
```  
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)  
```  
  
### <a name="parameters"></a>參數  
 [in] pFirstBarInGroup  
 群組中第一個自動隱藏列的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameupdatevisiblestatea--cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState  
 架構會在需要重新繪製自動隱藏列時呼叫。  
  
```  
void UpdateVisibleState();
```  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane 類別](../../mfc/reference/cpane-class.md)   
 [CAutoHideDockSite 類別](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)

