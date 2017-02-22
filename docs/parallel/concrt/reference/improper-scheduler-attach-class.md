---
title: "improper_scheduler_attach 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::improper_scheduler_attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_attach 類別"
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# improper_scheduler_attach 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`Attach`上呼叫方法`Scheduler`物件已經附加到目前的內容。  
  
## 語法  
  
```  
class improper_scheduler_attach : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[improper\_scheduler\_attach::improper\_scheduler\_attach 建構函式](../Topic/improper_scheduler_attach::improper_scheduler_attach%20Constructor.md)|多載。  建構 `improper_scheduler_attach` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `improper_scheduler_attach`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)