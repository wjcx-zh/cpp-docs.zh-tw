---
title: "max_variable_size 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::max_variable_size"
  - "allocators/stdext::max_variable_size"
  - "stdext.max_variable_size"
  - "max_variable_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_variable_size 類別"
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# max_variable_size 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [類別的最大](../standard-library/allocators-header.md) 限制的物件 [freelist](../standard-library/freelist-class.md) 大致上與數目成比例的最大長度的物件配置記憶體區塊。  
  
## 語法  
  
```  
class max_variable_size  
```  
  
### 建構函式  
  
|||  
|-|-|  
|[max\_variable\_size](../Topic/max_variable_size::max_variable_size.md)|建構類型 `max_variable_size` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/max_variable_size::allocated.md)|配置的記憶體區塊的計數遞增。|  
|[解除配置](../Topic/max_variable_size::deallocated.md)|遞減的計數配置記憶體區塊。|  
|[完整](../Topic/max_variable_size::full.md)|傳回值，這個值會指定是否應該以可用的清單中加入更多的記憶體區塊。|  
|[發行](../Topic/max_variable_size::released.md)|遞減計數的記憶體區塊上可用的清單。|  
|[儲存](../Topic/max_variable_size::saved.md)|可用清單上的記憶體區塊的計數遞增。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)