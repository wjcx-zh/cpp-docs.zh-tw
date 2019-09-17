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
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502511"
---
# <a name="csliderctrl-class"></a>CSliderCtrl 類別

提供 Windows 通用滑桿控制項的功能。

## <a name="syntax"></a>語法

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|建構 `CSliderCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|清除滑杆控制項中目前的選取範圍。|
|[CSliderCtrl::ClearTics](#cleartics)|從滑杆控制項中移除目前的刻度。|
|[CSliderCtrl::Create](#create)|建立滑杆控制項並將其附加至`CSliderCtrl`物件。|
|[CSliderCtrl::CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的滑杆控制項，並將其附加`CSliderCtrl`至物件。|
|[CSliderCtrl::GetBuddy](#getbuddy)|抓取位於指定位置之滑杆控制項好友視窗的控制碼。|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|抓取滑杆控制項的通道大小。|
|[CSliderCtrl::GetLineSize](#getlinesize)|抓取滑杆控制項的線條大小。|
|[CSliderCtrl::GetNumTics](#getnumtics)|抓取滑杆控制項中的刻度數。|
|[CSliderCtrl::GetPageSize](#getpagesize)|抓取滑杆控制項的頁面大小。|
|[CSliderCtrl::GetPos](#getpos)|抓取滑杆的目前位置。|
|[CSliderCtrl::GetRange](#getrange)|抓取滑杆的最小和最大位置。|
|[CSliderCtrl::GetRangeMax](#getrangemax)|抓取滑杆的最大位置。|
|[CSliderCtrl::GetRangeMin](#getrangemin)|抓取滑杆的最小位置。|
|[CSliderCtrl::GetSelection](#getselection)|抓取目前選取範圍的範圍。|
|[CSliderCtrl::GetThumbLength](#getthumblength)|抓取目前的  跟蹤 控制項中滑杆的長度。|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|抓取滑杆控制項捲動方塊的大小。|
|[CSliderCtrl::GetTic](#gettic)|抓取指定之刻度的位置。|
|[CSliderCtrl::GetTicArray](#getticarray)|抓取滑杆控制項之刻度標記位置的陣列。|
|[CSliderCtrl::GetTicPos](#getticpos)|在用戶端座標中，捕獲指定之刻度的位置。|
|[CSliderCtrl::GetToolTips](#gettooltips)|抓取指派給滑杆控制項的工具提示控制項的控制碼（如果有的話）。|
|[CSliderCtrl::SetBuddy](#setbuddy)|將視窗指派為滑杆控制項的合作者視窗。|
|[CSliderCtrl::SetLineSize](#setlinesize)|設定滑杆控制項的線條大小。|
|[CSliderCtrl::SetPageSize](#setpagesize)|設定滑杆控制項的頁面大小。|
|[CSliderCtrl::SetPos](#setpos)|設定滑杆的目前位置。|
|[CSliderCtrl::SetRange](#setrange)|設定滑杆的最小和最大位置。|
|[CSliderCtrl::SetRangeMax](#setrangemax)|設定滑杆的最大位置。|
|[CSliderCtrl::SetRangeMin](#setrangemin)|設定滑杆的最小位置。|
|[CSliderCtrl::SetSelection](#setselection)|設定目前選取範圍。|
|[CSliderCtrl::SetThumbLength](#setthumblength)|設定目前的 在|
|[CSliderCtrl::SetTic](#settic)|設定指定之刻度的位置。|
|[CSliderCtrl::SetTicFreq](#setticfreq)|設定每個滑杆控制項增量的刻度頻率。|
|[CSliderCtrl::SetTipSide](#settipside)|放置 [並排] 控制項所使用的工具提示控制項。|
|[CSliderCtrl::SetToolTips](#settooltips)|將工具提示控制項指派給滑杆控制項。|

## <a name="remarks"></a>備註

「滑杆控制項」（也稱為「捲軸」）是一個視窗，其中包含滑杆和選擇性的刻度標記。 當使用者使用滑鼠或方向鍵移動滑杆時，控制項會傳送通知訊息來表示變更。

當您想要使用者選取一個不連續的值或一組範圍內的連續值時，滑桿控制項就很有用。 例如，您可以使用滑桿控制項允許使用者透過移動滑桿至指定的刻度標記，設定鍵盤的重複率。

這個控制項（因此`CSliderCtrl`類別）僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

滑杆會以您在建立時所指定的增量移動。 例如，如果您指定滑杆的範圍應為五個，則滑杆只能佔用六個位置：滑杆控制項左邊的位置，以及範圍內每個增量的一個位置。 一般來說，這些位置的每一個都以刻度標記來識別。

您可以使用的函式和`Create`成員`CSliderCtrl`函式來建立滑杆。 建立滑杆控制項之後，您可以使用中`CSliderCtrl`的成員函式來變更其許多屬性。 您可以進行的變更包括設定滑桿的最小和最大位置、繪製刻度標記、設定選取範圍，以及重新調整滑桿定位。

如需使用`CSliderCtrl`的詳細資訊，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="clearsel"></a>CSliderCtrl：： ClearSel

清除滑杆控制項中目前的選取範圍。

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*bRedraw*<br/>
重繪旗標。 如果此參數為 TRUE，則會在清除選取範圍之後重新繪製滑杆;否則滑杆不會重新繪製。

##  <a name="cleartics"></a>  CSliderCtrl::ClearTics

從滑杆控制項中移除目前的刻度。

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*bRedraw*<br/>
重繪旗標。 如果此參數為 TRUE，則會在清除刻度之後重新繪製滑杆;否則滑杆不會重新繪製。

##  <a name="create"></a>CSliderCtrl：： Create

建立滑杆控制項並將其附加至`CSliderCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定滑杆控制項的樣式。 將[滑杆控制項樣式](/windows/win32/Controls/trackbar-control-styles)的任意組合（如 Windows SDK 中所述）套用至控制項。

*rect*<br/>
指定滑杆控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構。

*pParentWnd*<br/>
指定滑杆控制項的父視窗，通常是`CDialog`。 不得為 Null。

*nID*<br/>
指定滑杆控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為0。

### <a name="remarks"></a>備註

您可以使用`CSliderCtrl`兩個步驟來建立。 首先，呼叫此函式，然後呼叫`Create`，它會建立滑杆控制項並將其附加`CSliderCtrl`至物件。

根據為*dwStyle*所設定的值而定，滑杆控制項可以是垂直或水準方向。 它可以在兩側、兩邊或兩者都有刻度標記。 它也可以用來指定連續值的範圍。

若要將擴充的視窗樣式套用至滑杆控制項，請呼叫[CreateEx](#createex)，而不是`Create`。

##  <a name="createex"></a>CSliderCtrl：： CreateEx

建立控制項（子視窗），並將它與`CSliderCtrl`物件產生關聯。

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
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定滑杆控制項的樣式。 將[滑杆控制項樣式](/windows/win32/Controls/trackbar-control-styles)的任意組合（如 Windows SDK 中所述）套用至控制項。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考，描述要建立之視窗的大小和位置，以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx` ，而不是[Create](#create)來套用擴充的 windows 樣式（由 Windows 擴充樣式指定于**WS_EX_** 的前面）。

##  <a name="csliderctrl"></a>CSliderCtrl：： CSliderCtrl

建構 `CSliderCtrl` 物件。

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>CSliderCtrl：： GetBuddy

抓取位於指定位置之滑杆控制項好友視窗的控制碼。

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>參數

*fLocation*<br/>
布林值，指出要抓取的兩個合作者視窗控制碼中的哪一個。 可為下列其中一個值：

- TRUE 會抓取滑杆左邊的好友控制碼。 如果滑杆控制項使用 TBS_VERT 樣式，訊息將會抓取滑杆上方的好友。

- FALSE 會抓取滑杆右邊的合作者控制碼。 如果滑杆控制項使用 TBS_VERT 樣式，訊息將會抓取滑杆下方的好友。

### <a name="return-value"></a>傳回值

[CWnd](../../mfc/reference/cwnd-class.md)物件的指標，這是*fLocation*所指定位置的合作者視窗，如果該位置沒有任何合作者視窗，則為 Null。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)的行為，如 Windows SDK 中所述。 如需滑杆控制項樣式的說明，請參閱 Windows SDK 中的 [敘述][控制項樣式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="getchannelrect"></a>CSliderCtrl：： GetChannelRect

抓取滑杆控制項通道的周框大小和位置。

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*lprc*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標，其中包含函式傳回時，通道周框的大小和位置。

### <a name="remarks"></a>備註

通道是滑杆移動的區域，其中包含選取範圍時的反白顯示。

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

抓取滑杆控制項的線條大小。

```
int GetLineSize() const;
```

### <a name="return-value"></a>傳回值

滑杆控制項的線條大小。

### <a name="remarks"></a>備註

線條大小會影響滑杆針對 TB_LINEUP 和 TB_LINEDOWN 通知移動的程度。 線條大小的預設設定為1。

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

抓取滑杆控制項中的刻度數。

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>傳回值

滑杆控制項中的刻度數。

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

抓取滑杆控制項的頁面大小。

```
int GetPageSize() const;
```

### <a name="return-value"></a>傳回值

滑杆控制項的頁面大小。

### <a name="remarks"></a>備註

頁面大小會影響 TB_PAGEUP 和 TB_PAGEDOWN 通知的滑杆移動量。

##  <a name="getpos"></a>CSliderCtrl：： GetPos

抓取滑杆控制項中滑杆的目前位置。

```
int GetPos() const;
```

### <a name="return-value"></a>傳回值

目前位置。

##  <a name="getrange"></a>CSliderCtrl：： GetRange

抓取滑杆控制項中滑杆的最大和最小位置。

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>參數

*nMin*<br/>
參考接收最小位置的整數。

*nMax*<br/>
參考接收最大位置的整數。

### <a name="remarks"></a>備註

此函式會將值複製到*n 每天下限*和*n 上限*所參考的整數中。

##  <a name="getrangemax"></a>CSliderCtrl：： GetRangeMax

抓取滑杆控制項中滑杆的最大位置。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>傳回值

控制項的最大位置。

##  <a name="getrangemin"></a>CSliderCtrl：： GetRangeMin

抓取滑杆控制項中滑杆的最小位置。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>傳回值

控制項的最小位置。

##  <a name="getselection"></a>CSliderCtrl：： GetSelection

抓取滑杆控制項中目前選取範圍的開始和結束位置。

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>參數

*nMin*<br/>
參考接收目前選取範圍之開始位置的整數。

*nMax*<br/>
參考接收目前選取範圍結束位置的整數。

##  <a name="getthumblength"></a>CSliderCtrl：： GetThumbLength

抓取目前的  跟蹤 控制項中滑杆的長度。

```
int GetThumbLength() const;
```

### <a name="return-value"></a>傳回值

滑杆的長度（以圖元為單位）。

### <a name="remarks"></a>備註

這個方法會傳送[TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength)訊息，如 Windows SDK 中所述。

##  <a name="getthumbrect"></a>CSliderCtrl：： GetThumbRect

抓取滑杆控制項中滑杆（捲軸）的周框大小和位置。

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*lprc*<br/>
`CRect`物件的指標，其中包含函式傳回時滑杆的周框。

##  <a name="gettic"></a>CSliderCtrl：： GetTic

抓取滑杆控制項中刻度的位置。

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>參數

*nTic*<br/>
以零為基底的索引，識別刻度。

### <a name="return-value"></a>傳回值

指定之刻度的位置，如果*nTic*未指定有效的索引，則為-1。

##  <a name="getticarray"></a>CSliderCtrl：： GetTicArray

抓取陣列的位址，其中包含滑杆控制項之刻度的位置。

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>傳回值

包含滑杆控制項刻度標記位置之陣列的位址。

##  <a name="getticpos"></a>CSliderCtrl：： GetTicPos

抓取滑杆控制項中刻度的目前實體位置。

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>參數

*nTic*<br/>
以零為基底的索引，識別刻度。

### <a name="return-value"></a>傳回值

指定之刻度的實體位置（以工作區座標表示）; 如果*nTic*未指定有效的索引，則為-1。

##  <a name="gettooltips"></a>CSliderCtrl：： GetToolTips

抓取指派給滑杆控制項的工具提示控制項的控制碼（如果有的話）。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標，如果工具提示不在使用中，則為 Null。 如果滑杆控制項不使用 TBS_TOOLTIPS 樣式，則傳回值會是 Null。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)的行為，如 Windows SDK 中所述。 請注意，此成員`CToolTipCtrl`函式會傳回物件，而不是控制項的控制碼。

如需滑杆控制項樣式的說明，請參閱 Windows SDK 中的 [敘述][控制項樣式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="setbuddy"></a>CSliderCtrl：： SetBuddy

將視窗指派為滑杆控制項的合作者視窗。

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>參數

*pWndBuddy*<br/>
`CWnd`物件的指標，將設定為滑杆控制項的好友。

*fLocation*<br/>
值，指定要顯示好友視窗的位置。 此值可以是下列其中一項：

- 如果 [列數] 控制項使用 TBS_HORZ 樣式，則 [好友] 會出現在 [顯示] 的左側。 如果您使用 TBS_VERT 樣式，則該好友會顯示在 [在 []] 控制項上方。

- 錯誤如果 [跟蹤] 控制項使用 TBS_HORZ 樣式，則好友會出現在 [顯示] 的右側。 如果您使用 TBS_VERT 樣式，則該好友會出現在 [顯示在] 控制項下方。

### <a name="return-value"></a>傳回值

[CWnd](../../mfc/reference/cwnd-class.md)物件的指標，先前已指派給該位置的滑杆控制項。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)的行為，如 Windows SDK 中所述。 請注意，此成員函式會`CWnd`使用物件的指標，而不是其傳回值和參數的視窗控制碼。

如需滑杆控制項樣式的說明，請參閱 Windows SDK 中的 [敘述][控制項樣式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

設定滑杆控制項的線條大小。

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
滑杆控制項的新行大小。

### <a name="return-value"></a>傳回值

先前的行大小。

### <a name="remarks"></a>備註

線條大小會影響滑杆針對 TB_LINEUP 和 TB_LINEDOWN 通知移動的程度。

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

設定滑杆控制項的頁面大小。

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
滑杆控制項的新頁面大小。

### <a name="return-value"></a>傳回值

先前的頁面大小。

### <a name="remarks"></a>備註

頁面大小會影響 TB_PAGEUP 和 TB_PAGEDOWN 通知的滑杆移動量。

##  <a name="setpos"></a>CSliderCtrl：： SetPos

設定滑杆控制項中滑杆的目前位置。

```
void SetPos(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定蜪鎏 彸。

##  <a name="setrange"></a>CSliderCtrl：： SetRange

設定滑杆控制項中滑杆的範圍（最小和最大位置）。

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*nMin*<br/>
滑杆的最小位置。

*nMax*<br/>
滑杆的最大位置。

*bRedraw*<br/>
重繪旗標。 如果此參數為 TRUE，則會在設定範圍之後重新繪製滑杆;否則滑杆不會重新繪製。

##  <a name="setrangemax"></a>CSliderCtrl：： SetRangeMax

設定滑杆控制項中滑杆的最大範圍。

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*nMax*<br/>
滑杆的最大位置。

*bRedraw*<br/>
重繪旗標。 如果此參數為 TRUE，則會在設定範圍之後重新繪製滑杆;否則滑杆不會重新繪製。

##  <a name="setrangemin"></a>CSliderCtrl：： SetRangeMin

設定滑杆控制項中滑杆的最小範圍。

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>參數

*nMin*<br/>
滑杆的最小位置。

*bRedraw*<br/>
重繪旗標。 如果此參數為 TRUE，則會在設定範圍之後重新繪製滑杆;否則滑杆不會重新繪製。

##  <a name="setselection"></a>CSliderCtrl：： SetSelection

設定滑杆控制項中目前選取範圍的開始和結束位置。

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
滑杆的開始位置。

*nMax*<br/>
滑杆的結束位置。

##  <a name="setthumblength"></a>CSliderCtrl：： SetThumbLength

設定目前的 在

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*nLength*|在滑杆的長度（以圖元為單位）。|

### <a name="remarks"></a>備註

這個方法需要將 [設置] 控制項設定為[TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles)樣式。

這個方法會傳送[TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength)訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_sliderCtrl`存取目前的 [動作] 控制項的變數。 此範例也會定義一個變數`thumbLength`，用來儲存 [捲軸] 控制項的 [thumb] 元件的預設長度。 下一個範例會使用這些變數。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會將 [動作] 控制項的 [thumb] 元件設定為預設長度的兩倍。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

設定滑杆控制項中刻度的位置。

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>參數

*nTic*<br/>
刻度的位置。 這個參數必須指定正數值。

### <a name="return-value"></a>傳回值

如果已設定刻度，則為非零值;否則為0。

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

設定用來在滑杆中顯示刻度的頻率。

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>參數

*nFreq*<br/>
刻度的頻率。

### <a name="remarks"></a>備註

例如，如果 frequency 設定為2，滑杆範圍內的每個其他增量都會顯示刻度標記。 頻率的預設值為1（也就是，範圍中的每個增量都會與刻度相關聯）。

您必須建立具有 TBS_AUTOTICKS 樣式的控制項，才能使用此函數。 如需詳細資訊，請參閱[CSliderCtrl：： Create](#create)。

##  <a name="settipside"></a>CSliderCtrl：： SetTipSide

放置 [並排] 控制項所使用的工具提示控制項。

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>參數

*nLocation*<br/>
值，表示要顯示工具提示控制項的位置。 如需可能值的清單，請參閱 Win32 message [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)，如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

值，表示工具提示控制項的先前位置。 傳回值等於*n 位置*的其中一個可能值。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message TBM_SETTIPSIDE 的行為，如 Windows SDK 中所述。 使用 TBS_TOOLTIPS 樣式的滑杆控制項會顯示工具提示。 如需滑杆控制項樣式的說明，請參閱 Windows SDK 中的 [敘述][控制項樣式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips

將工具提示控制項指派給滑杆控制項。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>參數

*pWndTip*<br/>
[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件的指標，其中包含要與滑杆控制項搭配使用的工具提示。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)的行為，如 Windows SDK 中所述。 當使用 TBS_TOOLTIPS 樣式建立滑杆控制項時，它會建立一個預設的工具提示控制項，它會顯示在滑杆的旁邊，並顯示滑杆的目前位置。 如需滑杆控制項樣式的說明，請參閱 Windows SDK 中的 [敘述][控制項樣式](/windows/win32/Controls/trackbar-control-styles)。

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl 類別](../../mfc/reference/cprogressctrl-class.md)
