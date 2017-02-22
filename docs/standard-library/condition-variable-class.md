---
title: "condition_variable 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "condition_variable/std::condition_variable"
dev_langs: 
  - "C++"
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# condition_variable 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您有 `unique_lock<mutex>` 型別的 `mutex` 時，請使用 `condition_variable` 類別等候事件。  這個型別的物件可能比型別 [condition\_variable\_any\<unique\_lock\<mutex\>\>](../standard-library/condition-variable-any-class.md) 物件有更好的效能。  
  
## 語法  
  
```  
class condition_variable;  
```  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[condition\_variable::condition\_variable 建構函式](../Topic/condition_variable::condition_variable%20Constructor.md)|建構 `condition_variable` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[condition\_variable::native\_handle 方法](../Topic/condition_variable::native_handle%20Method.md)|傳回表示 condition\_variable 控制代碼的這個實作特定的型別。|  
|[condition\_variable::notify\_all 方法](../Topic/condition_variable::notify_all%20Method.md)|解除等候 `condition_variable` 物件的所有執行緒之封鎖。|  
|[condition\_variable::notify\_one 方法](../Topic/condition_variable::notify_one%20Method.md)|解除等候 `condition_variable` 物件的其中一個執行緒之封鎖。|  
|[condition\_variable::wait 方法](../Topic/condition_variable::wait%20Method.md)|封鎖執行緒。|  
|[condition\_variable::wait\_for 方法](../Topic/condition_variable::wait_for%20Method.md)|阻隔一個線程，在線程解開後設定時間間隔。|  
|[condition\_variable::wait\_until 方法](../Topic/condition_variable::wait_until%20Method.md)|封鎖執行緒，並在執行緒解除封鎖時設定最大時間點。|  
  
## 需求  
 **標頭：** condition\_variable  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<condition\_variable\>](../standard-library/condition-variable.md)