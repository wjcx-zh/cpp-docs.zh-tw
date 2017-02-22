---
title: "sync_shared 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sync_shared"
  - "allocators/stdext::sync_shared"
  - "stdext.sync_shared"
  - "stdext::sync_shared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_shared 類別"
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# sync_shared 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述[同步處理篩選](../standard-library/allocators-header.md)，使用 mutex 來控制由所有配置器共用的快取物件存取權。  
  
## 語法  
  
```  
template <class Cache> class sync_shared  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Cache`|與同步處理篩選相關聯的快取類型。 可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md) 或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### 成員函式  
  
|||  
|-|-|  
|[allocate](../Topic/sync_shared::allocate.md)|配置記憶體區塊。|  
|[取消配置](../Topic/sync_shared::deallocate.md)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[等於](../Topic/sync_shared::equals.md)|比較兩個快取是否相等。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)