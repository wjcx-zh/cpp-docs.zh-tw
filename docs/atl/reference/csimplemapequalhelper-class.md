---
title: "CSimpleMapEqualHelper 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: ddb793889748446b9613c91ce6fcefe28da32eb3
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper 類別
這個類別是 helper [CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```  
  
#### <a name="parameters"></a>參數  
 `TKey`  
 索引鍵的項目。  
  
 `TVal`  
 值的項目。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|（靜態）測試兩個索引鍵相等。|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|（靜態）測試兩個值相等。|  
  
## <a name="remarks"></a>備註  
 此特性類別是補充`CSimpleMap`類別。 它提供方法來比較兩個`CSimpleMap`物件是否相等的項目 （特別是，索引鍵和值元件）。 根據預設，索引鍵和值會使用比較`operator==()`，但如果對應包含沒有自己的等號比較運算子的複雜資料型別，這個類別可以覆寫來提供額外需要的功能。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpcoll.h  
  
##  <a name="a-nameisequalkeya--csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey  
 測試兩個索引鍵相等。  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>參數  
 `k1`  
 第一個索引鍵。  
  
 `k2`  
 第二個索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果索引鍵相等，false 否則傳回 true。  
  
##  <a name="a-nameisequalvaluea--csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue  
 測試兩個值相等。  
  
```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```  
  
### <a name="parameters"></a>參數  
 *v1*  
 第一個值。  
  
 *v2*  
 第二個值。  
  
### <a name="return-value"></a>傳回值  
 如果值相等，false 否則傳回 true。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleMapEqualHelperFalse 類別](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

