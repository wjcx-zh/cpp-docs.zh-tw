---
title: CScrollView 類別
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: d60082092bd42fbe220eee08953ad5fda0ff0a85
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339596"
---
# <a name="cscrollview-class"></a>CScrollView 類別

A [CView](../../mfc/reference/cview-class.md)具有捲動功能。

## <a name="syntax"></a>語法

```
class CScrollView : public CView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|建構 `CScrollView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|指出捲動檢視是否有水平和垂直捲軸。|
|[CScrollView::FillOutsideRect](#filloutsiderect)|填滿檢視捲動區域外的區域。|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|取得目前捲動位置，以裝置為單位。|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|取得目前的對應模式、 總大小和列和頁面大小的可捲動檢視。 大小是以裝置為單位。|
|[CScrollView::GetScrollPosition](#getscrollposition)|取得目前捲動位置，以邏輯單位表示。|
|[CScrollView::GetTotalSize](#gettotalsize)|取得捲動檢視的大小總計，以邏輯單位表示。|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|導致要決定其框架大小的檢視大小。|
|[CScrollView::ScrollToPosition](#scrolltoposition)|捲動至指定的點，以邏輯單位表示指定的檢視。|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|捲動檢視放來調整規模模式。|
|[CScrollView::SetScrollSizes](#setscrollsizes)|設定捲軸檢視的對應模式，總大小和水平和垂直捲動的數量。|

## <a name="remarks"></a>備註

您可以處理標準的任何類別衍生自捲動自行`CView`藉由覆寫訊息對應[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)並[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式。 但是`CScrollView`新增下列功能，其`CView`功能：

- 它會管理視窗和檢視區大小和對應的模式。

- 它會自動捲動捲軸的訊息回應。

- 它會自動捲動以回應訊息從鍵盤、 非捲動滑鼠或將 intellimouse 滑鼠滾輪。

若要自動捲動，以回應訊息從鍵盤，加入 WM_KEYDOWN 訊息，並測試 VK_DOWN、 VK_PREV 和呼叫[SetScrollPos](/windows/desktop/api/winuser/nf-winuser-setscrollpos)。

您可以處理您自己藉由覆寫訊息對應中捲動滑鼠滾輪[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)並[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成員函式。 因為它們是針對`CScrollView`，這些成員函式支援建議的行為[WM_MOUSEWHEEL](/windows/desktop/inputdev/wm-mousewheel)，滾輪旋轉訊息。

若要利用自動捲動，衍生您的檢視類別，從`CScrollView`而不是從`CView`。 檢視第一次建立時，如果您想要計算的文件中，呼叫大小為基礎的可捲動檢視的大小`SetScrollSizes`成員函式的覆寫[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)。 （您必須撰寫自己的程式碼來查詢文件大小。 如需範例，請參閱[Scribble 範例](../../overview/visual-cpp-samples.md)。)

若要呼叫`SetScrollSizes`成員函式設定檢視的對應模式中，捲動檢視] 和 [水平與垂直捲動的數量總計的維度。 所有大小都都以邏輯單位表示。 檢視的邏輯大小通常會計算從儲存在文件中的資料，但在某些情況下您可能想要指定固定的大小。 如需這兩種方法的範例，請參閱 < [CScrollView::SetScrollSizes](#setscrollsizes)。

您指定的數量，以水平和垂直捲動以邏輯單位表示。 根據預設，如果使用者按一下捲軸桿捲動方塊中，外部`CScrollView`捲動 「 頁面 」。 如果使用者按一下捲軸，任一端的捲動箭號`CScrollView`捲動"line"。 根據預設，頁面是檢視; 的總大小的 1/10線條是頁面大小的 1/10。 覆寫這些預設值，藉由傳遞中的自訂大小`SetScrollSizes`成員函式。 比方說，您可能會設定為一部分的總大小和行高度的垂直大小的寬度的水平大小，以目前的字型。

而不是向下捲動，`CScrollView`可以自動調整目前的視窗大小的檢視。 在此模式中，檢視有沒有捲軸和邏輯的檢視會延伸或縮小以完全符合視窗的工作區。 若要使用此來調整規模功能，請呼叫[CScrollView::SetScaleToFitSize](#setscaletofitsize)。 (呼叫`SetScaleToFitSize`或`SetScrollSizes`，但非兩者。)

再`OnDraw`稱為衍生的檢視類別成員函式，`CScrollView`會自動調整的檢視區原點`CPaintDC`裝置內容物件，就會傳遞至`OnDraw`。

若要調整捲動視窗中，檢視區原點`CScrollView`會覆寫[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 這項調整會自動針對`CPaintDC`裝置內容的`CScrollView`將傳遞給`OnDraw`，但您必須呼叫`CScrollView::OnPrepareDC`自己的任何其他的裝置內容使用，例如`CClientDC`。 您可以覆寫`CScrollView::OnPrepareDC`設定畫筆、 背景色彩和其他繪圖的屬性，但呼叫基底類別進行調整。

捲軸可以出現在相對於檢視中，三個位置中，在下列情況所示：

- 標準的視窗樣式的捲軸可以設定檢視使用 WS_HSCROLL 和 WS_VSCROLL[Windows 樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

- 捲軸控制項也可以加入包含檢視的框架，在此情況下，架構轉送給時傳遞 WM_HSCROLL 和 WM_VSCROLL 訊息框架視窗從目前使用中的檢視。

- 此架構也會轉送捲動訊息從`CSplitterWnd`目前作用中的分隔窗格 （檢視） 來分隔器控制項。 當置於[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)與共用的捲軸`CScrollView`物件使用的共用項目，而不是建立它自己。

如需有關使用`CScrollView`，請參閱 <<c2> [ 文件/檢視架構](../../mfc/document-view-architecture.md)並[衍生檢視類別中可用 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars

呼叫此成員函式，以判斷捲軸檢視是否具有水平及垂直軸。

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>參數

*bHasHorzBar*<br/>
表示應用程式有水平捲軸。

*bHasVertBar*<br/>
表示應用程式有垂直捲軸。

##  <a name="cscrollview"></a>  CScrollView::CScrollView

建構 `CScrollView` 物件。

```
CScrollView();
```

### <a name="remarks"></a>備註

您必須呼叫`SetScrollSizes`或`SetScaleToFitSize`之前捲軸檢視是可使用。

##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect

呼叫`FillOutsideRect`來填滿的區域出現在捲動區域外部的檢視。

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>參數

*pDC*<br/>
填滿為完成的裝置內容。

*pBrush*<br/>
區域是填滿筆刷。

### <a name="remarks"></a>備註

使用`FillOutsideRect`在您的捲軸檢視`OnEraseBkgnd`處理常式函式，以避免過多的背景重新繪製。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition

呼叫`GetDeviceScrollPosition`當您需要的目前水平和垂直位置的捲動方塊中的捲軸。

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>傳回值

水平和垂直位置 （以裝置為單位） 為捲軸方塊`CPoint`物件。

### <a name="remarks"></a>備註

此座標組對應到已捲動檢視的左上角的文件中的位置。 這是適用於位移至捲動檢視裝置位置的滑鼠裝置位置。

`GetDeviceScrollPosition` 以裝置為單位傳回值。 如果您想要邏輯單元，使用`GetScrollPosition`改。

##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes` 取得目前的對應模式、 總大小和列和頁面大小的可捲動檢視。

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>參數

*nMapMode*<br/>
傳回目前的對應模式，此檢視。 如需可能值的清單，請參閱`SetScrollSizes`。

*sizeTotal*<br/>
以裝置為單位傳回捲動檢視的目前總大小。

*sizePage*<br/>
傳回目前的水平和垂直數量，以回應滑鼠的每個方向捲動按一下捲軸。 `cx`成員包含水平量。 `cy`成員包含垂直數量。

*sizeLine*<br/>
傳回目前的水平和垂直數量，以回應滑鼠的每個方向捲動按一下捲動箭號。 `cx`成員包含水平量。 `cy`成員包含垂直數量。

### <a name="remarks"></a>備註

大小是以裝置為單位。 很少會呼叫此成員函式。

##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition

呼叫`GetScrollPosition`當您需要的目前水平和垂直位置的捲動方塊中的捲軸。

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>傳回值

水平和垂直位置 （以邏輯單位表示） 的捲軸方塊`CPoint`物件。

### <a name="remarks"></a>備註

此座標組對應到已捲動檢視的左上角的文件中的位置。

`GetScrollPosition` 傳回值，以邏輯單位表示。 如果您想要裝置單位，使用`GetDeviceScrollPosition`改。

##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize

呼叫`GetTotalSize`來擷取目前的水平和垂直大小的捲動檢視。

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>傳回值

以邏輯單位捲動檢視的大小總計。 水平大小處於`cx`隸屬`CSize`傳回值。 垂直大小處於`cy`成員。

##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit

呼叫`ResizeParentToFit`，讓您檢視的大小決定及其框架視窗的大小。

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>參數

*bShrinkOnly*<br/>
若要執行調整大小的種類。 如果適當的話，預設值為 TRUE，就會縮小框架視窗。 對於大型的檢視表或小型框架視窗，仍然會出現捲軸。 值為 FALSE 會導致一定要完全調整大小的框架視窗的檢視。 這可能會有點危險，因為框架視窗可能變得太大而無法配合多重文件介面 (MDI) 框架視窗或畫面。

### <a name="remarks"></a>備註

這被建議只針對 MDI 子框架視窗中的檢視。 使用`ResizeParentToFit`中`OnInitialUpdate`處理常式函式的您的衍生`CScrollView`類別。 如需這個成員函式的範例，請參閱 < [CScrollView::SetScrollSizes](#setscrollsizes)。

`ResizeParentToFit` 假設已設定的 [檢視] 視窗的大小。 如果檢視視窗大小尚未設定時`ResizeParentToFit`是呼叫，您會取得判斷提示。 為了確保這不會不會，進行下列呼叫之前呼叫`ResizeParentToFit`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition

呼叫`ScrollToPosition`捲動至檢視中的指定點。

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
要捲動，以邏輯單位表示的點。 `x`成員必須是正值 （大於或等於 0，最多總檢視的大小）。 這也適用於`y`MM_TEXT 對應模式時的成員。 `y`成員是負數 MM_TEXT 以外的對應模式。

### <a name="remarks"></a>備註

將捲動檢視，以便此點是在視窗的左上角。 如果此檢視會調整為適合，必須不會呼叫此成員函式。

##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize

呼叫`SetScaleToFitSize`當您想要自動調整檢視區大小為目前的視窗大小。

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>參數

*sizeTotal*<br/>
檢視是可水平和垂直大小。 捲動檢視大小的測量單位的邏輯單元。 中包含的水平大小`cx`成員。 中包含的垂直大小`cy`成員。 兩者`cx`和`cy`必須大於或等於 0。

### <a name="remarks"></a>備註

含捲軸，一部分的邏輯視圖隨時都可能會看到的。 但小數位數來調整功能，檢視有沒有捲軸而邏輯檢視會延伸或縮小以完全符合視窗的工作區。 當調整視窗大小時，檢視會在新視窗的大小為基礎的擴展上繪製其資料。

您通常要放置在呼叫`SetScaleToFitSize`在檢視表的覆寫`OnInitialUpdate`成員函式。 如果您不想自動調整，呼叫`SetScrollSizes`成員函式。

`SetScaleToFitSize` 可用來實作 「 縮小以適合欄寬 」 作業。 使用`SetScrollSizes`重新初始化捲動。

`SetScaleToFitSize` 假設已設定的 [檢視] 視窗的大小。 如果檢視視窗大小尚未設定時`SetScaleToFitSize`是呼叫，您會取得判斷提示。 為了確保這不會不會，進行下列呼叫之前呼叫`SetScaleToFitSize`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes

呼叫`SetScrollSizes`檢視即將更新。

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>參數

*nMapMode*<br/>
若要設定此檢視此對應模式。 可能的值包括：

|對應模式|邏輯單元|Y 軸的正值擴充...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 個像素|向下|
|MM_HIMETRIC|0.01 公釐|向上|
|MM_TWIPS|中的 1/1440|向上|
|MM_HIENGLISH|0.001 英|向上|
|MM_LOMETRIC|0.1 mm|向上|
|MM_LOENGLISH|0.01 英吋|向上|

所有這些模式是由 Windows 進行定義。 不會使用兩種標準的對應模式，MM_ISOTROPIC 和 MM_ANISOTROPIC， `CScrollView`。 類別庫會提供`SetScaleToFitSize`調整成視窗大小檢視的成員函式。 上表中的三個資料行描述的座標的方向。

*sizeTotal*<br/>
捲動檢視的大小總計。 `cx`成員包含水平的範圍。 `cy`成員包含垂直的範圍。 大小是以邏輯單位表示。 兩者`cx`和`cy`必須大於或等於 0。

*sizePage*<br/>
按一下捲軸捲動中每個方向，以回應滑鼠的水平和垂直數量。 `cx`成員包含水平量。 `cy`成員包含垂直數量。

*sizeLine*<br/>
中的捲動箭號，按一下捲動中每個方向，以回應滑鼠的水平和垂直數量。 `cx`成員包含水平量。 `cy`成員包含垂直數量。

### <a name="remarks"></a>備註

在 覆寫中呼叫它`OnUpdate`調整捲動的特性，例如，一開始顯示文件時，或大小變更時的成員函式。

您通常會取得從檢視相關聯的文件大小的資訊，藉由呼叫的文件成員函式，可能是呼叫`GetMyDocSize`，您提供與您在衍生的文件的類別。 下列程式碼顯示這種方法：

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

或者，您有時可能需要設定固定的大小，如下列程式碼所示：

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

您必須設定對應模式以任何 Windows 對應模式，但不包括 MM_ISOTROPIC 或 MM_ANISOTROPIC。 如果您想要使用未受限制的對應模式，呼叫`SetScaleToFitSize`成員函式，而不是`SetScrollSizes`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)
