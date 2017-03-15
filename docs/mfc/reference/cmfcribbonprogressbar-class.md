---
title: "CMFCRibbonProgressBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonProgressBar class
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 26
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
ms.openlocfilehash: 51efd8c4ac84dffe1384b7d664197b4bdebad110
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar 類別
實作以視覺效果指示長時間作業進度的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|建構並初始化 `CMFCRibbonProgressBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|傳回目前的進度。|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|傳回目前範圍的最大值。|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|傳回目前範圍的最小值。|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|指定是否在無限模式工作進度列。|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|設定進度列，才能以無限的模式運作。|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|設定目前的進度。|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|設定最小和最大值。|  
  
## <a name="remarks"></a>備註  
 A`CMFCRibbonProgressBar`可以在兩種模式下運作︰ 標準和無限。 在標準模式中，進度列會從左到右填滿，並達到最大值時，就會停止。 在無限模式中，進度列會重複填滿從最小值的最大值。 您可以使用無限的模式，表示作業正在進行中，但完成時間不明。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonProgressBar`類別。 設定進度列的最小和最大值，並設定進度列目前位置，範例會示範如何設定在 （其中一項作業的完成時間是未知） 無限的模式下，進度列。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&11;](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonProgressBar.h  
  
##  <a name="a-namecmfcribbonprogressbara--cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 建構並初始化[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)物件。  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 指定功能區進度列的命令 ID。  
  
 [in] `nWidth`  
 指定寬度，單位為像素功能區進度列。  
  
 [in] `nHeight`  
 指定高度，單位為像素功能區進度列。  
  
##  <a name="a-namegetposa--cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFCRibbonProgressBar::GetPos  
 傳回目前的進度列的位置。  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示目前的進度列的位置。  
  
### <a name="remarks"></a>備註  
 正在設定的範圍必須是所指定的範圍內[CMFCRibbonProgressBar::SetRange](#setrange)方法。  
  
##  <a name="a-namegetrangemaxa--cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax  
 傳回進度列的目前最大值。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前範圍的最大值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetrangemina--cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin  
 傳回進度列的目前最小範圍值。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前範圍的最小值。  
  
##  <a name="a-namegetregularsizea--cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisinfinitemodea--cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode  
 指定是否在無限模式工作進度列。  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果進度列是無限的模式，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 在無限模式中，進度列填滿重複從最小值的最大值。 您可以使用無限的模式，表示作業正在進行中，但完成時間不明。  
  
##  <a name="a-nameondrawa--cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetinfinitemodea--cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode  
 設定進度列，才能以無限的模式運作。  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 `TRUE`若要指定無限的模式，進度列否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 通常，如果進度列是無限的模式，它會告訴使用者作業正在進行中，但完成時間不明。 因此，進度列填滿重複從最小值的最大值。  
  
##  <a name="a-namesetposa--cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFCRibbonProgressBar::SetPos  
 設定進度列目前位置。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nPos`  
 指定設定進度列的位置。  
  
 [in] `bRedraw`  
 指定是否應該重新繪製進度列。  
  
### <a name="remarks"></a>備註  
 正在設定的範圍必須是所指定的範圍內[CMFCRibbonProgressBar::SetRange](#setrange)方法。  
  
##  <a name="a-namesetrangea--cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFCRibbonProgressBar::SetRange  
 設定進度列的最小和最大值。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 [in] `nMin`  
 指定範圍的最小值。  
  
 [in] `nMax`  
 指定範圍的最大值。  
  
### <a name="remarks"></a>備註  
 使用這個方法來定義進度列範圍，藉由設定最小和最大值。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)

