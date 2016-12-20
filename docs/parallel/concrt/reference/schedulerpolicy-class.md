---
title: "SchedulerPolicy 類別 | Microsoft Docs"
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
  - "concrt/concurrency::SchedulerPolicy"
  - "concrtrm/concurrency::SchedulerPolicy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SchedulerPolicy 類別"
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SchedulerPolicy 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`SchedulerPolicy` 類別包含一組索引鍵\/值組，每個原則項目一個，可控制排程器執行個體的行為。  
  
## 語法  
  
```  
class SchedulerPolicy;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[SchedulerPolicy::SchedulerPolicy 建構函式](../Topic/SchedulerPolicy::SchedulerPolicy%20Constructor.md)|多載。  建構新的排程器原則，並填入 [原則機碼](../Topic/PolicyElementKey%20Enumeration.md) 並行執行階段排程器和資源管理員所支援的值。|  
|[SchedulerPolicy::~SchedulerPolicy 解構函式](../Topic/SchedulerPolicy::~SchedulerPolicy%20Destructor.md)|終結排程器原則。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[SchedulerPolicy::GetPolicyValue 方法](../Topic/SchedulerPolicy::GetPolicyValue%20Method.md)|擷取提供做為 `_Key` 參數的原則機碼的值。|  
|[SchedulerPolicy::SetConcurrencyLimits 方法](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)|同時在 `SchedulerPolicy` 物件上設定 `MinConcurrency` 和 `MaxConcurrency` 原則。|  
|[SchedulerPolicy::SetPolicyValue 方法](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)|設定提供作為 `_Key` 參數之原則機碼的值，並傳回，並傳回舊值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[SchedulerPolicy::operator\= 運算子](../Topic/SchedulerPolicy::operator=%20Operator.md)|從另一個排程器原則指派排程器原則。|  
  
## 備註  
 如需可利用 `SchedulerPolicy` 類別控制之原則的詳細有關，請參閱 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)。  
  
## 繼承階層架構  
 `SchedulerPolicy`  
  
## 需求  
 **標題:** ， concrtrm.h concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [CurrentScheduler 類別](../../../parallel/concrt/reference/currentscheduler-class.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)