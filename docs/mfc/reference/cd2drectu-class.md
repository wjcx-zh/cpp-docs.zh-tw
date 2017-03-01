---
title: "CD2DRectU 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectU
- afxrendertarget/CD2DRectU
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU class
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
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
ms.openlocfilehash: 74c05d7f4be9b9308cdcb2b91a0455a4cd025dc1
ms.lasthandoff: 02/24/2017

---
# <a name="cd2drectu-class"></a>CD2DRectU 類別
`D2D1_RECT_U`的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DRectU::CD2DRectU](#cd2drectu)|多載。 建構`CD2DRectU`物件從`D2D1_RECT_U`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRectU::IsNull](#isnull)|傳回`boolean`值，指出運算式是否包含任何有效的資料 ( `null`)。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRectU::operator CRect](#operator_crect)|將轉換`CD2DRectU`到`CRect`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_RECT_U`  
  
 `CD2DRectU`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="a-namecd2drectua--cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU::CD2DRectU  
 建構 CD2DRectU 物件從 CRect 物件。  
  
```  
CD2DRectU(const CRect& rect);  
CD2DRectU(const D2D1_RECT_U& rect);  
  CD2DRectU(const D2D1_RECT_U* rect);

 
CD2DRectU(
    UINT32 uLeft = 0,  
    UINT32 uTop = 0,  
    UINT32 uRight = 0,  
    UINT32 uBottom = 0);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 來源矩形  
  
 `uLeft`  
 來源左方的座標  
  
 `uTop`  
 來源上方座標  
  
 `uRight`  
 來源右座標  
  
 `uBottom`  
 來源下方座標  
  
##  <a name="a-nameisnulla--cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU::IsNull  
 傳回布林值，指出運算式是否包含任何有效的資料 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>傳回值  
 矩形的上方、 左側、 底端和正確的值是否設為 0，所有相等，則為 TRUE。否則為 FALSE。  
  
##  <a name="a-nameoperatorcrecta--cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::operator CRect  
 將 CD2DRectU 轉換 CRect 物件。  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>傳回值  
 D2D 矩形的目前值。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

