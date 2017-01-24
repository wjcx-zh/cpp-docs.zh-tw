---
title: "allocator_variable_size 類別 | Microsoft Docs"
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
  - "allocators.allocator_variable_size"
  - "allocators::allocator_variable_size"
  - "allocators/stdext::allocator_variable_size"
  - "stdext.allocators.allocator_variable_size"
  - "allocator_variable_size"
  - "allocators/stdext::allocators::allocator_variable_size"
  - "stdext::allocators::allocator_variable_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_variable_size 類別"
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_variable_size 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述處理儲存區配置和釋放 `Type` 型別的物件上使用快取型別 [cache\_freelist](../standard-library/cache-freelist-class.md) 與 [max\_variable\_size](../standard-library/max-variable-size-class.md)處理的長度的物件。  
  
## 語法  
  
```  
template <class Type>  
    class allocator_variable_size;  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Type`|項目型別由配置器所配置的記憶體。|  
  
## 備註  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 巨集是透過此類別為以下陳述式的 `name` 參數: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)