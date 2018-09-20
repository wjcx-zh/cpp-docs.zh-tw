---
title: Scheduler 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 745ab1f4f992591927be101521e0f2902af0ccd7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448269"
---
# <a name="scheduler-class"></a>Scheduler 類別

代表並行執行階段排程器的抽象概念。

## <a name="syntax"></a>語法

```
class Scheduler;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[排程器](#ctor)|物件的`Scheduler`類別可以只使用 factory 方法，建立或隱含的方式。|
|[~ Scheduler 解構函式](#dtor)|物件的`Scheduler`不再存在於所有外部參考時，將以隱含方式終結類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Attach](#attach)|將排程器附加至呼叫的內容。 這個方法傳回之後，呼叫的內容由排程器和排程器會變成目前的排程器。|
|[建立](#create)|建立新的排程器，其行為由所描述`_Policy`參數，會在排程器，將初始的參考，並讓指標回到。|
|[CreateScheduleGroup](#createschedulegroup)|多載。 建立新的排程群組，則排程器內。 會採用參數的版本`_Placement`會導致變成優先執行在該參數所指定的位置在新建立的排程群組內的工作。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回排程器目前的虛擬處理器數目。|
|[GetPolicy](#getpolicy)|傳回以建立排程器原則的複本。|
|[Id](#id)|排程器傳回的唯一識別碼。|
|[IsAvailableLocation](#isavailablelocation)|判斷指定的位置是否可用排程器上。|
|[參考資料](#reference)|遞增排程器參考計數。|
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件控制代碼傳遞的原因`_Event`收到訊號時，排程器關閉並終結本身的參數。 在事件收到訊號時，所有已排程器已排程的工作已完成。 透過這個方法，可以註冊多個關機的事件。|
|[發行](#release)|遞減排程器的參考計數。|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|將預設排程器原則重設為執行階段預設值。 下一次建立預設排程器時，它會使用執行階段的預設原則設定。|
|[ScheduleTask](#scheduletask)|多載。 排程的排程器內的輕量級工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|可讓使用者定義原則，以用來建立預設排程器。 只有在沒有預設排程器存在於處理程序時，才可以呼叫這個方法。 設定預設原則之後，就會生效，直到下次有效呼叫其中一個`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。|

## <a name="remarks"></a>備註

並行執行階段排程器會使用對應至作業系統的執行內容，例如執行緒的執行內容，來執行工作排入佇列，您的應用程式。 在任何時間，排程器的並行層級等於授與資源管理員的虛擬處理器數目。 虛擬處理器是處理序的資源和對應至基礎的系統上的硬體執行緒的抽象概念。 只在單一排程器的內容可以在虛擬處理器上執行，在指定的時間。

並行執行階段會建立每個程序來執行平行工作的預設排程器。 此外，您可以建立您自己的排程器執行個體，並操作使用這個類別。

## <a name="inheritance-hierarchy"></a>繼承階層

`Scheduler`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="attach"></a> 附加

將排程器附加至呼叫的內容。 這個方法傳回之後，呼叫的內容由排程器和排程器會變成目前的排程器。

```
virtual void Attach() = 0;
```

### <a name="remarks"></a>備註

隱含附加排程器置於排程器的參考。

在某個時間點以後，您必須呼叫[currentscheduler:: Detach](currentscheduler-class.md#detach)方法，以允許要關閉的排程器。

如果從已在現有的排程器會記住先前的排程器，為不同的排程器中，附加的內容會呼叫這個方法，新建立的排程器會變成目前的排程器。 當您呼叫`CurrentScheduler::Detach`方法之後，先前的排程器會還原為目前的排程器。

這個方法會擲回[improper_scheduler_attach](improper-scheduler-attach-class.md)這個排程器目前的排程器，呼叫內容的例外狀況。

##  <a name="create"></a> 建立

建立新的排程器，其行為由所描述`_Policy`參數，會在排程器，將初始的參考，並讓指標回到。

```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>參數

*政策 （_p)*<br/>
排程器原則，告訴您新建立的排程器的行為。

### <a name="return-value"></a>傳回值

新建立的排程器指標。 這`Scheduler`物件具有初始參考計數放在其上。

### <a name="remarks"></a>備註

使用排程器建立之後`Create`方法，您必須呼叫`Release`在某個時間點以後，才能移除初始的參考計數，並允許要關閉的排程器的方法。

這個方法建立的排程器不會附加至呼叫內容中。 它可以附加至內容，使用[附加](#attach)方法。

這個方法可以擲回例外狀況，包括各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)並[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。

##  <a name="createschedulegroup"></a> CreateScheduleGroup

建立新的排程群組，則排程器內。 會採用參數的版本`_Placement`會導致變成優先執行在該參數所指定的位置在新建立的排程群組內的工作。

```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>參數

*放置 （_p)*<br/>
排程群組內的工作將會優先於執行的位置參考。

### <a name="return-value"></a>傳回值

新建立的排程群組指標。 這`ScheduleGroup`物件具有初始參考計數放在其上。

### <a name="remarks"></a>備註

您必須叫用[發行](schedulegroup-class.md#release)排程群組時完成它的排程工作的方法。 排程器將會損毀排程時所有的工作排入佇列至該群組已完成。

請注意，是否您明確建立此排程器，您必須釋放排程群組內後, 再發行您的參考，排程器上的所有參考。

##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors

傳回排程器目前的虛擬處理器數目。

```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>傳回值

目前的排程器的虛擬處理器數目。

##  <a name="getpolicy"></a> GetPolicy

傳回以建立排程器原則的複本。

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>傳回值

使用所建立的排程器原則的複本。

##  <a name="id"></a> Id

排程器傳回的唯一識別碼。

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>傳回值

排程器的唯一識別碼。

##  <a name="isavailablelocation"></a> IsAvailableLocation

判斷指定的位置是否可用排程器上。

```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>參數

*放置 （_p)*<br/>
若要查詢有關的排程器的位置參考。

### <a name="return-value"></a>傳回值

表示是否藉由指定的位置`_Placement`引數是使用排程器上。

### <a name="remarks"></a>備註

請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。

##  <a name="reference"></a> 參考

遞增排程器參考計數。

```
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>傳回值

新遞增的參考計數。

### <a name="remarks"></a>備註

這通常用來管理排程器的存留期的組合。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。

方法會擲回[improper_scheduler_reference](improper-scheduler-reference-class.md)例外狀況的參考計數之前呼叫如果`Reference`方法是零，並從排程器並未擁有的內容進行呼叫。

##  <a name="registershutdownevent"></a> RegisterShutdownEvent

Windows 事件控制代碼傳遞的原因`_Event`收到訊號時，排程器關閉並終結本身的參數。 在事件收到訊號時，所有已排程器已排程的工作已完成。 透過這個方法，可以註冊多個關機的事件。

```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>參數

*（_e)*<br/>
這個信號會在執行階段時，排程器關閉並終結本身的 Windows 事件物件的控制代碼。

##  <a name="release"></a> 版本

遞減排程器的參考計數。

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

新遞減參考計數。

### <a name="remarks"></a>備註

這通常用來管理排程器的存留期的組合。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。

##  <a name="resetdefaultschedulerpolicy"></a> ResetDefaultSchedulerPolicy

將預設排程器原則重設為執行階段預設值。 下一次建立預設排程器時，它會使用執行階段的預設原則設定。

```
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>備註

在程序中存在的預設排程器時，可以呼叫這個方法。 它不會影響現有的預設排程器原則。 不過，如果預設排程器已關閉，並且在稍後的時間點上建立新的預設值，則新的排程器會使用執行階段的預設原則設定。

##  <a name="ctor"></a> 排程器

物件的`Scheduler`類別可以只使用 factory 方法，建立或隱含的方式。

```
Scheduler();
```

### <a name="remarks"></a>備註

您可以利用許多執行階段函式需要排程器附加至呼叫的內容時，會隱含地建立該處理序的預設排程器。 方法內`CurrentScheduler`類別和 PPL 與代理程式的圖層的功能通常會執行隱含的附件。

您也可以建立明確透過排程器`CurrentScheduler::Create`方法或`Scheduler::Create`方法。

##  <a name="dtor"></a> ~ 排程器

物件的`Scheduler`不再存在於所有外部參考時，將以隱含方式終結類別。

```
virtual ~Scheduler();
```

##  <a name="scheduletask"></a> ScheduleTask

排程的排程器內的輕量級工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。

```
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
若要執行的輕量工作主體執行該函式指標。

*資料 （_d)*<br/>
將做為參數傳遞至工作的主體資料的 void 指標。

*放置 （_p)*<br/>
輕量工作將會變成優先執行的位置參考。

##  <a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy

可讓使用者定義原則，以用來建立預設排程器。 只有在沒有預設排程器存在於處理程序時，才可以呼叫這個方法。 設定預設原則之後，就會生效，直到下次有效呼叫其中一個`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。

```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>參數

*政策 （_p)*<br/>
要設定為預設的排程器原則的原則。

### <a name="remarks"></a>備註

如果`SetDefaultSchedulerPolicy`處理序中的預設排程器已存在時，會呼叫方法，執行階段會擲回[default_scheduler_exists](default-scheduler-exists-class.md)例外狀況。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

