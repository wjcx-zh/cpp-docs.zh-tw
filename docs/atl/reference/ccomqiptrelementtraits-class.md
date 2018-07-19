---
title: CComQIPtrElementTraits 類別 |Microsoft Docs
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
ms.openlocfilehash: e99299d1232fda75d6b0552b5236a060903a08e5
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879648"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits 類別
當建立 COM 介面指標的集合，這個類別會提供方法、 靜態的函式和實用的 typedef。  
  
## <a name="syntax"></a>語法  
  
```
template<typename I, const IID* piid=& __uuidof(I)>  
class CComQIPtrElementTraits : 
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```  
  
#### <a name="parameters"></a>參數  
 *I*  
 COM 介面，用來指定要儲存的指標的類型。  
  
 *piid*  
 指向 IID*我*。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|  
  
## <a name="remarks"></a>備註  
 此類別衍生的方法，並建立的集合類別時提供有用的 typedef [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM 介面指標物件。 這個類別會利用兩[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)並[CInterfaceList](../../atl/reference/cinterfacelist-class.md)類別。  
  
 如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="inargtype"></a>  CComQIPtrElementTraits::INARGTYPE  
 要用於將項目加入至集合的類別物件的資料類型。  
  
```
typedef I* INARGTYPE;
```  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
