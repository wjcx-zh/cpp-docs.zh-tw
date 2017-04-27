---
title: "cache_suballoc 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_suballoc
- stdext::cache_suballoc
- cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs:
- C++
helpviewer_keywords:
- cache_suballoc class
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 537930868e47fd1e947a99ff808d870532c38c58
ms.lasthandoff: 02/24/2017

---
# <a name="cachesuballoc-class"></a>cache_suballoc 類別
定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```
template <std::size_t Sz, size_t Nelts = 20>  
class cache_suballoc
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Sz`|陣列中要配置的項目數。|  
  
## <a name="remarks"></a>備註  
 cache_suballoc 樣板類別使用 `freelist<sizeof(Type), max_unbounded>` 將已解除配置的記憶體區塊 (Block) 儲存在不限長度的可用清單中，並在可用清單為空白時，對以 `operator new` 配置之較大區塊 (Chunk) 中的記憶體區塊 (Block) 進行子配置。  
  
 每個區塊會保留 `Sz * Nelts` 個位元組的可用記憶體，以及 `operator new` 和 `operator delete` 所需的資料。 永遠不會釋放已配置的區塊。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[cache_suballoc](#cache_suballoc__cache_suballoc)|建構類型 `cache_suballoc` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocate](#cache_suballoc__allocate)|配置記憶體區塊。|  
|[deallocate](#cache_suballoc__deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="cache_suballoc__allocate"></a>  cache_suballoc::allocate  
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
  
##  <a name="cache_suballoc__cache_suballoc"></a>  cache_suballoc::cache_suballoc  
 建構類型 `cache_suballoc` 的物件。  
  
```
cache_suballoc();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="cache_suballoc__deallocate"></a>  cache_suballoc::deallocate  
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
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




