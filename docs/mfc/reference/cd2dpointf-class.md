---
title: "CD2DPointF 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointF class
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
caps.latest.revision: 18
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
ms.openlocfilehash: 8449fcadfb72305e9e5b6ed2c6829ba9963ba7ca
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dpointf-class"></a>CD2DPointF 類別
`D2D1_POINT_2F`的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DPointF : public D2D1_POINT_2F;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DPointF::CD2DPointF](#cd2dpointf)|多載。 建構`CD2DPointF`物件從`D2D1_POINT_2F`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DPointF::operator CPoint](#operator_cpoint)|將轉換`CD2DPointF`到`CPoint`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_POINT_2F`  
  
 `CD2DPointF`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="cd2dpointf"></a>CD2DPointF::CD2DPointF  
 建構 CD2DPointF 物件從 CPoint 物件。  
  
```  
CD2DPointF(const CPoint& pt);    
CD2DPointF(const D2D1_POINT_2F& pt);    
CD2DPointF(const D2D1_POINT_2F* pt); 
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 來源點  
  
 `fX`  
 來源 X  
  
 `fY`  
 來源 Y  
  
##  <a name="operator_cpoint"></a>CD2DPointF::operator CPoint  
 將 CD2DPointF 轉換 CPoint 物件。  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>傳回值  
 D2D 點的目前值。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

