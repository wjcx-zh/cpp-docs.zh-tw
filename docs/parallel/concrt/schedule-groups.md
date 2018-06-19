---
title: 排程群組 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1395fbc58d8a4d1d06cd93eea21c0f3d2dec8c6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688787"
---
# <a name="schedule-groups"></a>排程群組
本文件說明並行執行階段中的排程群組的角色。 A*排程群組*視為，或分組，相關的工作。 每一個排程器有一或多個排程群組。 當您需要在工作之間有高度位置關係時 (例如一個相關工作的群組可因為在相同處理器節點上執行而受益)，請使用排程群組。 當您的應用程式都有特定品質需求，例如，當您想要限制配置給一組工作的處理資源量，相反地，使用排程器執行個體。 如需排程器執行個體的詳細資訊，請參閱[排程器執行個體](../../parallel/concrt/scheduler-instances.md)。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，我們建議您開始[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)如果您是新的並行執行階段。  
  
 每個`Scheduler`物件已排程的每個節點的預設排程群組。 A*排程節點*對應至基礎的系統拓撲。 執行階段會建立一個排程的節點，每個處理器封裝或非統一記憶體架構 (NUMA) 節點，大於任何數字。 如果您執行不明確關聯工作的排程群組，由排程器選擇要加入至工作群組。  
  
 `SchedulingProtocol`排程器原則會影響排程器會執行每個排程群組中的工作順序。 當`SchedulingProtocol`設`EnhanceScheduleGroupLocality`（此為預設值），工作排程器從它正在處理目前的工作完成，或以合作方式讓時的排程群組中選擇 下一項工作。 工作排程器會搜尋目前的排程群組的工作之前會移至下一個可用的群組。 相反地，當`SchedulingProtocol`設`EnhanceForwardProgress`，在每一項工作完成後，或者會產生排程器將移至下一個排程群組。 如需比較這些原則的範例，請參閱[How to： 使用排程群組的執行順序影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  

 執行階段使用[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)類別來代表排程群組。 若要建立`ScheduleGroup`物件，呼叫[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)或[concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)方法。 執行階段會使用參考計數機制來控制的存留期`ScheduleGroup`物件，就如同使用`Scheduler`物件。 當您建立`ScheduleGroup`物件，其中一個計數器的執行階段設定的參考。 [Schedulegroup](reference/schedulegroup-class.md#reference)方法的參考計數器遞增一。 [Schedulegroup](reference/schedulegroup-class.md#release)方法遞減參考計數器以其中一個。  
  
 並行執行階段中的許多類型可讓您將物件與排程群組產生關聯。 例如， [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)類別和訊息區之類的類別[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)， [concurrency:: join](../../parallel/concrt/reference/join-class.md)，和 concurrency::[計時器](reference/timer-class.md)，提供的建構函式多載的版本採用`ScheduleGroup`物件。 執行階段使用`Scheduler`與此相關聯的物件`ScheduleGroup`排程工作的物件。  
  
 您也可以使用[concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask)方法來排程輕量型工作。 如需輕量型工作的詳細資訊，請參閱[輕量型工作](../../parallel/concrt/lightweight-tasks.md)。  

  
## <a name="example"></a>範例  
 如需範例，會使用排程群組來控制工作執行的順序，請參閱[How to： 使用排程群組的執行順序影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [排程器執行個體](../../parallel/concrt/scheduler-instances.md)   
 [如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

