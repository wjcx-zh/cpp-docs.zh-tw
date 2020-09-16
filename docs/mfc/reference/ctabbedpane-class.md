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
ms.openlocfilehash: cfc0a3099b1d5ff9bd1093cc911745bd61cde64c
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686635"
---
# <a name="ctabbedpane-class"></a>CTabbedPane 類別

實作具有可拆式索引標籤之窗格的功能。

或更詳細的資訊，請參閱位於 Visual Studio 安裝的 **VC \\ atlmfc \\ src \\ mfc** 資料夾中的原始程式碼。

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
|[CTabbedPane::DetachPane](#detachpane)| (覆寫 [CBaseTabbedPane：:D etachpane](../../mfc/reference/cbasetabbedpane-class.md#detachpane)。 ) |
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|啟用或停用索引標籤的自動著色。|
|[CTabbedPane::FloatTab](#floattab)|浮動窗格，但只有在窗格目前位於可卸離的索引標籤中。 (覆寫 [CBaseTabbedPane：： FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。 ) |
|[CTabbedPane::GetTabArea](#gettabarea)|傳回索引標籤式視窗內的索引標籤區域的大小和位置。|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|決定索引標籤式窗格是否可切換為自動隱藏模式。  (覆寫 [CBaseTabbedPane：： HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)。 ) |
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

若要指定一般索引標籤而非 Outlook 樣式的索引標籤，請將 AFX_CBRS_REGULAR_TABS 樣式傳遞給 [CDockablePane：： CreateEx](../../mfc/reference/cdockablepane-class.md#createex) 方法。

如果您建立具有可卸離索引標籤的索引標籤式窗格，架構可能會自動終結該窗格，因此您不應儲存指標。 若要取得索引標籤式窗格的指標，請呼叫 `CBasePane::GetParentTabbedPane` 方法。

## <a name="examples"></a>範例

在此範例中，我們會建立 `CTabbedPane` 物件。 接下來，我們會使用 [CBaseTabbedPane：： AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) 附加其他索引標籤。

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

建立索引標籤式控制列物件的另一種方式是使用 [CDockablePane：： AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)。 `AttachToTabWnd`方法會使用[CDockablePane：： SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)所設定的執行時間類別資訊，以動態方式建立索引標籤式窗格物件。

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

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>需求

**標頭：** afxTabbedPane。h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a> CTabbedPane：:D etachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

在 *pBar*<br/>

在 *bHide*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a> CTabbedPane::EnableTabAutoColor

啟用或停用索引標籤的自動著色。

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示啟用索引標籤的自動著色;否則為 FALSE。

### <a name="remarks"></a>備註

使用這個靜態方法來啟用或停用應用程式中所有索引標籤式窗格的索引標籤自動著色。 啟用這項功能時，每個索引標籤都會填入自己的色彩。 您可以藉由呼叫 [CMFCBaseTabCtrl：： GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) 方法，尋找用來將索引標籤色彩的色彩清單。

您可以藉由呼叫 [CTabbedPane：： SetTabAutoColors](#settabautocolors)，指定將用於索引標籤的色彩清單。

預設會停用這個選項。

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a> CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

在 *pBar*<br/>
在 *nTabID*<br/>
在 *dockMethod*<br/>
在 *bHide*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a> CTabbedPane::GetTabArea

傳回索引標籤式視窗中索引標籤區域的大小和位置。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
擴展包含頂端索引標籤區域的大小和位置（以螢幕座標為單位）。

*rectTabAreaBottom*<br/>
擴展包含底部索引標籤區域的大小和位置（以螢幕座標為單位）。

### <a name="remarks"></a>備註

架構會呼叫這個方法，以決定如何停駐使用者正在拖曳的窗格。 當使用者將窗格拖曳到目標窗格的索引標籤區域時，架構會嘗試將它新增為目標窗格的新索引標籤。 否則，它會嘗試將窗格停駐在目標窗格的側邊，這牽涉到使用窗格分隔線來建立新的窗格容器來分隔兩個窗格。

在衍生的類別中覆寫這個方法 `CTabbedPane` ，以變更此行為。

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a> CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a> CTabbedPane::IsTabLocationBottom

決定索引標籤是否位於視窗底部。

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>傳回值

如果索引標籤區域位於索引標籤式視窗的底部，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a> CTabbedPane：： m_bTabsAlwaysTop

應用程式中的索引標籤的預設位置。

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>備註

將這個靜態成員設為 TRUE，以強制將應用程式中的所有索引標籤顯示在索引標籤式窗格的上方。

您必須在建立索引標籤式窗格之前設定這個值。

預設值為 FALSE。

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a> CTabbedPane：： m_pTabWndRTC

自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>備註

`CMFCTabCtrl`如果您使用索引標籤式窗格內的自訂索引標籤式視窗，請將這個靜態成員變數設定為衍生物件之執行時間類別資訊的指標。

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a> CTabbedPane::ResetTabs

將所有的索引標籤式窗格重設為預設狀態。

```
static void ResetTabs();
```

### <a name="remarks"></a>備註

呼叫此方法可將所有索引標籤式窗格還原為其預設狀態。 呼叫時，這個方法會重設所有索引標籤式窗格的框線大小和自動色彩狀態。

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a> CTabbedPane::SetTabAutoColors

設定啟用自動色彩功能時所使用的自訂色彩清單。

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>參數

*arColors*<br/>
在包含要設定之色彩的陣列。

### <a name="remarks"></a>備註

您可以使用這個方法來自訂啟用自動色彩功能時所使用的色彩清單。 這是靜態函式，會影響您應用程式中的所有索引標籤式窗格。

使用 [CTabbedPane：： EnableTabAutoColor](#enabletabautocolor) 來啟用或停用自動色彩功能。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
