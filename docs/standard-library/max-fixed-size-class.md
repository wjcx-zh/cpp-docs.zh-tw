---
title: "max_fixed_size 類別 | Microsoft Docs"
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
  - "allocators/stdext::max_fixed_size"
  - "max_fixed_size"
  - "stdext::max_fixed_size"
  - "stdext.max_fixed_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_fixed_size 類別"
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# max_fixed_size 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 [最大類別](../standard-library/allocators-header.md) 物件來限制固定的最大長度的 [freelist](../standard-library/freelist-class.md) 物件。  
  
## 語法  
  
```  
template <std::size_t Max> class max_fixed_size  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Max`|在 `freelist`所識別項目最大數目儲存的最大類別。|  
  
### 建構函式  
  
|||  
|-|-|  
|[max\_fixed\_size](../Topic/max_fixed_size::max_fixed_size.md)|建構屬於 `max_fixed_size` 類型的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/max_fixed_size::allocated.md)|將計算配置的記憶體區塊。|  
|[解除配置](../Topic/max_fixed_size::deallocated.md)|遞減計數配置的記憶體區塊。|  
|[full](../Topic/max_fixed_size::full.md)|傳回這個值指定是否應該加入更多記憶體區塊加入至可用清單。|  
|[釋放](../Topic/max_fixed_size::released.md)|會計算可用清單的記憶體區塊。|  
|[儲存](../Topic/max_fixed_size::saved.md)|將計算可用清單的記憶體區塊。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)