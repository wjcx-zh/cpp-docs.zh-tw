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
ms.openlocfilehash: 776892d71e2cb0f5d57512754cd7fa12730eb044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367437"
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
|[CReBarCtrl:CRebarCtrl](#crebarctrl)|建構 `CReBarCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CReBarCtrl::開始拖動](#begindrag)|將鋼筋控件置於拖放模式。|
|[CReBarCtrl:建立](#create)|創建鋼筋控件並將其附加到`CReBarCtrl`物件。|
|[CReBarCtrl::建立Ex](#createex)|使用指定的 Windows 擴充樣式創建鋼筋控制項,並將`CReBarCtrl`其附加到 物件。|
|[CReBarCtrl::DeleteBand](#deleteband)|從鋼筋控件中刪除帶。|
|[CReBarCtrl::D拉格移動](#dragmove)|呼叫 後,在鋼筋控制元件中更新拖動`BeginDrag`位置 。|
|[CReBarCtrl::結束拖動](#enddrag)|終止鋼筋控件的拖放操作。|
|[CReBarCtrl::取得班德邊界](#getbandborders)|檢索波段的邊界。|
|[CReBarCtrl::GetBandCount](#getbandcount)|檢索鋼筋控件中當前波段的計數。|
|[CReBarCtrl::取得班德資訊](#getbandinfo)|檢索鋼筋控件中指定頻段的資訊。|
|[CReBarCtrl::取得帶邊距](#getbandmargins)|檢索波段的邊距。|
|[CReBarCtrl::獲取巴爾高度](#getbarheight)|檢索鋼筋控件的高度。|
|[CReBarCtrl::取得巴資訊](#getbarinfo)|檢索有關鋼筋控件及其使用的圖像清單的資訊。|
|[CReBarCtrl:GetBkColor](#getbkcolor)|檢索鋼筋控件的預設背景顏色。|
|[CReBarCtrl:取得顏色機制](#getcolorscheme)|檢索與鋼筋控件關聯的[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)結構。|
|[CReBarCtrl::取得DropTarget](#getdroptarget)|檢索鋼筋控件的`IDropTarget`介面指標。|
|[CReBarCtrl::取得式延伸樣式](#getextendedstyle)|獲取當前鋼筋控件的擴展樣式。|
|[CReBarCtrl:抓取影像清單](#getimagelist)|檢索與鋼筋控件關聯的圖像清單。|
|[CReBarCtrl::取得調色板](#getpalette)|檢索鋼筋控件的當前調色板。|
|[CReBarCtrl::取得雷ct](#getrect)|檢索鋼筋控件中給定波段的邊界矩形。|
|[CReBarCtrl::取得羅計數](#getrowcount)|檢索鋼筋控件中的波段行數。|
|[CReBarCtrl::獲取羅高](#getrowheight)|檢索鋼筋控件中指定行的高度。|
|[CReBarCtrl::取得文字顏色](#gettextcolor)|檢索鋼筋控件的預設文本顏色。|
|[CReBarCtrl:抓取工具提示](#gettooltips)|檢索與鋼筋控件關聯的任何工具尖端控制項的句柄。|
|[CReBarCtrl:hitTest](#hittest)|確定鋼筋帶的哪個部分位於螢幕上的給定點,如果此時存在鋼筋帶。|
|[CReBarCtrl:: IDTOIndex](#idtoindex)|將帶標識碼轉換為鋼筋控件中的波段索引。|
|[CReBarCtrl::插入帶](#insertband)|在鋼筋控件中插入新頻段。|
|[CReBarCtrl::最大化樂隊](#maximizeband)|將鋼筋控件中的頻帶調整到其最大大小。|
|[CReBarCtrl::最小化帶](#minimizeband)|將鋼筋控件中的頻帶調整到其最小大小。|
|[CReBarCtrl::移動帶](#moveband)|將波段從一個索引移動到另一個索引。|
|[CReBarCtrl::P烏什·雪佛龍](#pushchevron)|以程式設計方式推送 V 形。|
|[CReBarCtrl::恢復樂隊](#restoreband)|將鋼筋控件中的頻帶調整到其理想大小。|
|[CReBarCtrl::SetBandinfo](#setbandinfo)|設置鋼筋控件中現有頻段的特徵。|
|[CReBarCtrl::設定頻寬度](#setbandwidth)|設置當前鋼筋控件中指定停靠頻的寬度。|
|[CReBarCtrl::SetBarinfo](#setbarinfo)|設置鋼筋控件的特徵。|
|[CReBarCtrl:setBkColor](#setbkcolor)|設置鋼筋控件的預設背景顏色。|
|[CReBarCtrl::設定顏色機制](#setcolorscheme)|設置鋼筋控件上的按鈕的色彩配置。|
|[CReBarCtrl::設定式延伸樣式](#setextendedstyle)|設置當前鋼筋控件的擴展樣式。|
|[CReBarCtrl::設定影像清單](#setimagelist)|設置鋼筋控件的圖像清單。|
|[CReBarCtrl::SetOwner](#setowner)|設置鋼筋控件的所有者視窗。|
|[CReBarCtrl::設定調色板](#setpalette)|設置鋼筋控件的當前調色板。|
|[CReBarCtrl::設定文字顏色](#settextcolor)|設定鋼筋控制件的預設文本顏色。|
|[CReBarCtrl::設定工具提示](#settooltips)|將工具尖端控件與鋼筋控件關聯。|
|[CReBarCtrl::設定視窗主題](#setwindowtheme)|設置鋼筋控件的可視樣式。|
|[CReBarCtrl::顯示樂隊](#showband)|在鋼筋控件中顯示或隱藏給定波段。|
|[CreBarctrl:大小托雷](#sizetorect)|將鋼筋控件擬合到指定的矩形。|

## <a name="remarks"></a>備註

鋼筋控件所在的應用程式將鋼筋控件中包含的子視窗分配給鋼筋帶。 子視窗通常是另一個常見控制項。

鋼筋控件包含一個或多個波段。 每個波段可以包含夾持欄、位圖、文本標籤和子視窗的組合。 波段只能包含其中一個專案。

鋼筋控件可以在指定的後台位圖上顯示子視窗。 所有鋼筋控制帶都可以調整大小,但使用RBBS_FIXEDSIZE樣式的帶除外。 重新置放或調整鋼筋控制帶的大小時,鋼筋控件將管理分配給該頻段的子視窗的大小和位置。 要調整控制項中波段的大小或更改順序,請按一下並拖動帶的夾持桿。

下圖顯示了具有三個波段的鋼筋控件:

- 波段 0 包含一個扁平的、透明的工具列控件。

- 波段 1 包含透明標準和透明下拉按鈕。

- 波段 2 包含一個組合框和四個標準按鈕。

   ![Rebar 功能表範例](../../mfc/reference/media/vc4scc1.gif "Rebar 功能表範例")

## <a name="rebar-control"></a>鋼筋控制

鋼筋控制項支援:

- 圖像清單。

- 消息處理。

- 自定義繪圖功能。

- 除了標準視窗樣式之外,還有多種控制樣式。 有關這些樣式的清單,請參閱 Windows SDK 中的[鋼筋控制元件樣式](/windows/win32/Controls/rebar-control-styles)。

有關詳細資訊,請參閱使用[CRebarCtrl](../../mfc/using-crebarctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CReBarCtrl::開始拖動

實現 Win32 消息[RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)的行為,如 Windows SDK 中所述。

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
拖放操作將影響的波段的零基索引。

*德波普斯*<br/>
包含啟動滑鼠座標的 DWORD 值。 水準座標包含在 LOWORD 中,垂直座標包含在 HIWORD 中。 如果通過 (DWORD)-1,鋼筋控件將在上次調`GetMessage`用 控件的線`PeekMessage`程時 使用滑鼠的位置。

## <a name="crebarctrlcreate"></a><a name="create"></a>CReBarCtrl:建立

創建鋼筋控件並將其附加到`CReBarCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定應用於控制的鋼筋控件樣式的組合。 有關支援的樣式清單,請參閱 Windows SDK 中的[鋼筋控制樣式](/windows/win32/Controls/rebar-control-styles)。

*矩形*<br/>
對[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,即鋼筋控件的位置和大小。

*pparentwnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該物件是鋼筋控件的父視窗。 它不得為 NULL。

*nID*<br/>
指定鋼筋控制的控制 ID。

### <a name="return-value"></a>傳回值

如果物件已成功創建,則非零;否則 0。

### <a name="remarks"></a>備註

通過兩個步驟創建鋼筋控件:

1. 調用[CReBarCtrl](#crebarctrl)`CReBarCtrl`建構 物件。

1. 調用此成員函數,該函數創建 Windows 鋼筋控件並將其`CReBarCtrl`附加到 物件。

呼叫`Create`時呼叫 ,將初始化公共控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CReBarCtrl::建立Ex

創建控制項(子視窗),並將其與`CReBarCtrl`物件關聯。

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
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定應用於控制的鋼筋控件樣式的組合。 有關支援的樣式清單,請參閱 Windows SDK 中的[鋼筋控制樣式](/windows/win32/Controls/rebar-control-styles)。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>CReBarCtrl:CRebarCtrl

建立 `CReBarCtrl` 物件。

```
CReBarCtrl();
```

### <a name="example"></a>範例

  請參考[CReBarCtrl 的範例:建立](#create)。

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl::DeleteBand

實現 Win32 消息[RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)的行為,如 Windows SDK 中所述。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
要刪除的波段的從零開始索引。

### <a name="return-value"></a>傳回值

如果頻帶成功刪除,則非零;否則為零。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl::D拉格移動

實現 Win32 消息[的行為RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove),如 Windows SDK 中所述。

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>參數

*德波普斯*<br/>
包含新滑鼠座標的 DWORD 值。 水準座標包含在 LOWORD 中,垂直座標包含在 HIWORD 中。 如果通過 (DWORD)-1,鋼筋控件將在上次調`GetMessage`用 控件的線`PeekMessage`程時 使用滑鼠的位置。

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>CReBarCtrl::結束拖動

實現 Win32 消息[RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)的行為,如 Windows SDK 中所述。

```
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>CReBarCtrl::取得班德邊界

實現 Win32 消息[RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)的行為,如 Windows SDK 中所述。

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>參數

*烏班德*<br/>
將為其檢索邊框的帶的零基索引。

*中國*<br/>
指向將接收波段邊框的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。 如果鋼筋控件具有RBS_BANDBORDERS樣式,則此結構的每個成員將收到構成邊框的帶子側的像素數。 如果鋼筋控件沒有RBS_BANDBORDERS樣式,則只有此結構的左側成員才會接收有效資訊。 有關鋼筋控件樣式的說明,請參閱 Windows SDK 中的[鋼筋控制式樣式](/windows/win32/Controls/rebar-control-styles)。

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CReBarCtrl::GetBandCount

實現 Win32 消息[RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)的行為,如 Windows SDK 中所述。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>傳回值

分配給控制件的頻段數。

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>CReBarCtrl::取得班德資訊

實現 Win32 消息的行為[RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) Windows SDK 中所述。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>參數

*烏班德*<br/>
將為其檢索資訊的波段的零基索引。

*普爾比*<br/>
指向[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的指標,用於接收波段資訊。 您必須將`cbSize`此結構的成員設置為`sizeof(REBARBANDINFO)`,`fMask`並將成員設置為要檢索的項目,然後再發送此消息。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl::取得帶邊距

檢索波段的邊距。

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>參數

*pMargins*<br/>
指向將接收資訊[的 MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins)結構的指標。

### <a name="remarks"></a>備註

此成員函數類比[RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins)消息的功能,如 Windows SDK 中所述。

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>CReBarCtrl::獲取巴爾高度

檢索鋼筋的高度。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>傳回值

表示控件的高度(以像素為單位)的值。

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>CReBarCtrl::取得巴資訊

實現 Win32 消息[RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)的行為,如 Windows SDK 中所述。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>參數

*普爾比*<br/>
指向將接收鋼筋控制資訊的[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)結構的指標。 送出此訊息之前,必須為此結構的*cbSize*成員設定`sizeof(REBARINFO)`到 。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl:GetBkColor

實現 Win32 消息[RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)的行為,如 Windows SDK 中所述。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

表示目前預設背景顏色的 COLORREF 值。

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CReBarCtrl:取得顏色機制

檢索鋼筋控件的[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)結構。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>參數

*lpcs*<br/>
指向[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)結構的指標,如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

該`COLORSCHEME`結構包括按鈕高光顏色和按鈕陰影顏色。

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>CReBarCtrl::取得DropTarget

實現 Win32 消息[RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)的行為,如 Windows SDK 中所述。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>傳回值

指向[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)介面的指標。

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CReBarCtrl::取得式延伸樣式

獲取當前鋼筋控件的擴展樣式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>傳回值

指示擴展樣式的標誌的位組合 (OR)。 可能的標誌RBS_EX_SPLITTER和RBS_EX_TRANSPARENT。 有關詳細資訊,請參閱[CReBarCtrl:set 擴展樣式](#setextendedstyle)方法的*dwMask*參數。

### <a name="remarks"></a>備註

此方法發送[RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove)消息,這在 Windows SDK 中介紹。

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>CReBarCtrl:抓取影像清單

獲取與`CImageList`鋼筋控件關聯的物件。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。 如果未為控制項設定影像清單,則傳回 NULL。

### <a name="remarks"></a>備註

此成員函數使用存儲在[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)結構中的大小和遮罩資訊,如 Windows SDK 中所述。

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>CReBarCtrl::取得調色板

檢索鋼筋控件的當前調色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>傳回值

指向指定鋼筋控件當前調色板的[CPalette](../../mfc/reference/cpalette-class.md)物件的指標。

### <a name="remarks"></a>備註

請注意,此成員函數使用`CPalette`對象作為其返回值,而不是 HPALETTE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl::取得雷ct

實現 Win32 消息[RB_GETRECT](/windows/win32/Controls/rb-getrect)的行為,如 Windows SDK 中所述。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>參數

*烏班德*<br/>
鋼筋控件中帶的零基索引。

*中國*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標,該結構將接收鋼筋帶的邊界。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CReBarCtrl::取得羅計數

實現 Win32 消息[RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)的行為,如 Windows SDK 中所述。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>傳回值

表示控制項中帶行數的 UINT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>CReBarCtrl::獲取羅高

實現 Win32 消息[RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)的行為,如 Windows SDK 中所述。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>參數

*uRow*<br/>
將檢索其高度的波段的從零開始索引。

### <a name="return-value"></a>傳回值

表示行高度(以像素為單位)的 UINT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>CReBarCtrl::取得文字顏色

實現 Win32 消息[RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)的行為,如 Windows SDK 中所述。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>傳回值

表示目前預設文字顏色的 COLORREF 值。

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>CReBarCtrl:抓取工具提示

實現 Win32 消息[RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)的行為,如 Windows SDK 中所述。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標。

### <a name="remarks"></a>備註

請注意,的`GetToolTips`MFC 實現返回`CToolTipCtrl`指向 的指標,而不是 HWND。

## <a name="crebarctrlhittest"></a><a name="hittest"></a>CReBarCtrl:hitTest

實現 Win32 消息[RB_HITTEST](/windows/win32/Controls/rb-hittest)的行為,如 Windows SDK 中所述。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>參數

*普爾巴特*<br/>
指向[RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo)結構的指標。 在傳送訊息之前`pt`, 必須初始化此結構的成員到將在客戶端座標中測試的點。

### <a name="return-value"></a>傳回值

給定點處的波段的零基索引,如果點沒有鋼筋帶,則為 -1。

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>CReBarCtrl:: IDTOIndex

實現 Win32 消息[RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)的行為,如 Windows SDK 中所述。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>參數

*烏班德*<br/>
指定頻段的應用程式定義標識符,在插入頻段時在`wID` [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的成員中傳遞。

### <a name="return-value"></a>傳回值

零基波段索引(如果成功)或 -1 否則。 如果存在重複的波段索引,則返回第一個波段索引。

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CReBarCtrl::插入帶

實現 Win32 消息[RB_INSERTBAND](/windows/win32/Controls/rb-insertband)的行為,如 Windows SDK 中所述。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>參數

*uIndex*<br/>
將插入波段的位置的零基索引。 如果將此參數設置為 -1,則控件將在最後一個位置添加新波段。

*普爾比*<br/>
指向[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的指標,用於定義要插入的頻帶。 在調用此函數之前,必須為此結構的`sizeof(REBARBANDINFO)`*cbSize*成員設置。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CReBarCtrl::最大化樂隊

將鋼筋控件中的頻帶調整到其最大大小。

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
要最大化的波段的零基索引。

### <a name="remarks"></a>備註

實現 Win32 消息[的行為,RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband)設置為`fIdeal`0,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>CReBarCtrl::最小化帶

將鋼筋控件中的頻帶調整到其最小大小。

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
要最小化的波段的零基索引。

### <a name="remarks"></a>備註

實現 Win32 消息[的行為RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband),如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>CReBarCtrl::移動帶

實現 Win32 消息[RB_MOVEBAND](/windows/win32/Controls/rb-moveband)的行為,如 Windows SDK 中所述。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>參數

*u 從*<br/>
要移動的波段的零基索引。

*uTo*<br/>
新波段位置的零基索引。 此參數值絕不能大於帶數減去 1。 要取得頻段數,請致電[GetBandCount](#getbandcount)。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl::P烏什·雪佛龍

實現 Win32 消息[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)的行為,如 Windows SDK 中所述。

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
其雪佛龍將推送的帶的零基指數。

*lAppValue*<br/>
應用程式定義了 32 位值。 請參閱 windows SDK 中[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)中的*lAppValue。*

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CReBarCtrl::恢復樂隊

將鋼筋控件中的頻帶調整到其理想大小。

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
要最大化的波段的零基索引。

### <a name="remarks"></a>備註

實現 Win32 消息[的行為RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband)設置為`fIdeal`1,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>CReBarCtrl::SetBandinfo

實現 Win32 消息[RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)的行為,如 Windows SDK 中所述。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
用於接收新設置的波段的從零為基礎的索引。

*普爾比*<br/>
指向定義要插入的頻帶的[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)結構的指標。 送出此訊息之前`cbSize`,必須為此結構的成員`sizeof(REBARBANDINFO)`設定到 。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>CReBarCtrl::設定頻寬度

設置當前鋼筋控件中指定停靠頻的寬度。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*烏班德*|[在]鋼筋帶的零基索引。|
|*cxWidth*|[在]鋼筋頻的新寬度,以像素為單位。|

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前的鋼筋控制`m_rebar`元件的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>範例

以下代碼示例將每個鋼筋帶設置為相同的寬度。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>CReBarCtrl::SetBarinfo

實現 Win32 消息[RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)的行為,如 Windows SDK 中所述。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>參數

*普爾比*<br/>
指向包含要設置的資訊的[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)結構的指標。 送出此訊息`sizeof(REBARINFO)`之前`cbSize`,必須為此結構的成員設定

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl:setBkColor

實現 Win32 消息[RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)的行為,如 Windows SDK 中所述。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
表示新預設背景顏色的 COLORREF 值。

### <a name="return-value"></a>傳回值

表示上一個預設背景顏色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

有關何時設置背景顏色以及如何設置預設值的詳細資訊,請參閱本主題。

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CReBarCtrl::設定顏色機制

設置鋼筋控件上的按鈕的色彩配置。

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>參數

*lpcs*<br/>
指向[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)結構的指標,如 Windows SDK 中所述。

### <a name="remarks"></a>備註

該`COLORSCHEME`結構包括按鈕高光顏色和按鈕陰影顏色。

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CReBarCtrl::設定式延伸樣式

設置當前鋼筋控件的擴展樣式。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwMask*|[在]標誌的位組合 (OR),用於指定*dwStyleEx*參數中應用哪些標誌。 使用以下一個或多個值:<br /><br /> RBS_EX_SPLITTER:默認情況下,以水平模式顯示底部的拆分器,在垂直模式下向右顯示拆分器。<br /><br /> RBS_EX_TRANSPARENT:將[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)消息轉發到父視窗。|
|*dwStyleEx*|[在]指定要應用的樣式的標誌的位組合 (OR)。 要設置樣式,請指定*dwMask*參數中使用的相同標誌。 要重置樣式,請指定二進位零。|

### <a name="return-value"></a>傳回值

上一個擴展樣式。

### <a name="remarks"></a>備註

此方法發送[RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle)消息,這在 Windows SDK 中介紹。

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>CReBarCtrl::設定影像清單

將圖像清單分配給鋼筋控件。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標,該物件包含要分配給鋼筋控件的圖像清單。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CReBarCtrl::SetOwner

實現 Win32 消息[RB_SETPARENT](/windows/win32/Controls/rb-setparent)的行為,如 Windows SDK 中所述。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向`CWnd`要設置為鋼筋控件所有者的物件的指標。

### <a name="return-value"></a>傳回值

指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該物件是鋼筋控件的當前擁有者。

### <a name="remarks"></a>備註

請注意,此成員函數使用指向`CWnd`物件的物件,用於鋼筋控件的當前和選定擁有者,而不是對視窗的句柄。

> [!NOTE]
> 此成員函數不會更改創建控制項時設置的實際父級;而是向指定的視窗發送通知消息。

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>CReBarCtrl::設定調色板

實現 Win32 消息[RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)的行為,如 Windows SDK 中所述。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>參數

*hPal*<br/>
指定鋼筋控件將使用的新調色板的 HPALETTE。

### <a name="return-value"></a>傳回值

指向指定鋼筋控件上一個調色板的[CPalette](../../mfc/reference/cpalette-class.md)物件的指標。

### <a name="remarks"></a>備註

請注意,此成員函數使用`CPalette`對象作為其返回值,而不是 HPALETTE。

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CReBarCtrl::設定文字顏色

實現 Win32 消息[RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)的行為,如 Windows SDK 中所述。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
表示物件中新文字顏色的`CReBarCtrl`COLORREF 值。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值表示`CReBarCtrl`與 物件關聯的上一個文字顏色。

### <a name="remarks"></a>備註

它用於支援鋼筋控件中的文本顏色靈活性。

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>CReBarCtrl::設定工具提示

將工具尖端控件與鋼筋控件關聯。

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標

### <a name="remarks"></a>備註

完成物件後,`CToolTipCtrl`必須銷毀該物件。

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl::設定視窗主題

設置鋼筋控件的可視樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pssSubApp 名稱*<br/>
指向 Unicode 字串的指標,其中包含要設置的鋼筋可視樣式。

### <a name="return-value"></a>傳回值

不使用返回值。

### <a name="remarks"></a>備註

此成員函數類比[RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme)消息的功能,如 Windows SDK 中所述。

## <a name="crebarctrlshowband"></a><a name="showband"></a>CReBarCtrl::顯示樂隊

實現 Win32 消息[的行為RB_SHOWBAND](/windows/win32/Controls/rb-showband),如 Windows SDK 中所述。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>參數

*烏班德*<br/>
鋼筋控件中帶的零基索引。

*f 顯示*<br/>
指示帶是應顯示還是隱藏。 如果此值為 TRUE,則顯示波段。 否則,將隱藏該波段。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CreBarctrl:大小托雷

實現 Win32 消息[RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)的行為,如 Windows SDK 中所述。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>參數

*矩形*<br/>
對[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的引用,該物件指定鋼筋控件應調整到的矩形。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

請注意,此成員函數使用`CRect`對象作為參數`RECT`,而不是結構。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
