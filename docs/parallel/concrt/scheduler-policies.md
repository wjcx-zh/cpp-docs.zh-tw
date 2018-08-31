---
title: 排程器原則 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbf9bb9fdbd930319147bfa2654915243fb8dd6a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219302"
---
# <a name="scheduler-policies"></a>排程器原則
本文件說明並行執行階段的排程器原則的角色。 A*排程器原則*控制管理工作時，會使用排程器的策略。 例如，請考慮要求某些工作執行 `THREAD_PRIORITY_NORMAL` 以及要求其他工作執行 `THREAD_PRIORITY_HIGHEST` 的應用程式。  您可以建立兩個排程器執行個體：一個將 `ContextPriority` 原則指定為 `THREAD_PRIORITY_NORMAL`，另一個將同一個原則指定為 `THREAD_PRIORITY_HIGHEST`。  
  
 使用排程器原則，您就可以分割可用處理資源，並將一組固定的資源指派給每個排程器。 例如，請考慮無法擴充超過四個處理器的平行演算法。 您可以建立排程器原則，以限制其工作，同時使用不超過四個處理器。  
  
> [!TIP]
>  並行執行階段會提供預設排程器。 因此，您不需要在應用程式中自行建立。 由於工作排程器可協助您微調應用程式的效能，建議您先使用[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)如果您是新並行執行階段。  
  
 當您使用[concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)， [scheduler](reference/scheduler-class.md#create)，或[concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)若要建立的排程器執行個體中，您所提供的方法[schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)物件，其中包含指定的排程器行為的索引鍵 / 值組的集合。 `SchedulerPolicy`建構函式接受可變數目的引數。 第一個引數是您要指定的原則項目數目。 其餘的引數是索引鍵 / 值組，每個原則項目。 下列範例會建立`SchedulerPolicy`物件，指定三個原則項目。 對於未指定的原則機碼，執行階段會使用預設值。  

  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]  
  

 [Concurrency:: policyelementkey](reference/concurrency-namespace-enums.md#policyelementkey)列舉會定義與工作排程器相關聯的原則機碼。 下表描述的原則機碼和執行階段會使用其各自的預設值。  
  
|原則金鑰|描述|預設值|  
|----------------|-----------------|-------------------|  
|`SchedulerKind`|A [concurrency:: schedulertype](reference/concurrency-namespace-enums.md#schedulertype)值，指定要用來排定工作的執行緒類型。|`ThreadScheduler` (使用一般執行緒)。 這是這個金鑰的唯一有效值。|  
|`MaxConcurrency`|`unsigned int`值，指定排程器使用的並行存取資源的數目上限。|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|  
|`MinConcurrency`|`unsigned int`值，指定排程器使用的並行存取資源的最小數目。|`1`|  
|`TargetOversubscriptionFactor`|`unsigned int`值，指定要配置給每個處理資源的幾個執行緒。|`1`|  
|`LocalContextCacheSize`|`unsigned int`值，指定本機佇列中的每個虛擬處理器的快取的內容的最大數目。|`8`|  
|`ContextStackSize`|`unsigned int`值，以 kb 為單位，要保留給每個內容中指定的堆疊大小。|`0` （使用預設堆疊大小）|  
|`ContextPriority`|`int`值，指定每個內容的執行緒優先權。 這可以是任何值，您可以傳遞給[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)或`INHERIT_THREAD_PRIORITY`。|`THREAD_PRIORITY_NORMAL`|  

|`SchedulingProtocol`|A [concurrency:: schedulingprotocoltype](reference/concurrency-namespace-enums.md#schedulingprotocoltype)值，指定要使用的排程演算法。 |`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`|A [dynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype)值，指定是否要重新平衡資源進行統計資料為基礎的進度資訊。<br /><br /> **附註**未設定此原則為`ProgressFeedbackDisabled`因為它保留供執行階段。 |`ProgressFeedbackEnabled`|  

  
 它會排程工作時，每個排程器就會使用自己的原則。 與某個排程器相關聯的原則並不會影響任何其他排程器的行為。 此外，您無法變更排程器原則建立之後`Scheduler`物件。  
  
> [!IMPORTANT]
>  您可以使用 僅排程器原則來控制執行階段建立的執行緒屬性。 不要變更執行緒同質性或執行階段所建立的執行緒優先權，因為這樣可能會造成未定義的行為發生。  
  
 如果您未明確地建立一個執行階段會建立為您的預設排程器。 如果您想要在應用程式中使用預設排程器，但您想要指定使用，呼叫該排程器原則[concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)之前在排定平行工作的方法。 如果您不能呼叫`Scheduler::SetDefaultSchedulerPolicy`方法中，執行階段會使用資料表值的預設原則。  
  
 使用[concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy)並[concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy)方法來擷取一份排程器原則。 您會收到這些方法的原則值可能不同於您在建立排程器時指定的原則值。  
  
## <a name="example"></a>範例  
 若要檢查使用特定排程器原則來控制的排程器行為的範例，請參閱[如何： 指定特定的排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)和[How to： 建立代理程式，使用特定排程器原則](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何： 指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [如何：建立使用特定排程器原則的代理程式](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

