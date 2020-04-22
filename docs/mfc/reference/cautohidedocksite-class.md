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
ms.openlocfilehash: 1f23729ced02a151c6186bdcc72cb8938416be46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753007"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 類別

擴展`CAutoHideDockSite` [CDockSite 類](../../mfc/reference/cdocksite-class.md)以實現自動隱藏停靠窗格。

## <a name="syntax"></a>語法

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CAutoHideDockSite::CAutoHideDockSite`|建構 `CAutoHideDockSite` 物件。|
|`CAutoHideDockSite::~CAutoHideDockSite`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指示`CAutoHideDockSite`是否顯示在窗格功能表上。|
|[CAutoHideDock網站::接受窗格](#canacceptpane)|確定基本窗格物件是否派生自[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)。|
|[CAutoHideDock網站::DockPane](#dockpane)|將窗格停靠到此`CAuotHideDockSite`物件。|
|[CAutoHideDock網站::獲得對齊](#getalignrect)|在螢幕座標中檢索停靠網站的大小。|
|[CAutoHideDock網站:重新置放窗格](#repositionpanes)|`CAutoHideDockSite`使用全域邊距和按鈕間距重繪 上的窗格。|
|[CAutoHideDock網站::設定偏移左](#setoffsetleft)|設置停靠欄左側的邊距。|
|[CAutoHideDock網站::設定偏移權](#setoffsetright)|設置停靠欄右側的邊距。|
|[CAutoHideDock網站::取消設定自動隱藏模式](#unsetautohidemode)|調用[CMFCAutoHideBar::取消設置 AutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)上`CAutoHideDockSite`的物件。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|[CAutoHideDock網站:m_nExtraSpace](#m_nextraspace)|定義工具列和停靠欄邊緣之間的空間大小。 此空間從左邊緣或上邊緣測量,具體取決於停靠空間的對齊方式。|

## <a name="remarks"></a>備註

當您調用[CFrameWndEx::啟用自動隱藏窗格時](../../mfc/reference/cframewndex-class.md#enableautohidepanes),框架會自動創建`CAutoHideDockSite`一個 物件。 在大多數情況下,您不必直接實例化或使用此類。

停靠欄是停靠窗格左側和[CMFCAutoHideButton 類](../../mfc/reference/cmfcautohidebutton-class.md)左側之間的間隙。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>範例

下面的示例演示如何從`CAutoHideDockSite``CMFCAutoHideBar`物件檢索物件,以及如何設置停靠欄的左右邊距。

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>需求

**標題:** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDock網站::接受窗格

確定基本窗格是[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件還是派`CMFCAutoHideBar`生自 。

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pBar*|[在]框架測試的基本窗格。|

### <a name="return-value"></a>傳回值

如果*pBar*派`CMFCAutoHideBar`生自 ,則為 TRUE。否則。

### <a name="remarks"></a>備註

如果基礎窗格物件派生自`CMFCAutoHideBar`,它可以包含`CAutoHideDockSite`。

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDock網站::DockPane

將窗格停靠到此[CAutoHideDockSite 物件](../../mfc/reference/cautohidedocksite-class.md)。

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pwnd*|[在]框架停靠的窗格。|
|*基方法*|[在]窗格的停靠選項。|
|*lpRect*|[在]指定停靠窗格邊界的矩形。|

### <a name="remarks"></a>備註

預設實現不使用參數*dockMethod,* 這是為將來使用而提供的。

如果*lpRect*為 NULL,則框架將窗格置於停靠網站上的預設位置。 如果停靠網站是水準的,則預設位置位於停靠網站的最左側。 否則,默認位置位於停靠網站的頂部。

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDock網站::獲得對齊

在螢幕座標中檢索停靠網站的大小。

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*矩形*|[在]對矩形的引用。 該方法在此矩形中存儲停靠網站的大小。|

### <a name="remarks"></a>備註

矩形會針對偏移邊距進行調整,以便不包含它們。

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDock網站:m_nExtraSpace

[CAutoHideDockSite 類](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideBar 類](../../mfc/reference/cmfcautohidebar-class.md)物件邊緣之間的空間大小。

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>備註

`CMFCAutoHideBar`當 停靠在`CAutoHideDockSite`時 ,它不應佔用整個停靠網站。 此全域變數控制 的`CMFCAutoHideBar`左側或頂部邊框與相應`CAutoHideDockSite`邊之間的額外空間。 使用上邊緣還是左邊緣取決於當前對齊方式。

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDock網站::設定偏移左

設置停靠欄左側的邊距。

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>參數

*n位移*<br/>
[在]新的偏移量。

### <a name="remarks"></a>備註

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件以靜態方式放置`CAutoHideDockSite`在 物件上。 這意味著用戶無法手動更改`CMFCAutoHideBar`物件的位置。 該方法`SetOffsetLeft`控制`CMFCAutoHideBar`左側與左邊之間的`CAutoHideDockSite`間距 。

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDock網站::設定偏移權

設置停靠欄右側的邊距。

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>參數

*n位移*<br/>
[在]新的偏移量。

### <a name="remarks"></a>備註

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件以靜態方式放置`CAutoHideDockSite`在 物件上。 這意味著用戶無法手動更改`CMFCAutoHideBar`物件的位置。 該方法`SetOffsetRight`控制`CMFCAutoHideBar`右方與右側`CAutoHideDockSite`之間的間距 。

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDock網站:重新置放窗格

重繪[CAutoHideDock Site 上的](../../mfc/reference/cautohidedocksite-class.md)窗格。

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*rectNewClient區域*|[在]保留值。|

### <a name="remarks"></a>備註

預設可使用*rectNewClientArea*。 它使用全域工具列邊距和按鈕間距重繪窗格。

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDock網站::取消設定自動隱藏模式

呼叫[CMFCAutoHideBar::取消設定停靠網站上的物件的自動隱藏模式](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)。

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pAutoHideToolbar*|[在]指向 位於上的[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)`CAutoHideDockSite`物件窗格 的指標。|

### <a name="remarks"></a>備註

此方法搜索包含*pAutoHideToolbar*的行。 它調用`CMFCAutoHideBar.UnSetAutoHideMode`該行`CMFCAutoHideBar`上 的所有物件。 如果未找到*pAutoHideToolbar*或它是 NULL,則`CMFCAutoHideBar.UnSetAutoHideMode`此方法將`CMFCAutoHideBar``CAutoHideDockSite`呼叫上的所有物件。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)
