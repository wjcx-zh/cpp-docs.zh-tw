---
title: "排程器類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: cc39a524e9a65aeab0c84fb43f5b38ddd892923e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="scheduler-class"></a>Scheduler 類別
代表並行執行階段排程器的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
class Scheduler;
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[排程器](#ctor)|物件的`Scheduler`類別可以僅使用 factory 方法建立限或隱含的方式。|  
|[~ Scheduler 解構函式](#dtor)|物件的`Scheduler`類別以隱含方式終結時就不再存在於所有外部參考。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Attach](#attach)|將排程附加至呼叫的內容。 這個方法傳回之後，呼叫的內容由排程器和排程器會變成目前的排程器。|  
|[建立](#create)|建立新的排程器所描述的行為`_Policy`參數，在排程器，將初始的參考，並傳回的指標。|  
|[CreateScheduleGroup](#createschedulegroup)|多載。 建立新的排程群組，則排程器內。 接受參數的版本`_Placement`會變成優先執行在該參數所指定的位置建立新的排程群組中的工作。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|排程器會傳回目前的虛擬處理器數目。|  
|[GetPolicy](#getpolicy)|傳回一份排程器所建立的原則。|  
|[識別碼](#id)|排程器傳回的唯一識別碼。|  
|[IsAvailableLocation](#isavailablelocation)|判斷某一特定的位置是否可在排程器。|  
|[參考](#reference)|遞增排程器的參考計數。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件的控制代碼傳的原因`_Event`收到信號時，排程器關閉並終結本身的參數。 此事件收到信號時，所有之前排程器已排定的工作已完成。 透過這個方法可以註冊多個關機事件。|  
|[發行](#release)|遞減排程器的參考計數。|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|將預設排程器原則重設為執行階段預設值。 下一次建立預設排程器時，它會使用執行階段的預設原則設定。|  
|[ScheduleTask](#scheduletask)|多載。 排程的輕量工作排程器內。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|可讓使用者定義原則，用來建立預設排程器。 沒有預設排程器存在於處理程序時，才可以呼叫這個方法。 設定預設原則後，就會生效，直到下一步為有效的呼叫`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。|  
  
## <a name="remarks"></a>備註  
 並行執行階段排程器會使用對應至作業系統的執行內容，例如執行緒的執行內容，來執行工作排入佇列，您的應用程式。 在任何時間，排程器的並行處理等級相當於授與資源管理員的虛擬處理器數目。 虛擬處理器是抽象的處理序的資源和對應至基礎系統的硬體執行緒。 虛擬處理器可以執行單一排程器內容在指定的時間。  
  
 並行執行階段會建立預設排程器每個處理序執行的平行工作。 此外，您可以建立您自己的排程器執行個體，並操作使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Scheduler`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="attach"></a>附加 

 將排程附加至呼叫的內容。 這個方法傳回之後，呼叫的內容由排程器和排程器會變成目前的排程器。  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>備註  
 以隱含方式附加排程器會參考放在排程器。  
  
 在某個時間點以後，您必須呼叫[currentscheduler:: Detach](currentscheduler-class.md#detach)方法，以便允許關閉排程器。  
  
 如果已經附加到不同的排程器的內容中呼叫這個方法時，現有的排程器會做為先前的排程器，記住，新建立的排程器會變成目前的排程器。 當您呼叫`CurrentScheduler::Detach`方法之後，先前的排程器會還原為目前的排程器。  
  
 這個方法會擲回[improper_scheduler_attach](improper-scheduler-attach-class.md)這個排程器目前的排程器呼叫內容的例外狀況。  
  
##  <a name="create"></a>建立 

 建立新的排程器所描述的行為`_Policy`參數，在排程器，將初始的參考，並傳回的指標。  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>參數  
 `_Policy`  
 排程器原則，告訴您新建立的排程器的行為。  
  
### <a name="return-value"></a>傳回值  
 新建立的排程器指標。 這`Scheduler`物件都放在它的初始的參考計數。  
  
### <a name="remarks"></a>備註  
 使用排程器建立後`Create`方法，您必須呼叫`Release`在某個時間點以後才能移除初始的參考計數，並允許關閉排程器的方法。  
  
 這個方法建立的排程器無法連接至呼叫的內容。 將它附加至內容中使用[附加](#attach)方法。  
  
 這個方法可以擲回例外狀況，包括各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 建立新的排程群組，則排程器內。 接受參數的版本`_Placement`會變成優先執行在該參數所指定的位置建立新的排程群組中的工作。  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 排程群組中的工作將會優先執行的位置參考。  
  
### <a name="return-value"></a>傳回值  
 新建立的排程群組指標。 這`ScheduleGroup`物件都放在它的初始的參考計數。  
  
### <a name="remarks"></a>備註  
 您必須叫用[版本](schedulegroup-class.md#release)方法，當您在排程工作的排程群組上。 排程器將會損毀排程群組時，所有的工作排入佇列，已完成。  
  
 請注意，是否您明確建立此排程器，您必須釋放排程群組，然後再發行您的參考，排程器上的所有參考。  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 排程器會傳回目前的虛擬處理器數目。  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 目前的排程器的虛擬處理器數目。  
  
##  <a name="getpolicy"></a>GetPolicy 

 傳回一份排程器所建立的原則。  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 排程器用來建立原則的複本。  
  
##  <a name="id"></a>識別碼 

 排程器傳回的唯一識別碼。  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 排程器的唯一識別碼。  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 判斷某一特定的位置是否可在排程器。  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 要查詢的排程器的位置參考。  
  
### <a name="return-value"></a>傳回值  
 指示是否由指定的位置`_Placement`引數是可在排程器。  
  
### <a name="remarks"></a>備註  
 請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。  
  
##  <a name="reference"></a>參考 

 遞增排程器的參考計數。  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>傳回值  
 新遞增的參考計數。  
  
### <a name="remarks"></a>備註  
 這通常用來管理排程器的存留期的組合。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。  
  
 方法會擲回[improper_scheduler_reference](improper-scheduler-reference-class.md)例外狀況的參考計數，然後才呼叫如果`Reference`方法是零，並從非排程器所擁有的內容進行呼叫。  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Windows 事件的控制代碼傳的原因`_Event`收到信號時，排程器關閉並終結本身的參數。 此事件收到信號時，所有之前排程器已排定的工作已完成。 透過這個方法可以註冊多個關機事件。  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Event`  
 當排程器關閉並終結本身會通知執行階段的 Windows 事件物件控制代碼。  
  
##  <a name="release"></a>發行 

 遞減排程器的參考計數。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 新遞減參考計數。  
  
### <a name="remarks"></a>備註  
 這通常用來管理排程器的存留期的組合。 當排程器的參考計數變成零時，排程器會於所有工作完成後關機並自行解構。  
  
##  <a name="resetdefaultschedulerpolicy"></a>ResetDefaultSchedulerPolicy 

 將預設排程器原則重設為執行階段預設值。 下一次建立預設排程器時，它會使用執行階段的預設原則設定。  
  
```
static void __cdecl ResetDefaultSchedulerPolicy();
```  
  
### <a name="remarks"></a>備註  
 在程序中的預設排程器存在時，可以呼叫這個方法。 它不會影響現有的預設排程器原則。 不過，如果預設排程器已關閉，並且在稍後的時間點上建立新的預設值，新的排程器就會使用執行階段的預設原則設定。  
  
##  <a name="ctor"></a>排程器 

 物件的`Scheduler`類別可以僅使用 factory 方法建立限或隱含的方式。  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>備註  
 您可以利用許多執行階段函式需要排程器來附加到呼叫的內容時，會以隱含方式建立處理序的預設排程器。 方法內`CurrentScheduler`類別和 PPL 和代理程式的圖層的功能通常會執行隱含的附件。  
  
 您也可以建立排程器是透過明確`CurrentScheduler::Create`方法或`Scheduler::Create`方法。  
  
##  <a name="dtor"></a>~ 排程器 

 物件的`Scheduler`類別以隱含方式終結時就不再存在於所有外部參考。  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a>ScheduleTask 

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
 若要執行的輕量工作主體執行的函式指標。  
  
 `_Data`  
 Void 指標會做為參數傳遞至工作主體的資料。  
  
 `_Placement`  
 輕量工作將會變成優先執行的位置參考。  
  
##  <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy 

 可讓使用者定義原則，用來建立預設排程器。 沒有預設排程器存在於處理程序時，才可以呼叫這個方法。 設定預設原則後，就會生效，直到下一步為有效的呼叫`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>參數  
 `_Policy`  
 要設定為預設排程器原則的原則。  
  
### <a name="remarks"></a>備註  
 如果`SetDefaultSchedulerPolicy`方法稱為 「 處理序中的預設排程器已存在時，執行階段會擲回[default_scheduler_exists](default-scheduler-exists-class.md)例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




