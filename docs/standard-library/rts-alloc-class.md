---
title: "rts_alloc 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::rts_alloc
- allocators/stdext::rts_alloc
- rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs:
- C++
helpviewer_keywords:
- rts_alloc class
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: 19
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: fe127f896fa902f4a8cdb44454cf6e4c5f449e79
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="rtsalloc-class"></a>rts_alloc 類別
rts_alloc 樣板類別描述一個[篩選](../standard-library/allocators-header.md)，其可保留快取執行個體的陣列，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。  
  
## <a name="syntax"></a>語法  
  
```
template <class Cache>  
class rts_alloc
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Cache`|包含在陣列中的快取執行個體類型， 這可以是 [cache_chunklist Class](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## <a name="remarks"></a>備註  
 這個樣板類別保留多個區塊配置器執行個體，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。 它會搭配不可編譯重新繫結的編譯器使用。  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocate](#allocate)|配置記憶體區塊。|  
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[equals](#equals)|比較兩個快取是否相等。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="allocate"></a>  rts_alloc::allocate  
 配置記憶體區塊。  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`count`|陣列中要配置的項目數。|  
  
### <a name="return-value"></a>傳回值  
 所配置物件的指標。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 `caches[_IDX].allocate(count)`，其中索引 `_IDX` 是透過要求的區塊大小 `count` 來判斷，或者，如果 `count` 太大，它會傳回 `operator new(count)`。 `cache`，代表快取物件。  
  
##  <a name="deallocate"></a>  rts_alloc::deallocate  
 從指定位置起算的儲存體中，釋放指定數目的物件。  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`ptr`|要從儲存體解除配置之第一個物件的指標。|  
|`count`|要從儲存空間解除配置的物件數目。|  
  
### <a name="remarks"></a>備註  
 成員函式會呼叫 `caches[_IDX].deallocate(ptr, count)`，其中索引 `_IDX` 是透過要求的區塊大小 `count` 來判斷，或者，如果 `count` 太大，它會傳回 `operator delete(ptr)`。  
  
##  <a name="equals"></a>  rts_alloc::equals  
 比較兩個快取是否相等。  
  
```
bool equals(const sync<_Cache>& _Other) const;
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`_Cache`|與篩選條件相關聯的快取物件。|  
|`_Other`|要比較是否相等的快取物件。|  
  
### <a name="remarks"></a>備註  
 若結果是 `caches[0].equals(other.caches[0])`，即為 `true`，否則為 `false`。 `caches` 代表快取物件的陣列。  
  
## <a name="see-also"></a>另請參閱  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)   
 [\<allocators>](../standard-library/allocators-header.md)




