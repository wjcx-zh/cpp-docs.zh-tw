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
ms.openlocfilehash: 872d577c2272939a6bf7ed1e3069cda426083e3f
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561891"
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
|[CReBarCtrl：： CReBarCtrl](#crebarctrl)|建構 `CReBarCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CReBarCtrl：： BeginDrag](#begindrag)|將 Rebar 控制項放在拖放模式中。|
|[CReBarCtrl：： Create](#create)|建立 Rebar 控制項並將其附加至 `CReBarCtrl` 物件。|
|[CReBarCtrl：： CreateEx](#createex)|使用指定的 Windows 擴充樣式建立 Rebar 控制項，並將其附加至 `CReBarCtrl` 物件。|
|[CReBarCtrl：:D eleteBand](#deleteband)|從 Rebar 控制項刪除頻外。|
|[CReBarCtrl：:D ragMove](#dragmove)|在呼叫之後，更新 Rebar 控制項中的拖曳位置 `BeginDrag` 。|
|[CReBarCtrl：： EndDrag](#enddrag)|終止 Rebar 控制項的拖放作業。|
|[CReBarCtrl：： GetBandBorders](#getbandborders)|抓取寬線的框線。|
|[CReBarCtrl：： GetBandCount](#getbandcount)|抓取目前在 Rebar 控制項中的條紋計數。|
|[CReBarCtrl：： GetBandInfo](#getbandinfo)|抓取 Rebar 控制項中指定之頻外的相關資訊。|
|[CReBarCtrl：： GetBandMargins](#getbandmargins)|抓取寬線的邊界。|
|[CReBarCtrl：： GetBarHeight](#getbarheight)|抓取 Rebar 控制項的高度。|
|[CReBarCtrl：： GetBarInfo](#getbarinfo)|抓取 Rebar 控制項及其所使用影像清單的相關資訊。|
|[CReBarCtrl：： GetBkColor](#getbkcolor)|抓取 Rebar 控制項的預設背景色彩。|
|[CReBarCtrl：： GetColorScheme](#getcolorscheme)|抓取與 Rebar 控制項相關聯的 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) 結構。|
|[CReBarCtrl：： GetDropTarget](#getdroptarget)|抓取 Rebar 控制項的 `IDropTarget` 介面指標。|
|[CReBarCtrl：： GetExtendedStyle](#getextendedstyle)|取得目前 Rebar 控制項的延伸樣式。|
|[CReBarCtrl：： GetImageList](#getimagelist)|抓取與 Rebar 控制項相關聯的影像清單。|
|[CReBarCtrl：： GetPalette](#getpalette)|抓取 Rebar 控制項的目前調色板。|
|[CReBarCtrl：： GetRect](#getrect)|抓取 Rebar 控制項中指定範圍的周框。|
|[CReBarCtrl：： GetRowCount](#getrowcount)|抓取 Rebar 控制項中的帶狀列數目。|
|[CReBarCtrl：： GetRowHeight](#getrowheight)|抓取 Rebar 控制項中指定之資料列的高度。|
|[CReBarCtrl：： GetTextColor](#gettextcolor)|抓取 Rebar 控制項的預設文字色彩。|
|[CReBarCtrl：： GetToolTips](#gettooltips)|抓取與 Rebar 控制項相關聯之任何工具提示控制項的控制碼。|
|[CReBarCtrl：： System.windows.media.visualtreehelper.hittest](#hittest)|判斷如果在該點上存在 Rebar 帶，則在螢幕上的某個點上，Rebar 區的哪個部分是在指定的點上。|
|[CReBarCtrl：： IDToIndex](#idtoindex)|將區段識別碼 (識別碼) 轉換為 Rebar 控制項中的寬線索引。|
|[CReBarCtrl：： InsertBand](#insertband)|在 Rebar 控制項中插入新的波段。|
|[CReBarCtrl：： MaximizeBand](#maximizeband)|將 Rebar 控制項中的寬線大小調整為最大的大小。|
|[CReBarCtrl：： MinimizeBand](#minimizeband)|將 Rebar 控制項中的寬線大小調整為最小的大小。|
|[CReBarCtrl：： MoveBand](#moveband)|將一個索引區從一個索引移至另一個索引。|
|[CReBarCtrl：:P ushChevron](#pushchevron)|以程式設計方式推送燕形。|
|[CReBarCtrl：： RestoreBand](#restoreband)|將 Rebar 控制項中的寬線大小調整為適合的大小。|
|[CReBarCtrl：： SetBandInfo](#setbandinfo)|在 Rebar 控制項中設定現有波段的特性。|
|[CReBarCtrl：： SetBandWidth](#setbandwidth)|在目前的 Rebar 控制項中，設定指定之停駐區的寬度。|
|[CReBarCtrl：： SetBarInfo](#setbarinfo)|設定 Rebar 控制項的特性。|
|[CReBarCtrl：： SetBkColor](#setbkcolor)|設定 Rebar 控制項的預設背景色彩。|
|[CReBarCtrl：： SetColorScheme](#setcolorscheme)|設定 Rebar 控制項上按鈕的色彩配置。|
|[CReBarCtrl：： SetExtendedStyle](#setextendedstyle)|設定目前 Rebar 控制項的延伸樣式。|
|[CReBarCtrl：： SetImageList](#setimagelist)|設定 Rebar 控制項的影像清單。|
|[CReBarCtrl：： SetOwner](#setowner)|設定 Rebar 控制項的擁有者視窗。|
|[CReBarCtrl：： SetPalette](#setpalette)|設定 Rebar 控制項的目前調色板。|
|[CReBarCtrl：： SetTextColor](#settextcolor)|設定 Rebar 控制項的預設文字色彩。|
|[CReBarCtrl：： SetToolTips](#settooltips)|將工具提示控制項與 Rebar 控制項產生關聯。|
|[CReBarCtrl：： SetWindowTheme](#setwindowtheme)|設定 Rebar 控制項的視覺化樣式。|
|[CReBarCtrl：： ShowBand](#showband)|顯示或隱藏 Rebar 控制項中的指定頻。|
|[CReBarCtrl：： SizeToRect](#sizetorect)|將 Rebar 控制項納入指定的矩形。|

## <a name="remarks"></a>備註

Rebar 控制項所在的應用程式會將 Rebar 控制項所包含的子視窗指派給 Rebar 頻外。 子視窗通常是另一個常見的控制項。

Rebar 控制項包含一或多個區段。 每個寬線都可以包含控制項列、點陣圖、文字標籤和子視窗的組合。 此寬線只能包含其中一個專案。

Rebar 控制項可以透過指定的背景點陣圖顯示子視窗。 所有 Rebar 控制項群組都可以調整大小，但使用 RBBS_FIXEDSIZE 樣式的控制項除外。 當您重新置放或調整 Rebar 控制區的大小時，Rebar 控制項會管理指派給該頻外之子視窗的大小和位置。 若要調整大小或變更控制項內的條紋順序，請按一下並拖曳一個頻外的控制條列。

下圖顯示具有三個區段的 Rebar 控制項：

- [寬線 0] 包含一個平面、透明的工具列控制項。

- [波段 1] 包含 [透明標準] 和 [透明] 下拉式按鈕。

- [波段 2] 包含一個下拉式方塊和四個標準按鈕。

   ![Rebar 功能表範例](../../mfc/reference/media/vc4scc1.gif "Rebar 功能表範例")

## <a name="rebar-control"></a>Rebar 控制項

Rebar 控制項支援：

- 影像清單。

- 訊息處理。

- 自訂繪製功能。

- 除了標準視窗樣式以外的各種控制項樣式。 如需這些樣式的清單，請參閱 Windows SDK 中的 [Rebar 控制項樣式](/windows/win32/Controls/rebar-control-styles) 。

如需詳細資訊，請參閱 [使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a> CReBarCtrl：： BeginDrag

依照 Windows SDK 所述，執行 Win32 訊息 [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)的行為。

```cpp
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的索引，此為拖放作業會影響的頻外索引。

*dwPos*<br/>
DWORD 值，包含開始的滑鼠座標。 水準座標是包含在 LOWORD 中，而垂直座標則是包含在 HIWORD 中。 如果您傳遞 (DWORD) -1，Rebar 控制項將會使用滑鼠最後一次呼叫或時的滑鼠位置 `GetMessage` `PeekMessage` 。

## <a name="crebarctrlcreate"></a><a name="create"></a> CReBarCtrl：： Create

建立 Rebar 控制項並將其附加至 `CReBarCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定套用至控制項的 Rebar 控制項樣式的組合。 如需支援的樣式清單，請參閱 Windows SDK 中的 [Rebar 控制項樣式](/windows/win32/Controls/rebar-control-styles) 。

*矩形*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構的參考，這是 Rebar 控制項的位置和大小。

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標，該物件為 Rebar 控制項的父視窗。 它不得為 NULL。

*nID*<br/>
指定 Rebar 控制項的控制項識別碼。

### <a name="return-value"></a>傳回值

如果成功建立物件，則為非零;否則為0。

### <a name="remarks"></a>備註

以兩個步驟建立 Rebar 控制項：

1. 呼叫 [CReBarCtrl](#crebarctrl) 來建立 `CReBarCtrl` 物件。

1. 呼叫這個成員函式，此函式會建立 Windows Rebar 控制項並將其附加至 `CReBarCtrl` 物件。

當您呼叫時 `Create` ，會初始化通用控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a> CReBarCtrl：： CreateEx

 (子視窗) 建立控制項，並將它與物件產生關聯 `CReBarCtrl` 。

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
指定要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定套用至控制項的 Rebar 控制項樣式的組合。 如需支援的樣式清單，請參閱 Windows SDK 中的 [Rebar 控制項樣式](/windows/win32/Controls/rebar-control-styles) 。

*矩形*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，描述要建立之視窗的大小和位置（以*pParentWnd*的用戶端座標表示）。

*pParentWnd*<br/>
視窗的指標，該視窗為控制項的父代。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用 `CreateEx` instead Of [Create](#create) 來套用延伸的 windows 樣式（依 Windows 擴充樣式的 "前言 **WS_EX_** 指定）。

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a> CReBarCtrl：： CReBarCtrl

建立 `CReBarCtrl` 物件。

```
CReBarCtrl();
```

### <a name="example"></a>範例

  請參閱 [CReBarCtrl：： Create](#create)的範例。

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a> CReBarCtrl：:D eleteBand

依照 Windows SDK 所述，執行 Win32 訊息 [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)的行為。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
要刪除之帶狀線的以零為基底的索引。

### <a name="return-value"></a>傳回值

如果成功刪除頻外，則為非零;否則為零。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a> CReBarCtrl：:D ragMove

依照 Windows SDK 所述，執行 Win32 訊息 [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)的行為。

```cpp
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>參數

*dwPos*<br/>
包含新滑鼠座標的 DWORD 值。 水準座標是包含在 LOWORD 中，而垂直座標則是包含在 HIWORD 中。 如果您傳遞 (DWORD) -1，Rebar 控制項將會使用滑鼠最後一次呼叫或時的滑鼠位置 `GetMessage` `PeekMessage` 。

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a> CReBarCtrl：： EndDrag

依照 Windows SDK 所述，執行 Win32 訊息 [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)的行為。

```cpp
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a> CReBarCtrl：： GetBandBorders

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)的行為。

```cpp
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引，將會取出框線。

*中國*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的指標，此結構會接收寬線框線。 如果 Rebar 控制項有 RBS_BANDBORDERS 樣式，則此結構的每個成員都會收到組成框線之帶狀邊的圖元數。 如果 Rebar 控制項沒有 RBS_BANDBORDERS 樣式，則只有此結構的左側成員會收到有效的資訊。 如需 Rebar 控制項樣式的描述，請參閱 Windows SDK 中的 [Rebar 控制項樣式](/windows/win32/Controls/rebar-control-styles) 。

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a> CReBarCtrl：： GetBandCount

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)的行為。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>傳回值

指派給控制項的條紋數目。

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a> CReBarCtrl：： GetBandInfo

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) 的行為。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為起始的寬線索引，將會抓取資訊。

*prbbi*<br/>
[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的指標，用來接收頻外資訊。 您必須將 `cbSize` 此結構的成員設定為 `sizeof(REBARBANDINFO)` ，並將 `fMask` 成員設定為您想要在傳送此訊息之前取得的專案。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a> CReBarCtrl：： GetBandMargins

抓取寬線的邊界。

```cpp
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>參數

*pMargins*<br/>
將接收資訊的 [邊界](/windows/win32/api/uxtheme/ns-uxtheme-margins)結構指標。

### <a name="remarks"></a>備註

此成員函式會模擬 [RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins) 訊息的功能，如 Windows SDK 中所述。

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a> CReBarCtrl：： GetBarHeight

抓取 Rebar 橫條的高度。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>傳回值

值，代表控制項的高度（以圖元為單位）。

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a> CReBarCtrl：： GetBarInfo

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)的行為。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>參數

*prbi*<br/>
[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)結構的指標，此結構會接收 Rebar 控制項資訊。 在傳送此訊息之前，您必須先將此結構的 *cbSize* 成員設定為 `sizeof(REBARINFO)` 。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a> CReBarCtrl：： GetBkColor

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)的行為。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

表示目前預設背景色彩的 COLORRE光圈值。

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a> CReBarCtrl：： GetColorScheme

抓取 Rebar 控制項的 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) 結構。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>參數

*lpc*<br/>
[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)結構的指標，如 Windows SDK 所述。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此 `COLORSCHEME` 結構包含按鈕醒目提示色彩和按鈕陰影色彩。

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a> CReBarCtrl：： GetDropTarget

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)的行為。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>傳回值

[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)介面的指標。

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a> CReBarCtrl：： GetExtendedStyle

取得目前 Rebar 控制項的延伸樣式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>傳回值

表示擴充樣式之旗標的位組合 (或) 。 可能的旗標為 RBS_EX_SPLITTER 和 RBS_EX_TRANSPARENT。 如需詳細資訊，請參閱[CReBarCtrl：： SetExtendedStyle](#setextendedstyle)方法的*dwMask*參數。

### <a name="remarks"></a>備註

這個方法會傳送 [RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove) 的訊息，如 Windows SDK 中所述。

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a> CReBarCtrl：： GetImageList

取得 `CImageList` 與 Rebar 控制項相關聯的物件。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。 如果未針對控制項設定影像清單，則傳回 Null。

### <a name="remarks"></a>備註

此成員函式會使用儲存在 [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) 結構中的大小和遮罩資訊，如 Windows SDK 中所述。

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a> CReBarCtrl：： GetPalette

抓取 Rebar 控制項的目前調色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>傳回值

[CPalette](../../mfc/reference/cpalette-class.md)物件的指標，指定 Rebar 控制項目前的調色板。

### <a name="remarks"></a>備註

請注意，此成員函式會使用 `CPalette` 物件做為其傳回值，而不是 HPALETTE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a> CReBarCtrl：： GetRect

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETRECT](/windows/win32/Controls/rb-getrect)的行為。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>參數

*uBand*<br/>
Rebar 控制項中的寬線索引（以零為基底）。

*中國*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的指標，此結構會接收 Rebar 區的範圍。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a> CReBarCtrl：： GetRowCount

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)的行為。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>傳回值

UINT 值，表示控制項中的帶狀列數目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a> CReBarCtrl：： GetRowHeight

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)的行為。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>參數

*uRow*<br/>
以零為基底的寬線索引，將會抓取其高度。

### <a name="return-value"></a>傳回值

表示資料列高度的 UINT 值（以圖元為單位）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a> CReBarCtrl：： GetTextColor

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)的行為。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>傳回值

COLORRE光圈值，代表目前的預設文字色彩。

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a> CReBarCtrl：： GetToolTips

依照 Windows SDK 所述，執行 Win32 訊息 [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)的行為。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標。

### <a name="remarks"></a>備註

請注意，的 MFC 實會傳回 `GetToolTips` 的指標 `CToolTipCtrl` ，而不是 HWND。

## <a name="crebarctrlhittest"></a><a name="hittest"></a> CReBarCtrl：： System.windows.media.visualtreehelper.hittest

依照 Windows SDK 所述，執行 Win32 訊息 [RB_HITTEST](/windows/win32/Controls/rb-hittest)的行為。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>參數

*prbht*<br/>
[RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo)結構的指標。 傳送訊息之前，必須先將 `pt` 此結構的成員初始化為將在用戶端座標中進行測試的時間點。

### <a name="return-value"></a>傳回值

在給定點以零為基底的索引，如果沒有 Rebar 頻外，則為-1。

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a> CReBarCtrl：： IDToIndex

依照 Windows SDK 所述，執行 Win32 訊息 [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)的行為。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>參數

*uBandID*<br/>
`wID`插入頻外時，在[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的成員中傳遞的指定帶狀的應用程式定義識別碼。

### <a name="return-value"></a>傳回值

如果成功，則為以零為基底的帶索引，否則為-1。 如果有重複的頻外索引，則會傳回第一個。

## <a name="crebarctrlinsertband"></a><a name="insertband"></a> CReBarCtrl：： InsertBand

依照 Windows SDK 所述，執行 Win32 訊息 [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)的行為。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>參數

*uIndex*<br/>
以零為基底的索引，也就是要插入頻外的位置。 如果您將此參數設定為-1，此控制項將會在最後一個位置新增新的頻外。

*prbbi*<br/>
[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的指標，該結構定義要插入的帶狀。 在呼叫此函式之前，您必須先將此結構的 *cbSize* 成員設定為 `sizeof(REBARBANDINFO)` 。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a> CReBarCtrl：： MaximizeBand

將 Rebar 控制項中的寬線大小調整為最大的大小。

```cpp
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引，要最大化。

### <a name="remarks"></a>備註

使用設定為0的 Win32 message [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) 的行為 `fIdeal` ，如 Windows SDK 所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a> CReBarCtrl：： MinimizeBand

將 Rebar 控制項中的寬線大小調整為最小的大小。

```cpp
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引，可將其最小化。

### <a name="remarks"></a>備註

依照 Windows SDK 所述，執行 Win32 訊息 [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a> CReBarCtrl：： MoveBand

依照 Windows SDK 所述，執行 Win32 訊息 [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)的行為。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>參數

*uFrom*<br/>
要移動之帶狀線的以零為基底的索引。

*自動 u）*<br/>
新的寬線位置之以零為基底的索引。 此參數值絕不能大於區段數減一。 若要取得區數，請呼叫 [GetBandCount](#getbandcount)。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a> CReBarCtrl：:P ushChevron

依照 Windows SDK 所述，執行 Win32 訊息 [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)的行為。

```cpp
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的範圍索引，其中的上推線會被推送。

*lAppValue*<br/>
應用程式定義的32位值。 請參閱 Windows SDK [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)中的*lAppValue* 。

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a> CReBarCtrl：： RestoreBand

將 Rebar 控制項中的寬線大小調整為適合的大小。

```cpp
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的寬線索引，要最大化。

### <a name="remarks"></a>備註

以設定為1的方式，執行 Win32 訊息 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) 的行為 `fIdeal` ，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a> CReBarCtrl：： SetBandInfo

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)的行為。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>參數

*uBand*<br/>
以零為基底的索引，這是用來接收新設定的頻外索引。

*prbbi*<br/>
[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的指標，該結構定義要插入的帶狀。 在傳送 `cbSize` 此訊息之前，您必須先將此結構的成員設定為 `sizeof(REBARBANDINFO)` 。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a> CReBarCtrl：： SetBandWidth

在目前的 Rebar 控制項中，設定指定之停駐區的寬度。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>參數

*uBand*\
在Rebar 區的以零為起始的索引。

*cxWidth*\
在Rebar 帶狀線的新寬度（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_rebar` 會定義用來存取目前 Rebar 控制項的變數（）。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>範例

下列程式碼範例會將每個 Rebar 波段設定為相同的寬度。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a> CReBarCtrl：： SetBarInfo

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)的行為。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>參數

*prbi*<br/>
[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)結構的指標，其中包含要設定的資訊。 傳送 `cbSize` 此訊息之前，您必須先將此結構的成員設定為 `sizeof(REBARINFO)`

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a> CReBarCtrl：： SetBkColor

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)的行為。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
代表新預設背景色彩的 COLORRE光圈值。

### <a name="return-value"></a>傳回值

表示先前預設背景色彩的 [COLORREF](/windows/win32/gdi/colorref) 值。

### <a name="remarks"></a>備註

請參閱本主題，以取得何時設定背景色彩的詳細資訊，以及如何設定預設值。

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a> CReBarCtrl：： SetColorScheme

設定 Rebar 控制項上按鈕的色彩配置。

```cpp
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>參數

*lpc*<br/>
[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)結構的指標，如 Windows SDK 所述。

### <a name="remarks"></a>備註

此 `COLORSCHEME` 結構包含按鈕醒目提示色彩和按鈕陰影色彩。

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a> CReBarCtrl：： SetExtendedStyle

設定目前 Rebar 控制項的延伸樣式。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>參數

*dwMask*\
在位元組合 (或旗標的) ，以指定要套用 *dwStyleEx* 參數中的旗標。 使用下列一或多個值：

- `RBS_EX_SPLITTER`：根據預設，會在水準模式下的底部顯示分隔器，並在垂直模式下顯示在右側。
- `RBS_EX_TRANSPARENT`：將 [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) 訊息轉寄至父視窗。

*dwStyleEx*\
在 (或) 指定要套用之樣式的旗標位組合。 若要設定樣式，請指定在 *dwMask* 參數中使用的相同旗標。 若要重設樣式，請指定二進位零。

### <a name="return-value"></a>傳回值

先前的擴充樣式。

### <a name="remarks"></a>備註

這個方法會傳送 [RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle) 的訊息，如 Windows SDK 中所述。

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a> CReBarCtrl：： SetImageList

將影像清單指派給 Rebar 控制項。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標，其中包含要指派給 Rebar 控制項的影像清單。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlsetowner"></a><a name="setowner"></a> CReBarCtrl：： SetOwner

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SETPARENT](/windows/win32/Controls/rb-setparent)的行為。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
要 `CWnd` 設定為 Rebar 控制項擁有者的物件指標。

### <a name="return-value"></a>傳回值

[CWnd](../../mfc/reference/cwnd-class.md)物件的指標，該物件為 Rebar 控制項目前的擁有者。

### <a name="remarks"></a>備註

請注意，這個成員函式會 `CWnd` 針對 Rebar 控制項目前和選取的擁有者，使用物件的指標，而不是對視窗的控制碼。

> [!NOTE]
> 此成員函式不會變更建立控制項時所設定的實際父系;相反地，它會將通知訊息傳送至您指定的視窗。

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a> CReBarCtrl：： SetPalette

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)的行為。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>參數

*hPal*<br/>
HPALETTE，指定 Rebar 控制項將使用的新調色板。

### <a name="return-value"></a>傳回值

[CPalette](../../mfc/reference/cpalette-class.md)物件的指標，指定 Rebar 控制項先前的調色板。

### <a name="remarks"></a>備註

請注意，此成員函式會使用 `CPalette` 物件做為其傳回值，而不是 HPALETTE。

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a> CReBarCtrl：： SetTextColor

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)的行為。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
COLORRE光圈值，代表物件中的新文字色彩 `CReBarCtrl` 。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值，表示與物件相關聯的先前文字色彩 `CReBarCtrl` 。

### <a name="remarks"></a>備註

它是提供來支援 Rebar 控制項中的文字色彩彈性。

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a> CReBarCtrl：： SetToolTips

將工具提示控制項與 Rebar 控制項產生關聯。

```cpp
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標

### <a name="remarks"></a>備註

完成時，您必須終結 `CToolTipCtrl` 物件。

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a> CReBarCtrl：： SetWindowTheme

設定 Rebar 控制項的視覺化樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
Unicode 字串的指標，其中包含要設定的 Rebar 視覺效果樣式。

### <a name="return-value"></a>傳回值

未使用傳回值。

### <a name="remarks"></a>備註

此成員函式會模擬 [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme) 訊息的功能，如 Windows SDK 中所述。

## <a name="crebarctrlshowband"></a><a name="showband"></a> CReBarCtrl：： ShowBand

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SHOWBAND](/windows/win32/Controls/rb-showband)的行為。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>參數

*uBand*<br/>
Rebar 控制項中的寬線索引（以零為基底）。

*fShow*<br/>
指出是否應該顯示或隱藏帶狀。 如果這個值為 TRUE，將會顯示此寬線。 否則，將會隱藏此波段。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a> CReBarCtrl：： SizeToRect

依照 Windows SDK 所述，執行 Win32 訊息 [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)的行為。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的參考，這個物件會指定應調整 Rebar 控制項大小的矩形。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

請注意，此成員函式會使用 `CRect` 物件做為參數，而不是 `RECT` 結構。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
