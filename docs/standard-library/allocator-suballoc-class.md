---
title: "allocator_suballoc 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators::allocator_suballoc"
  - "allocator_suballoc"
  - "stdext.allocators.allocator_suballoc"
  - "allocators/stdext::allocators::allocator_suballoc"
  - "stdext::allocators::allocator_suballoc"
  - "allocators/stdext::allocator_suballoc"
  - "allocators.allocator_suballoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_suballoc 類別"
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# allocator_suballoc 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述物件，可管理儲存體配置和釋放物件的型別 `Type` 使用類型的快取 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。  
  
## 語法  
  
```  
template <class Type>  
    class allocator_suballoc;  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Type`|配置器所配置的元素類型。|  
  
## 備註  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 巨集傳遞這個類別做為 `name` 下列陳述式中的參數︰ `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)