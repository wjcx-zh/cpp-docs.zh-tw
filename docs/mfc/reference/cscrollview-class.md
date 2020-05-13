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
ms.openlocfilehash: 5d0eb163fae2aa5fc63470e1c499311ab1a402a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754416"
---
# <a name="cscrollview-class"></a>CScrollView 類別

具有滾動功能的[CView。](../../mfc/reference/cview-class.md)

## <a name="syntax"></a>語法

```
class CScrollView : public CView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CScroll 檢視:CScroll檢視](#cscrollview)|建構 `CScrollView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CScroll查看::檢查滾動條](#checkscrollbars)|指示滾動檢視是否具有水準和垂直滾動條。|
|[CScroll 檢視::填充外部重新](#filloutsiderect)|填充滾動區域外的視圖區域。|
|[CScroll 檢視:抓取裝置滾動位置](#getdevicescrollposition)|獲取設備單位的當前滾動位置。|
|[CScroll 檢視::抓取裝置](#getdevicescrollsizes)|獲取可滾動檢視的當前映射模式、總大小以及行和頁面大小。 大小以設備單位為單位。|
|[CScroll 檢視:抓取捲動位置](#getscrollposition)|獲取邏輯單位的當前滾動位置。|
|[CScroll 檢視:抓取總計大小](#gettotalsize)|獲取邏輯單位滾動視圖的總大小。|
|[CScrollView:調整父級](#resizeparenttofit)|使視圖的大小決定其幀的大小。|
|[CScroll查看::滾動位置](#scrolltoposition)|將視圖滾動到給定點,以邏輯單位指定。|
|[CScroll 檢視::設定比例調整大小](#setscaletofitsize)|將滾動視圖置於縮放到擬合模式。|
|[CScroll 檢視::設定捲動大小](#setscrollsizes)|設置滾動檢視的映射模式、總大小以及水平和垂直滾動量。|

## <a name="remarks"></a>備註

您可以通過重寫消息映射的[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和`CView`[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函數來處理從派生的任何類中的標準滾動。 但是`CScrollView`,將以下功能添加到`CView`其 功能中:

- 它管理視窗和視口大小以及映射模式。

- 它會自動滾動以回應滾動條消息。

- 它會自動滾動以回應來自鍵盤、非滾動滑鼠或 IntelliMouse 滾輪的消息。

要自動捲動以回應來自鍵盤的消息,請添加WM_KEYDOWN訊息,並測試VK_DOWN、VK_PREV和呼叫[SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos)。

您可以通過重寫消息映射的[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[On 註冊滑鼠滾輪](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成員功能來處理滑鼠滾輪。 由於它們的作用`CScrollView`,這些成員函數支援[WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel)的建議行為,即車輪旋轉消息。

要利用自動滾動,請從`CScrollView`派生視圖類,而不是`CView`從 派生。 首次創建檢視時,如果要根據文檔的大小計算可滾動檢視的大小,請從`SetScrollSizes`[CView::上初始更新](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::onUpdate](../../mfc/reference/cview-class.md#onupdate)的重寫調用成員函數。 (您必須編寫自己的代碼來查詢文件的大小。 例如,請參閱[塗鴉範例](../../overview/visual-cpp-samples.md)。

對成員函數的`SetScrollSizes`調用設置檢視的映射模式、滾動檢視的總尺寸以及水準和垂直滾動的量。 所有大小均以邏輯單位為單位。 檢視的邏輯大小通常根據儲存在文件中的數據計算,但在某些情況下,您可能需要指定固定大小。 有關這兩種方法的範例,請參閱[CScrollView::設定 ScrollSizes](#setscrollsizes)。

指定以邏輯單位水準和垂直滾動的金額。 默認情況下,如果用戶單擊滾動框外的滾動條軸,則`CScrollView`滾動"頁面"。 如果用戶按下捲軸捲軸兩端的滾動箭頭`CScrollView`, 則滾動「行」。 默認情況下,頁面是視圖總大小的 1/10;如果頁面大小,則為 1/10。一行是頁面大小的 1/10。 通過在成員函數中傳遞自定義大小來`SetScrollSizes`覆蓋這些預設值。 例如,您可以將水準大小設置為總大小寬度的一部分,將垂直大小設置為當前字體中行的高度。

可以自動將檢視縮放`CScrollView`到當前視窗大小,而不是滾動。 在此模式下,視圖沒有滾動條,並且邏輯視圖將拉伸或收縮,以完全適合視窗的工作區。 要使用此「縮放到擬合」功能,請致電[CScrollView::設定ScaletoFitSize](#setscaletofitsize)。 (呼叫任`SetScaleToFitSize``SetScrollSizes`一 或 ,但不能同時呼叫兩者。

在`OnDraw`呼叫派生檢視類的成員函數之前,`CScrollView`自動調整它傳遞`CPaintDC``OnDraw`給的裝置上下文物件的視點源。

要調整捲動視窗的視口原點,`CScrollView`請覆[寫 CView::onPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 此調整對於`CPaintDC`傳遞`CScrollView``OnDraw`給的裝置中文字是自動的,但您必須針對您`CScrollView::OnPrepareDC`使用的任何其他裝置上下文(`CClientDC`如 。 您可以重寫`CScrollView::OnPrepareDC`以設置筆、背景色和其他繪圖屬性,但調用基類執行縮放。

滾動條可以相對於視圖出現在三個位置,如以下情況所示:

- 可以使用 WS_HSCROLL 和 WS_VSCROLL[Windows 樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)為檢視設置標準視窗樣式滾動條。

- 滾動條控件也可以添加到包含檢視的幀中,在這種情況下,框架會將WM_HSCROLL轉發,並將消息 WM_VSCROLL從框架窗口轉發到當前活動視圖。

- 框架還將滾動消息從`CSplitterWnd`拆分器控制件轉發到當前活動的拆分器窗格(視圖)。 當放置在帶有共用滾動條的[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)中`CScrollView`,物件將使用共用滾動條,而不是創建自己的滾動條。

有關使用`CScrollView`的詳細資訊,請參閱[MFC 中可用的文件/ 檢視體系結構](../../mfc/document-view-architecture.md)與[衍生檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScroll查看::檢查滾動條

調用此成員函數以確定滾動檢視是否具有水準和垂直條。

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>參數

*b哈斯霍茲酒吧*<br/>
指示應用程式具有水準滾動條。

*bHasvertbar*<br/>
指示應用程式具有垂直滾動條。

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScroll 檢視:CScroll檢視

建構 `CScrollView` 物件。

```
CScrollView();
```

### <a name="remarks"></a>備註

您必須在滾動`SetScrollSizes`檢視可用`SetScaleToFitSize`之前呼叫。

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScroll 檢視::填充外部重新

調用`FillOutsideRect`以填充顯示在滾動區域外部的檢視區域。

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要完成填充的設備上下文。

*pBrush*<br/>
要填充區域的刷子。

### <a name="remarks"></a>備註

在`FillOutsideRect`滾動檢視的`OnEraseBkgnd`處理程式函數中使用,以防止過度重新繪製背景。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScroll 檢視:抓取裝置滾動位置

當您`GetDeviceScrollPosition`需要滾動條中滾動框的當前水準和垂直位置時,請呼叫。

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>傳回值

滾動框作為`CPoint`物件的水準和垂直位置(以設備單位為單位)。

### <a name="remarks"></a>備註

此座標對對應於文檔中已滾動檢視左上角的位置。 這對於抵消滑鼠設備位置以滾動查看設備位置非常有用。

`GetDeviceScrollPosition`返回以設備單位為單位的值。 如果需要邏輯單位,請使用`GetScrollPosition`。

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScroll 檢視::抓取裝置

`GetDeviceScrollSizes`獲取可滾動檢視的當前映射模式、總大小以及行和頁面大小。

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>參數

*nMapMode*<br/>
返回此檢視的當前映射模式。 如需可能值的清單，請參閱 `SetScrollSizes`。

*大小總計*<br/>
以設備單位返回滾動視圖的當前總大小。

*大小頁*<br/>
返回當前水準和垂直量,以響應滾動條軸中的滑鼠按一下,在每個方向上滾動。 成員`cx`包含水準量。 成員`cy`包含垂直量。

*大小線*<br/>
返回當前水準和垂直量,以響應滾動箭頭中的滑鼠按一下,在每個方向上滾動。 成員`cx`包含水準量。 成員`cy`包含垂直量。

### <a name="remarks"></a>備註

大小以設備單位為單位。 很少調用此成員函數。

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScroll 檢視:抓取捲動位置

當您`GetScrollPosition`需要滾動條中滾動框的當前水準和垂直位置時,請呼叫。

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>傳回值

滾動框作為`CPoint`物件的水準和垂直位置(以邏輯單位表示)。

### <a name="remarks"></a>備註

此座標對對應於文檔中已滾動檢視左上角的位置。

`GetScrollPosition`返回邏輯單位中的值。 如果需要裝置儲存單元,請`GetDeviceScrollPosition`使用 。

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScroll 檢視:抓取總計大小

調用`GetTotalSize`以檢索滾動檢視的當前水準和垂直大小。

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>傳回值

以邏輯單位表示滾動視圖的總大小。 水準大小位於返回值`cx`的成員中。 `CSize` 垂直大小位於成員中`cy`。

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView:調整父級

呼叫`ResizeParentToFit`以讓檢視的大小決定其框架視窗的大小。

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>參數

*b收縮僅*<br/>
要執行的調整大小。 默認值 TRUE 會收縮幀視窗(如果適用)。 對於大型檢視或小框架視窗,仍會出現滾動條。 FALSE 的值會導致視圖始終精確調整幀視窗的大小。 這可能有點危險,因為框架視窗可能變得太大,無法容納多個文檔介面 (MDI) 框架視窗或螢幕。

### <a name="remarks"></a>備註

這僅適用於 MDI 子框架視窗中的檢視。 `ResizeParentToFit`在`OnInitialUpdate`派`CScrollView`生類的處理程式函數中使用。 有關此成員函數的範例,請參閱[CScrollView::設定 ScrollSizes](#setscrollsizes)。

`ResizeParentToFit`假定檢視視窗的大小已設置。 如果在呼叫時`ResizeParentToFit`尚未設定檢視視窗大小,您將獲得斷言。 為確保不會發生這種情況,請先呼叫`ResizeParentToFit`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScroll查看::滾動位置

調用`ScrollToPosition`以滾動到視圖中的給定點。

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>參數

*pt*<br/>
以邏輯單位滾動到的點。 成員`x`必須為正值(大於或等於 0,最多為視圖的總大小)。 當映射模式MM_TEXT時,`y`成員也是如此。 在`y`映射模式(MM_TEXT之外,成員為負值。

### <a name="remarks"></a>備註

視圖將被滾動,以便此點位於視窗的左上角。 如果視圖已縮放為適合,則不得調用此成員函數。

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScroll 檢視::設定比例調整大小

如果要`SetScaleToFitSize`自動將視口大小縮放到當前視窗大小,請進行調用。

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>參數

*大小總計*<br/>
要縮放檢視的水準和垂直大小。 滾動檢視的大小以邏輯單位度量。 水平大小包含在成員中`cx`。 垂直大小包含在成員中`cy`。 `cx`和`cy`必須大於或等於 0。

### <a name="remarks"></a>備註

使用滾動條時,邏輯視圖的一部分可能隨時可見。 但是,使用"縮放到擬合"功能,視圖沒有滾動條,並且邏輯視圖會拉伸或收縮,以完全適合視窗的工作區。 調整視窗大小時,檢視將根據視窗的大小以新比例繪製其數據。

通常,您將在覆蓋檢視`SetScaleToFitSize``OnInitialUpdate`的成員函數時將調用置於該函數的覆蓋位置。 如果不希望自動縮放,`SetScrollSizes`請改為呼叫成員函數。

`SetScaleToFitSize`可用於實現「縮放到適合」 操作。 用於`SetScrollSizes`重新初始化滾動。

`SetScaleToFitSize`假定檢視視窗的大小已設置。 如果在呼叫時`SetScaleToFitSize`尚未設定檢視視窗大小,您將獲得斷言。 為確保不會發生這種情況,請先呼叫`SetScaleToFitSize`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScroll 檢視::設定捲動大小

當`SetScrollSizes`視圖即將更新時調用。

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>參數

*nMapMode*<br/>
要為此檢視設置的映射模式。 可能的值包括：

|對應模式|邏輯單元|正 y 軸 延伸...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 佹萺慒|向下|
|MM_HIMETRIC|0.01 mm|向上|
|MM_TWIPS|1/1440 in|向上|
|MM_HIENGLISH|0.001 in|向上|
|MM_LOMETRIC|0.1 mm|向上|
|MM_LOENGLISH|0.01 in|向上|

所有這些模式都由 Windows 定義。 MM_ISOTROPIC與MM_ANISOTROPIC兩種標準對應模式不用於`CScrollView`。 類庫提供成員函數`SetScaleToFitSize`,用於將檢視縮放到視窗大小。 上表第三列描述了座標方向。

*大小總計*<br/>
滾動檢視的總大小。 成員`cx`包含水準範圍。 成員`cy`包含垂直範圍。 大小以邏輯單位表示。 `cx`和`cy`必須大於或等於 0。

*大小頁*<br/>
水準和垂直量要在每個方向滾動,以響應滾動條軸中的滑鼠按一下。 成員`cx`包含水準量。 成員`cy`包含垂直量。

*大小線*<br/>
水準和垂直量要在每個方向滾動,以響應滾動箭頭中的滑鼠按一下。 成員`cx`包含水準量。 成員`cy`包含垂直量。

### <a name="remarks"></a>備註

在成員函數的`OnUpdate`重寫中調用它,以在最初顯示文檔或更改大小時調整滾動特徵。

您通常會透過調用文件成員函數(可能稱為`GetMyDocSize`,與派生文件類一起提供)從檢視的關聯文檔中獲取大小資訊。 以下代碼顯示了此方法:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

或者,有時您可能需要設定固定大小,如以下代碼:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

您必須將映射模式設置為除MM_ISOTROPIC或MM_ANISOTROPIC以外的任何 Windows 映射模式。 如果要使用無限制映射模式,`SetScaleToFitSize`請呼叫成員函數`SetScrollSizes`而不是 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)
