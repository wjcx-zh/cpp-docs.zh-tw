---
title: CurrentScheduler 類別
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143070"
---
# <a name="currentscheduler-class"></a>CurrentScheduler 類別

代表與呼叫內容相關之目前排程器的抽象概念。

## <a name="syntax"></a>語法

```cpp
class CurrentScheduler;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[建立](#create)|建立新的排程器，其行為是由 `_Policy` 參數所描述，並將其附加至呼叫內容。 新建立的排程器會成為呼叫內容的目前排程器。|
|[CreateScheduleGroup](#createschedulegroup)|已多載。 在與呼叫內容相關聯的排程器內，建立新的排程群組。 採用參數的版本 `_Placement` 會使新建立之排程群組內的工作，在該參數指定的位置上有偏差執行。|
|[Detach](#detach)|從呼叫內容卸離目前的排程器，並將先前附加的排程器還原為目前的排程器（如果有的話）。 當這個方法傳回之後，呼叫的內容就會由先前使用 `CurrentScheduler::Create` 或 `Scheduler::Attach` 方法附加至內容的排程器來管理。|
|[Get](#get)|傳回與呼叫內容相關聯之排程器的指標，也稱為目前的排程器。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回與呼叫內容相關聯之排程器的目前虛擬處理器數目。|
|[GetPolicy](#getpolicy)|傳回用來建立目前排程器的原則複本。|
|[ID](#id)|傳回目前排程器的唯一識別碼。|
|[IsAvailableLocation](#isavailablelocation)|判斷某一特定位置是否可在目前的排程器中使用。|
|[RegisterShutdownEvent](#registershutdownevent)|當與目前內容相關聯的排程器關閉並自行終結時，會導致在 `_ShutdownEvent` 參數中傳遞的 Windows 事件控制碼收到信號。 當事件收到通知時，所有已排定排程器的工作都已完成。 多個關機事件可以透過這個方法來註冊。|
|[ScheduleTask](#scheduletask)|已多載。 在與呼叫內容相關聯的排程器中排定輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|

## <a name="remarks"></a>備註

如果沒有與呼叫內容相關聯的排程器（請參閱排程器），則 `CurrentScheduler` 類別中的許多方法都會[導致程式的](scheduler-class.md)預設排程器附加。 這也可能表示在這類呼叫期間，會建立進程的預設排程器。

## <a name="inheritance-hierarchy"></a>繼承階層

`CurrentScheduler`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="create"></a> 建立

建立新的排程器，其行為是由 `_Policy` 參數所描述，並將其附加至呼叫內容。 新建立的排程器會成為呼叫內容的目前排程器。

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>參數

*_Policy*<br/>
排程器原則，描述新建立之排程器的行為。

### <a name="remarks"></a>備註

排程器到呼叫內容的附件會以隱含方式將參考計數放在排程器上。

使用 `Create` 方法建立排程器之後，您必須在未來某個時間點呼叫[CurrentScheduler：:D etach](#detach)方法，才能讓排程器關閉。

如果從已附加至不同排程器的內容呼叫這個方法，則會將現有的排程器記憶為先前的排程器，而新建立的排程器會成為目前的排程器。 當您稍後呼叫 `CurrentScheduler::Detach` 方法時，先前的排程器會還原為目前的排程器。

這個方法可能會擲回各種不同的例外狀況，包括[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。

## <a name="createschedulegroup"></a>CreateScheduleGroup

在與呼叫內容相關聯的排程器內，建立新的排程群組。 採用參數的版本 `_Placement` 會使新建立之排程群組內的工作，在該參數指定的位置上有偏差執行。

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>參數

*_Placement*<br/>
[排程] 群組內的工作在執行時，將會有偏差的位置參考。

### <a name="return-value"></a>傳回值

新建立之排程群組的指標。 這個 `ScheduleGroup` 物件的初始參考計數會放在其上。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

當您完成排程工作時，必須在排程群組上叫用[Release](schedulegroup-class.md#release)方法。 排程器會在所有排入佇列的工作完成時，終結排程群組。

請注意，如果您明確建立此排程器，則必須先將所有參考發行至其中的排程群組，然後再將目前的內容卸離，然後再釋放它的參考。

## <a name="detach"></a>Detach

從呼叫內容卸離目前的排程器，並將先前附加的排程器還原為目前的排程器（如果有的話）。 當這個方法傳回之後，呼叫的內容就會由先前使用 `CurrentScheduler::Create` 或 `Scheduler::Attach` 方法附加至內容的排程器來管理。

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>備註

`Detach` 方法會隱含地從排程器移除參考計數。

如果沒有任何排程器附加至呼叫內容，則呼叫這個方法會導致擲回[scheduler_not_attached](scheduler-not-attached-class.md)例外狀況。

從由排程器內部和管理的內容呼叫這個方法，或使用排程器[：： Attach](scheduler-class.md#attach)或[CurrentScheduler：： Create](#create)方法以外的方法附加的內容，將會導致擲回[improper_scheduler_detach](improper-scheduler-detach-class.md)例外狀況。

## <a name="get"></a>獲取

傳回與呼叫內容相關聯之排程器的指標，也稱為目前的排程器。

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>傳回值

與呼叫內容（目前排程器）相關聯之排程器的指標。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。 這個方法所傳回的 `Scheduler` 物件不會有其他參考。

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors

傳回與呼叫內容相關聯之排程器的目前虛擬處理器數目。

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>傳回值

如果排程器與呼叫內容相關聯，則為該排程器目前的虛擬處理器數目;否則，值 `-1`。

### <a name="remarks"></a>備註

如果呼叫內容尚未與排程器相關聯，這個方法將不會產生排程器附件。

這個方法的傳回值，是與呼叫內容相關聯之排程器的虛擬處理器數目的瞬間取樣。 這個值傳回時可能已過時。

## <a name="getpolicy"></a>GetPolicy

傳回用來建立目前排程器的原則複本。

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>傳回值

用來建立目前排程器的原則複本。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

## <a name="id"></a>號

傳回目前排程器的唯一識別碼。

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>傳回值

如果排程器與呼叫內容相關聯，則為該排程器的唯一識別碼;否則，值 `-1`。

### <a name="remarks"></a>備註

如果呼叫內容尚未與排程器相關聯，這個方法將不會產生排程器附件。

## <a name="isavailablelocation"></a>IsAvailableLocation

判斷某一特定位置是否可在目前的排程器中使用。

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>參數

*_Placement*<br/>
要查詢目前排程器的位置參考。

### <a name="return-value"></a>傳回值

指出目前排程器上是否有提供 `_Placement` 引數所指定的位置。

### <a name="remarks"></a>備註

如果呼叫內容尚未與排程器相關聯，這個方法將不會產生排程器附件。

請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。

## <a name="registershutdownevent"></a>RegisterShutdownEvent

當與目前內容相關聯的排程器關閉並自行終結時，會導致在 `_ShutdownEvent` 參數中傳遞的 Windows 事件控制碼收到信號。 當事件收到通知時，所有已排定排程器的工作都已完成。 多個關機事件可以透過這個方法來註冊。

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>參數

*_ShutdownEvent*<br/>
Windows 事件物件的控制碼，執行時間會在與目前內容相關聯的排程器關閉並自行終結時收到通知。

### <a name="remarks"></a>備註

如果沒有任何排程器附加至呼叫內容，則呼叫這個方法會導致擲回[scheduler_not_attached](scheduler-not-attached-class.md)例外狀況。

## <a name="scheduletask"></a>ScheduleTask

在與呼叫內容相關聯的排程器中排定輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>參數

*_Proc*<br/>
執行輕量工作主體的函式指標。

*_Data*<br/>
將當做參數傳遞至工作主體之資料的 void 指標。

*_Placement*<br/>
輕量工作將會變成優先執行的位置參考。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
