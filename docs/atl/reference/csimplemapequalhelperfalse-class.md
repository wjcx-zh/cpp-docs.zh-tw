---
title: "CSimpleMapEqualHelperFalse 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CSimpleMapEqualHelperFalse
- CSimpleMapEqualHelperFalse
- ATL.CSimpleMapEqualHelperFalse
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: 19
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
ms.openlocfilehash: 68a08ffc0ba126c523a779e3d1a72217dead6235
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 類別
這個類別是 helper [CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|（靜態）測試兩個索引鍵相等。|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|（靜態）傳回 false。|  
  
## <a name="remarks"></a>備註  
 此特性類別是補充`CSimpleMap`類別。 它提供方法來比較兩個項目中包含`CSimpleMap`物件，特別是兩個值項目或兩個索引鍵的項目。  
  
 數值比較一定會傳回 false，並另外，會呼叫`ATLASSERT`是 false，如果曾被參考的引數。 在等號比較測試未充分定義所在的情況下，這個類別可讓對應，其包含索引鍵/值配對的大部分方法正確運作，但在定義完善的方式，例如視比較的方法失敗[CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpcoll.h  
  
##  <a name="a-nameisequalkeya--csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey  
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
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)。  
  
##  <a name="a-nameisequalvaluea--csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue  
 傳回 false。  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法一律傳回 false，並將呼叫`ATLASSERT`是 false，如果曾被參考的引數。 目的`CSimpleMapEqualHelperFalse::IsEqualValue`是強制使用等號比較測試沒有充分定義完善的方式失敗的比較方法。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleMapEqualHelper 類別](../../atl/reference/csimplemapequalhelper-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

