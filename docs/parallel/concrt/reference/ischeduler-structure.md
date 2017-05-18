---
title: "IScheduler 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
dev_langs:
- C++
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: 18
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
ms.openlocfilehash: 24305fbdded1709ec51270b3a29a239b345a5679
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="ischeduler-structure"></a>IScheduler 結構
工作排程器抽象概念的介面。 並行執行階段的資源管理員會使用這個介面與工作排程器通訊。  
  
## <a name="syntax"></a>語法  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ischeduler:: Addvirtualprocessors](#addvirtualprocessors)|提供一組的虛擬處理器根的排程器，供其使用。 每個`IVirtualProcessorRoot`介面代表執行單一執行緒可以執行工作排程器代表權限。|  
|[Ischeduler:: Getid](#getid)|排程器傳回的唯一識別碼。|  
|[Ischeduler:: Getpolicy](#getpolicy)|傳回排程器原則的複本。 如需有關排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。|  
|[Ischeduler:: Notifyresourcesexternallybusy](#notifyresourcesexternallybusy)|這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`現在正由其他排程器。|  
|[Ischeduler:: Notifyresourcesexternallyidle](#notifyresourcesexternallyidle)|這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`未由其他排程器使用。|  
|[Ischeduler:: Removevirtualprocessors](#removevirtualprocessors)|起始移除先前已配置給這個排程器的虛擬處理器根。|  
|[Ischeduler:: Statistics](#statistics)|提供工作從抵達到完成速度，以及變更排程器佇列長度的相關資訊。|  
  
## <a name="remarks"></a>備註  
 如果您實作自訂的排程器進行通訊與資源管理員，您應該提供的實作`IScheduler`介面。 這個介面是通訊的雙向的排程器與資源管理員之間通道的一端。 另一端由`IResourceManager`和`ISchedulerProxy`資源管理員所實作的介面。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IScheduler`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="addvirtualprocessors"></a>Ischeduler:: Addvirtualprocessors 方法  
 提供一組的虛擬處理器根的排程器，供其使用。 每個`IVirtualProcessorRoot`介面代表執行單一執行緒可以執行工作排程器代表權限。  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>參數  
 `ppVirtualProcessorRoots`  
 陣列`IVirtualProcessorRoot`介面代表虛擬處理器根加入排程器。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 資源管理員會叫用`AddVirtualProcessor`方法，以授與排程器的一組初始的虛擬處理器根。 它也無法叫用方法，以重新平衡資源排程時，新增的虛擬處理器根排程器。  
  
##  <a name="getid"></a>Ischeduler:: Getid 方法  
 排程器傳回的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 唯一整數識別碼。  
  
### <a name="remarks"></a>備註  
 您應該使用[GetSchedulerId](concurrency-namespace-functions.md)函數，以取得實作之物件的唯一識別項`IScheduler`介面，您可以使用介面做為方法的參數之前提供資源管理員。 您應該會傳回相同的識別項時`GetId`函式會叫用。  
  
 從不同來源取得的識別項可能會導致未定義的行為。  
  
##  <a name="getpolicy"></a>Ischeduler:: Getpolicy 方法  
 傳回排程器原則的複本。 如需有關排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 排程器原則的複本。  
  
##  <a name="notifyresourcesexternallybusy"></a>Ischeduler:: Notifyresourcesexternallybusy 方法  
 這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`現在正由其他排程器。  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>參數  
 `ppVirtualProcessorRoots`  
 陣列`IVirtualProcessorRoot`所在的其他排程器已經變成忙碌的硬體執行緒相關聯的介面。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 就可以同時指派給多個排程器的特定硬體執行緒。 原因可能是沒有足夠的硬體執行緒在系統上，滿足所有排程器，而不需共用資源的最小的並行。 另一個可能的原因是，資源會暫時指派給其他排程器擁有的排程器未使用時，透過在正在停用該硬體執行緒上的虛擬處理器根。  
  
 硬體執行緒的訂閱層級以訂閱的執行緒數目，並啟動該硬體執行緒相關聯的虛擬處理器根。 從特定的排程器的觀點來看，硬體執行緒的外部訂閱層級是的訂閱的其他排程器所造成的部分。 當外部訂閱層級的硬體執行緒將從零到正數領域排程器傳送通知的資源都在外部忙碌中。  
  
 透過這種方式通知只傳送至原則之排程器的位置值`MinConcurrency`原則機碼的值等於`MaxConcurrency`原則機碼。 如需有關排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 取得通知的排程器取得一組初始的通知建立時，通知它其所指派的資源外部忙碌或閒置。  
  
##  <a name="notifyresourcesexternallyidle"></a>Ischeduler:: Notifyresourcesexternallyidle 方法  
 這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`未由其他排程器使用。  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>參數  
 `ppVirtualProcessorRoots`  
 陣列`IVirtualProcessorRoot`所在的其他排程器已成為閒置的硬體執行緒相關聯的介面。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 就可以同時指派給多個排程器的特定硬體執行緒。 原因可能是沒有足夠的硬體執行緒在系統上，滿足所有排程器，而不需共用資源的最小的並行。 另一個可能的原因是，資源會暫時指派給其他排程器擁有的排程器未使用時，透過在正在停用該硬體執行緒上的虛擬處理器根。  
  
 硬體執行緒的訂閱層級以訂閱的執行緒數目，並啟動該硬體執行緒相關聯的虛擬處理器根。 從特定的排程器的觀點來看，硬體執行緒的外部訂閱層級是的訂閱的其他排程器所造成的部分。 資源是外部忙碌時傳送通知，排程器硬體執行緒的外部訂閱層級降為零，從先前的正數值。  
  
 透過這種方式通知只傳送至原則之排程器的位置值`MinConcurrency`原則機碼的值等於`MaxConcurrency`原則機碼。 如需有關排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 取得通知的排程器取得一組初始的通知建立時，通知它其所指派的資源外部忙碌或閒置。  
  
##  <a name="removevirtualprocessors"></a>Ischeduler:: Removevirtualprocessors 方法  
 起始移除先前已配置給這個排程器的虛擬處理器根。  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>參數  
 `ppVirtualProcessorRoots`  
 陣列`IVirtualProcessorRoot`介面代表要移除的虛擬處理器根。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 資源管理員會叫用`RemoveVirtualProcessors`方法，以取回排程器的一組虛擬處理器根。 排程器所要叫用[移除](iexecutionresource-structure.md#remove)虛擬處理器根處理完成時，每個介面上的方法。 請勿使用`IVirtualProcessorRoot`介面之後叫用`Remove`方法。  
  
 參數`ppVirtualProcessorRoots`指向介面的陣列。 在要移除的虛擬處理器根組，當中的根項目永遠不會啟動可立即使用傳回`Remove`方法。 根項目都已啟動和是其中一個執行的工作，或已停用且正等候送達時，工作應該以非同步方式傳回。 排程器必須盡一切努力，盡快移除虛擬處理器根。 延遲移除虛擬處理器根，可能會導致意外的過度訂閱，排程器內。  
  
##  <a name="statistics"></a>Ischeduler:: Statistics 方法  
 提供工作從抵達到完成速度，以及變更排程器佇列長度的相關資訊。  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pTaskCompletionRate`  
 自上次呼叫這個方法來排程器所完成的工作數目。  
  
 `pTaskArrivalRate`  
 自上次呼叫這個方法所收到的排程器中的工作數目。  
  
 `pNumberOfTasksEnqueued`  
 所有排程器佇列中的工作總數。  
  
### <a name="remarks"></a>備註  
 若要收集的統計資料的排程器是叫用這個方法由資源管理員。 這裡所收集的統計資料將用來動態回應演算法來判斷指派更多資源排程器的適當時機為何，以及何時會佔用資源磁碟機。 排程器所提供的值可以是開放式，並不一定需要正確地反映目前的計數。  
  
 如果您希望資源管理員使用像是工作抵達這類事件的意見反應，決定如何在您的排程器與資源管理員中註冊的其他排程器之間平衡資源，則應該實作這個方法。 如果您選擇不以收集統計資料，您可以設定原則機碼`DynamicProgressFeedback`值`DynamicProgressFeedbackDisabled`在您的排程器原則和資源管理員不會叫用您的排程器上的這個方法。  
  
 在不存在的統計資訊，資源管理員將決定資源配置和移轉使用硬體執行緒的訂閱等級。 如需有關訂閱層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [SchedulerPolicy 類別](schedulerpolicy-class.md)   
 [IExecutionContext 結構](iexecutioncontext-structure.md)   
 [IThreadProxy 結構](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)   
 [IResourceManager 結構](iresourcemanager-structure.md)

