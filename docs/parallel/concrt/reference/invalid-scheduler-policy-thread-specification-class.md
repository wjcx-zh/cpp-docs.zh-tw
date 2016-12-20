---
title: "invalid_scheduler_policy_thread_specification 類別 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_scheduler_policy_thread_specification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_thread_specification 類別"
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_scheduler_policy_thread_specification 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述嘗試設定的並行處理限制時，擲回例外狀況`SchedulerPolicy`物件，讓值`MinConcurrency`機碼時的值小於`MaxConcurrency`機碼。  
  
## 語法  
  
```  
class invalid_scheduler_policy_thread_specification : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_scheduler\_policy\_thread\_specification::invalid\_scheduler\_policy\_thread\_specification 建構函式](../Topic/invalid_scheduler_policy_thread_specification::invalid_scheduler_policy_thread_specification%20Constructor.md)|多載。  建構 `invalid_scheduler_policy_value` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy 類別](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)