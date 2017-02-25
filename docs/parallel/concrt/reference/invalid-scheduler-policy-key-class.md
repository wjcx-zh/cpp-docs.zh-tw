---
title: "invalid_scheduler_policy_key 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_scheduler_policy_key"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_key 類別"
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_scheduler_policy_key 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述了無效時擲回例外狀況或未知的索引鍵會傳遞至`SchedulerPolicy`物件建構函式，或`SetPolicyValue`方法的`SchedulerPolicy`物件被傳遞的索引鍵，必須使用其他方法，如變更`SetConcurrencyLimits`方法。  
  
## 語法  
  
```  
class invalid_scheduler_policy_key : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_scheduler\_policy\_key::invalid\_scheduler\_policy\_key 建構函式](../Topic/invalid_scheduler_policy_key::invalid_scheduler_policy_key%20Constructor.md)|多載。  建構 `invalid_scheduler_policy_key` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy 類別](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetPolicyValue 方法](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)   
 [SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)