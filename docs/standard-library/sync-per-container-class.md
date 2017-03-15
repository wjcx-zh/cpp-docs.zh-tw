---
title: "sync_per_container 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.sync_per_container"
  - "sync_per_container"
  - "stdext::sync_per_container"
  - "allocators/stdext::sync_per_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_per_container 類別"
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# sync_per_container 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述針對每個配置器物件提供不同的快取物件的 [同步處理篩選條件](../standard-library/allocators-header.md) 。  
  
## 語法  
  
```  
template <class Cache> class sync_per_container  
    : public Cache  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Cache`|快取的型別與同步處理篩選條件。  這可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、 [cache\_freelist](../standard-library/cache-freelist-class.md)或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### 成員函式  
  
|||  
|-|-|  
|[equals](../Topic/sync_per_container::equals.md)|要比較是否相等的兩個快取。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)