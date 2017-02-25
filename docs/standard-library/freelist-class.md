---
title: "freelist 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::freelist"
  - "freelist"
  - "stdext.freelist"
  - "allocators/stdext::freelist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "freelist 類別"
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# freelist 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

處理記憶體區塊清單。  
  
## 語法  
  
```  
template <std::size_t Sz, class Max> class freelist  
    : public Max  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Sz`|項目數目是陣列的配置。|  
|`Max`|表示項目的最大數目上限類別將存放在可用清單。  最大類別可以是 [max\_none](../standard-library/max-none-class.md)、 [max\_unbounded](../standard-library/max-unbounded-class.md)、 [max\_fixed\_size](../standard-library/max-fixed-size-class.md)或 [max\_variable\_size](../standard-library/max-variable-size-class.md)。|  
  
## 備註  
 這個範本類別處理大小 `Sz` 記憶體區塊清單具有最大類別取決於清單中的最大長度的傳入 `Max`。  
  
### 建構函式  
  
|||  
|-|-|  
|[freelist](../Topic/freelist::freelist.md)|建構屬於 `freelist` 類型的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[pop](../Topic/freelist::pop.md)|從可用清單移除第一個記憶體區塊。|  
|[push](../Topic/freelist::push.md)|將記憶體區塊加入至清單。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)