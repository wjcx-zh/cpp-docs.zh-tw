---
title: CurrentScheduler 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27c295f1cf8c6d02721a999c46ce02d961cc3702
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419018"
---
# <a name="currentscheduler-class"></a>CurrentScheduler 類別

代表與呼叫內容相關之目前排程器的抽象概念。

## <a name="syntax"></a>語法

```
class CurrentScheduler;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[建立](#create)|建立新的排程器，其行為由所描述`_Policy`參數並將它附加至呼叫的內容。 新建立的排程器會呼叫內容的目前排程器。|
|[CreateScheduleGroup](#createschedulegroup)|多載。 建立新排程群組內呼叫的內容相關聯的排程器。 會採用參數的版本`_Placement`會導致變成優先執行在該參數所指定的位置在新建立的排程群組內的工作。|
|[Detach](#detach)|卸離目前的排程器，從呼叫的內容，並還原先前附加的排程器，做為目前的排程器，如果有的話。 這個方法傳回之後，呼叫的內容則由先前已附加至內容使用的排程器`CurrentScheduler::Create`或`Scheduler::Attach`方法。|
|[Get](#get)|讓指標回到呼叫的內容，也稱為目前排程器相關聯的排程器。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回與呼叫內容相關聯的排程器目前的虛擬處理器數目。|
|[GetPolicy](#getpolicy)|傳回一份目前的排程器所建立的原則。|
|[Id](#id)|傳回目前的排程器的唯一識別碼。|
|[IsAvailableLocation](#isavailablelocation)|判斷某一特定位置是否可在目前的排程器中使用。|
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件控制代碼傳遞的原因`_ShutdownEvent`收到訊號時與目前內容相關聯的排程器關閉並終結本身的參數。 在事件收到訊號時，所有已排程器已排程的工作已完成。 透過這個方法，可以註冊多個關機的事件。|
|[ScheduleTask](#scheduletask)|多載。 排程與呼叫內容相關聯的排程器內的輕量級工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|

## <a name="remarks"></a>備註

如果沒有任何排程器 (請參閱[排程器](scheduler-class.md)) 呼叫的內容中的許多方法相關聯`CurrentScheduler`類別將會導致處理序的預設排程器的附件。 這也可能表示這類呼叫時，就會建立該處理序的預設排程器。

## <a name="inheritance-hierarchy"></a>繼承階層

`CurrentScheduler`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="create"></a> 建立

建立新的排程器，其行為由所描述`_Policy`參數並將它附加至呼叫的內容。 新建立的排程器會呼叫內容的目前排程器。

```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>參數

*政策 （_p)*<br/>
排程器原則，告訴您新建立的排程器的行為。

### <a name="remarks"></a>備註

排程器的附件，以呼叫的內容會隱含地會排程器的參考計數。

使用排程器建立之後`Create`方法，您必須呼叫[currentscheduler:: Detach](#detach)在某個時間點以後，以便關閉的排程器的方法。

如果從已在現有的排程器會記住先前的排程器，為不同的排程器中，附加的內容會呼叫這個方法，新建立的排程器會變成目前的排程器。 當您呼叫`CurrentScheduler::Detach`方法之後，先前的排程器會還原為目前的排程器。

這個方法可以擲回例外狀況，包括各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)並[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。

##  <a name="createschedulegroup"></a> CreateScheduleGroup

建立新排程群組內呼叫的內容相關聯的排程器。 會採用參數的版本`_Placement`會導致變成優先執行在該參數所指定的位置在新建立的排程群組內的工作。

```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>參數

*放置 （_p)*<br/>
其中排程群組內的工作將會變成優先執行的位置參考。

### <a name="return-value"></a>傳回值

新建立的排程群組指標。 這`ScheduleGroup`物件具有初始參考計數放在其上。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

您必須叫用[發行](schedulegroup-class.md#release)排程群組時完成它的排程工作的方法。 排程器將會損毀排程時所有的工作排入佇列至該群組已完成。

請注意，是否您明確建立此排程器，您必須釋放排程群組內，在發行排程器中，您參考中斷連結目前的內容，從它之前的所有參考。

##  <a name="detach"></a> 卸離

卸離目前的排程器，從呼叫的內容，並還原先前附加的排程器，做為目前的排程器，如果有的話。 這個方法傳回之後，呼叫的內容則由先前已附加至內容使用的排程器`CurrentScheduler::Create`或`Scheduler::Attach`方法。

```
static void __cdecl Detach();
```

### <a name="remarks"></a>備註

`Detach`方法會隱含地移除排程器的參考計數。

如果沒有任何附加至呼叫內容的排程器，呼叫這個方法會導致[scheduler_not_attached](scheduler-not-attached-class.md)擲回例外狀況。

內部和由排程器或在已附加以外使用的方法呼叫這個方法從內容就[scheduler:: attach](scheduler-class.md#attach)或是[currentscheduler:: Create](#create)方法將會導致[improper_scheduler_detach](improper-scheduler-detach-class.md)擲回例外狀況。

##  <a name="get"></a> 取得

讓指標回到呼叫的內容，也稱為目前排程器相關聯的排程器。

```
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>傳回值

呼叫的內容 （目前的排程器） 相關聯的排程器指標。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。 沒有額外的參考會放在`Scheduler`這個方法所傳回的物件。

##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors

傳回與呼叫內容相關聯的排程器目前的虛擬處理器數目。

```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>傳回值

如果排程器呼叫的內容，該排程器; 的虛擬處理器的數目與相關聯否則，值`-1`。

### <a name="remarks"></a>備註

這個方法不會導致排程器附件如果呼叫的內容尚未排程器相關聯。

這個方法的傳回值是排程器與呼叫內容相關聯的虛擬處理器數目的瞬間取樣。 這個值傳回時可能已過時。

##  <a name="getpolicy"></a> GetPolicy

傳回一份目前的排程器所建立的原則。

```
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>傳回值

使用所建立的目前排程器原則的複本。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

##  <a name="id"></a> Id

傳回目前的排程器的唯一識別碼。

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>傳回值

如果與呼叫的內容，該排程器; 的唯一識別碼相關聯的排程器否則，值`-1`。

### <a name="remarks"></a>備註

這個方法不會導致排程器附件如果呼叫的內容尚未排程器相關聯。

##  <a name="isavailablelocation"></a> IsAvailableLocation

判斷某一特定位置是否可在目前的排程器中使用。

```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>參數

*放置 （_p)*<br/>
要查詢目前排程器的位置參考。

### <a name="return-value"></a>傳回值

指出目前排程器上是否有提供 `_Placement` 引數所指定的位置。

### <a name="remarks"></a>備註

這個方法不會導致排程器附件如果呼叫的內容尚未排程器相關聯。

請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。

##  <a name="registershutdownevent"></a> RegisterShutdownEvent

Windows 事件控制代碼傳遞的原因`_ShutdownEvent`收到訊號時與目前內容相關聯的排程器關閉並終結本身的參數。 在事件收到訊號時，所有已排程器已排程的工作已完成。 透過這個方法，可以註冊多個關機的事件。

```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>參數

*_ShutdownEvent*<br/>
這個信號會在執行階段時與目前內容相關聯的排程器關閉並終結本身的 Windows 事件物件的控制代碼。

### <a name="remarks"></a>備註

如果沒有任何附加至呼叫內容的排程器，呼叫這個方法會導致[scheduler_not_attached](scheduler-not-attached-class.md)擲回例外狀況。

##  <a name="scheduletask"></a> ScheduleTask

排程與呼叫內容相關聯的排程器內的輕量級工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。

```
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
若要執行的輕量工作主體執行該函式指標。

*資料 （_d)*<br/>
將做為參數傳遞至工作的主體資料的 void 指標。

*放置 （_p)*<br/>
輕量工作將會變成優先執行的位置參考。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

