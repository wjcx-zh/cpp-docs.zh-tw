---
title: CRectTracker 類別
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 1834c378246835314002cdf05fe9a294b609c4e4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259577"
---
# <a name="crecttracker-class"></a>CRectTracker 類別

可讓一個項目來顯示、 移動和調整大小不同的方式。

## <a name="syntax"></a>語法

```
class CRectTracker
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|建構 `CRectTracker` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|將矩形調整大小時呼叫。|
|[CRectTracker::Draw](#draw)|呈現的矩形。|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|繪製的框線時呼叫`CRectTracker`物件。|
|[CRectTracker::GetHandleMask](#gethandlemask)|呼叫以取得的遮罩`CRectTracker`項目的調整大小控點。|
|[CRectTracker::GetTrueRect](#gettruerect)|傳回矩形，包括調整大小控點的寬度和高度。|
|[CRectTracker::HitTest](#hittest)|傳回目前位置相關的資料指標`CRectTracker`物件。|
|[CRectTracker::NormalizeHit](#normalizehit)|正規化的點擊測試程式碼。|
|[CRectTracker::OnChangedRect](#onchangedrect)|已調整大小或移動矩形時呼叫。|
|[CRectTracker::SetCursor](#setcursor)|設定資料指標，根據透過矩形位置。|
|[CRectTracker::Track](#track)|可讓使用者管理的矩形。|
|[CRectTracker::TrackRubberBand](#trackrubberband)|可讓使用者 「 拖放矩形 」 選取項目。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|決定調整大小控點大小。|
|[CRectTracker::m_nStyle](#m_nstyle)|目前追蹤程式 style(s)。|
|[CRectTracker::m_rect](#m_rect)|目前位置 （以像素為單位） 的矩形。|
|[CRectTracker::m_sizeMin](#m_sizemin)|判斷最小的矩形寬度和高度。|

## <a name="remarks"></a>備註

`CRectTracker` 沒有基底類別。

雖然`CRectTracker`類別設計來讓使用者使用圖形化介面的 OLE 項目互動，其使用不限於 OLE 功能的應用程式。 它可以用於需要這類使用者介面的地方。

`CRectTracker` 框線可以是純色或點線。 項目可以出現陰影框線，或與規劃的模式，可表示的項目不同的狀態。 您可以將八個調整大小控點放在外部或內部項目的框線。 (如需調整大小控點的說明，請參閱 < [GetHandleMask](#gethandlemask)。)最後，`CRectTracker`可讓您變更項目期間調整大小的方向。

若要使用`CRectTracker`，建構`CRectTracker`物件，並指定初始化的顯示狀態。 您接著可以使用此介面使用者視覺化回饋提供 OLE 項目相關聯的目前狀態`CRectTracker`物件。

如需有關使用`CRectTracker`，請參閱文章[追蹤器](../../mfc/trackers.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CRectTracker`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="adjustrect"></a>  CRectTracker::AdjustRect

追蹤矩形是使用調整大小控點調整大小時，由架構呼叫。

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>參數

*nHandle*<br/>
使用控制代碼的索引。

*lpRect*<br/>
目前大小的矩形的指標。 （矩形的大小是由其高度和寬度所提供）。

### <a name="remarks"></a>備註

此函式的預設行為可讓矩形的方向變更時，才`Track`和`TrackRubberBand`反轉允許來呼叫。

此函式可控制追蹤矩形的調整，在拖曳作業期間會覆寫。 其中一個方法是調整所指定的座標*lpRect*傳回之前。

並不直接支援的特殊功能`CRectTracker`，例如貼齊至格線或保留外觀比例，可以藉由覆寫這個函式實作。

##  <a name="crecttracker"></a>  CRectTracker::CRectTracker

建立並初始化`CRectTracker`物件。

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*lpSrcRect*<br/>
矩形物件的座標。

*nStyle*<br/>
指定的樣式`CRectTracker`物件。 支援下列樣式：

- `CRectTracker::solidLine` 使用一條實線矩形框線。

- `CRectTracker::dottedLine` 使用一條虛線矩形框線。

- `CRectTracker::hatchedBorder` 使用矩形框線影線的圖樣。

- `CRectTracker::resizeInside` 調整大小控點位於矩形內部。

- `CRectTracker::resizeOutside` 調整大小控點位於矩形外。

- `CRectTracker::hatchInside` 影線圖樣涵蓋整個矩形。

### <a name="remarks"></a>備註

預設建構函式初始化`CRectTracker`物件的值從*lpSrcRect*並初始化其他大小，以系統預設值。 如果使用任何參數，建立物件`m_rect`和`m_nStyle`資料成員未初始化。

##  <a name="draw"></a>  CRectTracker::Draw

呼叫此函式可繪製的矩形外部的線條和內部的區域。

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>參數

*pDC*<br/>
在其上繪製的裝置內容指標。

### <a name="remarks"></a>備註

追蹤器的樣式會判斷如何進行繪圖。 請參閱的建構函式`CRectTracker`如需有關可用樣式。

##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect

每當變更追蹤器的位置時，由架構呼叫內時`Track`或`TrackRubberBand`成員函式。

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指標`RECT`，其中包含要繪製的矩形。

*pWndClipTo*<br/>
用於裁剪矩形的視窗指標。

*pDC*<br/>
在其上繪製的裝置內容指標。

*pWnd*<br/>
視窗繪圖就會發生在其的指標。

### <a name="remarks"></a>備註

預設實作會呼叫`CDC::DrawFocusRect`，其會繪製虛線的矩形。

覆寫這個函式來追蹤作業期間提供不同的意見反應。

##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask

架構會呼叫此成員函式，來擷取遮罩的矩形的調整大小控點。

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>傳回值

遮罩`CRectTracker`項目的調整大小控點。

### <a name="remarks"></a>備註

調整大小控點和矩形邊角上會出現，並允許使用者控制的形狀和大小的矩形。

矩形有 8 編號 0 到 7 的調整大小控點。 每個調整大小控點被以位元遮罩; 中該位元的值為 2 ^ *n*，其中*n*是調整大小控點數目。 位元 0-3 會對應至角調整大小控點，從左上方移動順時針旋轉。 位元的一端對應的 4-7 調整大小控點，依順時針方向移動從頂端開始。 下圖顯示矩形的大小調整控點和其對應調整大小控點數量和值：

![調整大小控點數字](../../mfc/reference/media/vc35dp1.gif "調整大小控點數量")

預設實作`GetHandleMask`傳回位元遮罩，以便調整大小控點出現。 如果單一的位元為開啟，就會繪製對應的大小調整控點。

覆寫此成員函式，來隱藏或顯示指定的調整大小控點。

##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect

呼叫此函式可擷取矩形的座標。

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>參數

*lpTrueRect*<br/>
指標`RECT`結構，它會包含裝置座標`CRectTracker`物件。

### <a name="remarks"></a>備註

矩形的維度包含的任何調整大小控點位於其外部框線的寬度與高度。 在傳回時， *lpTrueRect*永遠是以裝置座標表示的標準化的矩形。

##  <a name="hittest"></a>  CRectTracker::HitTest

呼叫此函式可找出使用者已拿起調整大小控點。

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>參數

*point*<br/>
若要測試的裝置座標點。

### <a name="return-value"></a>傳回值

傳回的值為基礎的列舉型別`CRectTracker::TrackerHit`，而且可以有下列值之一：

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6

- `CRectTracker::hitLeft` 7

- `CRectTracker::hitMiddle` 8

##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize

大小，單位為像素的`CRectTracker`調整大小控點。

```
int m_nHandleSize;
```

### <a name="remarks"></a>備註

初始化使用預設系統值。

##  <a name="m_rect"></a>  CRectTracker::m_rect

目前的位置矩形在工作區座標 （像素為單位）。

```
CRect m_rect;
```

##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin

矩形的大小下限。

```
CSize m_sizeMin;
```

### <a name="remarks"></a>備註

這兩個預設值，`cx`和`cy`，計算從預設系統的框線寬度的值。 此資料成員僅供`AdjustRect`成員函式。

##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle

目前矩形的樣式。

```
UINT m_nStyle;
```

### <a name="remarks"></a>備註

請參閱[CRectTracker::CRectTracker](#crecttracker)可能樣式的清單。

##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit

呼叫此函式來轉換可能逆轉控制代碼。

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>參數

*nHandle*<br/>
使用者所選取的控制代碼。

### <a name="return-value"></a>傳回值

標準化的控制代碼的索引。

### <a name="remarks"></a>備註

當`CRectTracker::Track`或`CRectTracker::TrackRubberBand`稱為使用反轉允許，就可以在 x 軸、 y 軸，或兩者皆要反轉的矩形。 當發生這種情況時，`HitTest`會傳回也已反轉相對於該矩形的控制代碼。 這是矩形的不適用於繪圖的資料指標意見反應，因為意見反應取決於畫面的位置，不會修改矩形資料結構的一部分。

##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect

每當呼叫期間變更 tracker 矩形時，由架構呼叫`Track`。

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>參數

*rectOld*<br/>
包含舊裝置座標`CRectTracker`物件。

### <a name="remarks"></a>備註

在此函式呼叫時，所有意見反應，以繪製`DrawTrackerRect`已移除。 此函式的預設實作不做任何動作。

當您想要在矩形已調整大小後執行任何動作，請覆寫這個函式。

##  <a name="setcursor"></a>  CRectTracker::SetCursor

呼叫此函式來變更指標形狀上時`CRectTracker`物件的區域。

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向目前包含游標的視窗。

*nHitTest*<br/>
先前的點擊測試，從 WM_SETCURSOR 訊息的結果。

### <a name="return-value"></a>傳回值

非零值，如果前一個點擊是經由追蹤器矩形;否則為 0。

### <a name="remarks"></a>備註

呼叫此函式從處理 WM_SETCURSOR 訊息視窗的函式內 (通常`OnSetCursor`)。

##  <a name="track"></a>  CRectTracker::Track

呼叫此函式可顯示使用者介面，調整大小的矩形。

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含矩形的視窗物件。

*point*<br/>
裝置目前的滑鼠位置，相對於用戶端區域的座標。

*bAllowInvert*<br/>
如果為 TRUE，矩形可以反轉沿著 x 軸或 y 軸;否則為 FALSE。

*pWndClipTo*<br/>
繪製作業會裁剪到視窗。 如果是 NULL， *pWnd*做裁剪方框。

### <a name="return-value"></a>傳回值

如果按下 ESC 鍵時，就會暫止追蹤程序、 儲存在追蹤程式中的矩形不會改變，和會傳回 0。 如果認可變更之後，藉由移動滑鼠，並釋放滑鼠左鍵，新的位置和/或大小會記錄在追蹤器的矩形，並傳回非零值。

### <a name="remarks"></a>備註

這通常稱為從您的應用程式會處理函式內`WM_LBUTTONDOWN`訊息 (通常`OnLButtonDown`)。

此函式會捕捉滑鼠，直到使用者放開滑鼠左的按鈕、 按下 ESC 鍵，或按下滑鼠右按鈕。 當使用者移動滑鼠游標，藉由呼叫更新意見反應`DrawTrackerRect`和`OnChangedRect`。

如果*bAllowInvert*為 TRUE 時，追蹤矩形可以反轉 x 軸或 y 軸上。

##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand

呼叫此函式來進行拖放矩形選取範圍。

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含矩形的視窗物件。

*point*<br/>
裝置目前的滑鼠位置，相對於用戶端區域的座標。

*bAllowInvert*<br/>
如果為 TRUE，矩形可以反轉沿著 x 軸或 y 軸;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果滑鼠已移動，而且該矩形不是空的則非零值否則為 0。

### <a name="remarks"></a>備註

它通常稱為從函式會處理 WM_LBUTTONDOWN 訊息的應用程式內 (通常`OnLButtonDown`)。

此函式會捕捉滑鼠，直到使用者放開滑鼠左的按鈕、 按下 ESC 鍵，或按下滑鼠右按鈕。 當使用者移動滑鼠游標，藉由呼叫更新意見反應`DrawTrackerRect`和`OnChangedRect`。

追蹤會使用從右下方的控制代碼的拖放頻外類型選取項目。 如果允許反轉，矩形可以是向上和向左或向下和向右拖曳調整大小。

## <a name="see-also"></a>另請參閱

[MFC 範例追蹤器](../../visual-cpp-samples.md)<br/>
[MFC 範例 DRAWCLI](../../visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar 類別](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)
