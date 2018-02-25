---
title: "cache_freelist 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 429b1f60fae11e8ed3fd91fd33ff2e5b9ab131bc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cachefreelist-class"></a>cache_freelist 類別
定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```
template <std::size_t Sz, class Max>  
class cache_freelist
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Sz`|所配置陣列中的元素數。|  
|`Max`|表示可用清單大小上限的 max 類別。 可以是 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|  
  
## <a name="remarks"></a>備註  
 cache_freelist 樣板類別維護一份 `Sz` 大小之記憶體區塊的可用清單。 當可用清單已滿時，它會使用 `operator delete` 解除配置記憶體區塊。 當可用清單為空白時，它會使用 `operator new` 配置新的記憶體區塊。 可用清單的大小上限取決於傳入 `Max` 參數的 max 類別。  
  
 每個記憶體區塊會保留 `Sz` 個位元組的可用記憶體，以及 `operator new` 和 `operator delete` 所需的資料。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[cache_freelist](#cache_freelist)|建構類型 `cache_freelist` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocate](#allocate)|配置記憶體區塊。|  
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="allocate"></a>  cache_freelist::allocate  
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
  
##  <a name="cache_freelist"></a>  cache_freelist::cache_freelist  
 建構類型 `cache_freelist` 的物件。  
  
```
cache_freelist();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="deallocate"></a>  cache_freelist::deallocate  
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
  
## <a name="see-also"></a>請參閱  
 [\<allocators>](../standard-library/allocators-header.md)



