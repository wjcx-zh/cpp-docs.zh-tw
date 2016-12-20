---
title: "allocator_chunklist 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::allocators::allocator_chunklist"
  - "allocators::allocator_chunklist"
  - "allocators/stdext::allocator_chunklist"
  - "allocators.allocator_chunklist"
  - "allocators/stdext::allocators::allocator_chunklist"
  - "allocator_chunklist"
  - "stdext.allocators.allocator_chunklist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_chunklist 類別"
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_chunklist 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述處理儲存區配置和釋放物件所使用的快取 [cache\_chunklist](../standard-library/cache-chunklist-class.md)型別的物件。  
  
## 語法  
  
```  
template <class Type>  
    class allocator_chunklist;  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Type`|項目型別由配置器所配置的記憶體。|  
  
## 備註  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 巨集是透過此類別為以下陳述式的 `name` 參數: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist``);`  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)