---
title: "CElementTraitsBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: a06af7698afb24c1c2391b762673c7e3633018d4
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 類別
這個類別會提供預設複製和移動集合類別的方法。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|若要使用項目加入集合類別物件的資料型別。|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|要用來擷取項目從集合類別物件的資料類型。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|呼叫這個方法來複製集合類別物件中儲存項目。|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|呼叫這個方法重新定位項目儲存在集合類別物件。|  
  
## <a name="remarks"></a>備註  
 這個基底類別會定義方法複製和重新配置的集合類別中的項目。 類別使用[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)， [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)，和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 呼叫這個方法來複製集合類別物件中儲存項目。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 接收複製的資料的第一個元素的指標。  
  
 `pSrc`  
 若要複製的第一個元素的指標。  
  
 `nElements`  
 要複製的項目數目。  
  
### <a name="remarks"></a>備註  
 來源和目的地的項目不應該重疊。  
  
##  <a name="inargtype"></a>CElementTraitsBase::INARGTYPE  
 要用來將項目加入至集合的資料類型。  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE  
 要用來從集合擷取項目資料型別。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 呼叫這個方法重新定位項目儲存在集合類別物件。  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 將會收到重新配置的資料的第一個元素的指標。  
  
 `pSrc`  
 若要重新配置的第一個元素的指標。  
  
 `nElements`  
 重新定位項目數目。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，即足以應付大部分的資料類型。 如果要移動的物件包含它們自己的成員的指標，此方法必須覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

