---
title: "ScheduleGroup 類別 | Microsoft Docs"
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
  - "concrt/concurrency::ScheduleGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ScheduleGroup 類別"
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ScheduleGroup 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表排程群組的抽象概念。  排程群組會組織一組相關的工作，這些工作受益於透過在同一個群組中執行另一個工作再移至另一個群組、透過再同一個 NUMA 節點或實體通訊端的同一個群組內執行多個項目而暫時緊密地排程在一起。  
  
## 語法  
  
```  
class ScheduleGroup;  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[ScheduleGroup::~ScheduleGroup 解構函式](../Topic/ScheduleGroup::~ScheduleGroup%20Destructor.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ScheduleGroup::Id 方法](../Topic/ScheduleGroup::Id%20Method.md)|傳回排程群組的識別碼，在該群組所屬的排程器中是唯一的。|  
|[ScheduleGroup::Reference 方法](../Topic/ScheduleGroup::Reference%20Method.md)|遞增排程器群組的參考計數。|  
|[ScheduleGroup::Release 方法](../Topic/ScheduleGroup::Release%20Method.md)|遞減排程器群組的參考計數。|  
|[ScheduleGroup::ScheduleTask 方法](../Topic/ScheduleGroup::ScheduleTask%20Method.md)|在排程內排程輕量工作。|  
  
## 繼承階層架構  
 `ScheduleGroup`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [CurrentScheduler 類別](../../../parallel/concrt/reference/currentscheduler-class.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)