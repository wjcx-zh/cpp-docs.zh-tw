---
title: "sync_per_thread 類別 | Microsoft Docs"
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
  - "stdext::sync_per_thread"
  - "sync_per_thread"
  - "allocators/stdext::sync_per_thread"
  - "stdext.sync_per_thread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_per_thread 類別"
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sync_per_thread 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述針對每一個執行緒提供不同的快取物件的 [同步處理篩選條件](../standard-library/allocators-header.md) 。  
  
## 語法  
  
```  
template <class Cache> class sync_per_thread  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Cache`|快取的型別與同步處理篩選條件。  這可以是 [cache\_chunklist](../standard-library/cache-chunklist-class.md)、 [cache\_freelist](../standard-library/cache-freelist-class.md)或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## 備註  
 使用 `sync_per_thread` 的配置器可能比較相等，即使在一個執行緒的區塊配置無法從另一個執行緒會解除配置。  當不應該使用一個配置器配置的記憶體區塊中的執行緒看見其他執行緒。  實際上這表示使用這些配置器之一的容器應該由單一執行緒只能存取。  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/sync_per_thread::allocate.md)|配置記憶體區塊。|  
|[解除配置](../Topic/sync_per_thread::deallocate.md)|從儲存體開始釋放物件所指定的數字在指定的位置。|  
|[equals](../Topic/sync_per_thread::equals.md)|要比較是否相等的兩個快取。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)