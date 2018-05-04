---
title: CSimpleArrayEqualHelper 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6660f72dbd91a41670b3c5f8772d21caf4b8abc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|（靜態）測試兩個`CSimpleArray`物件項目是否相等。|  
  
## <a name="remarks"></a>備註  
 這個特性類別是補強`CSimpleArray`類別。 它提供一種方法，比較兩個項目儲存在`CSimpleArray`物件。 根據預設，項目會比較使用**operator=()**，但如果陣列包含沒有自己的等號比較運算子的複雜資料型別，您就必須覆寫這個類別。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpcoll.h  
  
##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual  
 測試兩個`CSimpleArray`物件項目是否相等。  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>參數  
 *T1*  
 類型 t 的物件  
  
 *T2*  
 類型 t 的物件  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleArray 類別](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse 類別](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
