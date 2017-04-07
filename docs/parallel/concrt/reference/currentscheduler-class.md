---
title: "CurrentScheduler 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 9536dd28eeb375f3b9e018539cefb338812e340b
ms.lasthandoff: 03/17/2017

---
# <a name="currentscheduler-class"></a>CurrentScheduler 類別
代表與呼叫內容相關之目前排程器的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[建立](#create)|建立新的排程器所描述的行為`_Policy`參數並將它附加至呼叫的內容。 新建立的排程器會呼叫內容的目前排程器。|  
|[CreateScheduleGroup](#createschedulegroup)|多載。 建立新的排程群組內呼叫的內容相關聯的排程器。 接受參數的版本`_Placement`會變成優先執行在該參數所指定的位置建立新的排程群組中的工作。|  
|[Detach](#detach)|卸離目前的排程器，從呼叫的內容，並還原先前附加的排程器視為目前排程器，如果有的話。 這個方法傳回之後，呼叫的內容則由先前已附加至內容使用的排程器`CurrentScheduler::Create`或`Scheduler::Attach`方法。|  
|[取得](#get)|傳回呼叫的內容，也稱為目前排程器相關聯的排程器的指標。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回呼叫的內容相關聯的排程器目前的虛擬處理器數目。|  
|[GetPolicy](#getpolicy)|傳回一份目前排程器所建立的原則。|  
|[識別碼](#id)|傳回目前的排程器的唯一識別碼。|  
|[IsAvailableLocation](#isavailablelocation)|判斷某一特定位置是否可在目前的排程器中使用。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件的控制代碼傳的原因`_ShutdownEvent`收到信號時，與目前內容相關聯的排程器關閉並終結本身的參數。 此事件收到信號時，所有之前排程器已排定的工作已完成。 透過這個方法可以註冊多個關機事件。|  
|[ScheduleTask](#scheduletask)|多載。 排程與呼叫的內容相關聯的排程器中的輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|  
  
## <a name="remarks"></a>備註  
 如果沒有任何排程器 (請參閱[排程器](scheduler-class.md)) 呼叫內容中的許多方法相關聯`CurrentScheduler`類別將會導致處理序的預設排程器的附件。 這也可能表示將處理序的預設排程器會建立這類呼叫期間。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CurrentScheduler`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="create"></a>建立 

 建立新的排程器所描述的行為`_Policy`參數並將它附加至呼叫的內容。 新建立的排程器會呼叫內容的目前排程器。  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>參數  
 `_Policy`  
 排程器原則描述新建立的排程器的行為。  
  
### <a name="remarks"></a>備註  
 排程器的附件，呼叫的內容，隱含地耗用排程器的參考計數。  
  
 使用排程器建立後`Create`方法，您必須呼叫[currentscheduler:: Detach](#detach)在某個時間點，在未來，以便關閉排程器的方法。  
  
 如果已經附加到不同的排程器的內容中呼叫這個方法時，現有的排程器會做為先前的排程器，記住，新建立的排程器會變成目前的排程器。 當您呼叫`CurrentScheduler::Detach`方法之後，先前的排程器會還原為目前的排程器。  
  
 這個方法可以擲回例外狀況，包括各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 建立新的排程群組內呼叫的內容相關聯的排程器。 接受參數的版本`_Placement`會變成優先執行在該參數所指定的位置建立新的排程群組中的工作。  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 其中排程群組中的工作將會變成優先執行的位置參考。  
  
### <a name="return-value"></a>傳回值  
 新建立的排程群組指標。 這`ScheduleGroup`物件都放在它的初始的參考計數。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
 您必須叫用[版本](schedulegroup-class.md#release)方法，當您在排程工作的排程群組上。 排程器將會損毀排程群組時，所有的工作排入佇列，已完成。  
  
 請注意，是否您明確建立此排程器，您必須釋放排程群組，然後再從其目前的內容，中斷連結發行排程器，將參考的所有參考。  
  
##  <a name="detach"></a>卸離 

 卸離目前的排程器，從呼叫的內容，並還原先前附加的排程器視為目前排程器，如果有的話。 這個方法傳回之後，呼叫的內容則由先前已附加至內容使用的排程器`CurrentScheduler::Create`或`Scheduler::Attach`方法。  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>備註  
 `Detach`方法隱含地移除排程器的參考計數。  
  
 如果沒有任何附加到呼叫內容的排程器，呼叫這個方法會導致[scheduler_not_attached](scheduler-not-attached-class.md)擲回例外狀況。  
  
 呼叫這個方法從內容都內部，並由排程器或使用一種方法不是附加的內容管理[scheduler:: attach](scheduler-class.md#attach)或[currentscheduler:: Create](#create)方法，將會導致[improper_scheduler_detach](improper-scheduler-detach-class.md)擲回例外狀況。  
  
##  <a name="get"></a>取得 

 傳回呼叫的內容，也稱為目前排程器相關聯的排程器的指標。  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>傳回值  
 呼叫的內容 （目前的排程器） 相關聯的排程器指標。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。 沒有其他的參考會放在`Scheduler`這個方法所傳回的物件。  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 傳回呼叫的內容相關聯的排程器目前的虛擬處理器數目。  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>傳回值  
 如果呼叫的內容，該排程器; 的虛擬處理器的數目與相關聯的排程器否則，值`-1`。  
  
### <a name="remarks"></a>備註  
 這個方法不會導致排程器附件如果呼叫的內容尚未排程器相關聯。  
  
 這個方法的傳回值是排程器呼叫的內容相關聯的虛擬處理器數目的瞬間取樣。 這個值傳回時可能已過時。  
  
##  <a name="getpolicy"></a>GetPolicy 

 傳回一份目前排程器所建立的原則。  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>傳回值  
 原則的複本，以建立目前排程器。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
##  <a name="id"></a>識別碼 

 傳回目前的排程器的唯一識別碼。  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>傳回值  
 如果呼叫的內容，該排程器; 的唯一識別項相關聯的排程器否則，值`-1`。  
  
### <a name="remarks"></a>備註  
 這個方法不會導致排程器附件如果呼叫的內容尚未排程器相關聯。  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 判斷某一特定位置是否可在目前的排程器中使用。  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 要查詢目前排程器的位置參考。  
  
### <a name="return-value"></a>傳回值  
 指出目前排程器上是否有提供 `_Placement` 引數所指定的位置。  
  
### <a name="remarks"></a>備註  
 這個方法不會導致排程器附件如果呼叫的內容尚未排程器相關聯。  
  
 請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Windows 事件的控制代碼傳的原因`_ShutdownEvent`收到信號時，與目前內容相關聯的排程器關閉並終結本身的參數。 此事件收到信號時，所有之前排程器已排定的工作已完成。 透過這個方法可以註冊多個關機事件。  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>參數  
 `_ShutdownEvent`  
 當目前的內容相關聯的排程器關閉並終結本身會通知執行階段的 Windows 事件物件控制代碼。  
  
### <a name="remarks"></a>備註  
 如果沒有任何附加到呼叫內容的排程器，呼叫這個方法會導致[scheduler_not_attached](scheduler-not-attached-class.md)擲回例外狀況。  
  
##  <a name="scheduletask"></a>ScheduleTask 

 排程與呼叫的內容相關聯的排程器中的輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。  
  
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
 `_Proc`  
 若要執行的輕量工作主體執行的函式指標。  
  
 `_Data`  
 Void 指標會做為參數傳遞至工作主體的資料。  
  
 `_Placement`  
 輕量工作將會變成優先執行的位置參考。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




