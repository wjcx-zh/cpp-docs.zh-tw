---
title: "CMFCRibbonProgressBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1354b0b15837a733a890c438c7771ffe39526773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar 類別
實作以視覺效果指示長時間作業進度的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|建構並初始化 `CMFCRibbonProgressBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|傳回目前的進度。|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|傳回目前範圍的最大值。|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|傳回目前範圍的最小值。|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|指定是否在無限模式工作進度列。|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|設定無限的模式中工作的進度列。|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|設定目前的進度。|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|設定最小和最大值。|  
  
## <a name="remarks"></a>備註  
 A`CMFCRibbonProgressBar`可以在兩種模式下操作： 一般和無限。 在標準模式中，進度列會從左到右填滿，並停止到達最大值時。 在無限模式中，進度列會重複填滿從最小值的最大值。 您可以使用無限的模式，表示作業正在進行中，但是完成時間不明。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonProgressBar`類別。 設定最小和最大值進度列，以及設定進度列的目前位置，範例會示範如何設定中 （其中一項作業的完成時間是未知） 的無限模式下，工作的進度列。 此程式碼片段是部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 建構並初始化[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)物件。  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nID`  
 指定功能區進度列的命令 ID。  
  
 [輸入] `nWidth`  
 指定的寬度，以像素的功能區進度列。  
  
 [輸入] `nHeight`  
 指定高度，單位為像素的功能區進度列。  
  
##  <a name="getpos"></a>CMFCRibbonProgressBar::GetPos  
 傳回目前進度列的位置。  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示目前進度列的位置。  
  
### <a name="remarks"></a>備註  
 正在設定的範圍必須是所指定的範圍內[CMFCRibbonProgressBar::SetRange](#setrange)方法。  
  
##  <a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax  
 傳回進度列的目前最大值。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前範圍的最大值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin  
 進度列的目前會傳回最小範圍值。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前範圍的最小值。  
  
##  <a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode  
 指定是否在無限模式工作進度列。  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果進度列為無限的模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 在無限模式中，進度列填滿重複從最小值的最大值。 您可以使用無限的模式，表示作業正在進行中，但是完成時間不明。  
  
##  <a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode  
 設定無限的模式中工作的進度列。  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bSet`  
 `TRUE`若要指定無限的模式，進度列否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 通常，如果進度列是無限的模式，它在告訴使用者作業正在進行中，但完成時間不明。 因此，進度列填滿重複從最小值的最大值。  
  
##  <a name="setpos"></a>CMFCRibbonProgressBar::SetPos  
 設定目前進度列的位置。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nPos`  
 指定設定的進度列的位置。  
  
 [輸入] `bRedraw`  
 指定是否應該重新繪製進度列。  
  
### <a name="remarks"></a>備註  
 正在設定的範圍必須是所指定的範圍內[CMFCRibbonProgressBar::SetRange](#setrange)方法。  
  
##  <a name="setrange"></a>CMFCRibbonProgressBar::SetRange  
 設定進度列的最小和最大值。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nMin`  
 指定範圍的最小值。  
  
 [輸入] `nMax`  
 指定範圍的最大值。  
  
### <a name="remarks"></a>備註  
 使用這個方法來定義進度列範圍，藉由設定 最小和最大值。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
