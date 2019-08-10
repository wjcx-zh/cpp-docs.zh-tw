---
title: CReBarCtrl 類別
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 102c06879ffaedb91f20a4b5085a10015d7a4c8b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916874"
---
# <a name="crebarctrl-class"></a>CReBarCtrl 類別

封裝 Rebar 控制項的功能，這個控制項是子視窗的容器。

## <a name="syntax"></a>語法

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CReBarCtrl:: CReBarCtrl](#crebarctrl)|建構 `CReBarCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|將 Rebar 控制項放入拖放模式。|
|[CReBarCtrl::Create](#create)|建立 Rebar 控制項並將其附加至`CReBarCtrl`物件。|
|[CReBarCtrl::CreateEx](#createex)|使用指定的 Windows 擴充樣式建立 Rebar 控制項, 並將其附加至`CReBarCtrl`物件。|
|[CReBarCtrl::DeleteBand](#deleteband)|從 Rebar 控制項刪除寬線。|
|[CReBarCtrl::DragMove](#dragmove)|呼叫之後, 更新 Rebar 控制項中的拖曳位置`BeginDrag`。|
|[CReBarCtrl::EndDrag](#enddrag)|終止 Rebar 控制項的拖放作業。|
|[CReBarCtrl::GetBandBorders](#getbandborders)|抓取寬線的框線。|
|[CReBarCtrl::GetBandCount](#getbandcount)|抓取目前在 Rebar 控制項中的區段計數。|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|抓取 Rebar 控制項中指定之帶狀線的相關資訊。|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|抓取寬線的邊界。|
|[CReBarCtrl::GetBarHeight](#getbarheight)|抓取 Rebar 控制項的高度。|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|抓取 Rebar 控制項和它所使用之影像清單的相關資訊。|
|[CReBarCtrl::GetBkColor](#getbkcolor)|抓取 Rebar 控制項的預設背景色彩。|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|抓取與 Rebar 控制項相關聯的[COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)結構。|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|抓取 Rebar 控制項的`IDropTarget`介面指標。|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|取得目前 Rebar 控制項的延伸樣式。|
|[CReBarCtrl::GetImageList](#getimagelist)|抓取與 Rebar 控制項相關聯的影像清單。|
|[CReBarCtrl::GetPalette](#getpalette)|抓取 Rebar 控制項的目前調色板。|
|[CReBarCtrl::GetRect](#getrect)|抓取 Rebar 控制項中指定之寬線的周框。|
|[CReBarCtrl::GetRowCount](#getrowcount)|抓取 Rebar 控制項中的帶狀資料列數目。|
|[CReBarCtrl::GetRowHeight](#getrowheight)|抓取 Rebar 控制項中指定之資料列的高度。|
|[CReBarCtrl::GetTextColor](#gettextcolor)|抓取 Rebar 控制項的預設文字色彩。|
|[CReBarCtrl::GetToolTips](#gettooltips)|抓取與 Rebar 控制項相關聯之任何工具提示控制項的控制碼。|
|[CReBarCtrl::HitTest](#hittest)|判斷 Rebar 帶狀的哪個部分位於螢幕上的指定點 (如果該點上有 Rebar 帶狀)。|
|[CReBarCtrl::IDToIndex](#idtoindex)|將寬線識別碼 (ID) 轉換成 Rebar 控制項中的寬線索引。|
|[CReBarCtrl::InsertBand](#insertband)|在 Rebar 控制項中插入新的寬線。|
|[CReBarCtrl::MaximizeBand](#maximizeband)|將 Rebar 控制項中的寬線調整成最大的大小。|
|[CReBarCtrl::MinimizeBand](#minimizeband)|將 Rebar 控制項中的寬線調整為其最小大小。|
|[CReBarCtrl::MoveBand](#moveband)|將一條線從一個索引移至另一個。|
|[CReBarCtrl::PushChevron](#pushchevron)|以程式設計方式推送 v 形箭號。|
|[CReBarCtrl::RestoreBand](#restoreband)|將 Rebar 控制項中的寬線調整為其理想大小。|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|設定 Rebar 控制項中現有寬線的特性。|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|設定目前 Rebar 控制項中指定之停駐區的寬度。|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|設定 Rebar 控制項的特性。|
|[CReBarCtrl::SetBkColor](#setbkcolor)|設定 Rebar 控制項的預設背景色彩。|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|設定 Rebar 控制項上按鈕的色彩配置。|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|設定目前 Rebar 控制項的延伸樣式。|
|[CReBarCtrl::SetImageList](#setimagelist)|設定 Rebar 控制項的影像清單。|
|[CReBarCtrl::SetOwner](#setowner)|設定 Rebar 控制項的擁有者視窗。|
|[CReBarCtrl::SetPalette](#setpalette)|設定 Rebar 控制項的目前調色板。|
|[CReBarCtrl::SetTextColor](#settextcolor)|設定 Rebar 控制項的預設文字色彩。|
|[CReBarCtrl::SetToolTips](#settooltips)|將工具提示控制項與 Rebar 控制項產生關聯。|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|設定 Rebar 控制項的視覺化樣式。|
|[CReBarCtrl::ShowBand](#showband)|在 Rebar 控制項中顯示或隱藏指定的寬線。|
|[CReBarCtrl::SizeToRect](#sizetorect)|將 Rebar 控制項符合指定的矩形。|

## <a name="remarks"></a>備註

Rebar 控制項所在的應用程式會將 Rebar 控制項所包含的子視窗指派給 Rebar 區段。 子視窗通常是另一個常見的控制項。

Rebar 控制項包含一個或多個波段。 每個寬線都可以包含移駐夾列、點陣圖、文字標籤和子視窗的組合。 寬線只能包含其中一個專案。

Rebar 控制項可以透過指定的背景點陣圖來顯示子視窗。 除了使用 RBBS_FIXEDSIZE 樣式的所有 Rebar 控制項群組外, 您都可以調整其大小。 當您重新置放或調整 Rebar 控制區的大小時, Rebar 控制項會管理指派給該寬線之子視窗的大小和位置。 若要調整大小或變更控制項內的頻帶順序, 請按一下並拖曳寬線的移駐夾列。

下圖顯示具有三個頻帶的 Rebar 控制項:

- 寬線0包含一個平面、透明的工具列控制項。

- 寬線1同時包含 [透明標準] 和 [透明] 下拉式按鈕。

- 頻外2包含下拉式方塊和四個標準按鈕。

   ![Rebar 功能表的範例](../../mfc/reference/media/vc4scc1.gif "Rebar 功能表的範例")

## <a name="rebar-control"></a>Rebar 控制項

Rebar 控制項支援:

- 影像清單。

- 訊息處理。

- 自訂繪製功能。

- 除了標準視窗樣式以外的各種控制項樣式。 如需這些樣式的清單, 請參閱 Windows SDK 中的[Rebar 控制項樣式](/windows/desktop/Controls/rebar-control-styles)。

如需詳細資訊, 請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag

執行 Win32 message [RB_BEGINDRAG](/windows/desktop/Controls/rb-begindrag)的行為, 如 Windows SDK 中所述。

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>參數

*uBand*<br/>
拖放作業將會影響的寬線索引 (以零為基底)。

*dwPos*<br/>
包含起始滑鼠座標的 DWORD 值。 水準座標會包含在 LOWORD 中, 而垂直座標則包含在 HIWORD 中。 如果您通過 (DWORD)-1, Rebar 控制項將會使用上一次控制項執行緒呼叫`GetMessage`或`PeekMessage`的滑鼠位置。

##  <a name="create"></a>CReBarCtrl:: Create

建立 Rebar 控制項並將其附加至`CReBarCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定套用至控制項的 Rebar 控制項樣式的組合。 如需支援的樣式清單, 請參閱 Windows SDK 中的[Rebar 控制項樣式](/windows/desktop/Controls/rebar-control-styles)。

*rect*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考, 這是 Rebar 控制項的位置和大小。

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標, 這是 Rebar 控制項的父視窗。 不得為 Null。

*nID*<br/>
指定 Rebar 控制項的控制項 ID。

### <a name="return-value"></a>傳回值

如果成功建立物件, 則為非零;否則為0。

### <a name="remarks"></a>備註

以兩個步驟建立 Rebar 控制項:

1. 呼叫[CReBarCtrl](#crebarctrl)來建立`CReBarCtrl`物件。

1. 呼叫這個成員函式, 它會建立 Windows Rebar 控制項並將其附加`CReBarCtrl`至物件。

當您呼叫`Create`時, 會初始化通用控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>CReBarCtrl:: CreateEx

建立控制項 (子視窗), 並將它與`CReBarCtrl`物件產生關聯。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)的*dwExStyle*參數。

*dwStyle*<br/>
指定套用至控制項的 Rebar 控制項樣式的組合。 如需支援的樣式清單, 請參閱 Windows SDK 中的[Rebar 控制項樣式](/windows/desktop/Controls/rebar-control-styles)。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 描述要建立之視窗的大小和位置, 以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx` , 而不是[Create](#create)來套用擴充的 windows 樣式 (由 Windows 擴充樣式指定于**WS_EX_** 的前面)。

##  <a name="crebarctrl"></a>CReBarCtrl:: CReBarCtrl

建立 `CReBarCtrl` 物件。

```
CReBarCtrl();
```

### <a name="example"></a>範例

  請參閱[CReBarCtrl:: Create](#create)的範例。

##  <a name="deleteband"></a>CReBarCtrl::D eleteBand

執行 Win32 message [RB_DELETEBAND](/windows/desktop/Controls/rb-deleteband)的行為, 如 Windows SDK 中所述。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
要刪除之寬線的以零為基底的索引。

### <a name="return-value"></a>傳回值

如果已成功刪除寬頻, 則為非零;否則為零。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>  CReBarCtrl::DragMove

執行 Win32 message [RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove)的行為, 如 Windows SDK 中所述。

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>參數

*dwPos*<br/>
包含新滑鼠座標的 DWORD 值。 水準座標會包含在 LOWORD 中, 而垂直座標則包含在 HIWORD 中。 如果您通過 (DWORD)-1, Rebar 控制項將會使用上一次控制項執行緒呼叫`GetMessage`或`PeekMessage`的滑鼠位置。

##  <a name="enddrag"></a>CReBarCtrl:: EndDrag

執行 Win32 message [RB_ENDDRAG](/windows/desktop/Controls/rb-enddrag)的行為, 如 Windows SDK 中所述。

```
void EndDrag();
```

##  <a name="getbandborders"></a>CReBarCtrl:: GetBandBorders

執行 Win32 message [RB_GETBANDBORDERS](/windows/desktop/Controls/rb-getbandborders)的行為, 如 Windows SDK 中所述。

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引, 將會抓取框線的範圍。

*prc*<br/>
將接收寬線框線之[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。 如果 Rebar 控制項具有 RBS_BANDBORDERS 樣式, 則此結構的每個成員都會在組成邊界的寬線對應端收到圖元數目。 如果 Rebar 控制項沒有 RBS_BANDBORDERS 樣式, 只有此結構的左方成員會收到有效的資訊。 如需 Rebar 控制項樣式的說明, 請參閱 Windows SDK 中的[Rebar 控制項樣式](/windows/desktop/Controls/rebar-control-styles)。

##  <a name="getbandcount"></a>CReBarCtrl:: GetBandCount

執行 Win32 message [RB_GETBANDCOUNT](/windows/desktop/Controls/rb-getbandcount)的行為, 如 Windows SDK 中所述。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>傳回值

指派給控制項的波段數。

##  <a name="getbandinfo"></a>CReBarCtrl:: GetBandInfo

依照 Windows SDK 中的說明, 執行 Win32 訊息[RB_GETBANDINFO](/windows/desktop/Controls/rb-getbandinfo)的行為。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引, 將會抓取資訊。

*prbbi*<br/>
[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)結構的指標, 用來接收寬線資訊。 您必須將此`cbSize`結構的成員設定為`sizeof(REBARBANDINFO)` , 並將`fMask`成員設為您想要取得的專案, 然後再傳送此訊息。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

##  <a name="getbandmargins"></a>CReBarCtrl:: GetBandMargins

抓取寬線的邊界。

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>參數

*pMargins*<br/>
將接收資訊之[邊界](/windows/desktop/api/uxtheme/ns-uxtheme-margins)結構的指標。

### <a name="remarks"></a>備註

此成員函式會模擬[RB_GETBANDMARGINS](/windows/desktop/Controls/rb-getbandmargins)訊息的功能, 如 Windows SDK 中所述。

##  <a name="getbarheight"></a>CReBarCtrl:: GetBarHeight

抓取 Rebar 橫條的高度。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>傳回值

值, 表示控制項的高度 (以圖元為單位)。

##  <a name="getbarinfo"></a>CReBarCtrl:: GetBarInfo

執行 Win32 message [RB_GETBARINFO](/windows/desktop/Controls/rb-getbarinfo)的行為, 如 Windows SDK 中所述。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>參數

*prbi*<br/>
將接收 Rebar 控制項資訊之[REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo)結構的指標。 您必須先將此結構的*cbSize*成員設定`sizeof(REBARINFO)`為, 才能傳送此訊息。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

##  <a name="getbkcolor"></a>CReBarCtrl:: GetBkColor

執行 Win32 message [RB_GETBKCOLOR](/windows/desktop/Controls/rb-getbkcolor)的行為, 如 Windows SDK 中所述。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

COLORRE光圈值, 表示目前的預設背景色彩。

##  <a name="getcolorscheme"></a>CReBarCtrl:: GetColorScheme

抓取 Rebar 控制項的[COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)結構。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>參數

*lpcs*<br/>
[COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)結構的指標, 如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

`COLORSCHEME`結構包括按鈕反白顯示色彩和按鈕陰影色彩。

##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget

執行 Win32 message [RB_GETDROPTARGET](/windows/desktop/Controls/rb-getdroptarget)的行為, 如 Windows SDK 中所述。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>傳回值

指向[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)介面的指標。

##  <a name="getextendedstyle"></a>CReBarCtrl:: GetExtendedStyle

取得目前 Rebar 控制項的延伸樣式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>傳回值

旗標的位元組合 (OR), 表示擴充樣式。 可能的旗標為 RBS_EX_SPLITTER 和 RBS_EX_TRANSPARENT。 如需詳細資訊, 請參閱[CReBarCtrl:: SetExtendedStyle](#setextendedstyle)方法的*dwMask*參數。

### <a name="remarks"></a>備註

這個方法會傳送[RB_GETEXTENDEDSTYLE](/windows/desktop/Controls/rb-dragmove)訊息, 如 Windows SDK 中所述。

##  <a name="getimagelist"></a>CReBarCtrl:: GetImageList

取得與`CImageList` Rebar 控制項相關聯的物件。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。 如果沒有為控制項設定影像清單, 則會傳回 Null。

### <a name="remarks"></a>備註

此成員函式會使用儲存在[REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo)結構中的大小和遮罩資訊, 如 Windows SDK 中所述。

##  <a name="getpalette"></a>CReBarCtrl:: GetPalette

抓取 Rebar 控制項的目前調色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>傳回值

[CPalette](../../mfc/reference/cpalette-class.md)物件的指標, 指定 Rebar 控制項的目前調色板。

### <a name="remarks"></a>備註

請注意, 此成員函式`CPalette`會使用物件做為其傳回值, 而不是 HPALETTE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>CReBarCtrl:: GetRect

執行 Win32 message [RB_GETRECT](/windows/desktop/Controls/rb-getrect)的行為, 如 Windows SDK 中所述。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>參數

*uBand*<br/>
Rebar 控制項中寬線的以零為基底的索引。

*prc*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的指標, 將會接收 Rebar 寬線的範圍。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>CReBarCtrl:: GetRowCount

執行 Win32 message [RB_GETROWCOUNT](/windows/desktop/Controls/rb-getrowcount)的行為, 如 Windows SDK 中所述。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>傳回值

UINT 值, 表示控制項中的區段資料列數目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>CReBarCtrl:: GetRowHeight

執行 Win32 message [RB_GETROWHEIGHT](/windows/desktop/Controls/rb-getrowheight)的行為, 如 Windows SDK 中所述。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>參數

*uRow*<br/>
以零為基底的寬線索引, 將會抓取其高度。

### <a name="return-value"></a>傳回值

UINT 值, 表示資料列高度 (以圖元為單位)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>CReBarCtrl:: GetTextColor

執行 Win32 message [RB_GETTEXTCOLOR](/windows/desktop/Controls/rb-gettextcolor)的行為, 如 Windows SDK 中所述。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>傳回值

COLORRE光圈值, 表示目前的預設文字色彩。

##  <a name="gettooltips"></a>CReBarCtrl:: GetToolTips

執行 Win32 message [RB_GETTOOLTIPS](/windows/desktop/Controls/rb-gettooltips)的行為, 如 Windows SDK 中所述。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標。

### <a name="remarks"></a>備註

請注意, 的 MFC 執行`GetToolTips`會傳回的`CToolTipCtrl`指標, 而不是 HWND。

##  <a name="hittest"></a>CReBarCtrl:: HitTest

執行 Win32 message [RB_HITTEST](/windows/desktop/Controls/rb-hittest)的行為, 如 Windows SDK 中所述。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>參數

*prbht*<br/>
[RBHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_rb_hittestinfo)結構的指標。 在傳送訊息之前, `pt`必須將此結構的成員初始化為要測試的點 (以工作區座標表示)。

### <a name="return-value"></a>傳回值

以零為基底的寬線索引, 如果在該點上沒有 Rebar 寬線, 則為-1。

##  <a name="idtoindex"></a>CReBarCtrl:: IDToIndex

執行 Win32 message [RB_IDTOINDEX](/windows/desktop/controls/rb-idtoindex)的行為, 如 Windows SDK 中所述。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>參數

*uBandID*<br/>
插入寬線時, 傳入`wID` [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)結構成員的指定寬線的應用程式定義識別碼。

### <a name="return-value"></a>傳回值

如果成功, 則為以零為基底的區段索引, 否則為-1。 如果有重複的帶位索引, 則會傳回第一個。

##  <a name="insertband"></a>CReBarCtrl:: InsertBand

執行 Win32 message [RB_INSERTBAND](/windows/desktop/Controls/rb-insertband)的行為, 如 Windows SDK 中所述。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>參數

*uIndex*<br/>
以零為基底的索引, 這是要插入寬線的位置。 如果您將此參數設定為-1, 控制項就會在最後一個位置加入新的寬線。

*prbbi*<br/>
[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)結構的指標, 定義要插入的寬線。 您必須先將此結構的*cbSize*成員設定`sizeof(REBARBANDINFO)`為, 才能呼叫此函式。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>CReBarCtrl:: MaximizeBand

將 Rebar 控制項中的寬線調整成最大的大小。

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
要最大化的寬線索引 (以零為基底)。

### <a name="remarks"></a>備註

`fIdeal`將設定為0的 Win32 message [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband)行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>CReBarCtrl:: MinimizeBand

將 Rebar 控制項中的寬線調整為其最小大小。

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
要最小化之寬線的以零為基底的索引。

### <a name="remarks"></a>備註

執行 Win32 message [RB_MINIMIZEBAND](/windows/desktop/Controls/rb-minimizeband)的行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>CReBarCtrl:: MoveBand

執行 Win32 message [RB_MOVEBAND](/windows/desktop/Controls/rb-moveband)的行為, 如 Windows SDK 中所述。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>參數

*uFrom*<br/>
要移動之寬線的以零為基底的索引。

*自動 u)*<br/>
新帶狀位置的以零為基底的索引。 這個參數值絕對不能大於群組的數目減一。 若要取得波段的數目, 請呼叫[GetBandCount](#getbandcount)。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

##  <a name="pushchevron"></a>CReBarCtrl::P ushChevron

執行 Win32 message [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron)的行為, 如 Windows SDK 中所述。

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引, 其燕尾的箭號會被推送。

*lAppValue*<br/>
應用程式定義了32位的值。 請參閱 Windows SDK 中[RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron)的*lAppValue* 。

##  <a name="restoreband"></a>CReBarCtrl:: RestoreBand

將 Rebar 控制項中的寬線調整為其理想大小。

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
要最大化的寬線索引 (以零為基底)。

### <a name="remarks"></a>備註

`fIdeal`將設定為1的 Win32 message [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband)行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>CReBarCtrl:: SetBandInfo

執行 Win32 message [RB_SETBANDINFO](/windows/desktop/Controls/rb-setbandinfo)的行為, 如 Windows SDK 中所述。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引, 用來接收新的設定。

*prbbi*<br/>
[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)結構的指標, 定義要插入的寬線。 您必須先將`cbSize`此結構的成員設定`sizeof(REBARBANDINFO)`為, 才能傳送此訊息。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>CReBarCtrl:: SetBandWidth

設定目前 Rebar 控制項中指定之停駐區的寬度。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*uBand*|在Rebar 波段的以零為基底的索引。|
|*cxWidth*|在Rebar 寬線的新寬度 (以圖元為單位)。|

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[RB_SETBANDWIDTH](/windows/desktop/Controls/rb-setbandwidth)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_rebar`存取目前 Rebar 控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>範例

下列程式碼範例會將每個 Rebar 波段設為相同的寬度。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>CReBarCtrl:: SetBarInfo

執行 Win32 message [RB_SETBARINFO](/windows/desktop/Controls/rb-setbarinfo)的行為, 如 Windows SDK 中所述。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>參數

*prbi*<br/>
[REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo)結構的指標, 其中包含要設定的資訊。 您必須先將`cbSize`此結構的成員設定`sizeof(REBARINFO)`為, 才能傳送此訊息

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>CReBarCtrl:: SetBkColor

執行 Win32 message [RB_SETBKCOLOR](/windows/desktop/Controls/rb-setbkcolor)的行為, 如 Windows SDK 中所述。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
COLORRE光圈值, 表示新的預設背景色彩。

### <a name="return-value"></a>傳回值

表示先前預設背景色彩的[COLORREF](/windows/desktop/gdi/colorref)值。

### <a name="remarks"></a>備註

如需設定背景色彩的時機, 以及如何設定預設值的詳細資訊, 請參閱本主題。

##  <a name="setcolorscheme"></a>CReBarCtrl:: SetColorScheme

設定 Rebar 控制項上按鈕的色彩配置。

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>參數

*lpcs*<br/>
[COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)結構的指標, 如 Windows SDK 中所述。

### <a name="remarks"></a>備註

`COLORSCHEME`結構同時包含按鈕反白顯示色彩和按鈕陰影色彩。

##  <a name="setextendedstyle"></a>CReBarCtrl:: SetExtendedStyle

設定目前 Rebar 控制項的延伸樣式。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwMask*|在旗標的位元組合 (OR), 指定要套用*dwStyleEx*參數中的旗標。 使用下列一個或多個值:<br /><br /> RBS_EX_SPLITTER:根據預設, 會在水準模式下的底部顯示分隔器, 並在垂直模式中顯示在右側。<br /><br /> RBS_EX_TRANSPARENT:將[WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd)訊息轉送到父視窗。|
|*dwStyleEx*|在旗標的位元組合 (OR), 指定要套用的樣式。 若要設定樣式, 請指定在*dwMask*參數中使用的相同旗標。 若要重設樣式, 請指定 binary 零。|

### <a name="return-value"></a>傳回值

先前的延伸樣式。

### <a name="remarks"></a>備註

這個方法會傳送[RB_SETEXTENDEDSTYLE](/windows/desktop/Controls/rb-setextendedstyle)訊息, 如 Windows SDK 中所述。

##  <a name="setimagelist"></a>CReBarCtrl:: SetImageList

將影像清單指派給 Rebar 控制項。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標, 其中包含要指派給 Rebar 控制項的影像清單。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

##  <a name="setowner"></a>  CReBarCtrl::SetOwner

執行 Win32 message [RB_SETPARENT](/windows/desktop/Controls/rb-setparent)的行為, 如 Windows SDK 中所述。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
`CWnd`物件的指標, 要設定為 Rebar 控制項的擁有者。

### <a name="return-value"></a>傳回值

[CWnd](../../mfc/reference/cwnd-class.md)物件的指標, 這是 Rebar 控制項的目前擁有者。

### <a name="remarks"></a>備註

請注意, 此成員函式會`CWnd`針對 Rebar 控制項的目前和選取的擁有者, 使用物件的指標, 而不是視窗的控制碼。

> [!NOTE]
>  這個成員函式不會變更建立控制項時所設定的實際父系;相反地, 它會將通知訊息傳送至您指定的視窗。

##  <a name="setpalette"></a>CReBarCtrl:: SetPalette

執行 Win32 message [RB_SETPALETTE](/windows/desktop/Controls/rb-setpalette)的行為, 如 Windows SDK 中所述。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>參數

*hPal*<br/>
HPALETTE, 指定 Rebar 控制項將使用的新調色板。

### <a name="return-value"></a>傳回值

指定 Rebar 控制項先前的調色板之[CPalette](../../mfc/reference/cpalette-class.md)物件的指標。

### <a name="remarks"></a>備註

請注意, 此成員函式`CPalette`會使用物件做為其傳回值, 而不是 HPALETTE。

##  <a name="settextcolor"></a>CReBarCtrl:: SetTextColor

執行 Win32 message [RB_SETTEXTCOLOR](/windows/desktop/Controls/rb-settextcolor)的行為, 如 Windows SDK 中所述。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
代表`CReBarCtrl`物件中新文字色彩的 COLORRE光圈值。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/desktop/gdi/colorref)值, 表示與`CReBarCtrl`物件相關聯的先前文字色彩。

### <a name="remarks"></a>備註

它是為了支援 Rebar 控制項中的文字色彩彈性而提供的。

##  <a name="settooltips"></a>CReBarCtrl:: SetToolTips

將工具提示控制項與 Rebar 控制項產生關聯。

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標

### <a name="remarks"></a>備註

當您完成時`CToolTipCtrl` , 必須終結物件。

##  <a name="setwindowtheme"></a>CReBarCtrl:: SetWindowTheme

設定 Rebar 控制項的視覺化樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
Unicode 字串的指標, 其中包含要設定的 Rebar 視覺效果樣式。

### <a name="return-value"></a>傳回值

不使用傳回值。

### <a name="remarks"></a>備註

此成員函式會模擬[RB_SETWINDOWTHEME](/windows/desktop/Controls/rb-setwindowtheme)訊息的功能, 如 Windows SDK 中所述。

##  <a name="showband"></a>CReBarCtrl:: ShowBand

執行 Win32 message [RB_SHOWBAND](/windows/desktop/Controls/rb-showband)的行為, 如 Windows SDK 中所述。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>參數

*uBand*<br/>
Rebar 控制項中寬線的以零為基底的索引。

*fShow*<br/>
指出是否應該顯示或隱藏帶狀線。 如果此值為 TRUE, 將會顯示寬線。 否則, 將會隱藏寬線。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

##  <a name="sizetorect"></a>CReBarCtrl:: SizeToRect

執行 Win32 message [RB_SIZETORECT](/windows/desktop/Controls/rb-sizetorect)的行為, 如 Windows SDK 中所述。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>參數

*rect*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的參考, 指定 Rebar 控制項應調整大小的矩形。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

請注意, 此成員函式`CRect`會使用物件做為參數, 而`RECT`不是結構。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
