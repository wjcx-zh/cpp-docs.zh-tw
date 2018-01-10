---
title: "CurrentScheduler 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 936904f19687463a9b5c51262c8e6f7a8b9fe5a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[建立](#create)|建立新的排程器所描述的行為`_Policy`參數並將其附加至呼叫的內容。 新建立的排程器會呼叫內容的目前排程器。|  
|[CreateScheduleGroup](#createschedulegroup)|多載。 建立新的排程群組內呼叫內容相關聯的排程器。 接受參數的版本`_Placement`會導致新建立的排程群組會變成優先執行該參數所指定的位置中的工作。|  
|[Detach](#detach)|卸離目前的排程器，從呼叫的內容，並還原先前附加的排程器視為目前排程器，如果有的話。 這個方法傳回之後，呼叫的內容再受先前已附加至內容使用的排程器`CurrentScheduler::Create`或`Scheduler::Attach`方法。|  
|[Get](#get)|讓指標回到呼叫的內容，也稱為目前排程器相關聯的排程器。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|傳回與呼叫內容相關聯的排程器目前的虛擬處理器數目。|  
|[GetPolicy](#getpolicy)|傳回一份目前的排程器所建立的原則。|  
|[識別碼](#id)|傳回目前的排程器的唯一識別碼。|  
|[IsAvailableLocation](#isavailablelocation)|判斷某一特定位置是否可在目前的排程器中使用。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件的控制代碼傳的原因`_ShutdownEvent`參數時的目前內容相關聯的排程器關閉並終結本身發出信號。 事件發出信號時，所有已排程器已排程的工作已完成。 透過這個方法可以註冊多個關機的事件。|  
|[ScheduleTask](#scheduletask)|多載。 排程與呼叫內容相關聯的排程器中的輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。|  
  
## <a name="remarks"></a>備註  
 如果沒有任何排程器 (請參閱[排程器](scheduler-class.md)) 呼叫的內容中的許多方法相關聯`CurrentScheduler`類別將會導致處理序的預設排程器的附件。 這也可能表示這類呼叫期間建立的處理序的預設排程器。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CurrentScheduler`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="create"></a>建立 

 建立新的排程器所描述的行為`_Policy`參數並將其附加至呼叫的內容。 新建立的排程器會呼叫內容的目前排程器。  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>參數  
 `_Policy`  
 排程器原則描述新建立的排程器的行為。  
  
### <a name="remarks"></a>備註  
 排程器的附件，以呼叫的內容以隱含方式放置於參考計數，排程器。  
  
 使用建立排程器之後`Create`方法，您必須呼叫[currentscheduler:: Detach](#detach)在某個時間點，在未來，才能關閉排程器的方法。  
  
 如果已經附加到不同的排程器的內容中呼叫此方法時，現有的排程器會記住做為先前的排程器，而且新建立的排程器會變成目前的排程器。 當您呼叫`CurrentScheduler::Detach`還原方法，在稍後，先前的排程器視為目前排程器。  
  
 這個方法可以擲回的例外狀況，其中包含各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 建立新的排程群組內呼叫內容相關聯的排程器。 接受參數的版本`_Placement`會導致新建立的排程群組會變成優先執行該參數所指定的位置中的工作。  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>參數  
 `_Placement`  
 排程群組內的工作變成優先執行的位置參考。  
  
### <a name="return-value"></a>傳回值  
 指標，新建的排程群組。 這`ScheduleGroup`物件具有置於其上執行初始的參考計數。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
 您必須叫用[發行](schedulegroup-class.md#release)當您完成排程工作的排程群組上的方法。 排程器將會損毀排程群組時，所有的工作排入佇列，已完成。  
  
 請注意，是否您明確建立此排程器，您必須釋放排程群組中，在發行您的排程器上的參考從其目前的內容，中斷連結前的所有參考。  
  
##  <a name="detach"></a>卸離 

 卸離目前的排程器，從呼叫的內容，並還原先前附加的排程器視為目前排程器，如果有的話。 這個方法傳回之後，呼叫的內容再受先前已附加至內容使用的排程器`CurrentScheduler::Create`或`Scheduler::Attach`方法。  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>備註  
 `Detach`方法隱含地移除排程器的參考計數。  
  
 如果沒有附加至呼叫的內容沒有排程器，呼叫這個方法會導致[scheduler_not_attached](scheduler-not-attached-class.md)擲回例外狀況。  
  
 從內容呼叫這個方法是內部且由排程器或已附加以外使用方法的內容管理[scheduler:: attach](scheduler-class.md#attach)或[currentscheduler:: Create](#create)方法將會導致[improper_scheduler_detach](improper-scheduler-detach-class.md)擲回例外狀況。  
  
##  <a name="get"></a>取得 

 讓指標回到呼叫的內容，也稱為目前排程器相關聯的排程器。  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>傳回值  
 在呼叫端的內容 （目前排程器） 相關聯的排程器指標。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。 沒有額外的參考會放在`Scheduler`這個方法所傳回的物件。  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 傳回與呼叫內容相關聯的排程器目前的虛擬處理器數目。  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>傳回值  
 如果呼叫的內容，該排程器; 的虛擬處理器的數目與相關聯的排程器否則，值`-1`。  
  
### <a name="remarks"></a>備註  
 這個方法不會導致排程器附件如果呼叫的內容是不與排程器相關聯。  
  
 這個方法的傳回值是排程器與呼叫內容相關聯的虛擬處理器數目的瞬間取樣。 這個值傳回時可能已過時。  
  
##  <a name="getpolicy"></a>GetPolicy 

 傳回一份目前的排程器所建立的原則。  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>傳回值  
 原則的複本，目前的排程器所建立。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
##  <a name="id"></a>識別碼 

 傳回目前的排程器的唯一識別碼。  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>傳回值  
 如果呼叫的內容，該排程器; 的唯一識別項與相關聯的排程器否則，值`-1`。  
  
### <a name="remarks"></a>備註  
 這個方法不會導致排程器附件如果呼叫的內容是不與排程器相關聯。  
  
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
 這個方法不會導致排程器附件如果呼叫的內容是不與排程器相關聯。  
  
 請注意，傳回值是某一特定位置是否可用的瞬間取樣。 若有多個排程器，動態資源管理可以隨時在排程器中加入或移除資源。 如果發生這種情況，這個特定位置的可用性可能會改變。  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Windows 事件的控制代碼傳的原因`_ShutdownEvent`參數時的目前內容相關聯的排程器關閉並終結本身發出信號。 事件發出信號時，所有已排程器已排程的工作已完成。 透過這個方法可以註冊多個關機的事件。  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>參數  
 `_ShutdownEvent`  
 將執行階段用來簽署時的目前內容相關聯的排程器關閉並終結本身的 Windows 事件物件控制代碼。  
  
### <a name="remarks"></a>備註  
 如果沒有附加至呼叫的內容沒有排程器，呼叫這個方法會導致[scheduler_not_attached](scheduler-not-attached-class.md)擲回例外狀況。  
  
##  <a name="scheduletask"></a>ScheduleTask 

 排程與呼叫內容相關聯的排程器中的輕量工作。 輕量工作會置於執行階段所決定的排程群組中。 採用 `_Placement` 參數的版本會造成工作在指定的位置變成優先執行。  
  
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
 若要執行的輕量工作主體中執行的函式指標。  
  
 `_Data`  
 將做為參數傳遞至工作的主體資料的 void 指標。  
  
 `_Placement`  
 輕量工作將會變成優先執行的位置參考。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



