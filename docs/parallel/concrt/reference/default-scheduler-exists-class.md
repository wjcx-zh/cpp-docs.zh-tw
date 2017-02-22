---
title: "default_scheduler_exists 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::default_scheduler_exists"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default_scheduler_exists 類別"
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# default_scheduler_exists 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回的時機`Scheduler::SetDefaultSchedulerPolicy`處理序中的預設排程器已經存在時，會呼叫方法。  
  
## 語法  
  
```  
class default_scheduler_exists : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[default\_scheduler\_exists::default\_scheduler\_exists 建構函式](../Topic/default_scheduler_exists::default_scheduler_exists%20Constructor.md)|多載。  建構 `default_scheduler_exists` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `default_scheduler_exists`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler::SetDefaultSchedulerPolicy 方法](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)