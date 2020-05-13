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
ms.openlocfilehash: c3600bc5a945c24e91269bc280b4b8e99c54d4c8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750450"
---
# <a name="crecttracker-class"></a>CRectTracker 類別

允許以不同方式顯示、移動和調整專案。

## <a name="syntax"></a>語法

```
class CRectTracker
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRect 追蹤器::CRect 追蹤器](#crecttracker)|建構 `CRectTracker` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Crect 追蹤器::調整已調整](#adjustrect)|調整矩形大小時調用。|
|[CRectTracker::D原](#draw)|渲染矩形。|
|[CRectTracker::D原始追蹤器Rect](#drawtrackerrect)|繪製對象的邊框`CRectTracker`時調用。|
|[CRect 追蹤器::抓碼](#gethandlemask)|呼叫以獲取`CRectTracker`項的調整大小句柄的掩碼。|
|[CRect 追蹤器::取得 Truerect](#gettruerect)|返回矩形的寬度和高度,包括調整控點的大小。|
|[CRect追蹤器::命中測試](#hittest)|返回與物件相關的游標的`CRectTracker`當前位置。|
|[CRect 追蹤器::規範化](#normalizehit)|規範化命中測試代碼。|
|[CrectTracker::打開已更換](#onchangedrect)|在調整大小或移動矩形時調用。|
|[CRect 追蹤器::設定游標](#setcursor)|設置游標,具體取決於其在矩形上的位置。|
|[CRect 追蹤器::追蹤](#track)|允許使用者操作矩形。|
|[CRectTracker::軌道橡膠帶](#trackrubberband)|允許使用者「橡皮筋」的選擇。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRect跟蹤:m_nHandleSize](#m_nhandlesize)|確定調整大小控點的大小。|
|[CRectTracker:m_nStyle](#m_nstyle)|跟蹤器的當前樣式。|
|[CRect跟蹤:m_rect](#m_rect)|矩形的當前位置(以像素為單位)。|
|[CRectTracker::m_sizeMin](#m_sizemin)|確定最小矩形寬度和高度。|

## <a name="remarks"></a>備註

`CRectTracker`沒有基類。

儘管該`CRectTracker`類旨在允許使用者使用圖形介面與 OLE 項進行互動,但其使用並不僅限於啟用 OLE 的應用程式。 它可以在需要此類用戶介面的任何地方使用。

`CRectTracker`邊框可以是實線或虛線。 可以為專案提供陰影邊框或覆蓋與陰影圖案,以指示專案的不同狀態。 您可以在專案的外側或內部邊框上放置八個調整大小的控點。 (有關調整大小句柄的說明,請參閱[GetHandleMask](#gethandlemask)。最後,允許您`CRectTracker`在調整大小期間更改專案的方向。

要使用`CRectTracker`,建`CRectTracker`構 物件並指定初始化的顯示狀態。 然後,可以使用此介面向使用者提供與物件關聯的 OLE 項的當前`CRectTracker`狀態的 可視反饋。

有關使用`CRectTracker`的詳細資訊,請參考文章[追蹤器](../../mfc/trackers.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CRectTracker`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>Crect 追蹤器::調整已調整

使用調整大小句柄調整跟蹤矩形的大小時,由框架調用。

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>參數

*nHandle*<br/>
使用的句柄索引。

*lpRect*<br/>
指向矩形的當前大小的指標。 (矩形的大小由其高度和寬度給出。

### <a name="remarks"></a>備註

此函數的默認行為允許矩形的方向僅在允許反轉時更改`Track``TrackRubberBand`和調用。

覆蓋此函數以控制拖動操作期間跟蹤矩形的調整。 一種方法是在返回之前調整*lpRect*指定的座標。

不直接支援的`CRectTracker`特殊功能(如對齊到網格或保持縱橫比)可以通過重寫此函數來實現。

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRect 追蹤器::CRect 追蹤器

建立及初始化 `CRectTracker` 物件。

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*lpSrcrect*<br/>
矩形物件的座標。

*nStyle*<br/>
指定`CRectTracker`物件的樣式。 支援下列樣式：

- `CRectTracker::solidLine`對矩形邊框使用實線。

- `CRectTracker::dottedLine`對矩形邊框使用虛線。

- `CRectTracker::hatchedBorder`對矩形邊框使用陰影圖案。

- `CRectTracker::resizeInside`調整位於矩形內的控點的大小。

- `CRectTracker::resizeOutside`調整位於矩形外部的控點的大小。

- `CRectTracker::hatchInside`陰影圖案覆蓋整個矩形。

### <a name="remarks"></a>備註

預設建構函數使用`CRectTracker`*lpSrcRect*的值初始化物件,並將其他大小初始化到系統預設值。 如果物件是在沒有參數的創建中創建的,則`m_rect``m_nStyle`未初始化 和資料成員。

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker::D原

調用此函數以繪製矩形的外線和內部區域。

```cpp
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向要繪製的設備上下文的指標。

### <a name="remarks"></a>備註

跟蹤器的樣式確定繪圖的完成方式。 `CRectTracker`有關可用樣式的詳細資訊,請參閱構造函數。

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::D原始追蹤器Rect

當跟蹤器的位置在`Track`或`TrackRubberBand`成員 函數內發生變化時,由框架調用。

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指標指向`RECT`包含要繪製的矩形的 。

*pwndClipto*<br/>
指向用於裁剪矩形的視窗的指標。

*pDC*<br/>
指向要繪製的設備上下文的指標。

*pwnd*<br/>
指向要在其上進行繪圖的視窗。

### <a name="remarks"></a>備註

預設實現對 發出調`CDC::DrawFocusRect`用 ,該調用繪製一個虛線矩形。

重寫此函數以在跟蹤操作期間提供不同的反饋。

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRect 追蹤器::抓碼

框架調用此成員函數以檢索矩形調整大小的控點的蒙版。

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>傳回值

`CRectTracker`項調整大小的控點的掩碼。

### <a name="remarks"></a>備註

調整大小的控點顯示在矩形的側面和角上,並允許使用者控制矩形的形狀和大小。

矩形有 8 個大小調整控點,編號為 0-7。 每個調整大小的句柄都由掩碼中的位表示;該位的值為 2° *n*,*其中 n*是調整大小句柄數。 位 0-3 對應於角調整大小手柄,從左上角順時針移動。 位 4-7 對應於從頂部順時針移動的側調整大小手柄。 底線顯示矩形調整大小控制點與調整大小句柄數和值:

![調整大小控點數字](../../mfc/reference/media/vc35dp1.gif "調整大小控點數字")

的`GetHandleMask`默認實現返回位的掩碼,以便出現調整大小的控點。 如果單個位處於打開,將繪製相應的調整大小控點。

覆蓋此成員函數以隱藏或顯示指示的調整大小控點。

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRect 追蹤器::取得 Truerect

呼叫此函數以檢索矩形的座標。

```cpp
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>參數

*lpTrueRect*<br/>
指向將包含`RECT`物件的設備座標的結構`CRectTracker`的指標。

### <a name="remarks"></a>備註

矩形的尺寸包括位於外部邊框上的任何調整大小的控點的高度和寬度。 返回後 *,lpTrueRect*始終是設備座標中的規範化矩形。

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRect追蹤器::命中測試

呼叫此函數,瞭解使用者是否抓取了調整大小的句柄。

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>參數

*點*<br/>
要測試的點(在設備座標中)。

### <a name="return-value"></a>傳回值

返回的值基於枚舉類型`CRectTracker::TrackerHit`,可以具有以下值之一:

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRect跟蹤:m_nHandleSize

`CRectTracker`調整大小控點的大小(以像素為單位)。

```
int m_nHandleSize;
```

### <a name="remarks"></a>備註

使用預設系統值初始化。

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRect跟蹤:m_rect

矩形在用戶端座標(圖元)中的當前位置。

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin

矩形的最小大小。

```
CSize m_sizeMin;
```

### <a name="remarks"></a>備註

預設值`cx``cy`和 都是 根據邊框寬度的預設系統值計算的。 此數據成員僅由`AdjustRect`成員函數使用。

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker:m_nStyle

矩形的當前樣式。

```
UINT m_nStyle;
```

### <a name="remarks"></a>備註

有關可能樣式的清單,請參閱[CRectTracker::CRectTracker。](#crecttracker)

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRect 追蹤器::規範化

調用此函數以轉換潛在的反轉句柄。

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>參數

*nHandle*<br/>
由用戶選擇的句柄。

### <a name="return-value"></a>傳回值

規範化句柄的索引。

### <a name="remarks"></a>備註

當`CRectTracker::Track``CRectTracker::TrackRubberBand`允許 或在允許反轉的情況下調用時,矩形可以在 x 軸、y 軸或兩者上反轉。 發生這種情況時,`HitTest`將傳回與矩形有關也反轉的控點。 這不適合繪製游標反饋,因為反饋取決於矩形的螢幕位置,而不是要修改的矩形數據結構部分。

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CrectTracker::打開已更換

每當追蹤器矩形在呼叫 期間發生變更時,由框架呼叫`Track`。

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>參數

*rectOld*<br/>
包含`CRectTracker`物件的舊設備座標。

### <a name="remarks"></a>備註

在調用此功能時,已刪除繪製的所有`DrawTrackerRect`反饋。 此函式的預設實作不做任何動作。

如果要在調整矩形大小後執行任何操作,則重寫此函數。

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRect 追蹤器::設定游標

調用此函數以更改游標形狀,而該形狀位於物件`CRectTracker`區域上。

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向當前包含游標的視窗。

*nHitTest*<br/>
上一個命中測試的結果,來自WM_SETCURSOR消息。

### <a name="return-value"></a>傳回值

如果上次命中超過跟蹤器矩形,則非零;否則 0。

### <a name="remarks"></a>備註

從處理WM_SETCURSOR消息的視窗函數內部調用此函數(通常`OnSetCursor`為)。

## <a name="crecttrackertrack"></a><a name="track"></a>CRect 追蹤器::追蹤

呼叫此函數以顯示用於調整矩形大小的用戶介面。

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
包含矩形的視窗物件。

*點*<br/>
當前滑鼠位置相對於工作區的設備座標。

*布勞弗*<br/>
如果為 TRUE,矩形可以沿 x 軸或 y 軸反轉;如果為 TRUE,則矩形可以沿 x 軸或 y 軸反轉。否則 FALSE。

*pwndClipto*<br/>
繪圖操作將剪切到的視窗。 如果 NULL,*則 pWnd*用作裁剪矩形。

### <a name="return-value"></a>傳回值

如果按下 ESC 鍵,跟蹤過程將停止,儲存在跟蹤器中的矩形不會更改,並且返回 0。 如果提交更改,通過移動滑鼠並釋放滑鼠左鍵,新位置和/或大小將記錄在跟蹤器的矩形中,並且返回非零。

### <a name="remarks"></a>備註

這通常是從處理消息的應用程式的函數內部調用的`WM_LBUTTONDOWN`(`OnLButtonDown`通常為)。

此功能將捕獲滑鼠,直到使用者釋放滑鼠左鍵、按下 ESC 鍵或按下滑鼠右鍵。 當使用者移動滑鼠游標時,反饋將通過調用`DrawTrackerRect`和`OnChangedRect`更新。

如果*bAllowInvert*為 TRUE,則可以在 x 軸或 y 軸上反轉跟蹤矩形。

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker::軌道橡膠帶

調用此函數以執行橡皮筋選擇。

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
包含矩形的視窗物件。

*點*<br/>
當前滑鼠位置相對於工作區的設備座標。

*布勞弗*<br/>
如果為 TRUE,矩形可以沿 x 軸或 y 軸反轉;如果為 TRUE,則矩形可以沿 x 軸或 y 軸反轉。否則 FALSE。

### <a name="return-value"></a>傳回值

如果滑鼠已移動且矩形不為空,則非零;否則 0。

### <a name="remarks"></a>備註

它通常從處理WM_LBUTTONDOWN消息的應用程式函數內部調用(通常`OnLButtonDown`為)。

此功能將捕獲滑鼠,直到使用者釋放滑鼠左鍵、按下 ESC 鍵或按下滑鼠右鍵。 當使用者移動滑鼠游標時,反饋將通過調用`DrawTrackerRect`和`OnChangedRect`更新。

跟蹤使用右下角手柄的橡皮帶類型選擇進行。 如果允許反轉,則可以通過向上、向左或向下和向右拖動來調整矩形的大小。

## <a name="see-also"></a>另請參閱

[MFC 樣品追蹤器](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar 類別](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)
