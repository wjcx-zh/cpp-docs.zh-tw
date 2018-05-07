---
title: CScrollView 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82ffdb26c5766a0ff7cbada511c9bc9c82ebfd93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|[CScrollView::FillOutsideRect](#filloutsiderect)|填滿區域的捲動區域的外面的檢視。|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|取得目前捲動位置以裝置為單位。|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|取得目前的對應模式、 的總大小，以及可捲動檢視的列和頁面大小。 大小是以裝置為單位。|  
|[CScrollView::GetScrollPosition](#getscrollposition)|取得目前捲動位置以邏輯單位表示。|  
|[CScrollView::GetTotalSize](#gettotalsize)|取得捲動檢視的大小總計，以邏輯單位表示。|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|導致要聽寫的及其框架大小之檢視的大小。|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|捲動至指定的時間點，以邏輯單位表示指定的檢視。|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|置於標尺來調整模式的捲動檢視。|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|設定捲動檢視的對應模式、 總大小，以及水平和垂直捲動金額。|  
  
## <a name="remarks"></a>備註  
 您可以處理標準任何類別衍生自中捲動自行`CView`藉由覆寫訊息對應[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式。 但是`CScrollView`新增下列功能，其`CView`功能：  
  
-   它會管理視窗和檢視區大小和對應的模式。  
  
-   它會自動捲動捲軸訊息回應。  
  
-   它會自動捲動以回應訊息從鍵盤、 非捲動滑鼠或將 intellimouse 滑鼠滾輪。  
  
 若要自動捲動，以從鍵盤回應訊息，新增 WM_KEYDOWN 訊息，並測試 VK_DOWN、 VK_PREV 和呼叫[SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 您可以處理滑鼠滾輪捲動自行藉由覆寫訊息對應[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成員函式。 對`CScrollView`，這些成員函式支援建議的行為，如[WM_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617)，滾輪旋轉訊息。  
  
 若要利用自動捲動，衍生檢視類別從`CScrollView`而不是從`CView`。 檢視第一次建立時，如果您想要計算的大小為基礎的文件，呼叫大小可捲動檢視`SetScrollSizes`成員函式，從您的覆寫中的其中一個[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)。 （您必須撰寫自己的程式碼來查詢文件的大小。 如需範例，請參閱[Scribble 範例](../../visual-cpp-samples.md)。)  
  
 若要呼叫`SetScrollSizes`成員函式會將檢視的對應模式中，捲動檢視] 和 [水平與垂直捲動的數量總計的維度。 所有的大小是以邏輯單位表示。 檢視的邏輯大小通常計算資料儲存在文件，但在某些情況下您可能想要指定固定的大小。 如需這兩種方法的範例，請參閱[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 您指定的數量，以水平和垂直捲動以邏輯單位表示。 根據預設，如果使用者按一下捲軸列軸的捲動方塊中，外部`CScrollView`捲動 「 頁面 」。 如果使用者按一下捲軸，任一端的捲動箭號`CScrollView`捲動"line"。 根據預設，頁面大小是大小的檢視的 1/10; 總計線條是頁面大小的 1/10。 傳遞自訂的大小，以覆寫這些預設值`SetScrollSizes`成員函式。 比方說，您可能設定為一部分的總大小，以及要行高度的垂直大小的寬度的水平大小，以目前的字型。  
  
 而不是向下捲動，`CScrollView`可以自動調整為目前的視窗大小的檢視。 在此模式中，檢視有沒有捲軸，延伸或壓縮到完全符合視窗的工作區的邏輯檢視。 若要使用此小數位數來調整功能，請呼叫[CScrollView::SetScaleToFitSize](#setscaletofitsize)。 (呼叫`SetScaleToFitSize`或`SetScrollSizes`，但非兩者。)  
  
 之前`OnDraw`稱為衍生的檢視類別成員函式，`CScrollView`自動調整檢視區原點`CPaintDC`裝置內容物件，就會傳遞至`OnDraw`。  
  
 若要調整檢視區原點捲動視窗中，請`CScrollView`會覆寫[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 這項調整會自動針對`CPaintDC`裝置內容的`CScrollView`給`OnDraw`，但是您必須呼叫**CScrollView::OnPrepareDC**自己的任何其他裝置內容中使用，例如`CClientDC`. 您可以覆寫**CScrollView::OnPrepareDC**設定畫筆、 背景色彩，以及其他的繪圖屬性，但呼叫基底類別進行調整。  
  
 捲軸可以出現在相對於檢視中，三個位置，如下所示：  
  
-   可以設定標準的視窗樣式捲軸檢視使用**WS_HSCROLL**和**WS_VSCROLL**[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
-   捲軸控制項也可以加入至框架包含檢視中，將案例架構轉送`WM_HSCROLL`和`WM_VSCROLL`訊息從框架視窗至目前使用的檢視。  
  
-   架構也會轉送捲動訊息從`CSplitterWnd`目前作用中的分隔窗格 （檢視） 來分隔器控制項。 當放置在[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)與共用的捲軸，`CScrollView`物件使用的共用項目，而不是建立它自己。  
  
 如需有關使用`CScrollView`，請參閱[文件/檢視架構](../../mfc/document-view-architecture.md)和[衍生檢視類別中可用 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars  
 呼叫此成員函式可判斷捲動檢視是否具有水平及垂直軸。  
  
```  
void CheckScrollBars(
    BOOL& bHasHorzBar,  
    BOOL& bHasVertBar) const;  
```  
  
### <a name="parameters"></a>參數  
 *bHasHorzBar*  
 指出應用程式有水平捲軸。  
  
 *bHasVertBar*  
 指出應用程式有垂直捲軸。  
  
##  <a name="cscrollview"></a>  CScrollView::CScrollView  
 建構 `CScrollView` 物件。  
  
```  
CScrollView();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫`SetScrollSizes`或`SetScaleToFitSize`之前捲軸檢視可供使用。  
  
##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect  
 呼叫`FillOutsideRect`填滿區域的捲動區域外部顯示的檢視。  
  
```  
void FillOutsideRect(
    CDC* pDC,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 在其中填入執行的裝置內容。  
  
 `pBrush`  
 筆刷的區域是要填滿。  
  
### <a name="remarks"></a>備註  
 使用`FillOutsideRect`中捲動檢視的`OnEraseBkgnd`處理常式函式，以避免過多的背景重新繪製。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition  
 呼叫`GetDeviceScrollPosition`何時該添目前水平和垂直位置的捲軸方塊中的捲軸。  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 水平和垂直位置 （以裝置為單位） 的捲動方塊`CPoint`物件。  
  
### <a name="remarks"></a>備註  
 此座標組對應的捲動檢視的左上角的文件中的位置。 這是適用於移轉至捲動檢視裝置位置的滑鼠裝置位置。  
  
 `GetDeviceScrollPosition` 以裝置為單位傳回值。 如果您想邏輯單元，請使用`GetScrollPosition`改為。  
  
##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes  
 `GetDeviceScrollSizes` 取得目前的對應模式、 的總大小，以及可捲動檢視的列和頁面大小。  
  
```  
void GetDeviceScrollSizes(
    int& nMapMode,  
    SIZE& sizeTotal,  
    SIZE& sizePage,  
    SIZE& sizeLine) const;  
```  
  
### <a name="parameters"></a>參數  
 `nMapMode`  
 傳回目前的對應模式，此檢視。 如需可能值的清單，請參閱`SetScrollSizes`。  
  
 `sizeTotal`  
 以裝置為單位傳回目前的捲動檢視的總大小。  
  
 `sizePage`  
 傳回目前的水平和垂直數量，以回應滑鼠每一個方向的捲動按一下捲軸中。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
 `sizeLine`  
 傳回目前的水平和垂直數量，以回應滑鼠每一個方向的捲動按一下捲動箭號。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
### <a name="remarks"></a>備註  
 大小是以裝置為單位。 很少呼叫此成員函式。  
  
##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition  
 呼叫`GetScrollPosition`何時該添目前水平和垂直位置的捲軸方塊中的捲軸。  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 水平和垂直位置 （以邏輯單位表示） 的捲動方塊`CPoint`物件。  
  
### <a name="remarks"></a>備註  
 此座標組對應的捲動檢視的左上角的文件中的位置。  
  
 `GetScrollPosition` 傳回值以邏輯單位表示。 如果您想裝置單位時，使用`GetDeviceScrollPosition`改為。  
  
##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize  
 呼叫`GetTotalSize`擷取目前的水平和垂直大小的捲動檢視。  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 捲動檢視，以邏輯單位的大小總計。 水平大小**cx**隸屬`CSize`傳回值。 垂直大小**cy**成員。  
  
##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit  
 呼叫`ResizeParentToFit`，讓您檢視的大小指示其框架視窗的大小。  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bShrinkOnly*  
 若要執行調整大小的種類。 預設值為**TRUE**，如果適當的話，會縮小框架視窗。 對於大型的檢視表或小型的框架視窗，仍然會出現捲軸。 值為**FALSE**造成一定要完全調整大小的框架視窗的檢視。 這可能會稍微危險，因為太大，無法配合多重文件介面 (MDI) 框架的視窗或畫面取得框架視窗。  
  
### <a name="remarks"></a>備註  
 這被建議只針對 MDI 子框架視窗中的檢視。 使用`ResizeParentToFit`中`OnInitialUpdate`處理常式函式的衍生`CScrollView`類別。 如需這個成員函式的範例，請參閱[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 `ResizeParentToFit` 假設已設定的 [檢視] 視窗的大小。 如果檢視視窗大小尚未設定時`ResizeParentToFit`是呼叫，就會判斷提示。 為了確保，這不會發生，請進行下列呼叫之前先呼叫`ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition  
 呼叫`ScrollToPosition`捲動至檢視中的指定點。  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 要捲動，以邏輯單位表示的點。 **x**成員必須是正數 （大於或等於 0，最多總檢視的大小）。 同樣適用於**y**成員對應模式時`MM_TEXT`。 **y**成員中為負數以外對應模式`MM_TEXT`。  
  
### <a name="remarks"></a>備註  
 檢視將會使此點是在視窗的左上角捲動。 此成員函式必須不呼叫檢視縮放成最適大小。  
  
##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize  
 呼叫`SetScaleToFitSize`當您想要自動調整檢視區大小為目前的視窗大小。  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>參數  
 `sizeTotal`  
 檢視是要調整大小水平和垂直大小。 捲動檢視的大小被以邏輯單位。 水平大小包含在**cx**成員。 中包含的垂直大小**cy**成員。 同時**cx**和**cy**必須大於或等於 0。  
  
### <a name="remarks"></a>備註  
 含捲軸，一部分的邏輯檢視隨時都可能會看到的。 但使用的小數位數來調整功能，檢視有沒有捲軸而延伸或壓縮到完全符合視窗的工作區的邏輯檢視。 當調整視窗大小時，檢視會在視窗的大小為基礎的新標尺繪製其資料。  
  
 您通常放置呼叫`SetScaleToFitSize`中檢視的覆寫`OnInitialUpdate`成員函式。 如果您不想自動縮放比例，呼叫`SetScrollSizes`成員函式。  
  
 `SetScaleToFitSize` 可用來實作 「 縮放最適大小 」 的作業。 使用`SetScrollSizes`捲動重新初始化。  
  
 `SetScaleToFitSize` 假設已設定的 [檢視] 視窗的大小。 如果檢視視窗大小尚未設定時`SetScaleToFitSize`是呼叫，就會判斷提示。 為了確保，這不會發生，請進行下列呼叫之前先呼叫`SetScaleToFitSize`:  
  
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
 `nMapMode`  
 若要設定此檢視的對應模式。 可能的值包括：  
  
|對應模式|邏輯單元|正數 y 軸延伸...|  
|------------------|------------------|---------------------------------|  
|`MM_TEXT`|1 個像素|向下|  
|`MM_HIMETRIC`|0.01 公釐|向上|  
|`MM_TWIPS`|中的 1/1440|向上|  
|`MM_HIENGLISH`|0.001 中|向上|  
|`MM_LOMETRIC`|0.1 公釐|向上|  
|`MM_LOENGLISH`|0.01 英吋|向上|  
  
 這些模式是由 Windows 定義。 兩種的標準對應模式`MM_ISOTROPIC`和`MM_ANISOTROPIC`，不會用於`CScrollView`。 類別庫會提供`SetScaleToFitSize`調整視窗大小檢視的成員函式。 上表中的三個資料行描述座標的方向。  
  
 `sizeTotal`  
 捲動檢視的大小總計。 **Cx**成員包含水平的範圍。 **Cy**成員包含垂直範圍。 大小是以邏輯單位表示。 同時**cx**和**cy**必須大於或等於 0。  
  
 `sizePage`  
 捲軸中，按一下滑鼠的回應中的每個方向的捲動水平和垂直數量。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
 `sizeLine`  
 滑鼠的回應中的每個方向的捲動水平和垂直數量按一下捲動箭號。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
### <a name="remarks"></a>備註  
 在覆寫中呼叫`OnUpdate`成員函式時，例如，一開始顯示的文件，或當監視變更大小調整捲動的特性。  
  
 您通常會取得從檢視表的相關聯的文件大小資訊，藉由呼叫文件呼叫成員函式，可能是`GetMyDocSize`，您提供與衍生的文件類別。 下列程式碼會示範這種方法：  
  
 [!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 或者，您有時可能需要設定固定的大小，如下列程式碼所示：  
  
 [!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 您必須設定對應模式除了 Windows 對應模式的任何`MM_ISOTROPIC`或`MM_ANISOTROPIC`。 如果您想要使用未受限制的對應模式時，呼叫`SetScaleToFitSize`成員函式，而不是`SetScrollSizes`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)
