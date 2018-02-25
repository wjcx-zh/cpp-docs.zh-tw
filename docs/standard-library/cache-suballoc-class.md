---
title: "cache_suballoc 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08124225ae5ee0bf7e2575e0eb8cf97a5e683620
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cachesuballoc-class"></a>cache_suballoc 類別
定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```
template <std::size_t Sz, size_t Nelts = 20>  
class cache_suballoc
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Sz`|陣列中要配置的項目數。|  
  
## <a name="remarks"></a>備註  
 cache_suballoc 樣板類別使用 `freelist<sizeof(Type), max_unbounded>` 將已解除配置的記憶體區塊 (Block) 儲存在不限長度的可用清單中，並在可用清單為空白時，對以 `operator new` 配置之較大區塊 (Chunk) 中的記憶體區塊 (Block) 進行子配置。  
  
 每個區塊會保留 `Sz * Nelts` 個位元組的可用記憶體，以及 `operator new` 和 `operator delete` 所需的資料。 永遠不會釋放已配置的區塊。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[cache_suballoc](#cache_suballoc)|建構類型 `cache_suballoc` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocate](#allocate)|配置記憶體區塊。|  
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="allocate"></a>  cache_suballoc::allocate  
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
  
##  <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc  
 建構類型 `cache_suballoc` 的物件。  
  
```
cache_suballoc();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="deallocate"></a>  cache_suballoc::deallocate  
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



