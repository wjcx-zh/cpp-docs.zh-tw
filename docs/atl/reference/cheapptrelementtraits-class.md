---
title: "CHeapPtrElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: cf442a47a8f7f56a9563b73d03224165248232d5
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits 類別
建立集合的堆積指標時，這個類別會提供方法、 靜態函式和有用的 typedef。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要儲存於集合類別的物件類型。  
  
 `Allocator`  
 要使用的記憶體配置類別。 預設值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|若要使用項目加入集合類別物件的資料型別。|  
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取項目從集合類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法、 靜態函式和 typedef 輔助包含堆積的指標集合類別物件的建立。 類別`CHeapPtrList`衍生自`CHeapPtrElementTraits`。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="inargtype"></a>CHeapPtrElementTraits::INARGTYPE  
 若要使用項目加入集合類別物件的資料型別。  
  
```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CHeapPtrElementTraits::OUTARGTYPE  
 要用來擷取項目從集合類別物件的資料類型。  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

