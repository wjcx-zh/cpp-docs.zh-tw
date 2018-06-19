---
title: CDefaultCompareTraits 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5b06bf475c60c0190fc6ab78f4357e1b247f1d8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361635"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 類別
這個類別會提供預設的比較函式項目。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CDefaultCompareTraits
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](#compareelements)|（靜態）呼叫此函式可比較兩個項目相等。|  
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|（靜態）呼叫此函式可判斷大於且較少的項目。|  
  
## <a name="remarks"></a>備註  
 這個類別包含兩個靜態函式來比較項目儲存在集合類別物件。 這個類別使用[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements  
 呼叫此函式可比較兩個項目相等。  
  
```
static bool CompareElements(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>參數  
 `element1`  
 第一個元素。  
  
 `element2`  
 第二個項目中。  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作是等號比較 ( `==`) 運算子。 物件的簡單資料類型以外，此函式可能需要覆寫。  
  
##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered  
 呼叫此函式可判斷大於且較少的項目。  
  
```
static int CompareElementsOrdered(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>參數  
 `element1`  
 第一個元素。  
  
 `element2`  
 第二個項目中。  
  
### <a name="return-value"></a>傳回值  
 傳回整數，根據下表：  
  
|條件|傳回值|  
|---------------|------------------|  
|`element1` < `element2`|<0|  
|`element1` == `element2`|0|  
|`element1` > `element2`|>0|  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會使用`==`， **\<**，和**>** 運算子。 物件的簡單資料類型以外，此函式可能需要覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
