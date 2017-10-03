---
title: "sync_per_thread 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 817f52e11a39de64288c4433b5f29c48ae45ca22
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="syncperthread-class"></a>sync_per_thread 類別
描述可為每個執行緒物件提供不同快取物件的[同步處理篩選](../standard-library/allocators-header.md)。  
  
## <a name="syntax"></a>語法  
  
```
template <class Cache>  
class sync_per_thread
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Cache`|與同步處理篩選相關聯的快取類型。 這可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## <a name="remarks"></a>備註  
 即使無法從另一個執行緒中取消配置某個執行緒中配置的區塊，使用 `sync_per_thread` 的配置器還是可以比較是否相等。 當您使用這其中一個配置器時，其他執行緒應該看不到某個執行緒中配置的記憶體區塊。 實際上，這表示使用這其中一個配置器的容器只能透過單一執行緒來存取。  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocate](#allocate)|配置記憶體區塊。|  
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[equals](#equals)|比較兩個快取是否相等。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="allocate"></a>  sync_per_thread::allocate  
 配置記憶體區塊。  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`count`|陣列中要配置的項目數。|  
  
### <a name="remarks"></a>備註  
 成員函式會在屬於目前執行緒的快取物件上傳回 `cache::allocate(count)` 呼叫的結果。 如果未針對目前的執行緒配置任何快取物件，則它會先配置一個。  
  
##  <a name="deallocate"></a>  sync_per_thread::deallocate  
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
 成員函式會在屬於目前執行緒的快取物件上呼叫 `deallocate`。 如果未針對目前的執行緒配置任何快取物件，則它會先配置一個。  
  
##  <a name="equals"></a>  sync_per_thread::equals  
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
 如果未針對目前的執行緒或目前執行緒中的 `Other` 配置任何快取物件，即會傳回 `false`。 否則會傳回將 `operator==` 套用到這兩個快取物件的結果。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




