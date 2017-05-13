---
title: "max_none 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- max_none
- stdext::max_none
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs:
- C++
helpviewer_keywords:
- max_none class
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a8d3380f89f3bd25be0c23e719dfa94df5539ae4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="maxnone-class"></a>max_none 類別
描述 [max 類別](../standard-library/allocators-header.md)物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為零。  
  
## <a name="syntax"></a>語法  
  
```
template <std::size_t Max>  
class max_none
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Max`|max 類別，可決定要在 `freelist` 中儲存的元素數目上限。|  
  
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
  
##  <a name="allocated"></a>  max_none::allocated  
 遞增已配置的記憶體區塊計數。  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`_Nx`|遞增值。|  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每次 `cache_freelist::allocate` 成功呼叫運算子 `new` 之後，都會呼叫它。 引數 `_Nx` 是運算子 `new` 所配置之區塊中的記憶體區塊數目。  
  
##  <a name="deallocated"></a>  max_none::deallocated  
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
  
##  <a name="full"></a>  max_none::full  
 傳回指定是否應該為可用清單新增更多記憶體區塊的值。  
  
```
bool full();
```  
  
### <a name="return-value"></a>傳回值  
 此成員函式一律會傳回 `true`。  
  
### <a name="remarks"></a>備註  
 此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果此呼叫傳回 `true`，`deallocate` 便會將記憶體區塊放到可用清單上，如果傳回 false，`deallocate` 則會呼叫運算子 `delete` 來將區塊解除配置。  
  
##  <a name="released"></a>  max_none::released  
 遞減可用清單上的記憶體區塊計數。  
  
```
void released();
```  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 max 類別的 `released` 成員函式。  
  
##  <a name="saved"></a>  max_none::saved  
 遞增可用清單上的記憶體區塊計數。  
  
```
void saved();
```  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫它。  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




