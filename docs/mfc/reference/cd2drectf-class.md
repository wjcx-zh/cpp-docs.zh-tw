---
title: "CD2DRectF 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs: C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b0919780e4fcad86772892bb0b300a735df81e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cd2drectf-class"></a>CD2DRectF 類別
`D2D1_RECT_F`的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](#cd2drectf)|多載。 建構`CD2DRectF`物件從`D2D1_RECT_F`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|傳回`boolean`值，指出運算式是否包含任何有效的資料 ( `null`)。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRectF::operator CRect](#operator_crect)|將轉換`CD2DRectF`至`CRect`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>CD2DRectF::CD2DRectF  
 建構來自 CRect 物件 CD2DRectF 物件。  
  
```  
CD2DRectF(const CRect& rect);  
CD2DRectF(const D2D1_RECT_F& rect);  
  CD2DRectF(const D2D1_RECT_F* rect);

 
CD2DRectF(
    FLOAT fLeft = 0.,  
    FLOAT fTop = 0.,  
    FLOAT fRight = 0.,  
    FLOAT fBottom = 0.);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 來源矩形  
  
 `fLeft`  
 來源左方的座標  
  
 `fTop`  
 來源的上方座標  
  
 `fRight`  
 來源右方座標  
  
 `fBottom`  
 來源下方座標  
  
##  <a name="isnull"></a>CD2DRectF::IsNull  
 傳回布林值，指出運算式是否包含任何有效的資料 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>傳回值  
 矩形的頂端、 左邊、 下框線和右值所有等於 0; 如果為 TRUE否則為 FALSE。  
  
##  <a name="operator_crect"></a>CD2DRectF::operator CRect  
 將 CD2DRectF 轉換 CRect 物件。  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>傳回值  
 D2D 矩形的目前值。  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
