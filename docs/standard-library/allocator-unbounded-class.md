---
title: "allocator_unbounded 類別 | Microsoft Docs"
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
  - "stdext::allocators::allocator_unbounded"
  - "allocator_unbounded"
  - "allocators/stdext::allocator_unbounded"
  - "allocators::allocator_unbounded"
  - "allocators/stdext::allocators::allocator_unbounded"
  - "allocators.allocator_unbounded"
  - "stdext.allocators.allocator_unbounded"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_unbounded 類別"
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: 17
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_unbounded 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述處理儲存區配置和釋放 `Type` 型別的物件上使用快取型別 [cache\_freelist](../standard-library/cache-freelist-class.md) 與 [max\_unbounded](../standard-library/max-unbounded-class.md)處理的長度的物件。  
  
## 語法  
  
```  
template <class Type>  
    class allocator_unbounded;  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Type`|項目型別由配置器所配置的記憶體。|  
  
## 備註  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 巨集是透過此類別為以下陳述式的 `name` 參數:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)