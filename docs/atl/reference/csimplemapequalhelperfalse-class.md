---
title: CSimpleMapEqualHelperFalse 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bebd9c6628924b5927fb48518925bdd665b0ee14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 類別
這個類別是 helper [CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|（靜態）測試兩個索引鍵相等。|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|（靜態）傳回 false。|  
  
## <a name="remarks"></a>備註  
 這個特性類別是補強`CSimpleMap`類別。 它提供方法來比較兩個項目中包含`CSimpleMap`物件，特別是兩個值項目或兩個索引鍵的項目。  
  
 值比較永遠會傳回 false，而且此外，會呼叫`ATLASSERT`false 曾經正在參考它的引數。 在等號比較測試未充分定義所在的情況下，這個類別可讓對應，其包含要對於大部分方法正確運作，但以妥善定義的方式，例如視比較的方法失敗的索引鍵/值組[CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey  
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
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)。  
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue  
 傳回 false。  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法一律會傳回 false，並將呼叫`ATLASSERT`false 曾經正在參考它的引數。 目的`CSimpleMapEqualHelperFalse::IsEqualValue`是強制方法使用的比較時沒有充分定義等號比較測試，以妥善定義的方式失敗。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleMapEqualHelper 類別](../../atl/reference/csimplemapequalhelper-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
