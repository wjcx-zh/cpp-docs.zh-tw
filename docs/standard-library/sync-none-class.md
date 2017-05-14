---
title: "sync_none 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sync_none
- allocators/stdext::sync_none
- stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_none class
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
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
ms.openlocfilehash: f56f09f3c3591d0c969ea3b3e242cf39812356fb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="syncnone-class"></a>sync_none 類別
描述未提供任何同步處理的[同步處理篩選](../standard-library/allocators-header.md)。  
  
## <a name="syntax"></a>語法  
  
```
template <class Cache>  
class sync_none
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Cache`|與同步處理篩選相關聯的快取類型。 這可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocate](#allocate)|配置記憶體區塊。|  
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[equals](#equals)|比較兩個快取是否相等。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="allocate"></a>  sync_none::allocate  
 配置記憶體區塊。  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`count`|陣列中要配置的項目數。|  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 `cache.allocate(count)`，其中 `cache` 是快取物件。  
  
##  <a name="deallocate"></a>  sync_none::deallocate  
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
 成員函式會呼叫 `cache.deallocate(ptr, count)`，其中 `cache` 代表快取物件。  
  
##  <a name="equals"></a>  sync_none::equals  
 比較兩個快取是否相等。  
  
```
bool equals(const sync<Cache>& Other) const;
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Cache`|同步處理篩選的快取物件。|  
|`Other`|要比較是否相等的快取物件。|  
  
### <a name="return-value"></a>傳回值  
 此成員函式一律會傳回 `true`。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




