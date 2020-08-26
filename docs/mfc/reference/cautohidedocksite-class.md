---
title: CAutoHideDockSite 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 14db8d93ea7706b3a4daad2ba751f8410974f6cb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841632"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 類別

會 `CAutoHideDockSite` 擴充 [CDockSite 類別](../../mfc/reference/cdocksite-class.md) ，以執行自動隱藏停駐窗格。

## <a name="syntax"></a>語法

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱 | 描述 |
|-|-|
|名稱|描述|
|`CAutoHideDockSite::CAutoHideDockSite`|建構 `CAutoHideDockSite` 物件。|
|`CAutoHideDockSite::~CAutoHideDockSite`|解構函式。|

### <a name="public-methods"></a>公用方法

| 名稱 | 描述 |
|-|-|
|名稱|描述|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指出是否 `CAutoHideDockSite` 顯示在窗格功能表上。|
|[CAutoHideDockSite：： CanAcceptPane](#canacceptpane)|判斷基底窗格物件是否衍生自 [CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)。|
|[CAutoHideDockSite：:D ockPane](#dockpane)|將窗格停駐于此 `CAuotHideDockSite` 物件。|
|[CAutoHideDockSite：： GetAlignRect](#getalignrect)|以螢幕座標抓取 dock 網站的大小。|
|[CAutoHideDockSite：： RepositionPanes](#repositionpanes)|`CAutoHideDockSite`以全域邊界和按鈕間距來重繪上的窗格。|
|[CAutoHideDockSite：： SetOffsetLeft](#setoffsetleft)|設定停駐列左邊的邊界。|
|[CAutoHideDockSite：： SetOffsetRight](#setoffsetright)|設定銜接列右邊的邊界。|
|[CAutoHideDockSite：： UnSetAutoHideMode](#unsetautohidemode)|針對上的物件呼叫 [CMFCAutoHideBar：： UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) `CAutoHideDockSite` 。|

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|名稱|描述|
|[CAutoHideDockSite：： m_nExtraSpace](#m_nextraspace)|定義工具列和銜接列邊緣之間的空間大小。 此空間是從左邊緣或上邊緣測量，視 dock 空間的對齊方式而定。|

## <a name="remarks"></a>備註

當您呼叫 [CFrameWndEx：： EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)時，架構會自動建立 `CAutoHideDockSite` 物件。 在大部分情況下，您應該不需要直接具現化或使用這個類別。

停駐列是停駐窗格左邊與 [CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)左側之間的間距。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>範例

下列範例示範如何 `CAutoHideDockSite` 從物件取出物件 `CMFCAutoHideBar` ，以及如何設定停駐列的左邊和右邊界。

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>規格需求

**標頭：** afxautohidedocksite。h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a> CAutoHideDockSite：： CanAcceptPane

判斷基底窗格是否為 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 物件或衍生自 `CMFCAutoHideBar` 。

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>參數

*pBar*\
在架構測試的基底窗格。

### <a name="return-value"></a>傳回值

如果 *pBar* 衍生自，則為 TRUE `CMFCAutoHideBar` ;否則為 FALSE。

### <a name="remarks"></a>備註

如果基底窗格物件衍生自 `CMFCAutoHideBar` ，它可以包含 `CAutoHideDockSite` 。

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a> CAutoHideDockSite：:D ockPane

將窗格停駐于這個 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) 物件。

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

*pWnd*\
在架構所停靠的窗格。

*dockMethod*\
在窗格的停駐選項。

*lpRect*\
在指定固定窗格界限的矩形。

### <a name="remarks"></a>備註

預設的執行不會使用 *dockMethod*參數，該參數會提供供日後使用。

如果 *lpRect* 為 Null，則架構會將窗格置於 dock 網站上的預設位置。 如果 dock 網站是水準的，則預設位置是位於 dock 網站的最左邊。 否則，預設位置會位於 dock 網站的最上方。

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a> CAutoHideDockSite：： GetAlignRect

以螢幕座標抓取 dock 網站的大小。

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

*矩形*\
在矩形的參考。 方法會在此矩形中儲存 dock 網站的大小。

### <a name="remarks"></a>備註

矩形會針對位移邊界進行調整，使其不包含在內。

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a> CAutoHideDockSite：： m_nExtraSpace

[CAutoHideDockSite 類別](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)物件邊緣之間的空間大小。

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>備註

當停 `CMFCAutoHideBar` 駐在上時 `CAutoHideDockSite` ，它不應該佔用整個 dock 網站。 這個全域變數會控制左邊或上框線與對應邊緣之間的額外空間 `CMFCAutoHideBar` `CAutoHideDockSite` 。 是否使用頂端或左邊緣取決於目前的對齊方式。

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a> CAutoHideDockSite：： SetOffsetLeft

設定停駐列左邊的邊界。

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>參數

*nOffset*<br/>
在新的位移。

### <a name="remarks"></a>備註

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 物件是在物件上以靜態方式定位 `CAutoHideDockSite` 。 這表示使用者無法手動變更物件的位置 `CMFCAutoHideBar` 。 `SetOffsetLeft`方法會控制左邊最左邊和左邊之間的間距（） `CMFCAutoHideBar` `CAutoHideDockSite` 。

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a> CAutoHideDockSite：： SetOffsetRight

設定銜接列右邊的邊界。

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>參數

*nOffset*<br/>
在新的位移。

### <a name="remarks"></a>備註

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 物件是在物件上以靜態方式定位 `CAutoHideDockSite` 。 這表示使用者無法手動變更物件的位置 `CMFCAutoHideBar` 。 `SetOffsetRight`方法會控制右邊最右邊和右邊之間的間隔間距 `CMFCAutoHideBar` `CAutoHideDockSite` 。

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a> CAutoHideDockSite：： RepositionPanes

重新繪製 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)上的窗格。

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>參數

*rectNewClientArea*\
在保留值。

### <a name="remarks"></a>備註

預設的執行不會使用 *rectNewClientArea*。 它會以全域工具列的邊界和按鈕間距來重繪窗格。

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a> CAutoHideDockSite：： UnSetAutoHideMode

針對 dock 網站上的物件呼叫 [CMFCAutoHideBar：： UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) 。

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>參數

*pAutoHideToolbar*\
在位於上之 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) 物件窗格的指標 `CAutoHideDockSite` 。

### <a name="remarks"></a>備註

這個方法會搜尋包含 *pAutoHideToolbar*的資料列。 它會呼叫 `CMFCAutoHideBar.UnSetAutoHideMode` 該資料 `CMFCAutoHideBar` 列上的所有物件。 如果找不到 *pAutoHideToolbar* ，或它是 Null，這個方法會呼叫 `CMFCAutoHideBar.UnSetAutoHideMode` 上的所有 `CMFCAutoHideBar` 物件 `CAutoHideDockSite` 。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite 類別](../../mfc/reference/cdocksite-class.md)
