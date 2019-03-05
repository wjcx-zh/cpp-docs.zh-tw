---
title: CTabbedPane 類別
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: af9c65e51f7230b0fc6a59d0eed42eca08d24837
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263347"
---
# <a name="ctabbedpane-class"></a>CTabbedPane 類別

實作具有可拆式索引標籤之窗格的功能。

或更多詳細資料，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

## <a name="syntax"></a>語法

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(覆寫[cbasetabbedpane:: Detachpane](../../mfc/reference/cbasetabbedpane-class.md#detachpane)。)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|啟用或停用索引標籤的自動著色。|
|[CTabbedPane::FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。(覆寫[cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|
|[CTabbedPane::GetTabArea](#gettabarea)|傳回索引標籤式視窗內的索引標籤區域的大小和位置。|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|決定索引標籤式窗格是否可切換為自動隱藏模式。 (覆寫[cbasetabbedpane:: Hasautohidemode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)。)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|決定索引標籤是否位於視窗底部。|
|[CTabbedPane::ResetTabs](#resettabs)|將所有的索引標籤式窗格重設為預設狀態。|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|設定在自動套色功能啟用時可以使用的自訂色彩清單。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|應用程式中的索引標籤的預設位置。|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。|

## <a name="remarks"></a>備註

當使用者指向第二個窗格的標題，將一個窗格附加到另一個窗格時，架構會自動建立此類別的執行個體。 架構所建立的所有索引標籤式窗格，ID 皆為 -1。

若要指定一般索引標籤，而不是 Outlook 樣式索引標籤，將傳遞的 AFX_CBRS_REGULAR_TABS 樣式[cdockablepane:: Createex](../../mfc/reference/cdockablepane-class.md#createex)方法。

如果您建立具有可卸離索引標籤的索引標籤式窗格，架構可能會自動終結該窗格，因此您不應儲存指標。 若要取得索引標籤式窗格的指標，請呼叫 `CBasePane::GetParentTabbedPane` 方法。

## <a name="example"></a>範例

在此範例中，我們會建立 `CTabbedPane` 物件。 接下來，我們使用[cbasetabbedpane:: Addtab](../../mfc/reference/cbasetabbedpane-class.md#addtab)附加其他索引標籤。

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

## <a name="example"></a>範例

若要建立索引標籤式的控制列物件的另一種方式是使用[cdockablepane:: Attachtotabwnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)。 `AttachToTabWnd`方法以動態方式建立索引標籤式的窗格物件，使用所設定的執行階段類別資訊[cdockablepane:: Settabbedpanertc](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)。

在此範例中，我們會以動態方式建立索引標籤式窗格、附加兩個索引標籤，然後使第二個索引標籤無法卸離。

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>需求

**標頭：** afxTabbedPane.h

##  <a name="detachpane"></a>  CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

[in] *pBar*<br/>

[in] *bHide*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="enabletabautocolor"></a>  CTabbedPane::EnableTabAutoColor

啟用或停用索引標籤的自動著色。

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]若要啟用的索引標籤; 的自動著色，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用這個靜態方法來啟用或停用在應用程式中的所有索引標籤式窗格中的索引標籤的自動著色。 啟用這項功能時，每個索引標籤會依自己的色彩填滿。 您可以找到用來藉由呼叫色彩索引標籤的色彩清單[CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors)方法。

您可以指定將用於藉由呼叫索引標籤的色彩清單[CTabbedPane::SetTabAutoColors](#settabautocolors)。

根據預設，此選項已停用。

##  <a name="floattab"></a>  CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

[in] *pBar*<br/>
[in] *nTabID*<br/>
[in]*dockMethod*<br/>
[in] *bHide*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="gettabarea"></a>  CTabbedPane::GetTabArea

傳回的大小和位置的索引標籤區域中的索引標籤式視窗。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
[out]包含的大小和位置，包括螢幕座標中的最上層索引標籤區域。

*rectTabAreaBottom*<br/>
[out]包含的大小和位置，包括螢幕座標中的底部索引標籤區域。

### <a name="remarks"></a>備註

架構會呼叫這個方法，以判斷停駐窗格中的使用者正在拖曳的方式。 當使用者拖曳窗格的 [目標] 窗格的索引標籤區域時，架構會嘗試將它新增為新的索引標籤的 [目標] 窗格。 否則，它會嘗試停駐牽涉到建立新的窗格容器與窗格分割線分隔的兩個窗格的 [目標] 窗格的側邊的窗格。

覆寫這個方法在`CTabbedPane`-衍生的類別，來變更此行為。

##  <a name="gettabwnd"></a>  CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="hasautohidemode"></a>  CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="istablocationbottom"></a>  CTabbedPane::IsTabLocationBottom

決定索引標籤是否位於視窗底部。

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>傳回值

如果索引標籤區域位於底部的索引標籤式視窗中，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="m_btabsalwaystop"></a>  CTabbedPane::m_bTabsAlwaysTop

應用程式中的索引標籤的預設位置。

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>備註

若要顯示在索引標籤式窗格的頂端應用程式中設定這個靜態成員，以 true 會強制所有索引標籤。

在建立索引標籤式的窗格之前，您必須設定此值。

預設值為 FALSE。

##  <a name="m_ptabwndrtc"></a>  CTabbedPane::m_pTabWndRTC

自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>備註

設定此靜態成員變數的執行階段類別資訊指標`CMFCTabCtrl`-衍生物件，如果您使用自訂的索引標籤式的視窗內的索引標籤式窗格。

##  <a name="resettabs"></a>  CTabbedPane::ResetTabs

將所有的索引標籤式窗格重設為預設狀態。

```
static void ResetTabs();
```

### <a name="remarks"></a>備註

呼叫這個方法，以還原為其預設狀態的所有索引標籤式的窗格。 呼叫時，這個方法會重設的框線大小和自動色彩狀態的所有索引標籤式窗格。

##  <a name="settabautocolors"></a>  CTabbedPane::SetTabAutoColors

設定自動套色功能啟用時，會使用的自訂色彩的清單。

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>參數

*arColors*<br/>
[in]包含要設定色彩的陣列。

### <a name="remarks"></a>備註

使用這個方法來自訂在自動套色功能啟用時，便會使用的色彩清單。 這是靜態的函式，而且會影響您的應用程式中的所有索引標籤式的窗格。

使用[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)啟用或停用自動套色功能。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
