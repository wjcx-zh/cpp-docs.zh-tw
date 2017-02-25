---
title: "improper_scheduler_detach 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::improper_scheduler_detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_detach 類別"
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# improper_scheduler_detach 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`CurrentScheduler::Detach`內容尚未附加到使用任何排程器上呼叫方法`Attach`方法的`Scheduler`物件。  
  
## 語法  
  
```  
class improper_scheduler_detach : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[improper\_scheduler\_detach::improper\_scheduler\_detach 建構函式](../Topic/improper_scheduler_detach::improper_scheduler_detach%20Constructor.md)|多載。  建構 `improper_scheduler_detach` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `improper_scheduler_detach`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [CurrentScheduler::Detach 方法](../Topic/CurrentScheduler::Detach%20Method.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)