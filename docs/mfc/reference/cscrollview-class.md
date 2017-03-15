---
title: "CScrollView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CScrollView
dev_langs:
- C++
helpviewer_keywords:
- CScrollView class
- views, scrolling
- scrolling views
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0dc937a9559306ff527779c45af9fdb62cf602df
ms.lasthandoff: 02/24/2017

---
# <a name="cscrollview-class"></a>CScrollView 類別
A [CView](../../mfc/reference/cview-class.md)具有捲動功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CScrollView : public CView  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CScrollView::CScrollView](#cscrollview)|建構 `CScrollView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CScrollView::CheckScrollBars](#checkscrollbars)|表示捲軸檢視是否有水平和垂直捲軸。|  
|[CScrollView::FillOutsideRect](#filloutsiderect)|填滿的區域外捲動區域的檢視。|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|取得目前捲動位置以裝置為單位。|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|取得目前的對應模式、 大小總計，以及可捲動檢視的列和頁面大小。 大小是以裝置為單位。|  
|[CScrollView::GetScrollPosition](#getscrollposition)|取得目前捲動位置以邏輯單位表示。|  
|[CScrollView::GetTotalSize](#gettotalsize)|取得捲動檢視的大小總計，以邏輯單位表示。|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|會指定其框架的大小檢視的大小。|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|捲動至指定的點，以邏輯單位表示指定的檢視。|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|將捲動檢視切換至小數位數來調整模式。|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|設定捲軸檢視的對應模式、 總大小和水平與垂直捲軸的量。|  
  
## <a name="remarks"></a>備註  
 您可以處理任何衍生自的類別中捲動您自己的標準`CView`藉由覆寫訊息對應[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式。 但是`CScrollView`加入下列功能，其`CView`功能︰  
  
-   它會管理視窗和檢視區的大小和對應的模式。  
  
-   它會自動捲動捲軸訊息回應。  
  
-   它會自動捲動以回應訊息從鍵盤、 非捲動滑鼠或將 intellimouse 滑鼠滾輪。  
  
 若要自動捲動，以回應訊息，請使用鍵盤，新增 WM_KEYDOWN 訊息，然後測試 VK_DOWN、 VK_PREV 和呼叫[SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597)。  
  
 您可以處理滑鼠滾輪捲動自行藉由覆寫訊息對應[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)和[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)成員函式。 對`CScrollView`，這些成員函式支援的建議的行為[WM_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617)，滾輪旋轉訊息。  
  
 若要利用自動捲動，衍生檢視類別從`CScrollView`而不是從`CView`。 檢視第一次建立時，如果您想要計算的大小可捲動檢視文件，呼叫大小所根據的`SetScrollSizes`成員函式中的其中一個覆寫從[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)或[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)。 （您必須撰寫自己的程式碼來查詢文件的大小。 如需範例，請參閱[Scribble 範例](../../visual-cpp-samples.md)。)  
  
 若要呼叫`SetScrollSizes`成員函式會將檢視的對應模式中，捲動檢視] 和 [水平與垂直捲動的數量總計的維度。 所有的大小是以邏輯單位表示。 檢視的邏輯大小通常是計算的資料儲存在文件，但在某些情況下您可能想要指定固定的大小。 如需這兩種方法的範例，請參閱[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 您指定水平與垂直捲動以邏輯單位的數量。 根據預設，如果使用者按一下捲軸桿捲動方塊中，外部`CScrollView`捲動 「 頁面 」。 如果使用者按一下捲軸，任一端的捲動箭號`CScrollView`捲動 「 列 」。 根據預設，頁面是檢視; 的總大小的 1/10線條是頁面大小的 1/10。 傳遞自訂的大小，以覆寫這些預設值`SetScrollSizes`成員函式。 例如，您可能會水平大小設定為一部分的總大小和線條的高度的垂直大小的寬度以目前的字型。  
  
 而不是向下捲動，`CScrollView`可以自動調整檢視以目前的視窗大小。 在此模式中，檢視有沒有捲軸，拉長或壓縮到完全符合視窗的工作區的邏輯檢視。 若要使用此比例來調整功能，請呼叫[CScrollView::SetScaleToFitSize](#setscaletofitsize)。 (呼叫`SetScaleToFitSize`或`SetScrollSizes`，但非兩者。)  
  
 之前`OnDraw`稱為衍生的檢視類別成員函式，`CScrollView`自動調整檢視區原點`CPaintDC`裝置內容物件，就會傳遞至`OnDraw`。  
  
 若要調整捲動視窗中，檢視區的原點`CScrollView`覆寫[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。 這項調整系統會自動針對`CPaintDC`裝置內容的`CScrollView`給`OnDraw`，但您必須呼叫**CScrollView::OnPrepareDC**自己任何其他的裝置內容的使用，例如`CClientDC`。 您可以覆寫**CScrollView::OnPrepareDC**可設定畫筆、 背景色彩和其他繪圖的屬性，但呼叫基底的類別，以進行調整。  
  
 捲軸可以在三個位置，相對於檢視，如下所示在下列情況︰  
  
-   可以為標準的視窗樣式捲軸檢視使用**WS_HSCROLL**和**WS_VSCROLL**[視窗樣式](../../mfc/reference/window-styles.md)。  
  
-   捲軸控制項也可以加入至包含的案例架構將轉送的檢視框架`WM_HSCROLL`和`WM_VSCROLL`訊息框架視窗從目前使用的檢視。  
  
-   架構也會轉送捲動訊息`CSplitterWnd`目前作用中的分隔窗格 （檢視） 來分隔器控制項。 當放在[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)與共用的捲軸，`CScrollView`物件使用的共用項目，而不是建立它自己。  
  
 如需有關使用`CScrollView`，請參閱[文件/檢視架構](../../mfc/document-view-architecture.md)和[衍生檢視類別中可用 MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecheckscrollbarsa--cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::CheckScrollBars  
 呼叫此成員函式，以判斷捲軸檢視是否具有水平及垂直軸。  
  
```  
void CheckScrollBars(
    BOOL& bHasHorzBar,  
    BOOL& bHasVertBar) const;  
```  
  
### <a name="parameters"></a>參數  
 *bHasHorzBar*  
 表示應用程式具有水平捲軸。  
  
 *bHasVertBar*  
 指出應用程式有垂直捲軸。  
  
##  <a name="a-namecscrollviewa--cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView  
 建構 `CScrollView` 物件。  
  
```  
CScrollView();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫`SetScrollSizes`或`SetScaleToFitSize`之前捲軸檢視可供使用。  
  
##  <a name="a-namefilloutsiderecta--cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect  
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
 區域是填滿筆刷。  
  
### <a name="remarks"></a>備註  
 使用`FillOutsideRect`中捲動檢視的`OnEraseBkgnd`處理常式函式，以避免過多的背景，重繪。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&164;](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="a-namegetdevicescrollpositiona--cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition  
 呼叫`GetDeviceScrollPosition`當您需要目前水平和垂直位置的捲動方塊中的捲軸。  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 水平和垂直位置 （以裝置為單位） 的捲動方塊`CPoint`物件。  
  
### <a name="remarks"></a>備註  
 此座標組會對應至文件已被捲動檢視的左上角中的位置。 這是用於移轉至捲動檢視裝置位置的滑鼠裝置位置。  
  
 `GetDeviceScrollPosition`傳回值以裝置為單位。 如果您想的邏輯單元，請使用`GetScrollPosition`改。  
  
##  <a name="a-namegetdevicescrollsizesa--cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes  
 `GetDeviceScrollSizes`取得目前的對應模式、 大小總計，以及可捲動檢視的列和頁面大小。  
  
```  
void GetDeviceScrollSizes(
    int& nMapMode,  
    SIZE& sizeTotal,  
    SIZE& sizePage,  
    SIZE& sizeLine) const;  
```  
  
### <a name="parameters"></a>參數  
 `nMapMode`  
 傳回目前的對應模式，此檢視。 如需可能的值，請參閱`SetScrollSizes`。  
  
 `sizeTotal`  
 傳回目前的總大小的捲軸檢視裝置單位。  
  
 `sizePage`  
 傳回目前的水平和垂直數量，以回應滑鼠的每個方向捲動按一下捲軸中。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
 `sizeLine`  
 傳回目前的水平和垂直數量，以回應滑鼠的每個方向捲動按一下捲動箭號。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
### <a name="remarks"></a>備註  
 大小是以裝置為單位。 此成員函式很少會被呼叫。  
  
##  <a name="a-namegetscrollpositiona--cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition  
 呼叫`GetScrollPosition`當您需要目前水平和垂直位置的捲動方塊中的捲軸。  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 水平和垂直位置 （以邏輯單位表示） 的捲動方塊`CPoint`物件。  
  
### <a name="remarks"></a>備註  
 此座標組會對應至文件已被捲動檢視的左上角中的位置。  
  
 `GetScrollPosition`傳回值，以邏輯單位表示。 如果您想裝置單位，請使用`GetDeviceScrollPosition`改。  
  
##  <a name="a-namegettotalsizea--cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize  
 呼叫`GetTotalSize`來擷取目前的水平和垂直大小的捲軸檢視。  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 捲動檢視，以邏輯單位的大小總計。 水平大小**cx**成員`CSize`傳回值。 垂直大小**cy**成員。  
  
##  <a name="a-nameresizeparenttofita--cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit  
 呼叫`ResizeParentToFit`讓指示其框架視窗的大小檢視的大小。  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bShrinkOnly*  
 若要執行調整大小的類型。 預設值， **TRUE**，如果適用的話，會縮小框架視窗。 對於大型的檢視表或小型框架視窗仍會顯示捲軸列。 值為**FALSE**會讓檢視一律完全調整框架視窗的大小。 這可能會有點危險，因為太大，無法配合多重文件介面 (MDI) 框架的視窗或螢幕取得框架視窗。  
  
### <a name="remarks"></a>備註  
 這被建議只為 MDI 子框架視窗中的檢視。 使用`ResizeParentToFit`中`OnInitialUpdate`處理常式函式的衍生`CScrollView`類別。 如需這個成員函式的範例，請參閱[CScrollView::SetScrollSizes](#setscrollsizes)。  
  
 `ResizeParentToFit`假設已設定 [檢視] 視窗的大小。 如果檢視的視窗大小尚未設定時`ResizeParentToFit`是呼叫，就會判斷提示。 若要確保這並不會不會，進行下列呼叫之前，先呼叫`ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView #&165;](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="a-namescrolltopositiona--cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::ScrollToPosition  
 呼叫`ScrollToPosition`以捲動到檢視中的指定點。  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 要捲動，以邏輯單位的點。 **x**成員必須是正數 （大於或等於 0，最多檢視的大小總計）。 這也適用於**y**成員對應模式時`MM_TEXT`。 **y**成員為負數以外的其他對應模式中`MM_TEXT`。  
  
### <a name="remarks"></a>備註  
 將捲動到檢視，使這點是在視窗的左上角。 如果此檢視會調整為適合，必須不會呼叫此成員函式。  
  
##  <a name="a-namesetscaletofitsizea--cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize  
 呼叫`SetScaleToFitSize`當您想要自動調整檢視區大小為目前的視窗大小。  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>參數  
 `sizeTotal`  
 檢視是要縮放的水平和垂直大小。 捲動檢視的大小被以邏輯單位。 水平大小包含在**cx**成員。 中包含的垂直大小**cy**成員。 同時**cx**和**cy**必須大於或等於 0。  
  
### <a name="remarks"></a>備註  
 含捲軸，只有部分的邏輯檢視隨時都可能會看到的。 但具有小數位數來調整功能，檢視任何捲軸，拉長或壓縮到完全符合視窗的工作區的邏輯檢視。 當調整視窗大小時，檢視新的小數位數的視窗大小為基礎，在上繪製其資料。  
  
 您通常要放置呼叫`SetScaleToFitSize`在檢視表的覆寫`OnInitialUpdate`成員函式。 如果您不想自動縮放比例，呼叫`SetScrollSizes`成員函式。  
  
 `SetScaleToFitSize`可用來實作 「 縮放至適合 」 的作業。 使用`SetScrollSizes`捲動重新初始化。  
  
 `SetScaleToFitSize`假設已設定 [檢視] 視窗的大小。 如果檢視的視窗大小尚未設定時`SetScaleToFitSize`是呼叫，就會判斷提示。 若要確保這並不會不會，進行下列呼叫之前，先呼叫`SetScaleToFitSize`:  
  
 [!code-cpp[NVC_MFCDocView #&165;](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="a-namesetscrollsizesa--cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes  
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
  
|對應模式|邏輯單元|正 y 軸延伸...|  
|------------------|------------------|---------------------------------|  
|`MM_TEXT`|1 個像素|向下|  
|`MM_HIMETRIC`|0.01 公釐|向上|  
|`MM_TWIPS`|在&1;/1440。|向上|  
|`MM_HIENGLISH`|0.001 中|向上|  
|`MM_LOMETRIC`|0.1 公釐|向上|  
|`MM_LOENGLISH`|0.01 英吋|向上|  
  
 所有這些模式是由 Windows 定義。 兩種標準的對應模式`MM_ISOTROPIC`和`MM_ANISOTROPIC`，不能用於`CScrollView`。 類別庫會提供`SetScaleToFitSize`調整視窗大小來檢視成員函式。 上表中的三個資料行描述座標的方向。  
  
 `sizeTotal`  
 捲動檢視的大小總計。 **Cx**成員包含水平範圍。 **Cy**成員包含垂直的範圍。 大小是以邏輯單位表示。 同時**cx**和**cy**必須大於或等於 0。  
  
 `sizePage`  
 按一下捲軸的水平和垂直的數量，以回應滑鼠的每個方向捲動。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
 `sizeLine`  
 水平和垂直數量，以回應滑鼠的每個方向捲動按一下捲動箭號。 **Cx**成員包含水平量。 **Cy**成員包含垂直量。  
  
### <a name="remarks"></a>備註  
 在覆寫中呼叫`OnUpdate`成員函式，或改變大小時最初顯示的文件，例如調整捲動的特性。  
  
 您通常會取得從檢視表的相關聯的文件大小的資訊，文件成員函式，可能是呼叫`GetMyDocSize`，您提供與您在衍生的文件的類別。 下列程式碼示範這種方法︰  
  
 [!code-cpp[NVC_MFCDocView #&166;](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 或者，您有時可能需要設定固定的大小，如下列程式碼所示︰  
  
 [!code-cpp[NVC_MFCDocView #&167;](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 您必須將對應模式設為任何 Windows 對應模式，除了`MM_ISOTROPIC`或`MM_ANISOTROPIC`。 如果您想要使用未受限制的對應模式，呼叫`SetScaleToFitSize`成員函式，而不是`SetScrollSizes`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&168;](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&169;](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)

