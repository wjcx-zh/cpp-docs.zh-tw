---
title: "sync_per_container 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c98e8f7524864e5249c08e2b6f3d4a38ea8e4be
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="syncpercontainer-class"></a>sync_per_container 類別
描述可為每個配置器物件提供不同快取物件的[同步處理篩選](../standard-library/allocators-header.md)。  
  
## <a name="syntax"></a>語法  
  
```
template <class Cache>  
class sync_per_container
 : public Cache
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Cache`|與同步處理篩選相關聯的快取類型。 這可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[equals](#equals)|比較兩個快取是否相等。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
##  <a name="equals"></a>  sync_per_container::equals  
 比較兩個快取是否相等。  
  
```
bool equals(const sync_per_container<Cache>& Other) const;
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`Cache`|同步處理篩選的快取物件。|  
|`Other`|要比較是否相等的快取物件。|  
  
### <a name="return-value"></a>傳回值  
 此成員函式一律會傳回 `false`。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [\<allocators>](../standard-library/allocators-header.md)



