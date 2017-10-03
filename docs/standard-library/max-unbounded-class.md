---
title: "max_unbounded 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: 18
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 499032343c20c308c2e2820420c725c8d6d43fee
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="maxunbounded-class"></a>max_unbounded 類別
描述 [max 類別](../standard-library/allocators-header.md)物件，此物件不會限制 [freelist](../standard-library/freelist-class.md) 物件的長度上限。  
  
## <a name="syntax"></a>語法  
  
```
class max_unbounded
```  
  
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
  
##  <a name="allocated"></a>  max_unbounded::allocated  
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
  
##  <a name="deallocated"></a>  max_unbounded::deallocated  
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
  
##  <a name="full"></a>  max_unbounded::full  
 傳回指定是否應該為可用清單新增更多記憶體區塊的值。  
  
```
bool full();
```  
  
### <a name="return-value"></a>傳回值  
 此成員函式一律會傳回 `false`。  
  
### <a name="remarks"></a>備註  
 此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果此呼叫傳回 `true`，`deallocate` 便會將記憶體區塊放到可用清單上，如果傳回 false，`deallocate` 則會呼叫運算子 `delete` 來將區塊解除配置。  
  
##  <a name="released"></a>  max_unbounded::released  
 遞減可用清單上的記憶體區塊計數。  
  
```
void released();
```  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 max 類別的 `released` 成員函式。  
  
##  <a name="saved"></a>  max_unbounded::saved  
 遞增可用清單上的記憶體區塊計數。  
  
```
void saved();
```  
  
### <a name="remarks"></a>備註  
 此成員函式不會執行任何動作。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫它。  
  
## <a name="see-also"></a>另請參閱  
 [\<allocators>](../standard-library/allocators-header.md)




