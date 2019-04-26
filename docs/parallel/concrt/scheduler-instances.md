---
title: 排程器執行個體
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: 19bd871857dcef6aaef153798388c0272239fa1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180163"
---
# <a name="scheduler-instances"></a>排程器執行個體

本文件說明並行執行階段，以及如何使用排程器執行個體的角色[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)並[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)類別來建立和管理排程器執行個體。 當您想要建立明確排程原則的關聯與特定類型的工作負載，排程器執行個體很有用。 例如，您可以建立一個排程器執行個體，在高權限的執行緒優先順序上執行一些工作，並使用預設排程器在正常的執行緒優先順序上執行其他工作。

> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，建議您先使用[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)如果您是新並行執行階段。

##  <a name="top"></a> 章節

- [排程器和 CurrentScheduler 類別](#classes)

- [建立排程器執行個體](#creating)

- [管理排程器執行個體的存留期](#managing)

- [方法和功能](#features)

- [範例](#example)

##  <a name="classes"></a> 排程器和 CurrentScheduler 類別

工作排程器可讓應用程式使用一或多個*排程器執行個體*排程工作。 [Concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)類別代表排程器執行個體，並包含與排程工作的功能。

附加至排程器的執行緒就所謂*執行內容*，或簡稱*內容*。 一個排程器可以在目前內容上作用，在任何時間。 作用中的排程器就是所謂*目前的排程器*。 並行執行階段會使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)類別提供存取目前排程器。 一個內容的目前排程器可能不同於另一個內容的目前排程器。 執行階段不提供目前排程器的處理序層級表示法。

一般而言，`CurrentScheduler`類別用來存取目前的排程器。 `Scheduler`類別就很有用，當您需要管理不是目前的排程器。

下列各節說明如何建立和管理排程器執行個體。 如需說明這些工作的完整範例，請參閱[How to:管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。

[[靠上](#top)]

##  <a name="creating"></a> 建立排程器執行個體

若要建立下列三種方式`Scheduler`物件：

- 有沒有排程器時，執行階段會建立預設排程器，當您使用執行階段功能，例如平行演算法，來執行工作。 預設排程器會變成目前的排程器起始的平行工作的內容。

- [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法會建立`Scheduler`使用特定原則，並將該排程器與目前內容相關聯的物件。

- [Scheduler](reference/scheduler-class.md#create)方法會建立`Scheduler`使用特定原則，但不會將它與目前內容中關聯的物件。

讓執行階段建立預設排程器可讓所有的並行工作共用相同的排程器。 一般而言，所提供的功能[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL) 或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)用來執行平行工作。 因此，您不必直接使用排程器，控制其原則或有存留期。 當您使用 PPL] 或 [代理程式庫時，如果它不存在，並且能夠針對每個內容的目前排程器執行階段會建立預設排程器。 當您建立排程器，並將它設為目前的排程器時，執行階段會使用該排程器來排定的工作。 只有當您需要特定的排程原則，請建立額外的排程器執行個體。 如需有關排程器相關聯的原則的詳細資訊，請參閱[排程器原則](../../parallel/concrt/scheduler-policies.md)。

[[靠上](#top)]

##  <a name="managing"></a> 管理排程器執行個體的存留期

執行階段會使用參考計數機制來控制的存留期`Scheduler`物件。

當您使用`CurrentScheduler::Create`方法或`Scheduler::Create`方法，以建立`Scheduler`物件，執行階段會將該排程器的初始參考計數設定為其中一個。 當您呼叫時，執行階段會遞增參考計數[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法。 `Scheduler::Attach`方法將`Scheduler`物件與目前的內容。 這使得目前排程器。 當您呼叫`CurrentScheduler::Create`方法中，執行階段同時建立`Scheduler`物件，並將它附加至目前的內容 （和參考計數設定為其中一個）。 您也可以使用[concurrency::Scheduler::Reference](reference/scheduler-class.md#reference)方法，以遞增參考次數的`Scheduler`物件。

執行階段會遞減參考計數當您呼叫[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)方法來卸離目前的排程器，或呼叫[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法。 當參考計數到達零時，執行階段會終結`Scheduler`物件在所有排定的工作完成。 要遞增參考次數的目前排程器允許正在執行的工作。 因此，如果參考計數到達零且工作遞增參考計數，執行階段不會終結`Scheduler`物件的參考計數再次達到零，並在所有工作都完成之前。

執行階段會維護的內部堆疊`Scheduler`針對每個內容的物件。 當您呼叫`Scheduler::Attach`或是`CurrentScheduler::Create`方法，執行階段推送`Scheduler`物件至目前的內容堆疊。 這使得目前排程器。 當您呼叫`CurrentScheduler::Detach`，執行階段會取出目前的排程器，從目前的內容堆疊，並設定做為目前的排程器上的一個。

執行階段會提供數種方式可以管理排程器執行個體的存留期。 下表顯示適當的方法，會釋放，或卸離的排程器，從目前的內容，每個方法建立，或將排程器附加至目前的內容。

|建立或附加方法|釋出或 detach 方法|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

呼叫不適當版本，或中斷連結方法在執行階段會產生未指定的行為。

當您使用的功能，比方說，PPL，造成執行階段建立您的預設排程器，請勿釋放或中斷連結這個排程器。 執行階段管理，它會建立任何排程器的存留期。

因為執行階段不會終結`Scheduler`物件的所有工作都完成之前，您可以使用[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法或[concurrency:: currentscheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法收到通知時`Scheduler`物件被終結。 您必須等待所排程的每項工作時，這是很有用`Scheduler`完成的物件。

[[靠上](#top)]

##  <a name="features"></a> 方法和功能

本節將摘要說明的重要方法`CurrentScheduler`和`Scheduler`類別。

把`CurrentScheduler`與目前內容上建立的排程器使用的 helper 類別。 `Scheduler`類別可讓您控制的排程器屬於另一個內容。

下表顯示所定義的重要方法`CurrentScheduler`類別。

|方法|描述|
|------------|-----------------|
|[建立](reference/currentscheduler-class.md#create)|建立`Scheduler`會使用指定的原則，並將它與目前內容相關聯的物件。|
|[Get](reference/currentscheduler-class.md#get)|擷取的指標`Scheduler`與目前內容相關聯的物件。 這個方法不會遞增參考計數的`Scheduler`物件。|
|[Detach](reference/currentscheduler-class.md#detach)|卸離目前的排程器，從目前的內容，並設定為目前的排程器上的一個。|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|註冊執行階段設定時終結目前排程器的事件。|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|會建立[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)目前排程器中的物件。|
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|將目前的排程器排程佇列中的輕量型工作。|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|擷取一份目前的排程器相關聯的原則。|

下表顯示所定義的重要方法`Scheduler`類別。

|方法|描述|
|------------|-----------------|
|[建立](reference/scheduler-class.md#create)|建立`Scheduler`物件，使用指定的原則。|
|[Attach](reference/scheduler-class.md#attach)|將`Scheduler`物件與目前的內容。|
|[參考資料](reference/scheduler-class.md#reference)|遞增參考計數器的`Scheduler`物件。|
|[發行](reference/scheduler-class.md#release)|遞減的參考計數器`Scheduler`物件。|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|註冊執行階段設定時的事件`Scheduler`物件被終結。|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|會建立[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)物件中`Scheduler`物件。|
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|排程輕量型工作`Scheduler`物件。|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|擷取一份相關聯的原則`Scheduler`物件。|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|設定執行階段，它會建立預設排程器時所要使用的原則。|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|還原預設原則的作用中 」 的呼叫之前`SetDefaultSchedulerPolicy`。 如果預設排程器建立在這個呼叫之後，執行階段會使用預設原則設定來建立排程器。|

[[靠上](#top)]

##  <a name="example"></a> 範例

如需如何建立及管理排程器執行個體的基本範例，請參閱[How to:管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[排程器原則](../../parallel/concrt/scheduler-policies.md)<br/>
[排程群組](../../parallel/concrt/schedule-groups.md)
