---
title: "CPrimitiveElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
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
ms.openlocfilehash: 44e3849ebf2de09bc9b62e28df0f70bf52ac95e6
ms.lasthandoff: 02/24/2017

---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits 類別
這個類別會提供預設的方法和函式的集合類別的基本資料型別所組成。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 集合類別物件中儲存的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|若要使用項目加入集合類別物件的資料型別。|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|要用來擷取項目從集合類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供預設的靜態函式和方法來移動、 複製、 比較和雜湊儲存在集合類別物件的基本資料型別項目。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE  
 若要使用項目加入集合類別物件的資料型別。  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE  
 要用來擷取項目從集合類別物件的資料類型。  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

