---
title: "排程器原則 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "排程器原則"
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
caps.latest.revision: 12
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 排程器原則
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明並行執行階段中排程器原則的角色。  「*排程器原則*」\(Scheduler Policy\) 會控制排程器在管理工作時所使用的策略。  例如，請考慮要求某些工作執行 `THREAD_PRIORITY_NORMAL` 和其他工作執行 `THREAD_PRIORITY_HIGHEST`的應用程式。您可以建立兩個排程器執行個體: 指定 `ContextPriority` 原則為 `THREAD_PRIORITY_NORMAL` 指定同一個原則是 `THREAD_PRIORITY_HIGHEST`的一項  
  
 使用排程器原則，您可分割可用處理資源，並將一組固定的資源指派給每個排程器。  例如，假設有延展性不超過四個處理器的平行演算法。  您可以建立會限制工作所能同時使用的處理器不超過四個的排程器原則。  
  
> [!TIP]
>  並行執行階段提供預設排程器。  因此，您不需要在您的應用程式建立。  因為工作排程器有助於微調應用程式效能，如果您是並行執行階段的新使用者，建議請從[平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)開始。  
  
 當您使用 [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md)、[concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) 或 [concurrency::Scheduler::SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md) 方法建立排程器執行個體時，要提供 [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 物件，其中包含指定排程器行為的索引鍵\/值組集合。  `SchedulerPolicy` 建構函式可採用不同數目的引數。  第一個引數是您即將指定之原則項目的數目。  其餘引數則是每個原則項目的機碼值組。  下列範例將建立會指定三個原則項目的 `SchedulerPolicy` 物件。  對於未指定的原則機碼，執行階段會使用預設值。  
  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/CPP/scheduler-policies_1.cpp)]  
  
 [concurrency::PolicyElementKey](../Topic/PolicyElementKey%20Enumeration.md) 列舉會定義與工作排程器相關聯的原則機碼。  下表說明原則機碼和執行階段為這些機碼所使用的預設值。  
  
|原則機碼|說明|預設值|  
|----------|--------|---------|  
|`SchedulerKind`|[concurrency::SchedulerType](../Topic/SchedulerType%20Enumeration.md) 值，指定要使用執行緒型別來排程工作。|`ThreadScheduler` \(使用一般執行緒\)  這是此金鑰的有效值。|  
|`MaxConcurrency`|`unsigned int` 值，指定排程器可使用的並行資源最大數目。|[concurrency::MaxExecutionResources](../Topic/MaxExecutionResources%20Constant.md)|  
|`MinConcurrency`|`unsigned int` 值，指定排程器可使用的並行資源最小數目。|`1`|  
|`TargetOversubscriptionFactor`|`unsigned int` 值，指定要為每項處理資源配置的執行緒數目。|`1`|  
|`LocalContextCacheSize`|`unsigned int` 值，指定在每個虛擬處理器的本機佇列中可快取的最大內容數目。|`8`|  
|`ContextStackSize`|`unsigned int` 值，指定要為每項內容保留的堆疊大小 \(以 KB 為單位\)。|`0` \(使用預設堆疊大小\)|  
|`ContextPriority`|`int` 值，指定每項內容的執行緒優先順序。  這可以是任何您能夠傳遞至 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) 或 `INHERIT_THREAD_PRIORITY` 的值。|`THREAD_PRIORITY_NORMAL`|  
|`SchedulingProtocol`|[concurrency::SchedulingProtocolType](../Topic/SchedulingProtocolType%20Enumeration.md) 值，指定要使用的排程演算法。|`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`|[concurrency::DynamicProgressFeedbackType](../Topic/DynamicProgressFeedbackType%20Enumeration.md) 值，指定是否要根據以統計資料為基礎的進度資訊，讓資源重新取得平衡。<br /><br /> **注意事項** 不要設定這個原則 `ProgressFeedbackDisabled` 因為它已保留供執行階段使用。|`ProgressFeedbackEnabled`|  
  
 每個排程器在排程工作時，都會使用它自己的原則。  與某個排程器相關聯的原則，並不會影響任何其他排程器的行為。  此外，在建立 `Scheduler` 物件後，您將無法變更排程器原則。  
  
> [!IMPORTANT]
>  只使用排程器原則來控制執行階段所建立之執行緒的屬性。  不要變更執行緒親和性或執行階段所建立之執行緒的優先權，因為可能會造成未定義的行為。  
  
 執行階段會為您建立預設排程器 \(如果尚未明確建立\)。  如果您要在應用程式中使用預設排程器，但要指定該排程器使用的原則，請在排定平行工作之前呼叫 [concurrency::Scheduler::SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md) 方法。  如果您未呼叫 `Scheduler::SetDefaultSchedulerPolicy` 方法，執行階段則會使用表格中的預設原則值。  
  
 請使用 [concurrency::CurrentScheduler::GetPolicy](../Topic/CurrentScheduler::GetPolicy%20Method.md) 和 [concurrency::Scheduler::GetPolicy](../Topic/Scheduler::GetPolicy%20Method.md) 方法，擷取排程器原則的複本。  您以這些方法擷取的原則值，可能會與您在建立排程器時所指定的原則值不同。  
  
## 範例  
 如需使用特定排程器原則來控制排程器行為的範例，請參閱 [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)和 [如何：建立使用特定排程器原則的代理程式](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。  
  
## 請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [如何：建立使用特定排程器原則的代理程式](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)