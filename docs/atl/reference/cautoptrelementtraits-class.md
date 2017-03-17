---
title: "CAutoPtrElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 1c543eaa678d86e083207915bcb4f43766ee23c5
ms.lasthandoff: 02/24/2017

---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits 類別
建立集合的智慧型指標時，這個類別會提供方法、 靜態函式和有用的 typedef。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CAutoPtrElementTraits 
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```    
  
#### <a name="parameters"></a>參數  
 `T`  
 指標類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|若要使用項目加入集合類別物件的資料型別。|  
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取項目從集合類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法、 靜態函式和 typedef 輔助包含智慧型指標的集合類別物件的建立。 類別[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)衍生自`CAutoPtrElementTraits`。 如果建置智慧型指標的集合，需要新的向量和 delete 運算子，請使用[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)改。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE  
 若要使用項目加入集合類別物件的資料型別。  
  
```
typedef CAutoPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE  
 要用來擷取項目從集合類別物件的資料類型。  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

