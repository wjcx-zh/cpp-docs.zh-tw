---
title: CMFCAutoHideBar 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: 62750f4fb1261f4f30286297c3a240ab67e6df1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369905"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar 類別

`CMFCAutoHideBar` 類別是實作自動隱藏功能的特殊工具列類別。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(覆蓋[CBasePane::CalcFixed 佈局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Create](#create)|創建控制欄並將其附加到[CPane](../../mfc/reference/cpane-class.md)物件。 (覆蓋[CPane:建立](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|當特殊窗格功能表即將顯示時由架構呼叫。 (覆蓋[CPane:在顯示控制欄選單](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(覆蓋[CPane:設定活動群組](../../mfc/reference/cpane-class.md#setactiveingroup)。)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|垂直或水平伸展窗格。 (覆蓋[CBasePane:拉伸窗格](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|用戶將滑鼠游標放在[CMFCAutoHideButton 類](../../mfc/reference/cmfcautohidebutton-class.md)上的時間延遲與框架顯示關聯視窗的瞬間之間的時間延遲。|

## <a name="remarks"></a>備註

當使用者將停駐窗格切換為自動隱藏模式時，架構會自動建立 `CMFCAutoHideBar` 物件。 它還創建必要的[CAutoHideDock SiteSite](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)物件。 每個 `CAutoHideDockSite` 物件與一個個別的 `CMFCAutoHideButton` 相關聯。

當使用者的滑鼠停留在 `CMFCAutoHideButton` 上方時，`CMFCAutoHideBar` 類別會實作 `CAutoHideDockSite` 的顯示。 當工具列收到 WM_MOUSEMOVE 訊息時，`CMFCAutoHideBar` 會啟動計時器。 當計時器完成時，會將 WM_TIMER 事件通知傳送給工具列。 工具列會藉由檢查滑鼠指標是否放置在相同的自動隱藏按鈕上方 (在計時器啟動時所放置)，以處理此事件。 如果是，則顯示附加的 `CAutoHideDockSite`。

您可以設定 `m_nShowAHWndDelay` 來控制計時器的延遲長度。 預設值為 400 毫秒。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCAutoHideBar` 物件及使用其 `GetDockSiteRow` 方法。

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFC 自動隱藏列:新增自動隱藏視窗

將功能加入 `CDockablePane` 視窗以自動隱藏該功能。

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>參數

*pAutoHidewnd*<br/>
[在]要隱藏的視窗。

*dwalignment*<br/>
[在]指定自動隱藏按鈕與應用程式視窗對齊的值。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

*dwAlignment*參數指示自動隱藏按鈕駐留在應用程式中的位置。 這個參數可以是下列任何一個值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFC 自動隱藏列::允許顯示帕內選單

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHidebar::CalcFixed佈局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[在]*b 伸*<br/>

[在]*布霍茲*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFC 自動隱藏列:CMFC自動隱藏列

建構 CMFCAutoHideBar 物件。

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHidebar:建立

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

*lpszClass 名稱*<br/>

*dwStyle*<br/>

*矩形*<br/>

*pparentwnd*<br/>

*nID*<br/>

*dwControlBar 樣式*<br/>

*pContext*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHidebar:取得第一AH視窗

傳回應用程式中第一個自動隱藏視窗的指標。

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>傳回值

應用程式中的第一個自動隱藏視窗，或如果沒有，則為 NULL。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHidebar:取得可見計數

取得可見的自動隱藏按鈕數目。

```
int GetVisibleCount();
```

### <a name="return-value"></a>傳回值

傳回可見的自動隱藏按鈕數目。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHidebar:m_nShowAHWndDelay

用戶將滑鼠游標放在[CMFCAutoHideButton 類](../../mfc/reference/cmfcautohidebutton-class.md)上的時間延遲與框架顯示關聯視窗的瞬間之間的時間延遲。

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>備註

當使用者將滑鼠游標放在上`CMFCAutoHideButton`時 ,框架顯示關聯的視窗之前會有輕微的延遲。 此參數確定該延遲的長度(以毫秒為單位)。

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFC 自動隱藏列:在顯示控制列選單

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>參數

[在]*CPoint*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFC 自動隱藏列:刪除自動隱藏視窗

移除和終結自動隱藏視窗。

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>參數

CdockPane® *pAutohided*自動隱藏視窗要刪除。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutohidebar::設定活動組

將自動隱藏列標幟為作用中。

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>參數

[在]BOOL *bActive* TRUE 設置為活動狀態;否則 FALSE。

### <a name="remarks"></a>備註

請參閱 [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)。

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHidebar::設定最近可見狀態

```
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>參數

*bState*<br/>
[在]要設置的狀態。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFC 自動隱藏列:顯示自動隱藏視窗

顯示自動隱藏視窗。

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>參數

*pAutoHidewnd*<br/>
[在]要顯示的視窗。

*b 顯示*<br/>
[在]TRUE 以顯示視窗。

*bDelay*<br/>
[在]忽略此參數。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFC自動隱藏列:拉伸窗格

將摺疊狀態的自動隱藏列調整成適合 `CMFCAutoHideButton` 物件的大小。

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>參數

*N 長度*<br/>
[在]該值在基本實現中未使用。 在衍生實作中，這個值可用來表示已調整窗格的長度。

*bVert*<br/>
[在]該值在基本實現中未使用。 在派生實現中,使用 TRUE 處理自動隱藏欄垂直摺疊的情況,對於自動隱藏欄水平摺疊的情況,請使用 FALSE。

### <a name="return-value"></a>傳回值

產生的已調整窗格大小。

### <a name="remarks"></a>備註

衍生類別可以覆寫這個方法以自訂行為。

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFC 自動隱藏列:取消設定自動隱藏模式

停用自動隱藏列群組的自動隱藏模式。

```
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>參數

[in] pFirstBarInGroup A 指標指向組中的第一個自動隱藏欄。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHidebar::更新可見狀態

架構會在需要重新繪製自動隱藏列時呼叫。

```
void UpdateVisibleState();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite 類別](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)
