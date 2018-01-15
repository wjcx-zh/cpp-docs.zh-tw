---
title: "CMFCDragFrameImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CMFCDragFrameImpl
dev_langs: C++
helpviewer_keywords: CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55cac28633b87ab8c103904f70b0d88269ffe02f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 類別
`CMFCDragFrameImpl`類別繪製使用者以標準停駐模式拖曳窗格時出現的拖曳矩形。  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>語法  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>備註  
 這個類別的物件會在每個內嵌[CPane 類別](../../mfc/reference/cpane-class.md)物件。 因此，會使用每個窗格`CanFloat`方法會在使用者拖曳時，會顯示拖曳矩形。  
  
 您可以控制的拖曳矩形的寬度，使用 [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat]--brokenlink--(afx-global-data-structure.md#m_ndragframethicknessfloat) 和[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bClearInternalRects`  
  
### <a name="remarks"></a>備註  
  
##  <a name="init"></a>CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDraggedWnd`  
  
### <a name="remarks"></a>備註  
  
##  <a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bForceMove`  
  
### <a name="remarks"></a>備註  
  
##  <a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pTabbedBar`  
 [輸入] `bFirstTime`  
 [輸入] `pCBarToPlaceOn`  
  
### <a name="remarks"></a>備註  
  
##  <a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pOldTargetBar`  
  
### <a name="remarks"></a>備註  
  
##  <a name="resetstate"></a>CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane 類別](../../mfc/reference/cpane-class.md)