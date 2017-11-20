---
title: "CElementTraitsBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs: C++
helpviewer_keywords: CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d0201ecd971b13b69e210b356ba9192bfdc89a54
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 類別
這個類別會提供預設複製並移動的集合類別的方法。  
  
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
|[CElementTraitsBase::INARGTYPE](#inargtype)|要用來將項目加入至集合的類別物件的資料類型。|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|呼叫此方法以複製項目儲存在集合類別物件。|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|呼叫這個方法，即可重新定位項目儲存在集合類別物件。|  
  
## <a name="remarks"></a>備註  
 這個基底類別會定義用於複製和重新定位項目中的集合類別的方法。 利用由類別[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)， [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)，和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 呼叫此方法以複製項目儲存在集合類別物件。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 將接收複製的資料的第一個元素的指標。  
  
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
 用來從集合擷取項目的資料類型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 呼叫這個方法，即可重新定位項目儲存在集合類別物件。  
  
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
 第一個項目，即可重新定位指標。  
  
 `nElements`  
 重新定位的項目數目。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，即足以應付大多數的資料類型。 如果要移動的物件包含它們自己的成員的指標，必須覆寫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
