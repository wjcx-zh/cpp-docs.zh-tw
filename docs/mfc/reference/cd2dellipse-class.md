---
title: CD2DEllipse 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
dev_langs:
- C++
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4c4a801952c6b29779c381237c291232ce2ef25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cd2dellipse-class"></a>CD2DEllipse 類別
`D2D1_ELLIPSE` 的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DEllipse : public D2D1_ELLIPSE;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|多載。 建構`CD2DEllipse`物件從`D2D1_ELLIPSE`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_ELLIPSE`  
  
 `CD2DEllipse`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse  
 建構來自 CD2DRectF 物件 CD2DEllipse 物件。  
  
```  
CD2DEllipse(const CD2DRectF& rect);  
CD2DEllipse(const D2D1_ELLIPSE& ellipse);  
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);

 
CD2DEllipse(
    const CD2DPointF& ptCenter,  
    const CD2DSizeF& sizeRadius);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 來源矩形  
  
 `ellipse`  
 來源橢圓形  
  
 `ptCenter`  
 橢圓形的中心點。  
  
 `sizeRadius`  
 X 半徑和橢圓形的 Y 半徑。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
