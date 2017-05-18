---
title: "CD2DSizeF 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF class
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f780dc919f102023f2bd524fa69e73e76feec02b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dsizef-class"></a>CD2DSizeF 類別
D2D1_SIZE_F 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|多載。 建構`CD2DSizeF`物件從`D2D1_SIZE_F`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSizeF::IsNull](#isnull)|傳回`boolean`值，指出運算式是否包含任何有效的資料 ( `null`)。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSizeF::operator CSize](#operator_csize)|將轉換`CD2DSizeF`到`CSize`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF  
 建構 CD2DSizeF 物件從 CSize 物件。  
  
```  
CD2DSizeF(const CSize& size);  
CD2DSizeF(const D2D1_SIZE_F& size);  
  CD2DSizeF(const D2D1_SIZE_F* size);

 
CD2DSizeF(
    FLOAT cx = 0.,  
    FLOAT cy = 0.);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 來源大小  
  
 `cx`  
 來源寬度  
  
 `cy`  
 來源高度  
  
##  <a name="isnull"></a>CD2DSizeF::IsNull  
 傳回布林值，指出運算式是否包含任何有效的資料 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是空的; 的寬度和高度，則為 TRUE。否則為 FALSE。  
  
##  <a name="operator_csize"></a>CD2DSizeF::operator CSize  
 將 CD2DSizeF 轉換 CSize 物件。  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>傳回值  
 目前 D2D 大小的值。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

