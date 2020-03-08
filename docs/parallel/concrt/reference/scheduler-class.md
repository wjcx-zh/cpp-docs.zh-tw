---
title: Scheduler 類別
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 77ad876b8352ab1ae86fde622b05712ec5f2cea9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867120"
---
# <a name="scheduler-class"></a>Scheduler 類別

代表並行執行階段排程器的抽象概念。

## <a name="syntax"></a>語法

```cpp
class Scheduler;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[排程器](#ctor)|`Scheduler` 類別的物件只能使用 factory 方法或隱含方式建立。|
|[~ 排程器析構函式](#dtor)|當所有外部參考都停止存在時，`Scheduler` 類別的物件會隱含地終結。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[附加](#attach)|將排程器附加至呼叫內容。 這個方法傳回之後，呼叫的內容會由排程器管理，而排程器會成為目前的排程器。|
|[建立](#create)|建立新的排程器，其行為是由 `_Policy` 參數所描述，將初始參考放在排程器上，並傳回它的指標。|
|[CreateScheduleGroup](#createschedulegroup)|已多載。 在排程器中建立新的排程群組。 採用參數的版本 `_Placement` 會使新建立之排程群組內的工作，在該參數指定的位置上有偏差執行。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回排程器目前的虛擬處理器數目。|
|[GetPolicy](#getpolicy)|傳回用來建立排程器的原則複本。|
|[Id](#id)|傳回排程器的唯一識別碼。|
|[IsAvailableLocation](#isavailablelocation)|判斷排程器上是否有指定的位置。|
|[參考](#reference)|遞增排程器的參考計數。|
|[RegisterShutdownEvent](#registershutdownevent)|當排程器關閉並終結其本身時，會導致在 `_Event` 參數中傳遞的 Windows 事件控制碼收到信號。 當事件收到通知時，所有已排定排程器的工作都已完成。 多個關機事件可以透過這個方法來註冊。|
|[版本](#release)|遞減排程器的參考計數。|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|將預設排程器原則重設為執行時間預設值。 下次建立預設排程器時，將會使用執行時間預設原則設定。|
|[ScheduleTask](#scheduletask)|已多載。 排定排程器內的輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|允許使用使用者定義的原則來建立預設排程器。 只有在進程內沒有預設排程器時，才能呼叫這個方法。 設定預設原則之後，它會持續有效，直到下一次有效呼叫 `SetDefaultSchedulerPolicy` 或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法為止。|

## <a name="remarks"></a>備註

並行執行階段排程器會使用執行內容，其對應至作業系統執行內容（例如執行緒），以執行您的應用程式排入佇列的工作。 排程器的並行層級會在任何時候，等於 Resource Manager 所授與的虛擬處理器數目。 虛擬處理器是處理資源的抽象概念，會對應到基礎系統上的硬體執行緒。 只有單一排程器內容可以在指定時間于虛擬處理器上執行。

並行執行階段將會為每個進程建立預設排程器，以執行平行工作。 此外，您還可以建立自己的排程器實例，並使用這個類別來操作它。

## <a name="inheritance-hierarchy"></a>繼承階層

`Scheduler`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="attach"></a>連

將排程器附加至呼叫內容。 這個方法傳回之後，呼叫的內容會由排程器管理，而排程器會成為目前的排程器。

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>備註

附加排程器會以隱含方式將參考放在排程器上。

在未來的某個時間點，您必須呼叫[CurrentScheduler：:D etach](currentscheduler-class.md#detach)方法，才能讓排程器關閉。

如果從已附加至不同排程器的內容呼叫這個方法，則會將現有的排程器記憶為先前的排程器，而新建立的排程器會成為目前的排程器。 當您稍後呼叫 `CurrentScheduler::Detach` 方法時，先前的排程器會還原為目前的排程器。

如果此排程器是目前呼叫內容的排程器，這個方法將會擲回[improper_scheduler_attach](improper-scheduler-attach-class.md)例外狀況。

## <a name="create"></a> 建立

建立新的排程器，其行為是由 `_Policy` 參數所描述，將初始參考放在排程器上，並傳回它的指標。

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>參數

*_Policy*<br/>
排程器原則，描述新建立之排程器的行為。

### <a name="return-value"></a>傳回值

新建立之排程器的指標。 這個 `Scheduler` 物件的初始參考計數會放在其上。

### <a name="remarks"></a>備註

使用 `Create` 方法建立排程器之後，您必須在未來某個時間點呼叫 `Release` 方法，才能移除初始參考計數並允許排程器關閉。

使用這個方法建立的排程器不會附加至呼叫內容。 它可以使用[Attach](#attach)方法附加至內容。

這個方法可能會擲回各種不同的例外狀況，包括[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。

## <a name="createschedulegroup"></a>CreateScheduleGroup

在排程器中建立新的排程群組。 採用參數的版本 `_Placement` 會使新建立之排程群組內的工作，在該參數指定的位置上有偏差執行。

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>參數

*_Placement*<br/>
[排程] 群組內的工作在執行時，會有偏差的位置參考。

### <a name="return-value"></a>傳回值

新建立之排程群組的指標。 這個 `ScheduleGroup` 物件的初始參考計數會放在其上。

### <a name="remarks"></a>備註

當您完成排程工作時，必須在排程群組上叫用[Release](schedulegroup-class.md#release)方法。 排程器會在所有排入佇列的工作完成時，終結排程群組。

請注意，如果您明確建立此排程器，您必須在發行排程器的參考之前，先釋放所有參考，以便在其中排程群組。

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors

傳回排程器目前的虛擬處理器數目。

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>傳回值

排程器目前的虛擬處理器數目。

## <a name="getpolicy"></a>GetPolicy

傳回用來建立排程器的原則複本。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>傳回值

建立排程器時所使用之原則的複本。

## <a name="id"></a>號

傳回排程器的唯一識別碼。

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>傳回值

排程器的唯一識別碼。

## <a name="isavailablelocation"></a>IsAvailableLocation

判斷排程器上是否有指定的位置。

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>參數

*_Placement*<br/>
要查詢排程器之位置的參考。

### <a name="return-value"></a>傳回值

表示排程器上是否有 `_Placement` 引數所指定的位置。

### <a name="remarks"></a>備註

請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。

## <a name="reference"></a>證明

遞增排程器的參考計數。

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>傳回值

新遞增的參考計數。

### <a name="remarks"></a>備註

這通常用來管理撰寫排程器的存留期。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。

如果呼叫 `Reference` 方法之前的參考計數為零，且從排程器未擁有的內容進行呼叫，此方法將會擲回[improper_scheduler_reference](improper-scheduler-reference-class.md)例外狀況。

## <a name="registershutdownevent"></a>RegisterShutdownEvent

當排程器關閉並終結其本身時，會導致在 `_Event` 參數中傳遞的 Windows 事件控制碼收到信號。 當事件收到通知時，所有已排定排程器的工作都已完成。 多個關機事件可以透過這個方法來註冊。

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>參數

*_Event*<br/>
Windows 事件物件的控制碼，執行時間會在排程器關閉並終結本身時收到通知。

## <a name="release"></a>版本

遞減排程器的參考計數。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

新遞減的參考計數。

### <a name="remarks"></a>備註

這通常用來管理撰寫排程器的存留期。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。

## <a name="resetdefaultschedulerpolicy"></a>ResetDefaultSchedulerPolicy

將預設排程器原則重設為執行時間預設值。 下次建立預設排程器時，將會使用執行時間預設原則設定。

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>備註

在進程內有預設排程器時，可以呼叫這個方法。 它不會影響現有預設排程器的原則。 不過，如果要關閉預設排程器，並在稍後建立新的預設排程器，則新的排程器會使用執行時間預設原則設定。

## <a name="ctor"></a>日程

`Scheduler` 類別的物件只能使用 factory 方法或隱含方式建立。

```cpp
Scheduler();
```

### <a name="remarks"></a>備註

當您使用許多需要將排程器附加至呼叫內容的執行時間函數時，就會隱含地建立進程的預設排程器。 `CurrentScheduler` 類別中的方法和 PPL 和代理程式層級的功能，通常會執行隱含的附件。

您也可以透過 `CurrentScheduler::Create` 方法或 `Scheduler::Create` 方法，明確建立排程器。

## <a name="dtor"></a>~ 排程器

當所有外部參考都停止存在時，`Scheduler` 類別的物件會隱含地終結。

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a>ScheduleTask

排定排程器內的輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>參數

*_Proc*<br/>
執行輕量工作主體的函式指標。

*_Data*<br/>
將當做參數傳遞至工作主體之資料的 void 指標。

*_Placement*<br/>
輕量工作將會變成優先執行的位置參考。

## <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy

允許使用使用者定義的原則來建立預設排程器。 只有在進程內沒有預設排程器時，才能呼叫這個方法。 設定預設原則之後，它會持續有效，直到下一次有效呼叫 `SetDefaultSchedulerPolicy` 或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法為止。

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>參數

*_Policy*<br/>
要設定為預設排程器原則的原則。

### <a name="remarks"></a>備註

如果在處理常式內已有預設排程器時呼叫 `SetDefaultSchedulerPolicy` 方法，執行時間將會擲回[default_scheduler_exists](default-scheduler-exists-class.md)例外狀況。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
