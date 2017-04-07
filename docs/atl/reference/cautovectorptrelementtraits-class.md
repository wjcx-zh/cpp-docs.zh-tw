---
title: "CAutoVectorPtrElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
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
ms.openlocfilehash: d7b7418b713993f539f56e70715296d5af265d28
ms.lasthandoff: 02/24/2017

---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits 類別
這個類別提供方法、 靜態函式和 typedef 建立集合的智慧型指標使用向量 new 和 delete 運算子時很有用。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CAutoVectorPtrElementTraits : 
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```    
  
#### <a name="parameters"></a>參數  
 `T`  
 指標類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|若要使用項目加入集合類別物件的資料型別。|  
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取項目從集合類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法、 靜態函式和 typedef 輔助包含智慧型指標的集合類別物件的建立。 不同於[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)，這個類別會使用新的向量和 delete 運算子。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoVectorPtrElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="inargtype"></a>CAutoVectorPtrElementTraits::INARGTYPE  
 若要使用項目加入集合類別物件的資料型別。  
  
```
typedef CAutoVectorPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CAutoVectorPtrElementTraits::OUTARGTYPE  
 要用來擷取項目從集合類別物件的資料類型。  
  
```
typedef T*& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [CAutoVectorPtr 類別](../../atl/reference/cautovectorptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

