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
ms.openlocfilehash: b89daaae4bb578d328e1468cc29470825e19c670
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502597"
---
# <a name="cscrollview-class"></a>CScrollView 類別

具有滾動功能的[CView](../../mfc/reference/cview-class.md) 。

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
|[CScrollView::CheckScrollBars](#checkscrollbars)|指出捲軸是否有水準和垂直捲動條。|
|[CScrollView::FillOutsideRect](#filloutsiderect)|在捲動區域外填滿視圖的區域。|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|取得裝置單位中目前的滾動位置。|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|取得目前的對應模式、總大小, 以及可滾動視圖的行和頁面大小。 大小是以裝置為單位。|
|[CScrollView::GetScrollPosition](#getscrollposition)|取得邏輯單元中的目前捲軸位置。|
|[CScrollView::GetTotalSize](#gettotalsize)|以邏輯單元取得捲軸的總大小。|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|使視圖的大小決定其框架的大小。|
|[CScrollView::ScrollToPosition](#scrolltoposition)|將此視圖滾動到指定的時間點, 以邏輯單位表示。|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|將捲軸放入縮放至適當模式。|
|[CScrollView::SetScrollSizes](#setscrollsizes)|設定捲軸的對應模式、總大小, 以及水準和垂直捲動數量。|

## <a name="remarks"></a>備註

您可以藉由覆寫訊息對應`CView` [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式, 在衍生自的任何類別中處理標準的滾動。 但`CScrollView`會將下列功能加入其`CView`功能:

- 它會管理視窗和視口大小和對應模式。

- 它會自動滾動以回應捲軸訊息。

- 它會自動滾動, 以回應鍵盤、非滑鼠滾輪或智慧按鈕的訊息。

若要自動滾動以回應鍵盤上的訊息, 請新增 WM_KEYDOWN 訊息, 並測試 VK_DOWN、VK_PREV 和呼叫[SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos)。

您可以藉由覆寫訊息對應的[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成員函式, 自行處理滑鼠滾輪的滾動。 這些成員函式`CScrollView`是針對, 支援[WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel)的建議行為, 即滾輪旋轉訊息。

若要利用自動滾動, 請從`CScrollView`衍生您的 view 類別, 而不是 from。 `CView` 第一次建立視圖時, 如果您想要根據檔案大小來計算可滾動視圖的大小, 請從您的`SetScrollSizes` [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)或[cview:: OnUpdate](../../mfc/reference/cview-class.md#onupdate)的覆寫呼叫成員函式。 (您必須撰寫自己的程式碼來查詢檔的大小。 如需範例, 請參閱「[塗抹」範例](../../overview/visual-cpp-samples.md)。)

`SetScrollSizes`成員函式的呼叫會設定視圖的對應模式、捲軸視圖的總維度, 以及水準和垂直捲動的數量。 所有大小都是以邏輯單位表示。 視圖的邏輯大小通常是從檔中儲存的資料計算而來的, 但在某些情況下, 您可能會想要指定固定大小。 如需這兩種方法的範例, 請參閱[CScrollView:: SetScrollSizes](#setscrollsizes)。

您可以指定在邏輯單元中水準和垂直捲動的數量。 根據預設, 如果使用者按一下捲動方塊外的捲軸軸, `CScrollView`則會滾動「頁面」。 如果使用者按一下捲軸任一結尾的滾動箭號, `CScrollView`則會將「行」捲軸。 根據預設, 頁面是視圖總大小的 1/10;線條是頁面大小的1/10。 藉由在`SetScrollSizes`成員函式中傳遞自訂大小來覆寫這些預設值。 例如, 您可以將水準大小設定為總大小寬度的某個分數, 並將垂直大小設為目前字型中線條的高度。

不是滾動, `CScrollView`可以自動將視圖調整成目前的視窗大小。 在此模式中, 視圖沒有捲軸, 而邏輯視圖則會延展或縮小, 以完全符合視窗的工作區。 若要使用這種調整功能, 請呼叫[CScrollView:: SetScaleToFitSize](#setscaletofitsize)。 (請呼叫`SetScaleToFitSize`或`SetScrollSizes`, 但不能同時呼叫)。

呼叫衍生`OnDraw`視圖類別的成員函式之前, `CScrollView`會自動調整它所傳遞之`CPaintDC` `OnDraw`裝置內容物件的視口原點。

若要調整 [滾動視窗] 的 [視口`CScrollView` ] 原點, 會覆寫[CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 此調整`CPaintDC`會針對`CScrollView`傳遞至`OnDraw`的裝置內容自動進行, 但您必須呼叫`CScrollView::OnPrepareDC`自己, `CClientDC`以取得您所使用的任何其他裝置內容, 例如。 您可以覆`CScrollView::OnPrepareDC`寫以設定畫筆、背景色彩和其他繪圖屬性, 但呼叫基類以進行調整。

捲軸可以顯示在與視圖相對的三個位置, 如下列情況所示:

- 您可以使用 WS_HSCROLL 和 WS_VSCROLL[Windows 樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles), 為視圖設定標準的視窗樣式捲軸。

- 捲軸控制項也可以加入包含此視圖的框架中, 在此情況下, 架構會將 WM_HSCROLL 和 WM_VSCROLL 訊息從框架視窗轉送到目前現用的視圖。

- 此架構也會將 scroll 訊息從`CSplitterWnd`分隔器控制項轉送至目前現用的分割器窗格 (視圖)。 當放在具有共用捲軸的[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)中時`CScrollView` , 物件將會使用共用的, 而不是自行建立。

如需使用`CScrollView`的詳細資訊, 請參閱 MFC 中提供的[檔/視圖架構](../../mfc/document-view-architecture.md)和[衍生視圖類別](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="checkscrollbars"></a>CScrollView:: CheckScrollBars

呼叫這個成員函式, 以判斷捲軸是否有水準和垂直橫條。

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>參數

*bHasHorzBar*<br/>
表示應用程式有水準捲軸。

*bHasVertBar*<br/>
表示應用程式有垂直捲動條。

##  <a name="cscrollview"></a>CScrollView:: CScrollView

建構 `CScrollView` 物件。

```
CScrollView();
```

### <a name="remarks"></a>備註

您必須呼叫`SetScrollSizes`或`SetScaleToFitSize` , 才可以使用捲軸。

##  <a name="filloutsiderect"></a>CScrollView:: FillOutsideRect

呼叫`FillOutsideRect`以填滿顯示在捲動區域外的視圖區域。

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要在其中完成填滿的裝置內容。

*pBrush*<br/>
要用來填滿區域的筆刷。

### <a name="remarks"></a>備註

在`FillOutsideRect`您的捲軸處理`OnEraseBkgnd`函式中使用, 以避免過度的背景重新繪製。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>CScrollView:: GetDeviceScrollPosition

當`GetDeviceScrollPosition`您需要捲軸中捲動方塊的目前水準和垂直位置時, 請呼叫。

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>傳回值

做為`CPoint`物件之捲動方塊的水準和垂直位置 (以裝置單位表示)。

### <a name="remarks"></a>備註

此座標配對會對應至視圖左上角已滾動到的檔位置。 這適用于將滑鼠裝置位置設為捲軸來顯示裝置位置。

`GetDeviceScrollPosition`傳回裝置單位中的值。 如果您想要邏輯單元, `GetScrollPosition`請改用。

##  <a name="getdevicescrollsizes"></a>CScrollView:: GetDeviceScrollSizes

`GetDeviceScrollSizes`取得目前的對應模式、總大小, 以及可滾動視圖的行和頁面大小。

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>參數

*nMapMode*<br/>
傳回此視圖的目前對應模式。 如需可能值的清單, 請`SetScrollSizes`參閱。

*sizeTotal*<br/>
傳回裝置單位中捲軸的目前大小總計。

*sizePage*<br/>
傳回目前的水準和垂直量, 以在每個方向上滾動以回應捲軸軸中的滑鼠按一下。 `cx`成員包含水準金額。 `cy`成員包含垂直量。

*sizeLine*<br/>
傳回目前的水準和垂直量, 以在每個方向上滾動, 以回應捲動箭號中的滑鼠按一下。 `cx`成員包含水準金額。 `cy`成員包含垂直量。

### <a name="remarks"></a>備註

大小是以裝置為單位。 這個成員函式很少被呼叫。

##  <a name="getscrollposition"></a>CScrollView:: GetScrollPosition

當`GetScrollPosition`您需要捲軸中捲動方塊的目前水準和垂直位置時, 請呼叫。

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>傳回值

做為`CPoint`物件之捲動方塊的水準和垂直位置 (以邏輯單位表示)。

### <a name="remarks"></a>備註

此座標配對會對應至視圖左上角已滾動到的檔位置。

`GetScrollPosition`傳回邏輯單元中的值。 如果您想要裝置單位, `GetDeviceScrollPosition`請改用。

##  <a name="gettotalsize"></a>CScrollView:: GetTotalSize

呼叫`GetTotalSize`以取得捲軸的目前水準和垂直大小。

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>傳回值

捲軸的總大小 (以邏輯單位表示)。 水準大小是在傳回值`cx`的成員`CSize`中。 垂直大小在`cy`成員中。

##  <a name="resizeparenttofit"></a>CScrollView:: ResizeParentToFit

呼叫`ResizeParentToFit` , 讓您的視圖大小決定其框架視窗的大小。

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>參數

*bShrinkOnly*<br/>
要執行的調整大小類型。 預設值為 TRUE, 會在適當時縮小框架視窗。 大型視圖或小型框架視窗仍會顯示捲軸。 如果值為 FALSE, 則表示視圖一律會精確地調整框架視窗的大小。 這可能會有點危險, 因為框架視窗可能會變得太大, 而無法放入多重文件介面 (MDI) 框架視窗或螢幕中。

### <a name="remarks"></a>備註

這只建議用於 MDI 子框架視窗中的 views。 在`ResizeParentToFit` `OnInitialUpdate`衍生類別`CScrollView`的處理常式函式中使用。 如需此成員函式的範例, 請參閱[CScrollView:: SetScrollSizes](#setscrollsizes)。

`ResizeParentToFit`假設已設定視圖視窗的大小。 如果呼叫時`ResizeParentToFit`未設定視圖視窗大小, 您會收到判斷提示。 若要確保不會發生這種情況, 請在呼叫`ResizeParentToFit`之前進行下列呼叫:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>CScrollView:: ScrollToPosition

呼叫`ScrollToPosition`以滾動至視圖中的指定點。

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
要在邏輯單元中滾動到的點。 `x`成員必須是正數值 (大於或等於 0, 最多可達視圖的總大小)。 當對應模式為 MM_TEXT 時`y` , 成員也是如此。 在`y` MM_TEXT 以外的對應模式中, 成員是負值。

### <a name="remarks"></a>備註

此視圖將會滾動, 讓這個點位於視窗的左上角。 如果要調整視圖的大小, 就不能呼叫這個成員函式。

##  <a name="setscaletofitsize"></a>CScrollView:: SetScaleToFitSize

當`SetScaleToFitSize`您想要自動將 [視口大小] 調整為目前的視窗大小時, 請呼叫。

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>參數

*sizeTotal*<br/>
要調整視圖的水準和垂直大小。 捲軸的大小會以邏輯單元來測量。 水準大小會包含在`cx`成員中。 垂直大小會包含在`cy`成員中。 `cx` 和`cy`都必須大於或等於0。

### <a name="remarks"></a>備註

使用捲軸時, 可以隨時顯示邏輯視圖的一部分。 但是使用「調整為適當」功能時, 此視圖沒有捲軸, 而邏輯視圖則會延展或縮小, 以完全符合視窗的工作區。 調整視窗大小時, 視圖會根據視窗的大小, 以新的尺規繪製其資料。

您通常會將的呼叫`SetScaleToFitSize`放在您的`OnInitialUpdate`視圖成員函式的覆寫中。 如果您不想要自動調整, 請改`SetScrollSizes`為呼叫成員函式。

`SetScaleToFitSize`可以用來執行「縮放至適當」作業。 用`SetScrollSizes`來重新初始化捲軸。

`SetScaleToFitSize`假設已設定視圖視窗的大小。 如果呼叫時`SetScaleToFitSize`未設定視圖視窗大小, 您會收到判斷提示。 若要確保不會發生這種情況, 請在呼叫`SetScaleToFitSize`之前進行下列呼叫:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>CScrollView:: SetScrollSizes

在`SetScrollSizes`即將更新視圖時呼叫。

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>參數

*nMapMode*<br/>
要為此視圖設定的對應模式。 可能的值包括：

|對應模式|邏輯單元|正 y 軸延伸 。|
|------------------|------------------|---------------------------------|
|MM_TEXT|1圖元|結點|
|MM_HIMETRIC|0.01 mm|轉|
|MM_TWIPS|1/1440 于|轉|
|MM_HIENGLISH|0.001 于|轉|
|MM_LOMETRIC|0.1 mm|轉|
|MM_LOENGLISH|0.01 于|轉|

所有這些模式都是由 Windows 所定義。 不會使用`CScrollView`兩種標準對應模式 MM_ISOTROPIC 和 MM_ANISOTROPIC。 類別庫會提供`SetScaleToFitSize`成員函式, 以將 view 調整成視窗大小。 上表中的第三欄描述座標方向。

*sizeTotal*<br/>
捲軸的總大小。 `cx`成員包含水準範圍。 `cy`成員包含垂直範圍。 大小是以邏輯單位表示。 `cx` 和`cy`都必須大於或等於0。

*sizePage*<br/>
要在每個方向中滾動的水準和垂直量, 以回應捲軸軸中的滑鼠按一下。 `cx`成員包含水準金額。 `cy`成員包含垂直量。

*sizeLine*<br/>
要在每個方向中滾動的水準和垂直量, 以回應滑鼠在捲動箭號中的按一下。 `cx`成員包含水準金額。 `cy`成員包含垂直量。

### <a name="remarks"></a>備註

在`OnUpdate`成員函式的覆寫中呼叫它, 以便在檔一開始顯示或變更大小時, 調整滾動特性。

您通常會藉由呼叫您與衍生檔類別一起提供的檔成員函式 (可能稱為`GetMyDocSize`), 從視圖的相關檔中取得大小資訊。 下列程式碼顯示此方法:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

或者, 您有時可能需要設定固定的大小, 如下列程式碼所示:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

您必須將對應模式設定為 MM_ISOTROPIC 或 MM_ANISOTROPIC 以外的任何 Windows 對應模式。 如果您想要使用不受限制的`SetScaleToFitSize` `SetScrollSizes`對應模式, 請呼叫成員函式, 而不是。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)
