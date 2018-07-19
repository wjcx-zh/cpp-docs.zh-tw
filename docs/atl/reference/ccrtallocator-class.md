---
title: CCRTAllocator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f026610469c75f37e49df6f42358a3ff378cb0e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879581"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator 類別
這個類別提供方法來管理使用 CRT 記憶體常式的記憶體。  
  
## <a name="syntax"></a>語法  
  
```
class ATL::CCRTAllocator
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ccrtallocator:: Allocate](#allocate)|（靜態）呼叫這個方法來配置記憶體。|  
|[Ccrtallocator:: Free](#free)|（靜態）呼叫這個方法來釋放記憶體。|  
|[Ccrtallocator:: Reallocate](#reallocate)|（靜態）呼叫這個方法來重新配置記憶體。|  
  
## <a name="remarks"></a>備註  
 此類別由[CHeapPtr](../../atl/reference/cheapptr-class.md)提供 CRT 記憶體配置常式。 對應類別[CComAllocator](../../atl/reference/ccomallocator-class.md)，提供相同的方法使用 COM 常式。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
##  <a name="allocate"></a>  Ccrtallocator:: Allocate  
 呼叫此靜態函式以配置記憶體。  
  
```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 *nBytes*  
 要配置的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回 void 指標至配置的空間，或如果沒有足夠的可用記憶體，則為 NULL。  
  
### <a name="remarks"></a>備註  
 配置記憶體。 請參閱[malloc](../../c-runtime-library/reference/malloc.md)如需詳細資訊。  
  
##  <a name="free"></a>  Ccrtallocator:: Free  
 呼叫此靜態函式來釋放記憶體。  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 配置的記憶體之指標。  
  
### <a name="remarks"></a>備註  
 釋放配置的記憶體。 請參閱[免費](../../c-runtime-library/reference/free.md)如需詳細資訊。  
  
##  <a name="reallocate"></a>  Ccrtallocator:: Reallocate  
 呼叫此靜態函式以重新配置記憶體。  
  
```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 配置的記憶體之指標。  
  
 *nBytes*  
 要重新配置的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回 void 指標至配置的空間，或如果沒有足夠的記憶體，則為 NULL。  
  
### <a name="remarks"></a>備註  
 調整配置的記憶體數量。 請參閱[realloc](../../c-runtime-library/reference/realloc.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
 [CComAllocator 類別](../../atl/reference/ccomallocator-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
