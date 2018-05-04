---
title: CComQIPtrElementTraits 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9122431d0d71d33406250a624048dbede46fd387
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits 類別
建立 COM 介面指標的集合時，這個類別會提供方法、 靜態函式和有用的 typedef。  
  
## <a name="syntax"></a>語法  
  
```
template<typename I, const IID* piid=& __uuidof(I)>  
class CComQIPtrElementTraits : 
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```  
  
#### <a name="parameters"></a>參數  
 `I`  
 指定要儲存的指標類型的 COM 介面。  
  
 `piid`  
 指向 IID 的`I`。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|要用來將項目加入至集合的類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 這個類別衍生方法，並建立的集合類別時，提供有用的 typedef [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM 介面指標物件。 這個類別同時利用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)和[CInterfaceList](../../atl/reference/cinterfacelist-class.md)類別。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="inargtype"></a>  CComQIPtrElementTraits::INARGTYPE  
 要用來將項目加入至集合的類別物件的資料類型。  
  
```
typedef I* INARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
