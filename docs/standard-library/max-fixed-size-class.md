---
title: "max_fixed_size 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
dev_langs: C++
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a2e91effe6cf13ce7a03f8e69c6d67d622ebdcd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="maxfixedsize-class"></a>max_fixed_size 類別
描述 [max 類別](../standard-library/allocators-header.md)物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為固定值。  
  
## <a name="syntax"></a>語法  
  
```
template <std::size_t Max>  
class max_fixed_size
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Max`|max 類別，可決定要在 `freelist` 中儲存的元素數目上限。|  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[max_fixed_size](#max_fixed_size)|建構類型 `max_fixed_size` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocated](#allocated)|遞增已配置的記憶體區塊計數。|  
|[deallocated](#deallocated)|遞減已配置的記憶體區塊計數。|  
|[full](#full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|  
|[released](#released)|遞減可用清單上的記憶體區塊計數。|  
|[saved](#saved)|遞增可用清單上的記憶體區塊計數。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="allocated"></a>  max_fixed_size::allocated  
 遞增已配置的記憶體區塊計數。  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`_Nx`|遞增值。|  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每次 `cache_freelist::allocate` 成功呼叫運算子 `new` 之後，都會呼叫此成員函式。 引數 `_Nx` 是運算子 `new` 所配置之區塊中的記憶體區塊數目。  
  
##  <a name="deallocated"></a>  max_fixed_size::deallocated  
 遞減已配置的記憶體區塊計數。  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`_Nx`|遞增值。|  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每次 `cache_freelist::deallocate` 呼叫運算子 `delete` 之後，都會呼叫此成員函式。 引數 `_Nx` 是運算子 `delete` 所解除配置之區塊中的記憶體區塊數目。  
  
##  <a name="full"></a>  max_fixed_size::full  
 傳回指定是否應該為可用清單新增更多記憶體區塊的值。  
  
```
bool full();
```  
  
### <a name="return-value"></a>傳回值  
 如果是 `Max <= _Nblocks`，則為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果此呼叫傳回 `true`，`deallocate` 便會將記憶體區塊放到可用清單上，如果傳回 false，`deallocate` 則會呼叫運算子 `delete` 來將區塊解除配置。  
  
##  <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size  
 建構類型 `max_fixed_size` 的物件。  
  
```
max_fixed_size();
```  
  
### <a name="remarks"></a>備註  
 此建構函式會將預存值 `_Nblocks` 初始化為零。  
  
##  <a name="released"></a>  max_fixed_size::released  
 遞減可用清單上的記憶體區塊計數。  
  
```
void released();
```  
  
### <a name="remarks"></a>備註  
 遞減預存值 `_Nblocks`。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 [max 類別](../standard-library/allocators-header.md)的 `released` 成員函式。  
  
##  <a name="saved"></a>  max_fixed_size::saved  
 遞增可用清單上的記憶體區塊計數。  
  
```
void saved();
```  
  
### <a name="remarks"></a>備註  
 此成員函式會遞增預存值 `_Nblocks`。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫此成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)



