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
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365942"
---
# <a name="ctabbedpane-class"></a>CTabbedPane 類別

實作具有可拆式索引標籤之窗格的功能。

或更多的詳細資訊,請參閱位於 Visual Studio 安裝的**\\VC\\\\atlmfc src mfc**資料夾中的原始程式碼。

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
|[CTabbedPane::DetachPane](#detachpane)|(覆蓋[CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|啟用或停用索引標籤的自動著色。|
|[CTabbedPane::FloatTab](#floattab)|浮動窗格,但前提是窗格當前駐留在可拆卸選項卡中。(覆蓋[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).|
|[CTabbedPane::GetTabArea](#gettabarea)|傳回索引標籤式視窗內的索引標籤區域的大小和位置。|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|決定索引標籤式窗格是否可切換為自動隱藏模式。 (覆蓋[CBaseTabbed 窗格::具有 AutoHideMode.)](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)|
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

要指定常規選項卡而不是 Outlook 樣式選項卡,請將AFX_CBRS_REGULAR_TABS樣式傳遞給[CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex)方法。

如果您建立具有可卸離索引標籤的索引標籤式窗格，架構可能會自動終結該窗格，因此您不應儲存指標。 若要取得索引標籤式窗格的指標，請呼叫 `CBasePane::GetParentTabbedPane` 方法。

## <a name="example"></a>範例

在此範例中，我們會建立 `CTabbedPane` 物件。 接下來,我們使用[CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab)附加其他選項卡。

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

建立選項卡式控制列物件的另一種方法是使用[可多克窗格::AttachToTabwnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)。 這個方法`AttachToTabWnd`使用 CDockablePane 設定的執行時類別資訊動態建立選項卡式窗格物件[::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)。

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

**標題:** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane::D埃塔奇帕內

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

[在]*bHide*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbed 窗格::開啟 TabAutoColor

啟用或停用索引標籤的自動著色。

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 以啟用選項卡的自動著色;否則,FALSE。

### <a name="remarks"></a>備註

使用此靜態方法在應用程式中的所有選項卡窗格中啟用或禁用選項卡的自動著色。 啟用此功能後,每個選項卡都由其自己的顏色填充。 您可以通過調用[CMFCBaseTabCtrl::getAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors)方法找到用於為選項卡著色的顏色清單。

您可以通過調用[CTabbedPane::setTabAutoColors](#settabautocolors)來指定將用於選項卡的顏色清單。

預設會停用這個選項。

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbed窗格::浮動選項卡

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>
[在]*nTabID*<br/>
[在]*基方法*<br/>
[在]*bHide*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbed窗格::取得塔布區域

在選項卡式視窗中返回選項卡區域的大小和位置。

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
[出]包含頂部選項卡區域的大小和位置(螢幕座標)。

*rectTab 區域底部*<br/>
[出]包含底部選項卡區域的大小和位置(螢幕座標)。

### <a name="remarks"></a>備註

框架調用此方法以確定如何停靠使用者拖動的窗格。 當使用者將窗格拖動到目標窗格的選項卡區域時,框架會嘗試將其添加為目標窗格的新選項卡。 否則,它將嘗試將窗格停靠到目標窗格的一側,這涉及使用分隔兩個窗格的窗格分隔器創建新窗格容器。

重寫`CTabbedPane`派生類中的此方法以更改此行為。

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane::GetTabwnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbed窗格::具有自動隱藏模式

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbed 窗格::位置位置底部

決定索引標籤是否位於視窗底部。

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>傳回值

如果選項卡區域位於選項卡式視窗的底部,則為 TRUE;如果選項卡區域位於選項卡式視窗的底部,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbed窗格::m_bTabsAlwaysTop

應用程式中的索引標籤的預設位置。

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>備註

將此靜態成員設置為 TRUE 以強制應用程式中的所有選項卡顯示在選項卡式窗格的頂部。

必須在創建選項卡式窗格之前設置此值。

預設值為 FALSE。

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC

自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>備註

如果要在選項卡式窗格中使用自定義選項卡式視窗,則將此靜態成員`CMFCTabCtrl`變數設置為指向派生物件的運行時類資訊的指標。

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbed窗格::重置選項卡

將所有的索引標籤式窗格重設為預設狀態。

```
static void ResetTabs();
```

### <a name="remarks"></a>備註

呼叫此方法將所有選項卡式窗格還原到其預設狀態。 呼叫時,此方法將重置所有選項卡式窗格的邊框大小和自動顏色狀態。

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbed 窗格::設定 TabAuto 顏色

設定啟用自動顏色功能時使用的自訂顏色的清單。

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>參數

*阿爾顏色*<br/>
[在]包含要設置的顏色陣列。

### <a name="remarks"></a>備註

使用此方法可以自定義啟用自動顏色功能時使用的顏色清單。 這是一個靜態函數,會影響應用程式中的所有選項卡式窗格。

使用[CTabbed 窗格:啟用 TabAutoColor](#enabletabautocolor)以啟用或關閉自動顏色功能。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
