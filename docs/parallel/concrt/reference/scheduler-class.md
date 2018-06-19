---
title: Scheduler 類別 |Microsoft 文件
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
ms.openlocfilehash: 97abec33d5fa4b372bc26874fd37397a2b78bb29
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693675"
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
|[排程器](#ctor)|物件的`Scheduler`類別可以僅使用 factory 方法，建立或隱含的方式。|  
|[~ Scheduler 解構函式](#dtor)|物件的`Scheduler`隱含終結類別之前就不再存在於所有外部參考時。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Attach](#attach)|將排程器附加至呼叫的內容。 這個方法傳回之後，呼叫的內容是由管理排程器並排程器會變成目前的排程器。|  
|[建立](#create)|建立新的排程器所描述的行為`_Policy`參數，將初始參考放置於排程器，而且傳回的指標。|  
|[CreateScheduleGroup](#createschedulegroup)|多載。 建立新的排程群組內的排程器。 接受參數的版本`_Placement`會導致新建立的排程群組會變成優先執行該參數所指定的位置中的工作。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回排程器目前的虛擬處理器數目。|  
|[GetPolicy](#getpolicy)|傳回與已建立的排程器原則的複本。|  
|[Id](#id)|排程器傳回的唯一識別碼。|  
|[IsAvailableLocation](#isavailablelocation)|判斷某一特定的位置是否可用排程器上。|  
|[參考資料](#reference)|遞增排程器的參考計數。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件的控制代碼傳的原因`_Event`參數時，排程器關閉並終結本身發出信號。 事件發出信號時，所有已排程器已排程的工作已完成。 透過這個方法可以註冊多個關機的事件。|  
|[發行](#release)|遞減排程器的參考計數。|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|將預設排程器原則重設為執行階段預設值。 下一次建立預設排程器時，它會使用執行階段的預設原則設定。|  
|[ScheduleTask](#scheduletask)|多載。 排程的輕量工作排程器內。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|可讓使用者定義原則，以用來建立預設排程器。 只有在沒有預設排程器存在於處理程序時，可以呼叫這個方法。 已設定預設原則後，仍作用中直到下次有效呼叫為`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。|  
  
## <a name="remarks"></a>備註  
 並行執行階段排程器會使用執行內容，對應至作業系統的執行內容，例如執行緒，來執行工作排入佇列，您的應用程式。 在任何時間，排程器的並行層級等於授與資源管理員的虛擬處理器數目。 虛擬處理器是處理序的資源和對應至基礎的系統上的硬體執行緒的抽象概念。 只有單一排程器的內容可以在虛擬處理器上執行，在指定的時間。  
  
 並行執行階段將會建立每個處理序執行的平行工作的預設排程器。 此外，您可以建立您自己的排程器執行個體，而且處理使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Scheduler`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="attach"></a> 附加 

 將排程器附加至呼叫的內容。 這個方法傳回之後，呼叫的內容是由管理排程器並排程器會變成目前的排程器。  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>備註  
 排程器上，隱含附加排程器設定的參考。  
  
 在某個時間點以後，您必須呼叫[currentscheduler:: Detach](currentscheduler-class.md#detach)方法，以允許關閉排程器。  
  
 如果已經附加到不同的排程器的內容中呼叫此方法時，現有的排程器會記住做為先前的排程器，而且新建立的排程器會變成目前的排程器。 當您呼叫`CurrentScheduler::Detach`還原方法，在稍後，先前的排程器視為目前排程器。  
  
 這個方法會擲回[improper_scheduler_attach](improper-scheduler-attach-class.md)例外狀況，如果這個排程器是在呼叫端內容的目前排程器。  
  
##  <a name="create"></a> 建立 

 建立新的排程器所描述的行為`_Policy`參數，將初始參考放置於排程器，而且傳回的指標。  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>參數  
 `_Policy`  
 排程器原則，告訴您新建立的排程器的行為。  
  
### <a name="return-value"></a>傳回值  
 新建立的排程器指標。 這`Scheduler`物件具有置於其上執行初始的參考計數。  
  
### <a name="remarks"></a>備註  
 使用建立排程器之後`Create`方法，您必須呼叫`Release`在某個時間點，未來若要移除的初始的參考計數，並允許關閉排程器的方法。  
  
 使用此方法建立的排程器未附加至呼叫的內容。 將它附加至內容中使用[附加](#attach)方法。  
  
 這個方法可以擲回的例外狀況，其中包含各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a> CreateScheduleGroup 

 建立新的排程群組內的排程器。 接受參數的版本`_Placement`會導致新建立的排程群組會變成優先執行該參數所指定的位置中的工作。  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 排程群組內的工作將會變成優先執行的位置參考。  
  
### <a name="return-value"></a>傳回值  
 指標，新建的排程群組。 這`ScheduleGroup`物件具有置於其上執行初始的參考計數。  
  
### <a name="remarks"></a>備註  
 您必須叫用[發行](schedulegroup-class.md#release)當您完成排程工作的排程群組上的方法。 排程器將會損毀排程群組時，所有的工作排入佇列，已完成。  
  
 請注意，是否您明確建立此排程器，您必須釋放排程群組內，才能釋放排程器上的您參考的所有參考。  
  
##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors 

 傳回排程器目前的虛擬處理器數目。  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 目前的排程器的虛擬處理器數目。  
  
##  <a name="getpolicy"></a> GetPolicy 

 傳回與已建立的排程器原則的複本。  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 與已建立的排程器原則的複本。  
  
##  <a name="id"></a> Id 

 排程器傳回的唯一識別碼。  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 排程器的唯一識別碼。  
  
##  <a name="isavailablelocation"></a> IsAvailableLocation 

 判斷某一特定的位置是否可用排程器上。  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 要查詢有關的排程器的位置參考。  
  
### <a name="return-value"></a>傳回值  
 不論所指定的位置表示`_Placement`引數是可在排程器。  
  
### <a name="remarks"></a>備註  
 請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。  
  
##  <a name="reference"></a> 參考 

 遞增排程器的參考計數。  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>傳回值  
 新遞增的參考計數。  
  
### <a name="remarks"></a>備註  
 這通常用來管理排程器的存留期的組合。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。  
  
 方法會擲回[improper_scheduler_reference](improper-scheduler-reference-class.md)例外狀況的參考計數，然後才呼叫如果`Reference`方法為零並呼叫從排程器並未擁有的內容。  
  
##  <a name="registershutdownevent"></a> RegisterShutdownEvent 

 Windows 事件的控制代碼傳的原因`_Event`參數時，排程器關閉並終結本身發出信號。 事件發出信號時，所有已排程器已排程的工作已完成。 透過這個方法可以註冊多個關機的事件。  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Event`  
 當排程器關閉並終結本身通知執行階段的 Windows 事件物件控制代碼。  
  
##  <a name="release"></a> 發行 

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
 處理序中的預設排程器存在時，可以呼叫這個方法。 它不會影響現有的預設排程器原則。 不過，如果預設排程器已關閉，並且在稍後針對某個點上建立新的預設值，新的排程器會使用執行階段的預設原則設定。  
  
##  <a name="ctor"></a> 排程器 

 物件的`Scheduler`類別可以僅使用 factory 方法，建立或隱含的方式。  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>備註  
 您可以利用許多執行階段函式需要將排程器附加至呼叫的內容時，會隱含地建立處理序的預設排程器。 方法內`CurrentScheduler`類別和 PPL 和代理程式的圖層的功能通常會執行隱含的附件。  
  
 您也可以建立排程器是透過明確`CurrentScheduler::Create`方法或`Scheduler::Create`方法。  
  
##  <a name="dtor"></a> ~ 排程器 

 物件的`Scheduler`隱含終結類別之前就不再存在於所有外部參考時。  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a> ScheduleTask 

 排程的輕量工作排程器內。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。  
  
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
 `_Proc`  
 若要執行的輕量工作主體中執行的函式指標。  
  
 `_Data`  
 將做為參數傳遞至工作的主體資料的 void 指標。  
  
 `_Placement`  
 輕量工作將會變成優先執行的位置參考。  
  
##  <a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy 

 可讓使用者定義原則，以用來建立預設排程器。 只有在沒有預設排程器存在於處理程序時，可以呼叫這個方法。 已設定預設原則後，仍作用中直到下次有效呼叫為`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>參數  
 `_Policy`  
 要設定為預設排程器原則的原則。  
  
### <a name="remarks"></a>備註  
 如果`SetDefaultSchedulerPolicy`呼叫方法時，預設排程器已經存在於處理程序，將會擲回執行階段[default_scheduler_exists](default-scheduler-exists-class.md)例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



