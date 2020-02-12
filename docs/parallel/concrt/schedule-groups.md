---
title: 排程群組
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: 1765c10f4cf8fe499aed1a140d2bba1ecaaf2300
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142303"
---
# <a name="schedule-groups"></a>排程群組

本檔說明並行執行階段中排程群組的角色。 *排程群組*會將相關的工作如何或群組在一起。 每個排程器都有一或多個排程群組。 當您需要在工作之間有高度位置關係時 (例如一個相關工作的群組可因為在相同處理器節點上執行而受益)，請使用排程群組。 相反地，當您的應用程式具有特定品質需求時（例如，當您想要限制配置給一組工作的處理資源數量）時，請使用排程器實例。 如需有關排程器實例的詳細資訊，請參閱排程器[實例](../../parallel/concrt/scheduler-instances.md)。

> [!TIP]
> 並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，因此如果您不熟悉並行執行階段，建議您從[平行模式程式庫（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫開始。

每個 `Scheduler` 物件都有每個排程節點的預設排程群組。 *排程節點*會對應到基礎系統拓撲。 執行時間會為每個處理器套件或非統一記憶體架構（NUMA）節點建立一個排程節點，以較大者為准。 如果您沒有明確地將工作與排程群組建立關聯，排程器會選擇要新增工作的群組。

`SchedulingProtocol` 排程器原則會影響排程器在每個排程群組中執行工作的順序。 當 `SchedulingProtocol` 設定為 `EnhanceScheduleGroupLocality` （這是預設值）時，工作排程器會從目前工作完成或以合作方式產生的排程群組中，選擇下一個工作。 工作排程器會先在目前的排程群組中搜尋工作，然後再移至下一個可用的群組。 相反地，當 `SchedulingProtocol` 設定為 `EnhanceForwardProgress`時，排程器會在每個工作完成或產生之後，移至下一個排程群組。 如需比較這些原則的範例，請參閱[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

執行時間會使用[concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)類別來代表排程群組。 若要建立 `ScheduleGroup` 物件，請呼叫[concurrency：： CurrentScheduler：： CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)或[concurrency：：排程器：： CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)方法。 執行時間會使用參考計數機制來控制 `ScheduleGroup` 物件的存留期，就如同處理 `Scheduler` 物件一樣。 當您建立 `ScheduleGroup` 物件時，執行時間會將參考計數器設定為一個。 [Concurrency：： ScheduleGroup：： reference](reference/schedulegroup-class.md#reference)方法會將參考計數器遞增一。 [Concurrency：： ScheduleGroup：： Release](reference/schedulegroup-class.md#release)方法會將參考計數器減一。

並行執行階段中的許多類型可讓您將物件與排程群組建立關聯。 例如，concurrency：： [agent](../../parallel/concrt/reference/agent-class.md)類別和訊息區塊類別（例如[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)、 [concurrency：： join](../../parallel/concrt/reference/join-class.md)和 concurrency：：[timer](reference/timer-class.md)）提供了接受 `ScheduleGroup` 物件之函式的多載版本。 執行時間會使用與此 `ScheduleGroup` 物件相關聯的 `Scheduler` 物件來排程工作。

您也可以使用[concurrency：： ScheduleGroup：： ScheduleTask](reference/schedulegroup-class.md#scheduletask)方法來排程輕量工作。 如需輕量工作的詳細資訊，請參閱[輕量](../../parallel/concrt/lightweight-tasks.md)工作。

## <a name="example"></a>範例

如需使用排程群組來控制工作執行順序的範例，請參閱[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[排程器執行個體](../../parallel/concrt/scheduler-instances.md)<br/>
[如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
