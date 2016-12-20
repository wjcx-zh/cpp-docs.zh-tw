---
title: "invalid_scheduler_policy_value 類別 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_scheduler_policy_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_value 類別"
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_scheduler_policy_value 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述的原則機碼時，擲回例外狀況`SchedulerPolicy`物件設定為 \[機碼值無效。  
  
## 語法  
  
```  
class invalid_scheduler_policy_value : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_scheduler\_policy\_value::invalid\_scheduler\_policy\_value 建構函式](../Topic/invalid_scheduler_policy_value::invalid_scheduler_policy_value%20Constructor.md)|多載。  建構 `invalid_scheduler_policy_value` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy 類別](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetPolicyValue 方法](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)   
 [SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)