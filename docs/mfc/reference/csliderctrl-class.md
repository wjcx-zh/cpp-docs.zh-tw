---
title: CSliderCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 2e3572b34f930bb6a7d99b437c01c8aaf970e6c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751270"
---
# <a name="csliderctrl-class"></a>CSliderCtrl 類別

提供 Windows 通用滑桿控制項的功能。

## <a name="syntax"></a>語法

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|建構 `CSliderCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSliderCtrl::清除塞爾](#clearsel)|清除滑塊控制項中的目前選擇。|
|[CSliderCtrl::清除](#cleartics)|從滑塊控制項中刪除目前的刻度線。|
|[CSliderCtrl::建立](#create)|創建滑塊控制項並將其附加到`CSliderCtrl`物件。|
|[CSliderCtrl::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建滑塊控制項並將`CSliderCtrl`其附加到 物件。|
|[CSliderCtrl:GetBuddy](#getbuddy)|將句柄檢索到給定位置的滑塊控制項夥伴視窗。|
|[CSliderCtrl::取得通道Rect](#getchannelrect)|檢索滑塊控制件通道的大小。|
|[CSliderCtrl::取得線尺寸](#getlinesize)|檢索滑塊控制件的行大小。|
|[CSliderCtrl:getNumTics](#getnumtics)|檢索滑塊控制項中的刻度線數。|
|[CSliderCtrl::取得頁面大小](#getpagesize)|檢索滑塊控制件的頁面大小。|
|[CSliderCtrl:GetPos](#getpos)|檢索滑塊的當前位置。|
|[CSliderCtrl:取得範圍](#getrange)|檢索滑塊的最小和最大位置。|
|[CSliderCtrl::取得山脈最大值](#getrangemax)|檢索滑塊的最大位置。|
|[CSliderCtrl::取得蘭格明](#getrangemin)|檢索滑塊的最小位置。|
|[CSliderCtrl:取得選擇](#getselection)|檢索當前選擇的範圍。|
|[CSliderCtrl::獲取拇指長度](#getthumblength)|檢索當前軌道欄控件中的滑塊長度。|
|[CSliderCtrl::取得Thumbrect](#getthumbrect)|檢索滑塊控件的拇指的大小。|
|[CSliderCtrl:GetTic](#gettic)|檢索指定刻度線的位置。|
|[CSliderCtrl::取得蒂卡雷](#getticarray)|檢索滑塊控制項的刻度線位置陣列。|
|[CSliderCtrl::取得蒂波](#getticpos)|在用戶端座標中檢索指定刻度線的位置。|
|[CSliderCtrl:抓取工具提示](#gettooltips)|檢索分配給滑塊控制項的工具提示控件的句柄(如果有)。|
|[CSliderCtrl::SetBuddy](#setbuddy)|將視窗指定為滑塊控制件的好友視窗。|
|[CSliderCtrl::設定線大小](#setlinesize)|設置滑塊控制元件的線大小。|
|[CSliderCtrl::設定頁面大小](#setpagesize)|設置滑塊控制件的頁面大小。|
|[CSliderCtrl::SetPos](#setpos)|設置滑塊的當前位置。|
|[CSliderCtrl::設定範圍](#setrange)|設置滑塊的最小和最大位置。|
|[CSliderCtrl::SetRangeMax](#setrangemax)|設置滑塊的最大位置。|
|[CSliderCtrl::SetRangeMin](#setrangemin)|設置滑塊的最小位置。|
|[CSliderCtrl::設定選擇](#setselection)|設置當前選擇的範圍。|
|[CSliderCtrl::設置拇指長度](#setthumblength)|設置當前軌道欄控件中的滑塊長度。|
|[CSliderCtrl::SetTic](#settic)|設置指定刻度線的位置。|
|[CSliderCtrl::SetTicFreq](#setticfreq)|設置每個滑塊控制的刻度標記頻率。|
|[CSliderCtrl::SetTipside](#settipside)|定位軌道桿控件使用的工具提示控制項。|
|[CSliderCtrl::設定工具提示](#settooltips)|將工具提示控制項分配給滑塊控制項。|

## <a name="remarks"></a>備註

"滑塊控制件"(也稱為軌道列)是包含滑塊和可選刻度線的視窗。 當使用者使用滑鼠或方向鍵移動滑塊時,控件會發送通知消息以指示更改。

當您想要使用者選取一個不連續的值或一組範圍內的連續值時，滑桿控制項就很有用。 例如，您可以使用滑桿控制項允許使用者透過移動滑桿至指定的刻度標記，設定鍵盤的重複率。

此控制項(因此該`CSliderCtrl`類別)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

滑塊以創建滑塊時指定的增量移動。 例如,如果指定滑塊應具有 5 個範圍,則滑塊只能佔據六個位置:滑塊控制件左側的位置和範圍中每個增量的一個位置。 一般來說，這些位置的每一個都以刻度標記來識別。

通過使用建構函數和`Create``CSliderCtrl`的成員函數創建滑塊。 創建滑塊控制項後,可以使用中`CSliderCtrl`的成員函數來更改其許多屬性。 您可以進行的變更包括設定滑桿的最小和最大位置、繪製刻度標記、設定選取範圍，以及重新調整滑桿定位。

有關`CSliderCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[與使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::清除塞爾

清除滑塊控制項中的目前選擇。

```cpp
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*bredraw*<br/>
重繪標誌。 如果此參數為 TRUE,則在清除所選內容後重繪滑塊;如果此參數為 TRUE,則在清除所選內容後重新繪製滑塊。否則,不會重繪滑塊。

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::清除

從滑塊控制項中刪除目前的刻度線。

```cpp
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*bredraw*<br/>
重繪標誌。 如果此參數為 TRUE,則在清除刻度線後重繪滑塊;如果此參數為 TRUE,則在清除刻度線後重新繪製滑塊。否則,不會重繪滑塊。

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::建立

創建滑塊控制項並將其附加到`CSliderCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定滑塊控制件的樣式。 將 Windows SDK 中描述的[滑塊控制項樣式](/windows/win32/Controls/trackbar-control-styles)的任意組合應用於控制項。

*矩形*<br/>
指定滑塊控制項大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指定滑動器的父視窗(通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定滑塊控制項的識別碼。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

在兩個步驟`CSliderCtrl`中構造 一個。 首先調用構造函數,然後調用`Create`,這將創建滑塊控制項並將其附加`CSliderCtrl`到 物件。

根據為*dwStyle*設置的值,滑塊控制項可以具有垂直或水準方向。 它可以有兩側,雙方,或兩者沒有刻度線。 它還可用於指定連續值的範圍。

要將延伸視窗樣式套用於滑動項控制,請呼叫[CreateEx](#createex)`Create`而不是 。

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::創建Ex

創建控制項(子視窗),並將其與`CSliderCtrl`物件關聯。

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
指定滑塊控制件的樣式。 將 Windows SDK 中描述的[滑塊控制項樣式](/windows/win32/Controls/trackbar-control-styles)的任意組合應用於控制項。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl

建構 `CSliderCtrl` 物件。

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl:GetBuddy

將句柄檢索到給定位置的滑塊控制項夥伴視窗。

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>參數

*fLocation*<br/>
一個布爾值,指示要檢索的兩個好友視窗句柄之一。 可以是下列其中一個值：

- TRUE 檢索滑塊左側好友的句柄。 如果滑塊控件使用TBS_VERT樣式,則消息將在滑塊上方檢索好友。

- FALSE 檢索滑塊右側好友的句柄。 如果滑塊控件使用TBS_VERT樣式,則消息將檢索滑塊下方的好友。

### <a name="return-value"></a>傳回值

指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該物件位於*fLocation*指定的位置的好友視窗,如果該位置不存在好友視窗,則指向 NULL。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)的行為,如 Windows SDK 中所述。 有關滑塊控制項樣式的說明,請參閱 Windows SDK 中的[「追蹤欄控制件樣式](/windows/win32/Controls/trackbar-control-styles)」。

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::取得通道Rect

檢索滑塊控制元件通道的邊界矩形的大小和位置。

```cpp
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*利赫浦*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標,該物件在函數傳回時包含通道邊界矩形的大小和位置。

### <a name="remarks"></a>備註

通道是滑塊移動的區域,在選擇範圍時包含高光。

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::取得線尺寸

檢索滑塊控制件的行大小。

```
int GetLineSize() const;
```

### <a name="return-value"></a>傳回值

滑塊控制的線條大小。

### <a name="remarks"></a>備註

行大小會影響滑塊為TB_LINEUP和TB_LINEDOWN通知移動的幅度。 行大小的預設設置為 1。

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl:getNumTics

檢索滑塊控制項中的刻度線數。

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>傳回值

滑塊控制項中的刻度線數。

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::取得頁面大小

檢索滑塊控制件的頁面大小。

```
int GetPageSize() const;
```

### <a name="return-value"></a>傳回值

滑塊控制項的頁面大小。

### <a name="remarks"></a>備註

頁面大小會影響滑塊為TB_PAGEUP移動和TB_PAGEDOWN通知的移動量。

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl:GetPos

檢索滑塊控制項中的滑塊的當前位置。

```
int GetPos() const;
```

### <a name="return-value"></a>傳回值

目前位置。

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl:取得範圍

檢索滑塊控制項中滑塊的最大和最小位置。

```cpp
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>參數

*nMin*<br/>
引用接收最小位置的整數。

*nMax*<br/>
對接收最大位置的整數的引用。

### <a name="remarks"></a>備註

此函數將值複製到*nMin*和*nMax*引用的整數中。

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::取得山脈最大值

檢索滑塊控制項中滑塊的最大位置。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>傳回值

控制項的最大位置。

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::取得蘭格明

檢索滑塊控制件中的滑塊的最小位置。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>傳回值

控制項最小位置。

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl:取得選擇

在滑塊控制項中檢索當前選擇的起始位置和結束位置。

```cpp
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>參數

*nMin*<br/>
引用接收當前選擇的起始位置的整數。

*nMax*<br/>
引用接收當前所選內容的結束位置的整數。

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::獲取拇指長度

檢索當前軌道欄控件中的滑塊長度。

```
int GetThumbLength() const;
```

### <a name="return-value"></a>傳回值

滑塊的長度(以像素為單位)。

### <a name="remarks"></a>備註

此方法發送[TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength)消息,這在 Windows SDK 中介紹。

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::取得Thumbrect

檢索滑塊(拇指)滑塊(拇指)在滑塊控制項中的邊界矩形的大小和位置。

```cpp
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*利赫浦*<br/>
當函數返回時`CRect`,指向包含滑塊邊界矩形的物件的指標。

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl:GetTic

檢索滑塊控件中刻度線的位置。

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>參數

*nTic*<br/>
識別刻度線的零基索引。

### <a name="return-value"></a>傳回值

指定的刻度線或 - 1 的位置(如果*nTic*未指定有效的索引)。

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::取得蒂卡雷

檢索包含滑塊控制項的刻度線位置的陣列的位址。

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>傳回值

包含滑塊控制的刻度線位置的陣列的位址。

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::取得蒂波

檢索滑塊控制項中刻度線當前的物理位置。

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>參數

*nTic*<br/>
識別刻度線的零基索引。

### <a name="return-value"></a>傳回值

在客戶端座標中,如果*nTic*未指定有效的索引,則指定刻度線或 - 1 的物理位置。

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl:抓取工具提示

檢索分配給滑塊控制項的工具提示控件的句柄(如果有)。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標,如果工具提示未使用,則為 NULL。 如果滑塊控制項不使用TBS_TOOLTIPS樣式,則傳回值為 NULL。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)的行為,如 Windows SDK 中所述。 請注意,此成員函數將`CToolTipCtrl`物件而不是句柄返回到控制件。

有關滑塊控制項樣式的說明,請參閱 Windows SDK 中的[「追蹤欄控制件樣式](/windows/win32/Controls/trackbar-control-styles)」。

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy

將視窗指定為滑塊控制件的好友視窗。

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>參數

*普恩德布迪*<br/>
指向物件的`CWnd`指標,該指標將設置為滑塊控制件的好友。

*fLocation*<br/>
指定顯示好友視窗的位置的值。 這個值可以是下列其中一個值：

- 如果軌道欄控件使用TBS_HORZ樣式,好友將顯示在軌道欄的左側。 如果軌道列使用TBS_VERT樣式,好友將顯示在軌道欄控件的上方。

- 如果軌道欄控件使用TBS_HORZ樣式,好友將顯示在軌道欄的右側。 如果軌道列使用TBS_VERT樣式,好友將顯示在軌道欄控件下方。

### <a name="return-value"></a>傳回值

指向以前分配給該位置的滑塊控件的[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy),如 Windows SDK 中所述。 請注意,此成員函數使用指向`CWnd`物件的指標,而不是對其返回值和參數的視窗句柄。

有關滑塊控制項樣式的說明,請參閱 Windows SDK 中的[「追蹤欄控制件樣式](/windows/win32/Controls/trackbar-control-styles)」。

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::設定線大小

設置滑塊控制元件的線條大小。

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
滑塊控制元件的新線大小。

### <a name="return-value"></a>傳回值

上一行大小。

### <a name="remarks"></a>備註

行大小會影響滑塊為TB_LINEUP和TB_LINEDOWN通知移動的幅度。

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::設定頁面大小

設置滑塊控制件的頁面大小。

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
滑塊控制項的新頁面大小。

### <a name="return-value"></a>傳回值

上一頁大小。

### <a name="remarks"></a>備註

頁面大小會影響滑塊為TB_PAGEUP移動和TB_PAGEDOWN通知的移動量。

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos

設置滑塊控制器中的滑塊的目前位置。

```cpp
void SetPos(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定新的滑塊位置。

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::設定範圍

設置滑塊控制項中滑塊的範圍(最小位置和最大位置)。

```cpp
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*nMin*<br/>
滑塊的最小位置。

*nMax*<br/>
滑塊的最大位置。

*bredraw*<br/>
重繪標誌。 如果此參數為 TRUE,則在設置範圍後重繪滑塊;如果此參數為 TRUE,則在設置範圍後重新繪製滑塊。否則,不會重繪滑塊。

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax

設置滑塊控制項中滑塊的最大範圍。

```cpp
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*nMax*<br/>
滑塊的最大位置。

*bredraw*<br/>
重繪標誌。 如果此參數為 TRUE,則在設置範圍後重繪滑塊;如果此參數為 TRUE,則在設置範圍後重新繪製滑塊。否則,不會重繪滑塊。

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin

設置滑塊控制器中的滑塊的最小範圍。

```cpp
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*nMin*<br/>
滑塊的最小位置。

*bredraw*<br/>
重繪標誌。 如果此參數為 TRUE,則在設置範圍後重繪滑塊;如果此參數為 TRUE,則在設置範圍後重新繪製滑塊。否則,不會重繪滑塊。

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::設定選擇

在滑塊控制項中設定當前選擇的起始位置和結束位置。

```cpp
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
滑塊的起始位置。

*nMax*<br/>
滑塊的結束位置。

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::設置拇指長度

設置當前軌道欄控件中的滑塊長度。

```cpp
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*N 長度*|[在]滑塊的長度(以像素為單位)。|

### <a name="remarks"></a>備註

此方法要求將軌道欄控件設置為[TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles)樣式。

此方法發送[TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前追蹤`m_sliderCtrl`列 控制項的變數 。 該示例還定義了一個變數`thumbLength`,用於存儲軌道欄控件的拇指元件的預設長度。 這些變數在下一個示例中使用。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>範例

以下代碼示例將軌道欄控件的拇指元件設置為其預設長度的兩倍。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic

設置滑塊控制項中刻度線的位置。

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>參數

*nTic*<br/>
刻度線的位置。 此參數必須指定正值。

### <a name="return-value"></a>傳回值

設置刻度線時非零;否則 0。

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq

設置在滑塊中顯示刻度線的頻率。

```cpp
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>參數

*恩弗雷克*<br/>
刻度線的頻率。

### <a name="remarks"></a>備註

例如,如果頻率設置為 2,則滑塊範圍內的其他增量將顯示一個刻度線。 頻率的預設設置為 1(即,範圍中的每個增量都與刻度線相關聯)。

您必須使用TBS_AUTOTICKS樣式創建控制項才能使用此函數。 有關詳細資訊,請參閱[CSliderCtrl::建立](#create)。

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipside

定位軌道桿控件使用的工具提示控制項。

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>參數

*n位置*<br/>
表示要顯示工具提示控件的位置的值。 有關可能值的清單,請參閱 win32 消息[TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside),如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

表示工具提示控件的上一位置的值。 返回值等於*nLocation*的可能值之一。

### <a name="remarks"></a>備註

此成員函數實現 win32 消息TBM_SETTIPSIDE的行為,如Windows SDK中所述。 使用TBS_TOOLTIPS樣式顯示工具提示的滑塊控制項。 有關滑塊控制項樣式的說明,請參閱 Windows SDK 中的[「追蹤欄控制件樣式](/windows/win32/Controls/trackbar-control-styles)」。

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::設定工具提示

將工具提示控制項分配給滑塊控制項。

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>參數

*pwndTip*<br/>
指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標,其中包含要與滑塊控制項一起使用的工具提示。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)的行為,如 Windows SDK 中所述。 使用TBS_TOOLTIPS樣式創建滑塊控制項時,它會創建顯示在滑塊旁邊的預設工具提示控制項,顯示滑塊的當前位置。 有關滑塊控制項樣式的說明,請參閱 Windows SDK 中的[「追蹤欄控制件樣式](/windows/win32/Controls/trackbar-control-styles)」。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl 類別](../../mfc/reference/cprogressctrl-class.md)
