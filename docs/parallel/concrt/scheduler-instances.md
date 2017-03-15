---
title: "排程器執行個體 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "排程器執行個體"
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 排程器執行個體
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明並行執行階段中排程器執行個體的角色，以及如何使用 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 和 [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) 類別建立及管理排程器執行個體。  當您要為明確的排程原則與特定類型的工作負載建立關聯時，排程器執行個體很實用。  例如，您可以建立一個排程器執行個體以更高的執行緒優先順序執行某些工作，而使用預設排程器以一般執行緒優先順序執行其他工作。  
  
> [!TIP]
>  並行執行階段提供了預設排程器，因此您不需要在應用程式中建立排程器。  因為工作排程器有助於微調應用程式效能，如果您是並行執行階段的新使用者，建議請從[平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)開始。  
  
##  <a name="top"></a> 章節  
  
-   [Scheduler 和 CurrentScheduler 類別](#classes)  
  
-   [建立排程器執行個體](#creating)  
  
-   [管理排程器執行個體的存留期](#managing)  
  
-   [方法和功能](#features)  
  
-   [範例](#example)  
  
##  <a name="classes"></a> Scheduler 和 CurrentScheduler 類別  
 工作排程器可讓應用程式使用一個或多個「*排程器執行個體*」\(Scheduler Instance\) 來排程工作。  [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 類別代表一個排程器執行個體，可封裝與排程工作相關的功能。  
  
 附加至排程器的執行緒稱為「*執行內容*」\(Execution Context\)，或簡稱為「*內容*」\(Context\)。  在目前的內容中，只有一個排程器可以在任何時間是作用中。  作用中的排程器又稱為「*目前排程器*」\(Current Scheduler\)。  並行執行階段會使用 [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) 類別，提供目前排程器的存取。  一項內容的目前排程器，可能會不同於另一項內容的目前排程器。  執行階段不會提供目前排程器的處理序層級表示。  
  
 `CurrentScheduler` 類別通常用以存取目前的排程器。  所要管理的排程器不是目前的排程器時，`Scheduler` 類別很實用。  
  
 下列章節將說明如何建立和管理排程器執行個體。  如需這些工作的完整範例，請參閱 [如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="creating"></a> 建立排程器執行個體  
 有三種方法可以建立 `Scheduler` 物件：  
  
-   如果沒有任何排程器，執行階段將會在您使用執行階段功能 \(如平行演算法\) 時為您建立預設排程器，以執行工作。  預設排程器會成為啟始平行工作之內容的目前排程器。  
  
-   [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md) 方法可建立會使用特定原則，並為該排程器與目前內容建立關聯的 `Scheduler` 物件。  
  
-   [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) 方法可建立會使用特定原則，但不會為該排程器與目前內容建立關聯的 `Scheduler` 物件。  
  
 如果允許執行階段建立預設排程器，將使所有的並行工作可共用相同的排程器。  [平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\) 或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)所提供的功能通常用以執行平行工作。  因此，您無須直接使用排程器來控制其原則或存留期。  當您使用 PPL 或代理程式程式庫時，執行階段會建立預設排程器 \(如果不存在\)，並使其成為每項內容的目前排程器。  當您建立了排程器，並將它設為目前的排程器，執行階段就會使用該排程器來排定工作。  只有在您需要特定的排程原則時，建立其他排程器執行個體。  如需與排程器相關聯之原則的詳細資訊，請參閱[排程器原則](../../parallel/concrt/scheduler-policies.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="managing"></a> 管理排程器執行個體的存留期  
 執行階段會使用參考計數機制，控制 `Scheduler` 物件的存留期。  
  
 當您使用 `CurrentScheduler::Create` 方法或 `Scheduler::Create` 方法建立 `Scheduler` 物件時，執行階段會將該排程器的初始參考計數設為 1。  當您呼叫 [concurrency::Scheduler::Attach](../Topic/Scheduler::Attach%20Method.md) 方法時，執行階段會遞增參考計數。  `Scheduler::Attach` 方法會建立 `Scheduler` 物件與目前內容的關聯。  這會使其成為目前的排程器。  當您呼叫 `CurrentScheduler::Create` 方法時，執行階段會建立 `Scheduler` 物件，並將其附加至目前的內容 \(並將參考計數設為 1\)。  您也可以使用 [concurrency::Scheduler::Reference](../Topic/Scheduler::Reference%20Method.md) 方法，來遞增 `Scheduler` 物件的參考計數。  
  
 當您呼叫 [concurrency::CurrentScheduler::Detach](../Topic/CurrentScheduler::Detach%20Method.md) 方法以中斷目前排程器的連結，或呼叫 [concurrency::Scheduler::Release](../Topic/Scheduler::Release%20Method.md) 方法時，執行階段會遞減參考計數。  當參考計數到達零時，執行階段會在所有的排程工作完成後終結 `Scheduler` 物件。  執行中的工作可遞增目前排程器的參考計數。  因此，如果參考計數到達零，而某項工作使參考計數遞增，則在參考計數再次到達零，且所有工作皆完成之前，執行階段將不會終結 `Scheduler` 物件。  
  
 執行階段會為每項內容維護 `Scheduler` 物件的內部堆疊。  當您呼叫 `Scheduler::Attach` 或 `CurrentScheduler::Create` 方法時，執行階段會將該 `Scheduler` 物件推入到目前內容的堆疊上。  這會使其成為目前的排程器。  當您呼叫 `CurrentScheduler::Detach` 時，執行階段會從目前內容的堆疊快顯目前的排程器，並將前一個排程器設為目前的排程器。  
  
 執行階段有數種方式可管理排程器執行個體的存留期。  下表針對每個可為目前的內容建立或附加排程器的方法，列出可從目前的內容釋放排程器或中斷排程器連結的適當方法。  
  
|建立或附加方法|釋放或中斷連結方法|  
|-------------|---------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 呼叫不當的釋放或中斷連結方法，會在執行階段中產生未指定的行為。  
  
 當您使用會使執行階段為您建立預設排程器的功能 \(如 PPL\) 時，請不要釋放這個排程器或中斷其連結。  執行階段對於任何它所建立的排程器，都會管理其存留期。  
  
 在所有的工作完成之前，執行階段將不會終結 `Scheduler` 物件，因此您可以使用 [concurrency::Scheduler::RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md) 方法或 [concurrency::CurrentScheduler::RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md) 方法，在 `Scheduler` 物件終結時接收通知。  如果您必須等候 `Scheduler` 物件所排程的每項工作完成作業，這會很有用。  
  
 \[[上方](#top)\]  
  
##  <a name="features"></a> 方法和功能  
 本節摘要了 `CurrentScheduler` 和 `Scheduler` 類別的重要方法。  
  
 請將 `CurrentScheduler` 類別視為輔助工具，用以建立目前的內容所使用的排程器。  `Scheduler` 類別可讓您控制屬於另一個內容的排程器。  
  
 下表列出 `CurrentScheduler` 類別所定義的重要方法。  
  
|方法|說明|  
|--------|--------|  
|[Create](../Topic/CurrentScheduler::Create%20Method.md)|建立會使用特定原則的 `Scheduler` 物件，並建立此物件與目前內容的關聯。|  
|[Get](../Topic/CurrentScheduler::Get%20Method.md)|擷取與目前的內容關聯之 `Scheduler` 物件的指標。  這個方法不會遞增 `Scheduler` 物件的參考計數。|  
|[中斷連結](../Topic/CurrentScheduler::Detach%20Method.md)|從目前的內容中斷目前排程器的連結，並將前一個排程器設為目前的排程器。|  
|[RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md)|在目前的排程器終結時，註冊執行階段所設定的事件。|  
|[CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md)|在目前的排程器中建立 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 物件。|  
|[ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md)|新增輕量型工作至目前排程器的排程佇列中。|  
|[GetPolicy](../Topic/CurrentScheduler::GetPolicy%20Method.md)|擷取與目前的排程器相關聯的原則複本。|  
  
 下表列出 `Scheduler` 類別所定義的重要方法。  
  
|方法|說明|  
|--------|--------|  
|[Create](../Topic/Scheduler::Create%20Method.md)|建立會使用指定原則的 `Scheduler` 物件。|  
|[附加](../Topic/Scheduler::Attach%20Method.md)|建立 `Scheduler` 物件與目前內容的關聯。|  
|[參考資料](../Topic/Scheduler::Reference%20Method.md)|遞增 `Scheduler` 物件的參考計數器。|  
|[Release](../Topic/Scheduler::Release%20Method.md)|遞減 `Scheduler` 物件的參考計數器。|  
|[RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md)|在 `Scheduler` 物件終結時，註冊執行階段所設定的事件。|  
|[CreateScheduleGroup](../Topic/Scheduler::CreateScheduleGroup%20Method.md)|在 `Scheduler` 物件中建立 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 物件|  
|[ScheduleTask](../Topic/Scheduler::ScheduleTask%20Method.md)|從 `Scheduler` 物件排程輕量型工作。|  
|[GetPolicy](../Topic/Scheduler::GetPolicy%20Method.md)|擷取與 `Scheduler` 物件相關聯的原則複本。|  
|[SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)|設定執行階段在建立預設排程器時所使用的原則。|  
|[ResetDefaultSchedulerPolicy](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md)|將預設原則還原成呼叫 `SetDefaultSchedulerPolicy` 前的作用中原則。  如果預設排程器是在這個呼叫之後所建立的，執行階段將會使用預設原則設定來建立排程器。|  
  
 \[[上方](#top)\]  
  
##  <a name="example"></a> 範例  
 如需如何建立和管理排程器執行個體的基本範例，請參閱 [如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。  
  
## 請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [排程器原則](../../parallel/concrt/scheduler-policies.md)   
 [排程群組](../../parallel/concrt/schedule-groups.md)