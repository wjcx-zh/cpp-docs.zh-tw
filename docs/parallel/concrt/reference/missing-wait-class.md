---
title: "missing_wait 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::missing_wait"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "missing_wait 類別"
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# missing_wait 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述有仍然安排的工作時，擲回例外狀況`task_group`或`structured_task_group`物件一次該物件的解構函式會執行。  解構函式會在達到因堆疊回溯例外狀況的結果時，將永遠不會擲回這個例外狀況。  
  
## 語法  
  
```  
class missing_wait : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[missing\_wait::missing\_wait 建構函式](../Topic/missing_wait::missing_wait%20Constructor.md)|多載。  建構 `missing_wait` 物件。|  
  
## 備註  
 例外狀況流程不存在，您必須先呼叫 `task_group` 或 `structured_task_group` 物件的 `wait` 或 `run_and_wait`方法，然後才能解構該物件。  執行階段會擲回這個例外狀況，表示您忘了呼叫 `wait` `run_and_wait` 方法。  
  
## 繼承階層架構  
 `exception`  
  
 `missing_wait`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group 類別](../Topic/task_group%20Class.md)   
 [task\_group::wait 方法](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait 方法](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group 類別](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)