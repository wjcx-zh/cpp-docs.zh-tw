---
title: 排程器執行個體
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: e9e9b8124254084ac30191d37d49f2ef72bd677e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142299"
---
# <a name="scheduler-instances"></a>排程器執行個體

本檔描述並行執行階段中排程器實例的角色，以及如何使用[concurrency：：](../../parallel/concrt/reference/scheduler-class.md)排程器和[Concurrency：： CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md)類別來建立和管理排程器實例。 當您想要將明確排程原則與特定類型的工作負載產生關聯時，排程器實例會很有用。 例如，您可以建立一個排程器執行個體，在高權限的執行緒優先順序上執行一些工作，並使用預設排程器在正常的執行緒優先順序上執行其他工作。

> [!TIP]
> 並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，因此如果您不熟悉並行執行階段，建議您從[平行模式程式庫（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫開始。

## <a name="top"></a> 章節

- [排程器和 CurrentScheduler 類別](#classes)

- [建立排程器實例](#creating)

- [管理排程器實例的存留期](#managing)

- [方法和功能](#features)

- [範例](#example)

## <a name="classes"></a>排程器和 CurrentScheduler 類別

工作排程器可讓應用程式使用一或多個排程器*實例*來排定工作。 [Concurrency：：](../../parallel/concrt/reference/scheduler-class.md)排程器類別代表排程器實例，並且會封裝與排程工作相關的功能。

附加至排程器的執行緒稱為*執行內容*，或只是*內容*。 一個排程器可以隨時在目前的內容上作用。 作用中排程器也稱為*目前*的排程器。 並行執行階段使用[Concurrency：： CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md)類別來提供目前排程器的存取權。 一個內容的目前排程器可能與另一個內容的目前排程器不同。 執行時間不會提供目前排程器的進程層級表示。

一般來說，`CurrentScheduler` 類別是用來存取目前的排程器。 當您需要管理的排程器不是目前的排程器時，`Scheduler` 類別會很有用。

下列各節說明如何建立和管理排程器實例。 如需說明這些工作的完整範例，請參閱[如何：管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)排程器實例。

[[靠上](#top)]

## <a name="creating"></a>建立排程器實例

建立 `Scheduler` 物件的方法有三種：

- 如果沒有排程器存在，當您使用執行時間功能（例如平行演算法）來執行工作時，執行時間會為您建立預設排程器。 預設排程器會成為起始平行工作之內容的目前排程器。

- [Concurrency：： CurrentScheduler：： Create](reference/currentscheduler-class.md#create)方法會建立一個使用特定原則的 `Scheduler` 物件，並將該排程器與目前的內容產生關聯。

- [Concurrency：：排程器：： Create](reference/scheduler-class.md#create)方法會建立一個使用特定原則的 `Scheduler` 物件，但不會將它與目前的內容產生關聯。

允許執行時間建立預設排程器，可讓所有並行工作共用相同的排程器。 通常，[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md)（PPL）或[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫所提供的功能會用來執行平行工作。 因此，您不需要直接使用排程器來控制其原則或存留期。 當您使用 PPL 或代理程式程式庫時，執行時間會建立預設排程器（如果它不存在），並使它成為每個內容的目前排程器。 當您建立排程器並將它設定為目前的排程器時，執行時間會使用該排程器來排定工作。 只有當您需要特定的排程原則時，才建立額外的排程器實例。 如需與排程器相關聯之原則的詳細資訊，請參閱排程器[原則](../../parallel/concrt/scheduler-policies.md)。

[[靠上](#top)]

## <a name="managing"></a>管理排程器實例的存留期

執行時間會使用參考計數機制來控制 `Scheduler` 物件的存留期。

當您使用 `CurrentScheduler::Create` 方法或 `Scheduler::Create` 方法來建立 `Scheduler` 物件時，執行時間會將該排程器的初始參考計數設定為一個。 當您呼叫[concurrency：：排程器：： Attach](reference/scheduler-class.md#attach)方法時，執行時間會遞增參考計數。 `Scheduler::Attach` 方法會將 `Scheduler` 物件與目前的內容產生關聯。 這會使其成為目前的排程器。 當您呼叫 `CurrentScheduler::Create` 方法時，執行時間會建立 `Scheduler` 物件，並將它附加至目前的內容（並將參考計數設定為一）。 您也可以使用[concurrency：：排程器：： Reference](reference/scheduler-class.md#reference)方法來遞增 `Scheduler` 物件的參考計數。

當您呼叫[concurrency：： CurrentScheduler：:D etach](reference/currentscheduler-class.md#detach)方法來卸離目前的排程器，或呼叫[concurrency：：排程器：： Release](reference/scheduler-class.md#release)方法時，執行時間會遞減參考計數。 當參考計數到達零時，執行時間會在所有排定的工作完成之後，終結 `Scheduler` 物件。 允許執行中的工作遞增目前排程器的參考計數。 因此，如果參考計數到達零，而工作遞增了參考計數，執行時間就不會損毀 `Scheduler` 物件，直到參考計數再次到達零，而且所有工作都完成為止。

執行時間會為每個內容維護 `Scheduler` 物件的內部堆疊。 當您呼叫 `Scheduler::Attach` 或 `CurrentScheduler::Create` 方法時，執行時間會將該 `Scheduler` 物件推送至目前內容的堆疊上。 這會使其成為目前的排程器。 當您呼叫 `CurrentScheduler::Detach`時，執行時間會從目前的內容堆疊中快顯目前的排程器，並將上一個排程器設為目前的排程器。

執行時間會提供數種方式來管理排程器實例的存留期。 下表顯示適當的方法，它會針對建立或附加排程器至目前內容的每個方法，從目前內容釋放或卸離排程器。

|Create 或 attach 方法|Release 或 detach 方法|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

呼叫不適當的釋放或卸離方法會在執行時間中產生未指定的行為。

當您使用可讓執行時間為您建立預設排程器的功能（例如 PPL）時，請勿釋放或卸離此排程器。 執行時間會管理它所建立之任何排程器的存留期。

因為執行時間不會在所有工作完成之前損毀 `Scheduler` 物件，所以您可以使用[concurrency：：排程器：： RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法或[Concurrency：： CurrentScheduler：： RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法，在終結 `Scheduler` 物件時接收通知。 當您必須等候 `Scheduler` 物件所排程的每項工作完成時，這會很有用。

[[靠上](#top)]

## <a name="features"></a>方法和功能

本節將摘要說明 `CurrentScheduler` 和 `Scheduler` 類別的重要方法。

請將 `CurrentScheduler` 類別視為協助程式，用來建立要在目前內容上使用的排程器。 `Scheduler` 類別可讓您控制屬於另一個內容的排程器。

下表顯示由 `CurrentScheduler` 類別所定義的重要方法。

|方法|描述|
|------------|-----------------|
|[建立](reference/currentscheduler-class.md#create)|建立使用指定之原則的 `Scheduler` 物件，並將它與目前的內容產生關聯。|
|[Get](reference/currentscheduler-class.md#get)|抓取與目前內容相關聯之 `Scheduler` 物件的指標。 這個方法不會遞增 `Scheduler` 物件的參考計數。|
|[Detach](reference/currentscheduler-class.md#detach)|從目前的內容卸離目前的排程器，並將上一個排程器設定為目前的排程器。|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|註冊當目前的排程器終結時，執行時間所設定的事件。|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|在目前的排程器中建立[concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)物件。|
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|將輕量工作加入目前排程器的排程佇列中。|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|抓取與目前排程器相關聯的原則複本。|

下表顯示由 `Scheduler` 類別所定義的重要方法。

|方法|描述|
|------------|-----------------|
|[建立](reference/scheduler-class.md#create)|建立使用指定之原則的 `Scheduler` 物件。|
|[附加](reference/scheduler-class.md#attach)|將 `Scheduler` 物件與目前的內容產生關聯。|
|[參考](reference/scheduler-class.md#reference)|遞增 `Scheduler` 物件的參考計數器。|
|[發行](reference/scheduler-class.md#release)|遞減 `Scheduler` 物件的參考計數器。|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|註冊當 `Scheduler` 物件終結時，執行時間所設定的事件。|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|在 `Scheduler` 物件中建立[concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)物件。|
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|從 `Scheduler` 物件排定輕量工作。|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|抓取與 `Scheduler` 物件相關聯的原則複本。|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|設定執行時間在建立預設排程器時要使用的原則。|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|將預設原則還原為 `SetDefaultSchedulerPolicy`的呼叫之前的作用中。 如果在此呼叫之後建立預設排程器，則執行時間會使用預設原則設定來建立排程器。|

[[靠上](#top)]

## <a name="example"></a> 範例

如需如何建立和管理排程器實例的基本範例，請參閱[如何：管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)排程器實例。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[排程器原則](../../parallel/concrt/scheduler-policies.md)<br/>
[排程群組](../../parallel/concrt/schedule-groups.md)
