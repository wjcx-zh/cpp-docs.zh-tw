---
title: "atomic_flag 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "atomic/std::atomic_flag"
dev_langs: 
  - "C++"
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# atomic_flag 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述原子集合和清除 `bool` 旗標的物件。  在不可部分完成的旗標之作業永遠是無鎖定。  
  
## 語法  
  
```  
struct atomic_flag;  
```  
  
## 成員  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[atomic\_flag::clear 方法](../Topic/atomic_flag::clear%20Method.md)|將儲存旗標設定為 `false` 。|  
|[atomic\_flag::test\_and\_set 方法](../Topic/atomic_flag::test_and_set%20Method.md)|將儲存旗標設定為 `true` 並傳回初始旗標值。|  
  
## 備註  
 `atomic_flag` 物件可以傳遞至非成員函式 [atomic\_flag\_clear](../Topic/atomic_flag_clear%20Function.md)、 [atomic\_flag\_clear\_explicit](../Topic/atomic_flag_clear_explicit%20Function.md)、 [atomic\_flag\_test\_and\_set](../Topic/atomic_flag_test_and_set%20Function.md)和 [atomic\_flag\_test\_and\_set\_explicit](../Topic/atomic_flag_test_and_set_explicit%20Function.md)。  使用 `ATOMIC_FLAG_INIT`值，其可以初始化。  
  
## 需求  
 **標頭：**atomic  
  
 **命名空間:** std  
  
## 請參閱  
 [\<atomic\>](../standard-library/atomic.md)