---
title: "CAutoVectorPtrElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
dev_langs: C++
helpviewer_keywords: CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 59aaaa19d696099c45d4b25f4c41f1cedf97a255
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits 類別
這個類別會提供方法、 靜態函式和建立使用新的向量的智慧型指標的集合和 delete 運算子時非常實用的 typedef。  
  
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
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|要用來將項目加入至集合的類別物件的資料類型。|  
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法，靜態函式和 typedef 達到包含智慧型指標集合類別物件的建立。 不同於[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)，這個類別會使用新的向量和 delete 運算子。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoVectorPtrElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="inargtype"></a>CAutoVectorPtrElementTraits::INARGTYPE  
 要用來將項目加入至集合的類別物件的資料類型。  
  
```
typedef CAutoVectorPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CAutoVectorPtrElementTraits::OUTARGTYPE  
 要用來擷取元素的集合類別物件的資料類型。  
  
```
typedef T*& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [CAutoVectorPtr 類別](../../atl/reference/cautovectorptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
