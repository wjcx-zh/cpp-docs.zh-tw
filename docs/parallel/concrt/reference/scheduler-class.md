---
title: "Scheduler 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::Scheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Scheduler 類別"
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# Scheduler 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表並行執行階段排程器的抽象概念。  
  
## 語法  
  
```  
class Scheduler;  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|說明|  
|--------|--------|  
|[Scheduler::Scheduler 建構函式](../Topic/Scheduler::Scheduler%20Constructor.md)|只能使用 Factory 方法或隱含地建立 `Scheduler` 類別的物件。|  
|[Scheduler::~Scheduler 解構函式](../Topic/Scheduler::~Scheduler%20Destructor.md)|對 `Scheduler` 類別之物件的參考全部不存在時，會隱含地終結此物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)|將排程器附加至呼叫內容。  這個方法傳回後，呼叫內容即由排程器管理，而排程器會變成目前的排程器。|  
|[Scheduler::Create 方法](../Topic/Scheduler::Create%20Method.md)|會建立新排程器，其行為由 `_Policy` 參數描述、將初始參照放置於排程器，並且傳回其指標。|  
|[Scheduler::CreateScheduleGroup 方法](../Topic/Scheduler::CreateScheduleGroup%20Method.md)|多載。  在排程器內建立新的排程群組。  採用 `_Placement` 參數的版本在新建立的排程群組中造成工作被偏移往執行該參數所指定的位置。|  
|[Scheduler::GetNumberOfVirtualProcessors 方法](../Topic/Scheduler::GetNumberOfVirtualProcessors%20Method.md)|傳回排程器目前的虛擬處理器數目。|  
|[Scheduler::GetPolicy 方法](../Topic/Scheduler::GetPolicy%20Method.md)|傳回建立排程器所使用的原則的複本。|  
|[Scheduler::id 方法](../Topic/Scheduler::Id%20Method.md)|傳回排程器的唯一識別碼。|  
|[Scheduler::IsAvailableLocation 方法](../Topic/Scheduler::IsAvailableLocation%20Method.md)|判斷指定的位置是否在排程器可用。|  
|[Scheduler::Reference 方法](../Topic/Scheduler::Reference%20Method.md)|遞增這個排程器的參考計數。|  
|[Scheduler::RegisterShutdownEvent 方法](../Topic/Scheduler::RegisterShutdownEvent%20Method.md)|會導致 `_Event` 參數中傳遞的 Windows 事件控制代碼在排程器關閉並自行終結時發出訊號。  發出事件訊號之後，即已完成所有已排定至排程器中的工作。  可以透過此方法註冊多個關機事件。|  
|[Scheduler::Release 方法](../Topic/Scheduler::Release%20Method.md)|遞減這個排程器的參考計數。|  
|[Scheduler::ResetDefaultSchedulerPolicy 方法](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md)|將預設排程器原則重設為執行階段的預設值。  下一次建立預設排程器時，它就會使用執行階段的預設原則設定。|  
|[Scheduler::ScheduleTask 方法](../Topic/Scheduler::ScheduleTask%20Method.md)|多載。  在排程器內排程輕量工作。  輕量工作會置於執行階段決定的排程群組中。  採用 `_Placement` 參數的版本會造成工作被偏移往執行所指定的位置。|  
|[Scheduler::SetDefaultSchedulerPolicy 方法](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)|可讓您使用使用者定義的原則建立預設排程器。  只能在處理序中沒有任何預設排程器時呼叫這個方法。  在設定預設原則後，該原則就會保持作用中，直到 `SetDefaultSchedulerPolicy` 或 [ResetDefaultSchedulerPolicy](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md) 方法的下一個有效呼叫。|  
  
## 備註  
 並行執行階段排程器會使用對應到作業系統執行內容的執行內容 \(例如執行緒\) 來執行應用程式佇列到該排程器中的工作。  排程器的並行存取層級隨時都等於資源管理員授與它的虛擬處理器的數目。  虛擬處理器是處理資源的抽象概念，對應於基礎系統的硬體執行緒。  在指定時間內，一個虛擬處理器只能執行一個排程器內容。  
  
 並行執行階段會根據處理序建立預設排程器，以執行平行工作。  此外，您可以建立自己的排程器執行個體，並使用這個類別操作該執行個體。  
  
## 繼承階層  
 `Scheduler`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler Class](../../../parallel/concrt/reference/scheduler-class.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)