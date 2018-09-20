---
title: 排程群組 |Microsoft Docs
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
ms.openlocfilehash: 4fa61772af96ba0d2602ff42a6a43b2b3a13a4e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385895"
---
# <a name="schedule-groups"></a>排程群組

本文件說明並行執行階段的排程群組的角色。 A*排程群組*建立親和性，或組合在一起，相關的工作。 每個排程器有一或多個排程群組。 當您需要在工作之間有高度位置關係時 (例如一個相關工作的群組可因為在相同處理器節點上執行而受益)，請使用排程群組。 相反地，使用排程器執行個體，當您的應用程式都有特定品質需求，比方說，當您想要限制配置給一組工作的處理資源的數量。 如需有關排程器執行個體的詳細資訊，請參閱 <<c0> [ 排程器執行個體](../../parallel/concrt/scheduler-instances.md)。

> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，建議您先使用[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)如果您是新並行執行階段。

每個`Scheduler`物件已排程的每個節點的預設排程群組。 A*排程節點*對應至基礎的系統拓撲。 執行階段會建立一個排程的節點，對於每個處理器套件或非統一記憶體架構 (NUMA) 節點，大於任何數字。 如果您不使用排程群組明確關聯的工作，排程器會選擇要加入至工作群組。

`SchedulingProtocol`排程器原則會影響排程器執行所在的每個排程群組中的工作順序。 當`SchedulingProtocol`設為`EnhanceScheduleGroupLocality`（此為預設值），工作排程器從它正在進行時目前的工作完成，或以合作方式會產生排程群組中選擇 下一項工作。 工作排程器會搜尋目前排程群組的工作之前就會移至下一個可用的群組。 相反地，當`SchedulingProtocol`設為`EnhanceForwardProgress`之後每個工作完成或產生, 排程器將移至下一個排程群組。 如需比較這些原則的範例，請參閱 <<c0> [ 如何： 使用排程群組的執行順序影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

執行階段會使用[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)類別來代表排程群組。 若要建立`ScheduleGroup`物件，請呼叫[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)或是[concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)方法。 執行階段會使用參考計數機制來控制的存留期`ScheduleGroup`物件，就如同使用`Scheduler`物件。 當您建立`ScheduleGroup`物件，其中一個計數器的執行階段設定的參考。 [Concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference)方法的參考計數器遞增一。 [Schedulegroup](reference/schedulegroup-class.md#release)方法遞減一個參考計數器。

並行執行階段中的許多類型可讓您將建立關聯的物件，以及排程群組。 例如， [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)這類類別和訊息區類別[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)， [concurrency:: join](../../parallel/concrt/reference/join-class.md)，和並行存取::[計時器](reference/timer-class.md)，提供多載建構函式版本採用`ScheduleGroup`物件。 執行階段會使用`Scheduler`與此相關聯的物件`ScheduleGroup`排程工作的物件。

您也可以使用[concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask)來排程輕量型工作的方法。 如需輕量型工作的詳細資訊，請參閱[輕量型工作](../../parallel/concrt/lightweight-tasks.md)。

## <a name="example"></a>範例

如需範例，會使用排程群組來控制工作執行的順序，請參閱[如何： 使用排程群組的執行順序影響](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[排程器執行個體](../../parallel/concrt/scheduler-instances.md)<br/>
[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

