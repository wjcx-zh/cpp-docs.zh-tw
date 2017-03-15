---
title: "排程群組 | Microsoft Docs"
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
  - "排程群組"
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 排程群組
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明並行執行階段中的排程群組的角色。 A *排程群組* 視為，或組合，相關的工作在一起。 每個排程器有一或多個排程群組。 當您需要在工作之間有高度位置關係時 (例如一個相關工作的群組可因為在相同處理器節點上執行而受益)，請使用排程群組。 相反地，使用排程器執行個體，當您的應用程式都有特定品質需求，例如，當您想要限制配置給一組工作的處理資源量。 如需有關排程器執行個體的詳細資訊，請參閱 [排程器執行個體](../../parallel/concrt/scheduler-instances.md)。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 因為工作排程器可協助您微調應用程式的效能，我們建議您開始 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md) 如果您不熟悉並行執行階段。  
  
 每個 `Scheduler` 物件已排程的每個節點的預設排程群組。 A *排程節點* 對應至基礎的系統拓撲。 執行階段會建立一個排程的節點，針對每個處理器封裝或非統一記憶體架構 (NUMA) 節點，大於任何數字。 如果您未使用的排程群組明確地將工作，排程器會選擇哪一個群組加入至工作。  
  
  `SchedulingProtocol` 排程器原則會影響排程器執行的工作，每個排程群組中的順序。 當 `SchedulingProtocol` 設為 `EnhanceScheduleGroupLocality` （此為預設值），工作排程器會選擇下一個工作從它正在進行時完成目前的工作，或以合作方式讓排程群組。 工作排程器會搜尋目前工作的排程群組之前會移至下一個可用的群組。 相反地，當 `SchedulingProtocol` 設為 `EnhanceForwardProgress`, ，在每個工作完成後，或者會產生排程器將移至下一個排程群組。 如需比較這些原則的範例，請參閱 [How to︰ 使用排程群組的執行順序會影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
 執行階段使用 [concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md) 類別代表排程群組。 若要建立 `ScheduleGroup` 物件，請呼叫 [concurrency::CurrentScheduler::CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md) 或 [concurrency::Scheduler::CreateScheduleGroup](../Topic/Scheduler::CreateScheduleGroup%20Method.md) 方法。 執行階段會使用參考計數的機制來控制的存留期 `ScheduleGroup` 物件時，就如同使用 `Scheduler` 物件。 當您建立 `ScheduleGroup` 物件，其中一個計數器的執行階段設定的參考。  [Schedulegroup](../Topic/ScheduleGroup::Reference%20Method.md) 方法的參考計數器遞增一。  [Schedulegroup](../Topic/ScheduleGroup::Release%20Method.md) 方法遞減 1 的參考計數器。  
  
 並行執行階段中的許多型別可讓您建立的排程群組與物件關聯。 例如， [concurrency](../../parallel/concrt/reference/agent-class.md) 類別和訊息區之類的類別 [unbounded_buffer](../Topic/unbounded_buffer%20Class.md), ，[concurrency:: join](../../parallel/concrt/reference/join-class.md), ，和並行存取::[計時器](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d5d4c847-5ad6-4c7f-b35b-d0b6f446d8b4/locales/en-US), ，提供的建構函式多載的版本採用 `ScheduleGroup` 物件。 執行階段使用 `Scheduler` 與此相關聯的物件 `ScheduleGroup` 來排定工作的物件。  
  
 您也可以使用 [concurrency::ScheduleGroup::ScheduleTask](../Topic/ScheduleGroup::ScheduleTask%20Method.md) 方法來排程輕量型工作。 如需輕量型工作的詳細資訊，請參閱 [輕量型工作](../../parallel/concrt/lightweight-tasks.md)。  
  
## <a name="example"></a>範例  
 如需範例，使用排程群組來控制工作執行的順序，請參閱 [How to︰ 使用排程群組的執行順序會影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [排程器執行個體](../../parallel/concrt/scheduler-instances.md)   
 [如何︰ 使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

