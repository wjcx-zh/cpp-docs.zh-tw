---
title: "CurrentScheduler 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::CurrentScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CurrentScheduler 類別"
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CurrentScheduler 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表與呼叫內容相關之目前排程器的抽象概念。  
  
## 語法  
  
```  
class CurrentScheduler;  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[CurrentScheduler::Create 方法](../Topic/CurrentScheduler::Create%20Method.md)|建立新排程器，其行為由 `_Policy` 參數描述，並將它附加至呼叫的內容。  新建立的排程器將會變成呼叫內容目前的排程器。|  
|[CurrentScheduler::CreateScheduleGroup 方法](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md)|多載。  在與呼叫內容相關的排程器內建立新的排程群組。  採用 `_Placement` 參數的版本在新建立的排程群組中造成工作被偏移往執行該參數所指定的位置。|  
|[CurrentScheduler::Detach 方法](../Topic/CurrentScheduler::Detach%20Method.md)|中斷連結目前的排程器與呼叫內容，並且將先前附加的排程器 \(如果有的話\) 還原為目前的排程器。  這個方法傳回之後，呼叫內容則由先前使用 `CurrentScheduler::Create` 或 `Scheduler::Attach` 方法附加至內容的排程器管理。|  
|[CurrentScheduler::Get 方法](../Topic/CurrentScheduler::Get%20Method.md)|傳回與呼叫內容相關之排程器 \(亦稱為目前的排程器\) 的指標。|  
|[CurrentScheduler::GetNumberOfVirtualProcessors 方法](../Topic/CurrentScheduler::GetNumberOfVirtualProcessors%20Method.md)|傳回目前與呼叫內容相關之排程器的虛擬處理器數目。|  
|[CurrentScheduler::GetPolicy 方法](../Topic/CurrentScheduler::GetPolicy%20Method.md)|傳回目前的排程器所建立的原則的複本。|  
|[CurrentScheduler::Id 方法](../Topic/CurrentScheduler::Id%20Method.md)|傳回目前排程器的唯一識別碼。|  
|[CurrentScheduler::IsAvailableLocation 方法](../Topic/CurrentScheduler::IsAvailableLocation%20Method.md)|判斷指定的位置是否可在目前的排程器。|  
|[CurrentScheduler::RegisterShutdownEvent 方法](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md)|會導致在 `_ShutdownEvent` 參數中傳遞的 Windows 事件控制代碼在與目前內容相關的排程器關閉並自行終結時發出訊號。  發出事件訊號之後，即已完成所有已排定至排程器中的工作。  可以透過此方法註冊多個關機事件。|  
|[CurrentScheduler::ScheduleTask 方法](../Topic/CurrentScheduler::ScheduleTask%20Method.md)|多載。  在與呼叫內容相關的排程器中排程輕量工作。  輕量工作會置於執行階段決定的排程群組中。  採用 `_Placement` 參數的版本會造成工作被偏移往執行所指定的位置。|  
  
## 備註  
 如果沒有任何排程器 \(請參閱[排程器](../../../parallel/concrt/reference/scheduler-class.md)\) 與呼叫內容關，`CurrentScheduler` 類別內的許多方法會造成附加處理序的預設排程器。  這可能也表示處理序的預設排程器是在此類呼叫期間建立的。  
  
## 繼承階層  
 `CurrentScheduler`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)