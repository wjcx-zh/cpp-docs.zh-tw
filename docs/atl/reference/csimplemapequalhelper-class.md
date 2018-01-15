---
title: "CSimpleMapEqualHelper 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs: C++
helpviewer_keywords: CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecc32dc8e6e9b249b0b8b334ec3d08bf26cbd1ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 Value 元素中。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|（靜態）測試兩個索引鍵相等。|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|（靜態）測試兩個值相等。|  
  
## <a name="remarks"></a>備註  
 這個特性類別是補強`CSimpleMap`類別。 它提供方法來比較兩個`CSimpleMap`物件是否相等的項目 （具體而言，索引鍵和值元件）。 根據預設，索引鍵和值會使用比較`operator==()`，但如果對應包含沒有自己的等號比較運算子的複雜資料型別，這個類別可以覆寫來提供額外需要的功能。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey  
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
 如果索引鍵相等，false 否則，就會傳回 true。  
  
##  <a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue  
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
 如果值相等，false 否則，就會傳回 true。  
  
## <a name="see-also"></a>請參閱  
 [CSimpleMapEqualHelperFalse 類別](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
