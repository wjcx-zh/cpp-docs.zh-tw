---
title: "CRectTracker 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRectTracker
dev_langs:
- C++
helpviewer_keywords:
- displaying items
- CRectTracker class
- resizing items
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
caps.latest.revision: 23
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
ms.openlocfilehash: 444eab5969339cf2a3d5797807eae3dcad32a694
ms.lasthandoff: 02/24/2017

---
# <a name="crecttracker-class"></a>CRectTracker 類別
允許的項目顯示、 移動和調整不同的方式。  
  
## <a name="syntax"></a>語法  
  
```  
class CRectTracker  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRectTracker::CRectTracker](#crecttracker)|建構 `CRectTracker` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRectTracker::AdjustRect](#adjustrect)|調整大小的矩形時呼叫。|  
|[CRectTracker::Draw](#draw)|呈現矩形。|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|繪製的框線時，呼叫`CRectTracker`物件。|  
|[CRectTracker::GetHandleMask](#gethandlemask)|呼叫以取得的遮罩`CRectTracker`項目的調整大小控點。|  
|[CRectTracker::GetTrueRect](#gettruerect)|傳回包含調整大小控點的矩形的寬度和高度。|  
|[CRectTracker::HitTest](#hittest)|傳回相關的資料指標的目前位置`CRectTracker`物件。|  
|[CRectTracker::NormalizeHit](#normalizehit)|正規化的點擊測試碼。|  
|[CRectTracker::OnChangedRect](#onchangedrect)|已調整大小或移動矩形時呼叫。|  
|[CRectTracker::SetCursor](#setcursor)|設定資料指標，根據其放置於矩形。|  
|[CRectTracker::Track](#track)|可讓使用者管理的矩形。|  
|[Crecttracker:: Trackrubberband](#trackrubberband)|可讓使用者 「 拖放矩形 」 選取範圍。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|決定調整大小控點大小。|  
|[CRectTracker::m_nStyle](#m_nstyle)|目前的追蹤者 style(s)。|  
|[Crecttracker:: M_rect](#m_rect)|目前位置 （以像素為單位） 的矩形。|  
|[CRectTracker::m_sizeMin](#m_sizemin)|決定最小矩形的寬度和高度。|  
  
## <a name="remarks"></a>備註  
 `CRectTracker`沒有基底類別。  
  
 雖然`CRectTracker`類別的設計可讓使用者能夠使用圖形化介面互動與 OLE 項目、 使用不限於 OLE 功能的應用程式。 它可以用於需要使用者介面的任何地方。  
  
 `CRectTracker`框線可以是實線或虛線。 項目可以出現陰影框線，或覆蓋陰影圖樣來表示不同狀態的項目。 您可以將八個調整大小控點放在外部或內部項目的框線。 (如需調整大小控點的說明，請參閱[GetHandleMask](#gethandlemask)。)最後，`CRectTracker`可讓您變更項目期間調整大小的方向。  
  
 若要使用`CRectTracker`，建構`CRectTracker`物件，並指定何種顯示狀態會初始化。 您接著可以使用此介面，讓使用者視覺化回饋 OLE 項目相關聯的目前狀態`CRectTracker`物件。  
  
 如需有關使用`CRectTracker`，請參閱文章[追蹤器](../../mfc/trackers.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CRectTracker`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="a-nameadjustrecta--crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect  
 追蹤矩形的大小時使用調整大小控點，由架構呼叫。  
  
```  
virtual void AdjustRect(
    int nHandle,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `nHandle`  
 使用控制代碼的索引。  
  
 `lpRect`  
 目前大小的矩形的指標。 （矩形的大小是由其高度和寬度所提供）。  
  
### <a name="remarks"></a>備註  
 此函式的預設行為可讓矩形的方向變更時，才`Track`和`TrackRubberBand`反轉允許呼叫。  
  
 覆寫此函式可控制在拖曳作業期間追蹤矩形的調整。 其中一個方法是調整指定的座標`lpRect`後再傳回。  
  
 不直接支援的特殊功能`CRectTracker`，例如貼齊至格線或保留外觀比例，可以藉由覆寫這個函式實作。  
  
##  <a name="a-namecrecttrackera--crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker  
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
 指定的樣式`CRectTracker`物件。 支援下列樣式︰  
  
- **CRectTracker::solidLine**實線用於矩形的框線。  
  
- **CRectTracker::dottedLine**使用虛線矩形外框。  
  
- **CRectTracker::hatchedBorder**用於矩形框線影線的圖樣。  
  
- **CRectTracker::resizeInside**調整大小控點位於矩形內部。  
  
- **CRectTracker::resizeOutside**調整大小控點放在矩形外。  
  
- **CRectTracker::hatchInside** Hatched 模式涵蓋整個矩形。  
  
### <a name="remarks"></a>備註  
 預設建構函式初始化`CRectTracker`物件的值`lpSrcRect`和初始化其他大小為系統預設值。 如果物件使用沒有參數，建立`m_rect`和`m_nStyle`資料成員都是未初始化。  
  
##  <a name="a-namedrawa--crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw  
 呼叫此函式可繪製的矩形外部的線條和內部區域。  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 若要在其上繪製的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 追蹤器的樣式會判斷如何進行繪圖。 請參閱的建構函式`CRectTracker`如需有關可用的樣式。  
  
##  <a name="a-namedrawtrackerrecta--crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect  
 每當追蹤器的位置已變更時，由框架呼叫內而`Track`或`TrackRubberBand`成員函式。  
  
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
 若要使用的裁剪矩形視窗的指標。  
  
 `pDC`  
 若要在其上繪製的裝置內容的指標。  
  
 `pWnd`  
 視窗繪圖將會發生的指標。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`CDC::DrawFocusRect`，以便繪製虛線的矩形。  
  
 此函式可提供不同的意見反應追蹤作業期間會覆寫。  
  
##  <a name="a-namegethandlemaska--crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask  
 架構會呼叫此成員函式的矩形的調整大小控點，擷取遮罩。  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>傳回值  
 遮罩`CRectTracker`項目的調整大小控點。  
  
### <a name="remarks"></a>備註  
 調整大小控點出現在和矩形的角落，並允許使用者控制的形狀和大小的矩形。  
  
 矩形有 8 編號 0-7 的調整大小控點。 每個調整大小控點被以位元遮罩。該位元的值為 2 ^ *n*，其中*n*是調整大小控點數目。 位元 0-3 對應到邊角調整大小控點，從左上角移動順時針旋轉。 位元 4-7 對應的側邊調整大小控點朝順時針方向移動從頂端開始。 下圖顯示矩形的大小調整控點，以及其對應調整大小控點數字和值︰  
  
 ![調整大小控點數字](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 預設實作**GetHandleMask**傳回的位元遮罩，以便調整大小控點出現。 如果在單一位元，來繪製對應的調整大小控點。  
  
 覆寫此成員函式，來隱藏或顯示指定的調整大小控點。  
  
##  <a name="a-namegettruerecta--crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect  
 呼叫此函式可擷取的矩形座標。  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpTrueRect`  
 指標`RECT`結構，它將包含裝置座標`CRectTracker`物件。  
  
### <a name="remarks"></a>備註  
 矩形的維度包含高度和寬度的外框上任何調整大小控點。 在傳回時，`lpTrueRect`永遠是在裝置座標的標準化的矩形。  
  
##  <a name="a-namehittesta--crecttrackerhittest"></a><a name="hittest"></a>CRectTracker::HitTest  
 呼叫此函式可了解使用者是否具有抓取調整大小控點。  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>參數  
 `point`  
 若要測試的裝置座標中的點。  
  
### <a name="return-value"></a>傳回值  
 傳回的值為基礎的列舉型別**CRectTracker::TrackerHit**而且可以具有下列值之一︰  
  
- **CRectTracker::hitNothing** –&1;  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="a-namemnhandlesizea--crecttrackermnhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize  
 大小，單位為像素的`CRectTracker`調整大小控點。  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>備註  
 初始化使用預設系統值。  
  
##  <a name="a-namemrecta--crecttrackermrect"></a><a name="m_rect"></a>Crecttracker:: M_rect  
 目前的位置矩形在工作區座標 （像素）。  
  
```  
CRect m_rect;  
```  
  
##  <a name="a-namemsizemina--crecttrackermsizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin  
 矩形的大小下限。  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>備註  
 預設值 （literal） **cx**和**cy**，計算從框線寬度的預設系統值。 此資料成員僅供`AdjustRect`成員函式。  
  
##  <a name="a-namemnstylea--crecttrackermnstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle  
 目前的矩形樣式。  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>備註  
 請參閱[CRectTracker::CRectTracker](#crecttracker)如需可能的樣式的清單。  
  
##  <a name="a-namenormalizehita--crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit  
 呼叫此函式來轉換可能會有反向的控制代碼。  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>參數  
 `nHandle`  
 使用者所選取的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 正規化的控制代碼的索引。  
  
### <a name="remarks"></a>備註  
 當`CRectTracker::Track`或`CRectTracker::TrackRubberBand`稱為反轉允許，您也可以針對要在 x 軸、 y 軸，或兩者皆會反轉的矩形。 當發生這種情況時，`HitTest`會傳回矩形方面也反轉的控制代碼。 因為意見反應而定的矩形中，不會修改矩形資料結構的部分的螢幕位置，這並不適用於繪製游標意見反應。  
  
##  <a name="a-nameonchangedrecta--crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect  
 每當追蹤器矩形已經在呼叫期間，由框架呼叫`Track`。  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>參數  
 *rectOld*  
 包含舊裝置座標`CRectTracker`物件。  
  
### <a name="remarks"></a>備註  
 同時會呼叫此函數，以繪製的所有意見反應`DrawTrackerRect`已移除。 此函式的預設實作不做任何動作。  
  
 當您想要已調整大小的矩形之後執行任何動作，請覆寫這個函式。  
  
##  <a name="a-namesetcursora--crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker::SetCursor  
 呼叫此函式可變更指標形狀，雖然它是透過`CRectTracker`物件的區域。  
  
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
 非零，如果上一個結果是經由追蹤器 的矩形。否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式從您處理的視窗函數內`WM_SETCURSOR`訊息 (通常`OnSetCursor`)。  
  
##  <a name="a-nametracka--crecttrackertrack"></a><a name="track"></a>CRectTracker::Track  
 呼叫此函式，以顯示使用者介面，來調整大小的矩形。  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含矩形視窗物件。  
  
 `point`  
 裝置目前的滑鼠位置，相對於用戶端區域的座標。  
  
 `bAllowInvert`  
 如果**TRUE**，矩形可以沿著 x 軸或 y 軸反轉，否則**FALSE**。  
  
 `pWndClipTo`  
 繪製作業會裁剪至視窗。 如果**NULL**，`pWnd`做為裁剪方框。  
  
### <a name="return-value"></a>傳回值  
 如果按下 ESC 鍵時，追蹤程序就會停止、 儲存在 [追蹤器] 中的矩形不會改變，而且就會傳回 0。 如果已認可變更，藉由移動滑鼠，並放開滑鼠左鍵，新的位置和/或大小記錄追蹤器 的矩形中並傳回非零值。  
  
### <a name="remarks"></a>備註  
 這通常稱為從函式會處理應用程式內`WM_LBUTTONDOWN`訊息 (通常`OnLButtonDown`)。  
  
 此函式會捕捉滑鼠，直到使用者釋放滑鼠左鍵，按下 ESC 鍵，或按下滑鼠按鈕。 當使用者移動滑鼠游標，藉由呼叫更新意見反應`DrawTrackerRect`和`OnChangedRect`。  
  
 如果`bAllowInvert`是**TRUE**，可以反轉追蹤矩形在 x 軸或 y 軸上。  
  
##  <a name="a-nametrackrubberbanda--crecttrackertrackrubberband"></a><a name="trackrubberband"></a>Crecttracker:: Trackrubberband  
 呼叫此函式執行拖放矩形選取範圍。  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含矩形視窗物件。  
  
 `point`  
 裝置目前的滑鼠位置，相對於用戶端區域的座標。  
  
 `bAllowInvert`  
 如果**為 TRUE，**矩形可以沿著 x 軸或 y 軸反轉，否則**FALSE**。  
  
### <a name="return-value"></a>傳回值  
 非零，如果滑鼠已移動，而且矩形不是空的。否則為 0。  
  
### <a name="remarks"></a>備註  
 它通常是從呼叫函式會處理應用程式內`WM_LBUTTONDOWN`訊息 (通常`OnLButtonDown`)。  
  
 此函式會捕捉滑鼠，直到使用者釋放滑鼠左鍵，按下 ESC 鍵，或按下滑鼠按鈕。 當使用者移動滑鼠游標，藉由呼叫更新意見反應`DrawTrackerRect`和`OnChangedRect`。  
  
 追蹤執行拖放頻外類型選取項目從右下方的控制代碼。 允許反轉，矩形可以是向上和向左或往下及往右邊拖曳調整大小。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例追蹤器](../../visual-cpp-samples.md)   
 [MFC 範例 DRAWCLI](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [Coleipframewnd 類別](../../mfc/reference/coleresizebar-class.md)   
 [CRect 類別](../../atl-mfc-shared/reference/crect-class.md)

