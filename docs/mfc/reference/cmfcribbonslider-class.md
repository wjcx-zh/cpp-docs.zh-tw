---
title: CMFCRibbonSlider 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4264f26028db4c581fe1dc143905ac0ffc8f66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372693"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider 類別
`CMFCRibbonSlider`類別會實作可以加入功能區列或功能區狀態列的滑桿控制項。 功能區滑桿控制項類似出現在 Office 2007 應用程式中的縮放滑桿。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|建構並初始化功能區滑桿控制項。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](#getpos)|傳回目前的滑桿控制項的位置。|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|傳回滑桿的最大值。|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|傳回滑桿的最小值。|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|傳回的滑桿控制項的縮放遞增的大小。|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|指定滑動軸是否顯示比例按鈕。|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonSlider::SetPos](#setpos)|設定滑桿控制項的目前位置。|  
|[CMFCRibbonSlider::SetRange](#setrange)|藉由設定 最小和最大值指定滑桿控制項的範圍。|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|顯示或隱藏顯示比例按鈕。|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|設定縮放增量滑桿控制項的大小。|  
  
## <a name="remarks"></a>備註  
 您可以使用`SetRange`的滑桿縮放增量的範圍設定的方法。 您可以透過設定滑桿的目前位置`SetPos`方法。  
  
 您也可以使用從左邊和右邊的滑桿控制項顯示循環顯示比例按鈕`SetZoomButtons`方法。 根據預設，請滑動軸是水平、 的左邊顯示比例按鈕顯示負號和右縮放 按鈕會顯示一個加號。  
  
 `SetZoomIncrement`方法所定義之遞增值加入或減去目前的位置，當使用者按一下 [縮放] 按鈕。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonSlider`類別來設定滑桿的屬性。 此範例示範如何建構`CMFCRibbonSlider`物件、 顯示 顯示比例按鈕、 滑桿控制項，將目前位置設定及設定的滑桿控制項的值範圍。  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribbonslider.h  
  
##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider  
 建構功能區滑桿。  
  
```  
CMFCRibbonSlider(
    UINT nID,  
    int nWidth=100);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nID`  
 滑桿識別碼。  
  
 [in]。 `nWidth`  
 滑桿寬度的像素。  
  
### <a name="remarks"></a>備註  
 建構功能區滑桿，`nWidth`像素寬面板分類加入滑桿的位置中。 根據預設，滑動軸是水平的。  
  
##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos  
 傳回目前的滑桿控制項的位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項，也就是滑桿位置相對於開頭的目前位置。  
  
##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax  
 取得滑動軸可行駛的滑桿控制項的滑桿的最大的遞增值。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿可行駛的滑桿控制項的滑桿的最大的遞增值。  
  
##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin  
 傳回最小滑桿可行駛的滑桿控制項的增量。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿可行駛滑桿控制項的最小的增量。  
  
##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement  
 取得滑動軸控制項的顯示比例增量。  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>傳回值  
 縮放滑桿控制項的增量。  
  
##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons  
 指定滑動軸是否顯示比例按鈕。  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果滑桿有顯示比例按鈕。`FALSE`否則。  
  
##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos  
 將滑桿控制項的目前位置的設定。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nPos`  
 指定要設定滑桿的位置。 這個位置是相對於滑桿的開頭。  
  
 [輸入] `bRedraw`  
 如果`TRUE`，滑桿會重新繪製。  
  
##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange  
 將滑桿控制項的值範圍的設定。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nMin`  
 指定滑桿控制項的最小值。  
  
 [輸入] `nMax`  
 指定滑桿控制項的最大值。  
  
### <a name="remarks"></a>備註  
 藉由設定 最小和最大值指定滑桿控制項的值範圍。  
  
##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons  
 顯示或隱藏顯示比例按鈕。  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]。 `bSet`  
 `TRUE` 若要顯示 顯示比例按鈕。`FALSE`隱藏起來。  
  
##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement  
 設定滑桿控制項的顯示比例增量。  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nZoomIncrement`  
 指定滑桿控制項的顯示比例增量。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)
