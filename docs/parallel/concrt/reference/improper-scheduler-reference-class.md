---
title: "improper_scheduler_reference 類別 | Microsoft Docs"
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
  - "concrt/concurrency::improper_scheduler_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_reference 類別"
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# improper_scheduler_reference 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`Reference`上呼叫方法`Scheduler`正在關機，來自不屬於該排程器的內容中的物件。  
  
## 語法  
  
```  
class improper_scheduler_reference : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[improper\_scheduler\_reference::improper\_scheduler\_reference 建構函式](../Topic/improper_scheduler_reference::improper_scheduler_reference%20Constructor.md)|多載。  建構 `improper_scheduler_reference` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `improper_scheduler_reference`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Reference 方法](../Topic/Scheduler::Reference%20Method.md)