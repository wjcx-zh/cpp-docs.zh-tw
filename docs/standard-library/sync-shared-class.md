---
title: "sync_shared 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aea3f774ecfff03e3c9738cf948f95d76773f063
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="syncshared-class"></a>sync_shared 類別
描述的[同步處理篩選](../standard-library/allocators-header.md)會使用 mutex 來控制對所有配置器所共用之快取物件的存取。  
  
## <a name="syntax"></a>語法  
  
```
template <class Cache>  
class sync_shared
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
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
  
##  <a name="allocate"></a>  sync_shared::allocate  
 配置記憶體區塊。  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`count`|所配置陣列中的元素數。|  
  
### <a name="return-value"></a>傳回值  
 所配置物件的指標。  
  
### <a name="remarks"></a>備註  
 成員函式會鎖定 mutex、呼叫 `cache.allocate(count)`、解除鎖定 mutex，然後傳回之前呼叫 `cache.allocate(count)` 的結果。 `cache`，代表目前的快取物件。  
  
##  <a name="deallocate"></a>  sync_shared::deallocate  
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
 此成員函式會鎖定 mutex、呼叫 `cache.deallocate(ptr, count)` (其中 `cache` 代表快取物件)，然後解除鎖定 mutex。  
  
##  <a name="equals"></a>  sync_shared::equals  
 比較兩個快取是否相等。  
  
```
bool equals(const sync_shared<Cache>& Other) const;
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Cache`|與同步處理篩選相關聯的快取類型。|  
|`Other`|要比較是否相等的快取。|  
  
### <a name="return-value"></a>傳回值  
 如果 `cache.equals(Other.cache)` 的結果 (其中 `cache` 代表快取物件) 是 `true`，即為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [\<allocators>](../standard-library/allocators-header.md)



