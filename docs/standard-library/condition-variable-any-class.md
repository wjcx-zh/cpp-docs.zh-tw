---
title: "condition_variable_any 類別 | Microsoft Docs"
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
  - "condition_variable/std::condition_variable_any"
dev_langs: 
  - "C++"
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
caps.latest.revision: 15
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# condition_variable_any 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用類別 `condition_variable_any` 等待有任何 `mutex` 型別的事件。  
  
## 語法  
  
```  
class condition_variable_any;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[condition\_variable\_any::condition\_variable\_any 建構函式](../Topic/condition_variable_any::condition_variable_any%20Constructor.md)|建構 `condition_variable_any` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[condition\_variable\_any::notify\_all 方法](../Topic/condition_variable_any::notify_all%20Method.md)|解除等候 `condition_variable_any` 物件的所有執行緒之封鎖。|  
|[condition\_variable\_any::notify\_one 方法](../Topic/condition_variable_any::notify_one%20Method.md)|解除等候 `condition_variable_any` 物件的其中一個執行緒之封鎖。|  
|[condition\_variable\_any::wait 方法](../Topic/condition_variable_any::wait%20Method.md)|封鎖執行緒。|  
|[condition\_variable\_any::wait\_for 方法](../Topic/condition_variable_any::wait_for%20Method.md)|阻隔一個線程，在線程解開後設定時間間隔。|  
|[condition\_variable\_any::wait\_until 方法](../Topic/condition_variable_any::wait_until%20Method.md)|封鎖執行緒，並在執行緒解除封鎖時設定最大時間點。|  
  
## 需求  
 **標頭：** condition\_variable  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<condition\_variable\>](../standard-library/condition-variable.md)