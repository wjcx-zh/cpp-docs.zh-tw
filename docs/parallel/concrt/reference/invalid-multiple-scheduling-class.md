---
title: "invalid_multiple_scheduling 類別 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_multiple_scheduling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_multiple_scheduling 類別"
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_multiple_scheduling 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`task_handle`物件是已排程的倍數，使用`run`方法的`task_group`或`structured_task_group`沒有任何一個的多餘呼叫物件`wait`或`run_and_wait`方法。  
  
## 語法  
  
```  
class invalid_multiple_scheduling : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_multiple\_scheduling::invalid\_multiple\_scheduling 建構函式](../Topic/invalid_multiple_scheduling::invalid_multiple_scheduling%20Constructor.md)|多載。  建構 `invalid_multiple_scheduling` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_handle 類別](../../../parallel/concrt/reference/task-handle-class.md)   
 [task\_group 類別](../Topic/task_group%20Class.md)   
 [task\_group::run 方法](../Topic/task_group::run%20Method.md)   
 [task\_group::wait 方法](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait 方法](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group 類別](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [structured\_task\_group::run 方法](../Topic/structured_task_group::run%20Method.md)   
 [structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)