---
title: "CSimpleArrayEqualHelper 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4a87879683257c66de5fe4e720dd29fa4c47031d
ms.lasthandoff: 02/24/2017

---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper 類別
這個類別是 helper [CSimpleArray](../../atl/reference/csimplearray-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 在衍生的類別中。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|（靜態）測試兩個`CSimpleArray`物件項目是否相等。|  
  
## <a name="remarks"></a>備註  
 此特性類別是補充`CSimpleArray`類別。 它提供一種方法，比較兩個項目儲存在`CSimpleArray`物件。 根據預設，項目都會比較使用**operator=()**，但是如果沒有自己的等號比較運算子的複雜資料型別陣列，您必須覆寫這個類別。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
 測試兩個`CSimpleArray`物件項目是否相等。  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>參數  
 *t1*  
 型別 t 物件  
  
 *t2*  
 型別 t 物件  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleArray 類別](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse 類別](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

