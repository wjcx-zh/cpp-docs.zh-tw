---
title: "CD2DSizeU 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeU class
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
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
ms.openlocfilehash: a43ea5448a0b0d09d4cf27eafb01a4d4b610e4f5
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 類別
D2D1_SIZE_U 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DSizeU : public D2D1_SIZE_U;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|多載。 建構`CD2DSizeU`物件從`D2D1_SIZE_U`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSizeU::IsNull](#isnull)|傳回`boolean`值，指出運算式是否包含任何有效的資料 ( `null`)。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DSizeU::operator CSize](#operator_csize)|將轉換`CD2DSizeU`到`CSize`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `D2D1_SIZE_U`  
  
 [CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU  
 建構 CD2DSizeU 物件從 CSize 物件。  
  
```  
CD2DSizeU(const CSize& size);  
CD2DSizeU(const D2D1_SIZE_U& size);  
  CD2DSizeU(const D2D1_SIZE_U* size);

 
CD2DSizeU(
    UINT32 cx = 0,  
    UINT32 cy = 0);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 來源大小  
  
 `cx`  
 來源寬度  
  
 `cy`  
 來源高度  
  
##  <a name="isnull"></a>CD2DSizeU::IsNull  
 傳回布林值，指出運算式是否包含任何有效的資料 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是空的; 的寬度和高度，則為 TRUE。否則為 FALSE。  
  
##  <a name="operator_csize"></a>CD2DSizeU::operator CSize  
 將 CD2DSizeU 轉換 CSize 物件。  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>傳回值  
 目前 D2D 大小的值。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

