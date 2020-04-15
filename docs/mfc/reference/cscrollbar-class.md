---
title: CScrollBar 類別
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: 761d7e9db650c6d95e916c85bd7456d9b1c647c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318525"
---
# <a name="cscrollbar-class"></a>CScrollBar 類別

提供 Windows 捲軸控制項的功能。

## <a name="syntax"></a>語法

```
class CScrollBar : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CScrollBar:CScrollBar](#cscrollbar)|建構 `CScrollBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CScrollBar:建立](#create)|創建 Windows 滾動條並將其`CScrollBar`附加到 物件。|
|[CScrollBar::開啟捲動](#enablescrollbar)|啟用或停用一個捲軸的一或兩個箭號。|
|[CScrollBar::取得ScrollBarInfo](#getscrollbarinfo)|使用`SCROLLBARINFO`結構檢索有關滾動條的資訊。|
|[CScrollBar::取得捲動資訊](#getscrollinfo)|檢索有關滾動條的資訊。|
|[CScrollBar:抓取捲動限制](#getscrolllimit)|檢索滾動條的限制|
|[CScrollBar:抓取捲動位置](#getscrollpos)|擷取捲動方塊的目前位置。|
|[CScrollBar::抓動範圍](#getscrollrange)|檢索給定滾動條的當前最小和最大滾動條位置。|
|[CScrollBar::設定Scrollinfo](#setscrollinfo)|設定捲軸的相關資訊。|
|[CScrollBar::設定捲動位置](#setscrollpos)|設定滾動框的當前位置。|
|[CScrollBar::設定捲動範圍](#setscrollrange)|設定給定捲軸的最小和最大位置值。|
|[CScrollBar::顯示捲動列](#showscrollbar)|顯示或隱藏滾動條。|

## <a name="remarks"></a>備註

通過兩個步驟創建滾動條控件。 首先,調用構造`CScrollBar`函數建`CScrollBar`構物件,然後調用[Create](#create)成員函數以創建 Windows 滾動條控制`CScrollBar`件並將其附加到 物件。

如果在對話框中建立`CScrollBar`物件(透過對話框資源),則當使用者關閉對話框時`CScrollBar`, 將自動銷毀 。

如果在視窗中創建`CScrollBar`物件,則可能需要銷毀它。

如果在堆疊上`CScrollBar`創建物件,則會自動銷毀該物件。 如果使用**新**函數在`CScrollBar`堆上創建物件,**則必須在使用者**終止 Windows 滾動欄時調用刪除物件以銷毀該物件。

如果在`CScrollBar`物件中分配任何記憶體,請重寫`CScrollBar`析構函數以釋放分配。

有關使用`CScrollBar`的相關資訊,請參閱[控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar:建立

創建 Windows 滾動條並將其`CScrollBar`附加到 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定滾動條的樣式。 將[滾動條樣式](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)的任意組合應用於滾動條。

*矩形*<br/>
指定捲軸的大小和位置。 可以是`RECT`結構或`CRect`物件。

*pparentwnd*<br/>
指定滾動條的父視窗(通常是`CDialog`物件)。 它不得為 NULL。

*nID*<br/>
滾動條的控制 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

分兩步`CScrollBar`構造物件。 首先,調用構造函數,該構造函數構造`CScrollBar`物件;然後調用`Create`,它創建並初始化關聯的 Windows 滾動條並將`CScrollBar`其附加到 物件。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)應用於捲動條:

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_GROUP元件

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar:CScrollBar

建構 `CScrollBar` 物件。

```
CScrollBar();
```

### <a name="remarks"></a>備註

建構物件後,調用`Create`成員函數創建和初始化 Windows 滾動條。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::開啟捲動

啟用或停用一個捲軸的一或兩個箭號。

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>參數

*nArrowFlags*<br/>
指定滾動箭頭是啟用還是禁用,以及啟用或禁用哪些箭頭。 這裡可以是以下值之一:

- ESB_ENABLE_BOTH 啟用滾動條的兩個箭頭。

- ESB_DISABLE_LTUP禁用水平滾動條的左箭頭或垂直滾動條的向上箭頭。

- ESB_DISABLE_RTDN禁用水平滾動條的右箭頭或垂直滾動條的向下箭頭。

- ESB_DISABLE_BOTH禁用滾動條的兩個箭頭。

### <a name="return-value"></a>傳回值

如果箭頭已啟用或禁用(如指定)則為非零;否則 0,表示箭頭已處於請求狀態或發生錯誤。

### <a name="example"></a>範例

  請參考[CScrollBar 的範例::設定捲動範圍](#setscrollrange)。

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::取得ScrollBarInfo

擷取 `SCROLLBARINFO` 結構維護的捲軸相關資訊。

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>參數

*pScrollInfo*<br/>
指向[SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)結構的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數類比[SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo)消息的功能,如 Windows SDK 中所述。

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::取得捲動資訊

擷取 `SCROLLINFO` 結構維護的捲軸相關資訊。

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>參數

*lpScrollInfo*<br/>
指向[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構的指標。 有關此結構的詳細資訊,請參閱 Windows SDK。

*nMask*<br/>
指定要檢索的滾動條參數。 典型的用法(SIF_ALL)指定SIF_PAGE、SIF_POS、SIF_TRACKPOS和SIF_RANGE的組合。 有關`SCROLLINFO`nMask 值的詳細資訊,請參閱。

### <a name="return-value"></a>傳回值

如果消息檢索了任何值,則返回為 TRUE。 否則,它是 FALSE。

### <a name="remarks"></a>備註

`GetScrollInfo`使應用程式能夠使用 32 位滾動位置。

[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構包含有關滾動條的資訊,包括最小和最大滾動位置、頁面大小和滾動框(拇指)的位置。 有關更改`SCROLLINFO`結構預設值的詳細資訊,請參閱 Windows SDK 中的結構主題。

指示滾動條位置的 MFC Windows 消息處理程式[CWnd::onHScroll]和[CWnd::onVScroll,](../../mfc/reference/cwnd-class.md#onvscroll)僅提供 16 位元位置數據。 `GetScrollInfo`並提供`SetScrollInfo`32 位滾動條位置數據。 因此,應用程式可以在處理任`GetScrollInfo`一`CWnd::OnHScroll``CWnd::OnVScroll`或獲取 32 位滾動條位置數據時調用。

### <a name="example"></a>範例

  請參考[CWnd 的範例:onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar:抓取捲動限制

檢索滾動條的最大滾動位置。

```
int GetScrollLimit();
```

### <a name="return-value"></a>傳回值

指定滾動條的最大位置(如果成功);否則 0。

### <a name="example"></a>範例

  請參考[CWnd 的範例:onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar:抓取捲動位置

擷取捲動方塊的目前位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>傳回值

指定滾動框的當前位置(如果成功);否則 0。

### <a name="remarks"></a>備註

當前位置是一個相對值,取決於當前滾動範圍。 例如,如果滾動範圍為 100 到 200,並且滾動框位於條形圖的中間,則當前位置為 150。

### <a name="example"></a>範例

  請參考[CWnd 的範例:onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::抓動範圍

將給定滾動條的當前最小和最大滾動條位置複製到*lpMinPos*和*lpMaxPos*指定的位置。

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>參數

*lpMinPos*<br/>
指向要接收最小位置的整數變數。

*lpMaxPos*<br/>
指向要接收最大位置的整數變數。

### <a name="remarks"></a>備註

滾動條控件的預設範圍為空(兩個值均為 0)。

### <a name="example"></a>範例

  請參考[CWnd 的範例:onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::設定Scrollinfo

設置`SCROLLINFO`結構維護有關滾動條的資訊。

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*lpScrollInfo*<br/>
指向[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構的指標。

*bredraw*<br/>
指定是否應重繪滾動條以反映新資訊。 如果*bRedraw*為 TRUE,則重繪滾動條。 如果是 FALSE,則不重繪。 默認情況下,滾動條將重繪。

### <a name="return-value"></a>傳回值

如果成功,則返回為 TRUE。 否則,它是 FALSE。

### <a name="remarks"></a>備註

您必須提供`SCROLLINFO`結構參數所需的值,包括標誌值。

結構`SCROLLINFO`包含有關滾動條的資訊,包括最小和最大滾動位置、頁面大小和滾動框(拇指)的位置。 有關更改結構預設值的詳細資訊,請參閱 Windows SDK 中的[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構主題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::設定捲動位置

將滾動框的當前位置設置為*nPos*指定的位置,如果指定,則重繪滾動條以反映新位置。

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定捲軸框的新位置。 它必須在滾動範圍內。

*bredraw*<br/>
指定是否應重繪滾動條以反映新位置。 如果*bRedraw*為 TRUE,則重繪滾動條。 如果是 FALSE,則不重繪。 默認情況下,滾動條將重繪。

### <a name="return-value"></a>傳回值

指定滾動框的上一個位置(如果成功);否則 0。

### <a name="remarks"></a>備註

每當滾動條通過後續調用另一個函數重新繪製時,將*bredraw*設置為 FALSE,以避免滾動條在短時間間隔內重繪兩次。

### <a name="example"></a>範例

  請參考[CScrollBar 的範例::設定捲動範圍](#setscrollrange)。

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::設定捲動範圍

設定給定捲軸的最小和最大位置值。

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nMinPos*<br/>
指定最小滾動位置。

*nMaxPos*<br/>
指定最大滾動位置。

*bredraw*<br/>
指定是否應重繪滾動條以反映更改。 如果 bRedraw 為 TRUE,則重繪滾動條;如果*bredraw*為 TRUE,則重新繪製滾動條。如果 FALSE,則不重繪。 默認情況下重繪它。

### <a name="remarks"></a>備註

將*nMinPos*和*nMaxPos*設置為 0 以隱藏標準滾動條。

在處理滾動條通知消息時,不要調用此功能來隱藏滾動條。

如果`SetScrollRange`調用後立即`SetScrollPos`調用成員函數,請將*bRedraw*設置為`SetScrollPos`0 以防止滾動條重繪兩次。

*nMinPos*和*nMaxPos*指定的值之間的差異不得大於 32,767。 滾動條控制項的預設範圍為空 *(nMinPos*和*nMaxPos*均為 0)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::顯示捲動列

顯示或隱藏滾動條。

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
指定捲軸項目是顯示還是隱藏。 如果此參數為 TRUE,將顯示滾動條;如果此參數為 TRUE,則顯示滾動條。否則,它是隱藏的。

### <a name="remarks"></a>備註

應用程式在處理滾動條通知消息時不應調用此函數來隱藏滾動條。

### <a name="example"></a>範例

  請參考[CScrollBar 的範例:建立](#create)。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
