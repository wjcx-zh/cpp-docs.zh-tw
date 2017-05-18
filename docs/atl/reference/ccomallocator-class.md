---
title: "CComAllocator 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: d395d347e81b24462a41de5ae3b9d8791d7f82fd
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomallocator-class"></a>CComAllocator 類別
這個類別會提供用來管理記憶體使用 COM 記憶體常式方法。  
  
## <a name="syntax"></a>語法  
  
```
class CComAllocator
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|呼叫這個靜態方法，以配置記憶體。|  
|[CComAllocator::Free](#free)|呼叫這個靜態方法來釋放已配置的記憶體。|  
|[CComAllocator::Reallocate](#reallocate)|呼叫這個靜態方法，以重新配置記憶體。|  
  
## <a name="remarks"></a>備註  
 這個類別由[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)提供 COM 記憶體配置常式。 對應項目類別， [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)，提供相同的方法使用 CRT 常式。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="allocate"></a>CComAllocator::Allocate  
 呼叫此靜態函式以配置記憶體。  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 要配置的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回 void 指標至配置的空間，或如果沒有足夠的可用記憶體，則為 NULL。  
  
### <a name="remarks"></a>備註  
 配置記憶體。 請參閱[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)如需詳細資訊。  
  
##  <a name="free"></a>CComAllocator::Free  
 呼叫此靜態函式來釋放已配置的記憶體。  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 配置的記憶體之指標。  
  
### <a name="remarks"></a>備註  
 釋出配置的記憶體。 請參閱[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)如需詳細資訊。  
  
##  <a name="reallocate"></a>CComAllocator::Reallocate  
 呼叫此靜態函式以重新配置記憶體。  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 配置的記憶體之指標。  
  
 `nBytes`  
 要重新配置的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體不足，無法配置的空間，或 NULL 會傳回 void 指標  
  
### <a name="remarks"></a>備註  
 調整配置的記憶體數量。 請參閱[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)   
 [CCRTAllocator 類別](../../atl/reference/ccrtallocator-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

