---
title: "max_fixed_size 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_fixed_size
- max_fixed_size
- stdext::max_fixed_size
- stdext.max_fixed_size
dev_langs:
- C++
helpviewer_keywords:
- max_fixed_size class
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c1d83d147fc163a8747a68baff16b1fa1401902b
ms.lasthandoff: 02/24/2017

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
|[max_fixed_size](#max_fixed_size__max_fixed_size)|建構類型 `max_fixed_size` 的物件。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[allocated](#max_fixed_size__allocated)|遞增已配置的記憶體區塊計數。|  
|[deallocated](#max_fixed_size__deallocated)|遞減已配置的記憶體區塊計數。|  
|[full](#max_fixed_size__full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|  
|[released](#max_fixed_size__released)|遞減可用清單上的記憶體區塊計數。|  
|[saved](#max_fixed_size__saved)|遞增可用清單上的記憶體區塊計數。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="a-namemaxfixedsizeallocateda--maxfixedsizeallocated"></a><a name="max_fixed_size__allocated"></a>  max_fixed_size::allocated  
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
  
##  <a name="a-namemaxfixedsizedeallocateda--maxfixedsizedeallocated"></a><a name="max_fixed_size__deallocated"></a>  max_fixed_size::deallocated  
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
  
##  <a name="a-namemaxfixedsizefulla--maxfixedsizefull"></a><a name="max_fixed_size__full"></a>  max_fixed_size::full  
 傳回指定是否應該為可用清單新增更多記憶體區塊的值。  
  
```
bool full();
```  
  
### <a name="return-value"></a>傳回值  
 如果是 `Max <= _Nblocks`，則為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果此呼叫傳回 `true`，`deallocate` 便會將記憶體區塊放到可用清單上，如果傳回 false，`deallocate` 則會呼叫運算子 `delete` 來將區塊解除配置。  
  
##  <a name="a-namemaxfixedsizemaxfixedsizea--maxfixedsizemaxfixedsize"></a><a name="max_fixed_size__max_fixed_size"></a>  max_fixed_size::max_fixed_size  
 建構類型 `max_fixed_size` 的物件。  
  
```
max_fixed_size();
```  
  
### <a name="remarks"></a>備註  
 此建構函式會將預存值 `_Nblocks` 初始化為零。  
  
##  <a name="a-namemaxfixedsizereleaseda--maxfixedsizereleased"></a><a name="max_fixed_size__released"></a>  max_fixed_size::released  
 遞減可用清單上的記憶體區塊計數。  
  
```
void released();
```  
  
### <a name="remarks"></a>備註  
 遞減預存值 `_Nblocks`。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 [max 類別](../standard-library/allocators-header.md)的 `released` 成員函式。  
  
##  <a name="a-namemaxfixedsizesaveda--maxfixedsizesaved"></a><a name="max_fixed_size__saved"></a>  max_fixed_size::saved  
 遞增可用清單上的記憶體區塊計數。  
  
```
void saved();
```  
  
### <a name="remarks"></a>備註  
 此成員函式會遞增預存值 `_Nblocks`。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫此成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




