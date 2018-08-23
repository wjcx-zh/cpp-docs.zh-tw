---
title: CMFCRibbonSlider 類別 |Microsoft Docs
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
ms.openlocfilehash: 0816a490a4375504168b11d8055ddbe41dae2109
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540771"
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
|[CMFCRibbonSlider::GetPos](#getpos)|傳回滑桿控制項的目前的位置。|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|傳回滑桿的最大值。|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|傳回滑桿的最小值。|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|傳回的滑桿控制項的縮放增量的大小。|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|指定是否在滑桿有顯示比例按鈕。|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonSlider::SetPos](#setpos)|設定滑桿控制項的目前位置。|  
|[CMFCRibbonSlider::SetRange](#setrange)|藉由設定 最小和最大值，指定滑桿控制項的範圍。|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|顯示或隱藏 [縮放] 按鈕。|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|設定縮放增量滑桿控制項的大小。|  
  
## <a name="remarks"></a>備註  
 您可以使用`SetRange`方法，以設定範圍的滑桿縮放增量。 您可以設定滑桿的目前位置使用`SetPos`方法。  
  
 您也可以使用在左邊和右邊的滑桿控制項顯示循環顯示比例按鈕`SetZoomButtons`方法。 根據預設，滑桿是水平的左側顯示比例按鈕會顯示減號，適當的顯示比例 按鈕會顯示一個加號。  
  
 `SetZoomIncrement`方法定義新增至，或當使用者按一下 [縮放] 按鈕，從目前位置減去遞增。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用中的各種方法`CMFCRibbonSlider`類別，以設定滑桿的屬性。 此範例示範如何建構`CMFCRibbonSlider`物件、 顯示縮放按鈕、 滑桿控制項，將目前位置設定和設定範圍滑桿控制項的值。  
  
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
 [in]*nID*  
 滑桿的識別碼。  
  
 [in]。 *nWidth*  
 滑桿寬度，以像素為單位。  
  
### <a name="remarks"></a>備註  
 建構是功能區滑桿*nWidth*像素寬面板類別加入滑桿的位置中。 根據預設，滑桿是水平的。  
  
##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos  
 傳回滑桿控制項的目前的位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的滑桿控制項，也就是相對於開始的位置，滑桿的位置。  
  
##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax  
 取得滑動軸可行駛的滑桿控制項的滑桿的最大的遞增值。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿可行駛的滑桿控制項的滑桿的最大的增量。  
  
##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin  
 傳回的最小值的遞增量滑桿可行駛的滑桿控制項。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿可行駛滑桿控制項的最小的增量。  
  
##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement  
 取得滑動軸控制項的縮放增量。  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項縮放增量。  
  
##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons  
 指定是否在滑桿有顯示比例按鈕。  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果滑桿縮放按鈕;，則為 TRUE。FALSE 否則。  
  
##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos  
 將滑桿控制項的目前位置的設定。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*nPos*  
 指定要設定滑桿的位置。 這個位置是相對於滑桿的開頭。  
  
 [in]*bRedraw*  
 如果為 TRUE，就會重新繪製滑桿。  
  
##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange  
 設定範圍滑桿控制項的值。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 [in]*nMin*  
 指定滑桿控制項的最小值。  
  
 [in]*nMax*  
 指定滑桿控制項的最大值。  
  
### <a name="remarks"></a>備註  
 藉由設定 最小和最大值，指定滑桿控制項的值範圍。  
  
##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons  
 顯示或隱藏縮放按鈕。  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]。 *bSet*  
 TRUE 表示縮放按鈕; 顯示若要隱藏它們，則為 FALSE。  
  
##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement  
 設定滑桿控制項的縮放增量。  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>參數  
 [in]*nZoomIncrement*  
 指定滑桿控制項的縮放增量。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)
