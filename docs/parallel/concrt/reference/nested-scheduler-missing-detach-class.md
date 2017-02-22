---
title: "nested_scheduler_missing_detach 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::nested_scheduler_missing_detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nested_scheduler_missing_detach 類別"
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# nested_scheduler_missing_detach 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別描述當並行執行階段偵測到您忘了使用 `Scheduler` 物件的 `Attach` 方法在附加到第二個排程器上呼叫 `CurrentScheduler::Detach` 方法時擲出的例外狀況。  
  
## 語法  
  
```  
class nested_scheduler_missing_detach : public std::exception;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[nested\_scheduler\_missing\_detach::nested\_scheduler\_missing\_detach 建構函式](../Topic/nested_scheduler_missing_detach::nested_scheduler_missing_detach%20Constructor.md)|多載。  建構 `nested_scheduler_missing_detach` 物件。|  
  
## 備註  
 當您在已由其他排程器擁有或附加的內容上呼叫 `Scheduler` 物件的`Attach` 方法，將排程器巢狀排列在另一個排程器內時，才會擲回這個例外狀況。  並行執行階段可以偵測案例以協助找出問題時，會擲回這個例外狀況。  不保證每一個忽略呼叫 `CurrentScheduler::Detach` 方法的執行個體都會擲回這個例外狀況。  
  
## 繼承階層  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [CurrentScheduler::Detach 方法](../Topic/CurrentScheduler::Detach%20Method.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)