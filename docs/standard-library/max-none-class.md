---
title: "max_none 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "max_none"
  - "stdext::max_none"
  - "stdext.max_none"
  - "allocators/stdext::max_none"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_none 類別"
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# max_none 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [類別的最大](../standard-library/allocators-header.md) 物件，以限制 [freelist](../standard-library/freelist-class.md) 最大長度為零的物件。  
  
## 語法  
  
```  
template <std::size_t Max> class max_none  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Max`|決定要儲存的項目數目上限的最大類別 `freelist`。|  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/max_none::allocated.md)|配置的記憶體區塊的計數遞增。|  
|[解除配置](../Topic/max_none::deallocated.md)|遞減的計數配置記憶體區塊。|  
|[完整](../Topic/max_none::full.md)|傳回值，這個值會指定是否應該以可用的清單中加入更多的記憶體區塊。|  
|[發行](../Topic/max_none::released.md)|遞減計數的記憶體區塊上可用的清單。|  
|[儲存](../Topic/max_none::saved.md)|可用清單上的記憶體區塊的計數遞增。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)