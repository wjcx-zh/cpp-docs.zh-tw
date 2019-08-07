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
ms.openlocfilehash: 5bc9c0190ea200b25b8ea3b20311c98c1c131838
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821263"
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
|[CScrollBar::CScrollBar](#cscrollbar)|建構 `CScrollBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CScrollBar::Create](#create)|建立 Windows 捲軸, 並將其附加至`CScrollBar`物件。|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|啟用或停用一個捲軸的一或兩個箭號。|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|使用`SCROLLBARINFO`結構抓取捲軸的相關資訊。|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|抓取捲軸的相關資訊。|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|抓取捲軸的限制|
|[CScrollBar::GetScrollPos](#getscrollpos)|擷取捲動方塊的目前位置。|
|[CScrollBar::GetScrollRange](#getscrollrange)|針對指定的捲軸, 抓取目前的最小和最大捲軸位置。|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|設定捲軸的相關資訊。|
|[CScrollBar::SetScrollPos](#setscrollpos)|設定捲動方塊的目前位置。|
|[CScrollBar::SetScrollRange](#setscrollrange)|設定給定捲軸的最小和最大位置值。|
|[CScrollBar::ShowScrollBar](#showscrollbar)|顯示或隱藏捲軸。|

## <a name="remarks"></a>備註

您可以使用兩個步驟來建立捲軸控制項。 首先`CScrollBar` , 呼叫函式`CScrollBar`來建立物件, 然後呼叫[create](#create)成員函式來建立 Windows 滾動`CScrollBar`條控制項, 並將它附加至物件。

如果您在對話方塊`CScrollBar`中建立物件 (透過對話資源) `CScrollBar` , 當使用者關閉對話方塊時, 會自動終結。

如果您在視窗`CScrollBar`中建立物件, 您可能也需要將它摧毀。

如果您在堆疊`CScrollBar`上建立物件, 它會自動終結。 如果您使用`CScrollBar` **新**的函式在堆積上建立物件, 您必須在物件上呼叫**delete** , 以在使用者終止 Windows 捲軸時終結它。

如果您在`CScrollBar`物件中配置任何記憶體, 請覆`CScrollBar`寫析構函式以處置配置。

如需使用`CScrollBar`的相關資訊, 請參閱[控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="create"></a>CScrollBar:: Create

建立 Windows 捲軸, 並將其附加至`CScrollBar`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定捲軸的樣式。 將任何[捲軸樣式](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)的組合套用至捲軸。

*rect*<br/>
指定捲軸的大小和位置。 可以是`CRect`結構或物件。 `RECT`

*pParentWnd*<br/>
指定捲軸的父視窗, 通常是`CDialog`物件。 不得為 Null。

*nID*<br/>
捲軸的控制項識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用`CScrollBar`兩個步驟來建立物件。 首先, 呼叫構造`CScrollBar`物件的函式, 然後呼叫`Create`, 它會建立並初始化相關聯的 Windows 捲軸, `CScrollBar`並將其附加至物件。

將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至捲軸:

- WS_CHILD 一律

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_GROUP 至群組控制項

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

##  <a name="cscrollbar"></a>CScrollBar::CScrollBar

建構 `CScrollBar` 物件。

```
CScrollBar();
```

### <a name="remarks"></a>備註

在建立物件之後, 呼叫`Create`成員函式來建立和初始化 Windows 捲軸。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

##  <a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

啟用或停用一個捲軸的一或兩個箭號。

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>參數

*nArrowFlags*<br/>
指定是否啟用或停用捲動箭號, 以及啟用或停用的箭號。 這個參數可以是下列其中一個值:

- ESB_ENABLE_BOTH 可同時啟用捲軸的兩個箭號。

- ESB_DISABLE_LTUP 會停用水準捲軸的向左箭號或垂直捲動條的向上箭號。

- ESB_DISABLE_RTDN 會停用水準捲軸的向右箭號或垂直捲動條的向下箭號。

- ESB_DISABLE_BOTH 會停用捲軸的兩個箭號。

### <a name="return-value"></a>傳回值

如果依指定啟用或停用箭號, 則為非零值;否則為 0, 表示箭號已處於要求的狀態或發生錯誤。

### <a name="example"></a>範例

  請參閱[CScrollBar:: SetScrollRange](#setscrollrange)的範例。

##  <a name="getscrollbarinfo"></a>CScrollBar:: GetScrollBarInfo

擷取 `SCROLLBARINFO` 結構維護的捲軸相關資訊。

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>參數

*pScrollInfo*<br/>
[SCROLLBARINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollbarinfo)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會模擬[SBM_SCROLLBARINFO](/windows/desktop/Controls/sbm-getscrollbarinfo)訊息的功能, 如 Windows SDK 中所述。

##  <a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

擷取 `SCROLLINFO` 結構維護的捲軸相關資訊。

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>參數

*lpScrollInfo*<br/>
[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構的指標。 如需此結構的詳細資訊, 請參閱 Windows SDK。

*nMask*<br/>
指定要取出的捲軸參數。 一般使用方式 (SIF_ALL) 會指定 SIF_PAGE、SIF_POS、SIF_TRACKPOS 和 SIF_RANGE 的組合。 如`SCROLLINFO`需 nMask 值的詳細資訊, 請參閱。

### <a name="return-value"></a>傳回值

如果訊息已抓取任何值, 則傳回為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

`GetScrollInfo`可讓應用程式使用32位的捲軸位置。

[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構包含捲軸的相關資訊, 包括最小和最大的滾動位置、頁面大小, 以及捲動方塊的位置 (thumb)。 如需`SCROLLINFO`變更結構預設值的詳細資訊, 請參閱 Windows SDK 中的結構主題。

指出捲軸位置、[CWnd:: OnHScroll 和[CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)的 MFC Windows 訊息處理常式, 只提供16個位的位置資料。 `GetScrollInfo`和`SetScrollInfo`提供32位的捲軸位置資料。 因此, 應用程式可以在`GetScrollInfo` `CWnd::OnHScroll`處理或`CWnd::OnVScroll`來取得32位捲軸位置資料時呼叫。

### <a name="example"></a>範例

  請參閱[CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的範例。

##  <a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

抓取捲軸的最大滾動位置。

```
int GetScrollLimit();
```

### <a name="return-value"></a>傳回值

指定捲軸成功時的最大位置;否則為0。

### <a name="example"></a>範例

  請參閱[CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的範例。

##  <a name="getscrollpos"></a>CScrollBar::GetScrollPos

擷取捲動方塊的目前位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>傳回值

指定捲動方塊的目前位置 (如果成功);否則為0。

### <a name="remarks"></a>備註

目前的位置是相依于目前滾動範圍的相對值。 例如, 如果捲軸範圍是100到 200, 而且捲動方塊位於橫條的中間, 則目前的位置是150。

### <a name="example"></a>範例

  請參閱[CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的範例。

##  <a name="getscrollrange"></a>CScrollBar::GetScrollRange

將指定捲軸的目前最小和最大捲軸位置複製到*lpMinPos*和*lpMaxPos*所指定的位置。

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

捲軸控制項的預設範圍是空的 (這兩個值都是 0)。

### <a name="example"></a>範例

  請參閱[CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的範例。

##  <a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

設定`SCROLLINFO`結構維護捲軸的相關資訊。

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*lpScrollInfo*<br/>
[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構的指標。

*bRedraw*<br/>
指定是否應該重新繪製捲軸以反映新的資訊。 如果*bRedraw*為 TRUE, 則會重新繪製捲軸。 如果為 FALSE, 則不會重新繪製。 預設會重新繪製捲軸。

### <a name="return-value"></a>傳回值

如果成功, 則傳回為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

您必須提供`SCROLLINFO`結構參數所需的值, 包括旗標值。

`SCROLLINFO`結構包含捲軸的相關資訊, 包括最小和最大的滾動位置、頁面大小, 以及捲動方塊的位置 (thumb)。 如需變更結構預設值的詳細資訊, 請參閱 Windows SDK 中的[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)結構主題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

##  <a name="setscrollpos"></a>CScrollBar::SetScrollPos

將捲動方塊的目前位置設定為*nPos*所指定的位置, 如果有指定, 則會重新繪製捲軸以反映新的位置。

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定捲動方塊的新位置。 它必須在滾動範圍內。

*bRedraw*<br/>
指定是否應該重新繪製捲軸以反映新的位置。 如果*bRedraw*為 TRUE, 則會重新繪製捲軸。 如果為 FALSE, 則不會重新繪製。 預設會重新繪製捲軸。

### <a name="return-value"></a>傳回值

指定捲動方塊的先前位置 (如果成功);否則為0。

### <a name="remarks"></a>備註

每當後續呼叫另一個函式來重新繪製捲軸時, 將*bRedraw*設定為 FALSE, 以避免捲軸在短時間內重新繪製兩次。

### <a name="example"></a>範例

  請參閱[CScrollBar:: SetScrollRange](#setscrollrange)的範例。

##  <a name="setscrollrange"></a>CScrollBar::SetScrollRange

設定給定捲軸的最小和最大位置值。

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nMinPos*<br/>
指定最小的滾動位置。

*nMaxPos*<br/>
指定最大的滾動位置。

*bRedraw*<br/>
指定是否應該重新繪製捲軸以反映變更。 如果*bRedraw*為 TRUE, 則會重新繪製捲軸;如果為 FALSE, 則不會重新繪製。 預設會重新繪製它。

### <a name="remarks"></a>備註

將*nMinPos*和*nMaxPos*設定為 0, 以隱藏標準捲軸。

請勿呼叫此函式, 在處理捲軸通知訊息時隱藏捲軸。

如果呼叫`SetScrollRange`緊接在`SetScrollPos`成員函式的呼叫之後, 請將中的 `SetScrollPos` bRedraw 設定為 0, 以防止捲軸重新繪製兩次。

*NMinPos*和*nMaxPos*所指定的值之間的差異不得大於32767。 捲軸控制項的預設範圍是空的 ( *nMinPos*和*nMaxPos*都是 0)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

##  <a name="showscrollbar"></a>CScrollBar:: ShowScrollBar

顯示或隱藏捲軸。

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>參數

*bShow*<br/>
指定是否要顯示或隱藏捲軸。 如果此參數為 TRUE, 則會顯示捲軸;否則會隱藏。

### <a name="remarks"></a>備註

應用程式不應該呼叫此函式, 在處理捲軸通知訊息時隱藏捲軸。

### <a name="example"></a>範例

  請參閱[CScrollBar:: Create](#create)的範例。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
