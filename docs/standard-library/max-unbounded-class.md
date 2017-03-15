---
title: "max_unbounded 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators/stdext::max_unbounded"
  - "stdext::max_unbounded"
  - "stdext.max_unbounded"
  - "max_unbounded"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_unbounded 類別"
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# max_unbounded 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [類別的最大](../standard-library/allocators-header.md) 物件，不會限制的最大長度 [freelist](../standard-library/freelist-class.md) 物件。  
  
## 語法  
  
```  
class max_unbounded  
```  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/max_unbounded::allocated.md)|配置的記憶體區塊的計數遞增。|  
|[解除配置](../Topic/max_unbounded::deallocated.md)|遞減的計數配置記憶體區塊。|  
|[完整](../Topic/max_unbounded::full.md)|傳回值，這個值會指定是否應該以可用的清單中加入更多的記憶體區塊。|  
|[發行](../Topic/max_unbounded::released.md)|遞減計數的記憶體區塊上可用的清單。|  
|[儲存](../Topic/max_unbounded::saved.md)|可用清單上的記憶體區塊的計數遞增。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)