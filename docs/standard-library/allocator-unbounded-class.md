---
title: "allocator_unbounded 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
dev_langs: C++
helpviewer_keywords: allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3511828e2d2c31851a1d85e1b6d122aadc80522
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded 類別
描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_unbounded](../standard-library/max-unbounded-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。  
  
## <a name="syntax"></a>語法  
  
```
template <class Type>  
class allocator_unbounded;
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Type`|配置器所配置的元素類型。|  
  
## <a name="remarks"></a>備註  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 巨集會將此類別傳遞為下列陳述式中的 `name` 參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
## <a name="see-also"></a>請參閱  
 [\<allocators>](../standard-library/allocators-header.md)



