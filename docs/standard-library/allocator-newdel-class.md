---
title: "allocator_newdel 類別 | Microsoft Docs"
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
  - "allocators::allocator_newdel"
  - "allocators/stdext::allocators::allocator_newdel"
  - "stdext.allocators.allocator_newdel"
  - "allocators/stdext::allocator_newdel"
  - "allocator_newdel"
  - "stdext::allocators::allocator_newdel"
  - "allocators.allocator_newdel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_newdel 類別"
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_newdel 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

實作使用 `operator delete` 解除配置記憶體區塊和 `operator new` 配置的記憶體區塊的配置器。  
  
## 語法  
  
```  
template <class Type>  
    class allocator_newdel;  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Type`|項目型別由配置器所配置的記憶體。|  
  
## 備註  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 巨集是透過此類別為以下陳述式的 `name` 參數: `ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)