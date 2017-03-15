---
title: "sync_none 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.sync_none"
  - "sync_none"
  - "allocators/stdext::sync_none"
  - "stdext::sync_none"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_none 類別"
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# sync_none 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述並不提供同步的 [同步處理篩選條件](../standard-library/allocators-header.md) 。  
  
## 語法  
  
```  
template <class Cache> class sync_none  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Cache`|快取的型別與同步處理篩選條件。  這可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、 [cache\_freelist](../standard-library/cache-freelist-class.md)或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/sync_none::allocate.md)|配置記憶體區塊。|  
|[解除配置](../Topic/sync_none::deallocate.md)|從儲存體開始釋放物件所指定的數字在指定的位置。|  
|[equals](../Topic/sync_none::equals.md)|要比較是否相等的兩個快取。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)