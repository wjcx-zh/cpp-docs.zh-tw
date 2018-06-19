---
title: CRectTracker 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eff57e1fde0af6e794c2c47db7d1e31daf545715
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375904"
---
# <a name="crecttracker-class"></a>CRectTracker 類別
可讓項目以顯示、 移動和調整大小不同的方式。  
  
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
|[CRectTracker::AdjustRect](#adjustrect)|將矩形調整時呼叫。|  
|[CRectTracker::Draw](#draw)|將矩形的呈現。|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|繪製的框線時呼叫`CRectTracker`物件。|  
|[CRectTracker::GetHandleMask](#gethandlemask)|呼叫以取得的遮罩`CRectTracker`項目的調整大小控點。|  
|[CRectTracker::GetTrueRect](#gettruerect)|傳回矩形中，包括調整大小控點的寬度和高度。|  
|[CRectTracker::HitTest](#hittest)|傳回目前的位置與相關的資料指標`CRectTracker`物件。|  
|[CRectTracker::NormalizeHit](#normalizehit)|將標準化的點擊測試碼。|  
|[CRectTracker::OnChangedRect](#onchangedrect)|已調整大小或移動矩形時呼叫。|  
|[CRectTracker::SetCursor](#setcursor)|設定資料指標，根據其透過矩形的位置。|  
|[CRectTracker::Track](#track)|可讓使用者管理的矩形。|  
|[Crecttracker:: Trackrubberband](#trackrubberband)|可讓使用者 「 拖放矩形 」 選取範圍。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|決定調整大小控點大小。|  
|[CRectTracker::m_nStyle](#m_nstyle)|目前的追蹤程式 style(s)。|  
|[Crecttracker:: M_rect](#m_rect)|目前位置 （以像素為單位） 的矩形。|  
|[CRectTracker::m_sizeMin](#m_sizemin)|決定最小的矩形寬度和高度。|  
  
## <a name="remarks"></a>備註  
 `CRectTracker` 沒有基底類別。  
  
 雖然`CRectTracker`類別設計來允許使用者使用圖形化介面的 OLE 項目互動，其使用不限於 OLE 功能的應用程式。 可以使用這類使用者介面的所需的任何位置。  
  
 `CRectTracker` 框線可以是實線或虛線。 可以指定陰影的框線或覆蓋影線的模式，表示不同的狀態項目的項目。 您可以將八個調整大小控點放在外部或內部項目的框線。 (如需調整大小控點的說明，請參閱[GetHandleMask](#gethandlemask)。)最後，`CRectTracker`可讓您變更項目期間調整大小的方向。  
  
 若要使用`CRectTracker`，建構`CRectTracker`物件，並指定哪些顯示狀態初始化。 您接著可以使用此介面上 OLE 項目相關聯的目前狀態提供給使用者的視覺化回應`CRectTracker`物件。  
  
 如需有關使用`CRectTracker`，請參閱文章[追蹤器](../../mfc/trackers.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CRectTracker`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="adjustrect"></a>  CRectTracker::AdjustRect  
 追蹤矩形使用調整大小控點來調整大小時，由架構呼叫。  
  
```  
virtual void AdjustRect(
    int nHandle,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `nHandle`  
 使用控制代碼的索引。  
  
 `lpRect`  
 目前大小的矩形的指標。 （矩形的大小是由它的高度和寬度所提供）。  
  
### <a name="remarks"></a>備註  
 此函式的預設行為可讓矩形的方向變更時，才`Track`和`TrackRubberBand`以反轉允許來呼叫。  
  
 覆寫這個函式來控制追蹤矩形拖曳作業期間的調整。 其中一個方法是調整所指定的座標`lpRect`後再傳回。  
  
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
 `lpSrcRect`  
 矩形物件的座標。  
  
 `nStyle`  
 指定的樣式`CRectTracker`物件。 支援下列樣式：  
  
- **CRectTracker::solidLine**實線用於矩形的框線。  
  
- **CRectTracker::dottedLine**使用矩形外框虛線。  
  
- **CRectTracker::hatchedBorder**矩形外框使用影線的圖樣。  
  
- **CRectTracker::resizeInside**調整大小控點位於矩形內部。  
  
- **CRectTracker::resizeOutside**調整大小控點放在矩形的外面。  
  
- **CRectTracker::hatchInside** Hatched 模式涵蓋整個矩形。  
  
### <a name="remarks"></a>備註  
 預設建構函式初始化`CRectTracker`物件的值填入`lpSrcRect`並初始化為系統預設值的其他大小。 如果使用任何參數，建立物件`m_rect`和`m_nStyle`資料成員都是未初始化。  
  
##  <a name="draw"></a>  CRectTracker::Draw  
 呼叫此函式可繪製的矩形外部線條和內部的區域。  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 若要在其上繪製的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 追蹤程式的樣式會判斷如何進行繪圖。 請參閱的建構函式`CRectTracker`如需有關可用樣式。  
  
##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect  
 每當追蹤器的位置已變更時由架構呼叫時內`Track`或`TrackRubberBand`成員函式。  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指標`RECT`，其中包含要繪製的矩形。  
  
 `pWndClipTo`  
 用於裁剪矩形視窗的指標。  
  
 `pDC`  
 若要在其上繪製的裝置內容的指標。  
  
 `pWnd`  
 視窗繪圖將會發生的指標。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`CDC::DrawFocusRect`，其中繪製虛線的矩形。  
  
 此函式可提供不同的意見反應追蹤作業期間會覆寫。  
  
##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask  
 架構會呼叫此成員函式，來擷取遮罩矩形的調整大小控點。  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>傳回值  
 遮罩`CRectTracker`項目的調整大小控點。  
  
### <a name="remarks"></a>備註  
 調整大小控點出現在側邊和矩形的圓角，並允許使用者控制的形狀和大小的矩形。  
  
 矩形有 8 編號 0-7 的調整大小控點。 每個調整大小控點被以的位元遮罩。該位元的值為 2 ^ *n*，其中*n*是調整大小控點數目。 位元 0-3 對應到邊角調整大小控點開始左上方移動順時針旋轉。 對應至側邊的 4-7 位元調整大小控點朝順時針方向移動從頂端開始。 下圖顯示矩形的調整大小控點和其相對應調整大小控點的數字和值：  
  
 ![調整大小控點數字](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 預設實作**GetHandleMask**傳回的位元遮罩，以便調整大小控點會出現。 如果單一的位元為開啟，就會繪製相對應的調整大小控點。  
  
 覆寫此成員函式，以隱藏或顯示指定的調整大小控點。  
  
##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect  
 呼叫此函式可擷取的矩形座標。  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpTrueRect`  
 指標`RECT`結構將會包含裝置座標`CRectTracker`物件。  
  
### <a name="remarks"></a>備註  
 矩形的維度會包含任何調整大小控點位於 外框的寬度與高度。 時傳回，`lpTrueRect`永遠是標準化的裝置座標中矩形。  
  
##  <a name="hittest"></a>  CRectTracker::HitTest  
 呼叫此函式可了解使用者是否具有捕捉調整大小控點。  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>參數  
 `point`  
 若要測試的裝置座標中的點。  
  
### <a name="return-value"></a>傳回值  
 傳回的值為基礎的列舉型別**CRectTracker::TrackerHit** ，而且可以有下列值之一：  
  
- **CRectTracker::hitNothing** -1  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize  
 大小，單位為像素的`CRectTracker`調整大小控點。  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>備註  
 初始化具有預設的系統值。  
  
##  <a name="m_rect"></a>  Crecttracker:: M_rect  
 矩形的工作區座標 （像素） 中的目前位置。  
  
```  
CRect m_rect;  
```  
  
##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin  
 矩形的大小下限。  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>備註  
 預設值 （literal） **cx**和**cy**，從預設系統的框線寬度的值計算所得。 此資料成員僅供`AdjustRect`成員函式。  
  
##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle  
 目前的矩形樣式。  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>備註  
 請參閱[CRectTracker::CRectTracker](#crecttracker)取得一份可能的樣式。  
  
##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit  
 呼叫此函式可將轉換可能會有反向的控制代碼。  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>參數  
 `nHandle`  
 使用者所選的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 正規化的控制代碼的索引。  
  
### <a name="remarks"></a>備註  
 當`CRectTracker::Track`或`CRectTracker::TrackRubberBand`稱為反轉允許，您也可以針對要在 x 軸、 y 軸，或兩者皆會反轉的矩形。 當發生這種情況時，`HitTest`會傳回相對於矩形也反轉的控制代碼。 因為意見反應取決於在矩形中，不會被修改的矩形資料結構一部分的螢幕位置，這並不適用於繪製游標意見反應。  
  
##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect  
 由架構呼叫，每當呼叫期間變更 tracker 矩形`Track`。  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>參數  
 *rectOld*  
 包含舊裝置座標`CRectTracker`物件。  
  
### <a name="remarks"></a>備註  
 在階段會呼叫此函數，以繪製所有意見反應`DrawTrackerRect`已移除。 此函式的預設實作不做任何動作。  
  
 當您想要執行任何動作矩形已調整大小之後，請覆寫這個函式。  
  
##  <a name="setcursor"></a>  CRectTracker::SetCursor  
 呼叫此函式可變更指標形狀時透過`CRectTracker`物件的區域。  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指向目前包含游標的視窗。  
  
 `nHitTest`  
 先前的點擊測試的結果從`WM_SETCURSOR`訊息。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果上一個結果是經由 tracker 矩形。否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式從您的視窗處理函式內`WM_SETCURSOR`訊息 (通常`OnSetCursor`)。  
  
##  <a name="track"></a>  CRectTracker::Track  
 呼叫此函式可顯示使用者介面的調整大小的矩形。  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含矩形的視窗物件。  
  
 `point`  
 裝置目前的滑鼠位置相對於用戶端區域的座標。  
  
 `bAllowInvert`  
 如果**TRUE**，矩形可以是反向沿著 x 軸或 y 軸，否則**FALSE**。  
  
 `pWndClipTo`  
 繪製作業會裁剪到視窗。 如果**NULL**，`pWnd`做裁剪方框。  
  
### <a name="return-value"></a>傳回值  
 如果按下 ESC 鍵時，則會暫止追蹤程序、 儲存在追蹤程式中的矩形不會改變，和會傳回 0。 如果認可變更時，藉由移動滑鼠，並釋放滑鼠左鍵，新的位置及/或大小會記錄在追蹤器的矩形，並為非零，則會傳回。  
  
### <a name="remarks"></a>備註  
 這通常稱為從函式會處理應用程式內`WM_LBUTTONDOWN`訊息 (通常`OnLButtonDown`)。  
  
 此函式會擷取滑鼠，直到使用者放開滑鼠左的按鈕、 按下 ESC 鍵，或按下滑鼠按鈕。 當使用者移動滑鼠游標，藉由呼叫也會更新意見反應`DrawTrackerRect`和`OnChangedRect`。  
  
 如果`bAllowInvert`是**TRUE**，追蹤矩形可以反轉 x 軸或 y 軸上。  
  
##  <a name="trackrubberband"></a>  Crecttracker:: Trackrubberband  
 呼叫此函式執行拖放矩形選取範圍。  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含矩形的視窗物件。  
  
 `point`  
 裝置目前的滑鼠位置相對於用戶端區域的座標。  
  
 `bAllowInvert`  
 如果**為 TRUE，** 矩形可以是反向沿著 x 軸或 y 軸，否則**FALSE**。  
  
### <a name="return-value"></a>傳回值  
 如果滑鼠移動，而且矩形不是空的則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 它通常稱為從函式會處理應用程式內`WM_LBUTTONDOWN`訊息 (通常`OnLButtonDown`)。  
  
 此函式會擷取滑鼠，直到使用者放開滑鼠左的按鈕、 按下 ESC 鍵，或按下滑鼠按鈕。 當使用者移動滑鼠游標，藉由呼叫也會更新意見反應`DrawTrackerRect`和`OnChangedRect`。  
  
 追蹤會使用從右下方的控制代碼的拖放頻外類型選取項目來執行。 如果允許反轉，矩形可以是向上和向左或往下及往右拖曳調整大小。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例追蹤器](../../visual-cpp-samples.md)   
 [MFC 範例 DRAWCLI](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleResizeBar 類別](../../mfc/reference/coleresizebar-class.md)   
 [CRect 類別](../../atl-mfc-shared/reference/crect-class.md)
