---
title: "IScheduler 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e38029e13bc342895922f4f3624076ab513f7a45
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ischeduler-structure"></a>IScheduler 結構
工作排程器抽象概念的介面。 並行執行階段的資源管理員會使用這個介面與工作排程器通訊。  
  
## <a name="syntax"></a>語法  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Ischeduler:: Addvirtualprocessors](#addvirtualprocessors)|提供一組的虛擬處理器根排程器，其用途。 每個`IVirtualProcessorRoot`介面代表執行單一執行緒可以執行工作，代表排程器的權限。|  
|[Ischeduler:: Getid](#getid)|排程器傳回的唯一識別碼。|  
|[Ischeduler:: Getpolicy](#getpolicy)|傳回排程器原則的複本。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。|  
|[Ischeduler:: Notifyresourcesexternallybusy](#notifyresourcesexternallybusy)|這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`現在正由其他排程器。|  
|[Ischeduler:: Notifyresourcesexternallyidle](#notifyresourcesexternallyidle)|這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`不正由其他排程器。|  
|[Ischeduler:: Removevirtualprocessors](#removevirtualprocessors)|起始移除先前配置給這個排程器的虛擬處理器根。|  
|[Ischeduler:: Statistics](#statistics)|提供工作從抵達到完成率和排程器佇列長度的變更相關資訊。|  
  
## <a name="remarks"></a>備註  
 如果您實作自訂的排程器進行通訊與資源管理員，您應該提供的實作`IScheduler`介面。 這個介面是通訊的雙向的排程器與資源管理員之間通道的一端。 另一端由`IResourceManager`和`ISchedulerProxy`介面會實作資源管理員。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IScheduler`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="addvirtualprocessors"></a>Ischeduler:: Addvirtualprocessors 方法  
 提供一組的虛擬處理器根排程器，其用途。 每個`IVirtualProcessorRoot`介面代表執行單一執行緒可以執行工作，代表排程器的權限。  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>參數  
 `ppVirtualProcessorRoots`  
 陣列`IVirtualProcessorRoot`介面代表虛擬處理器根排程器被加入。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 資源管理員會叫用`AddVirtualProcessor`授與一組初始的虛擬處理器根排程器的方法。 它也無法叫用方法時它會重新平衡排程器之間的資源，將虛擬處理器根排程器。  
  
##  <a name="getid"></a>Ischeduler:: Getid 方法  
 排程器傳回的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 的唯一整數識別碼。  
  
### <a name="remarks"></a>備註  
 您應該使用[GetSchedulerId](concurrency-namespace-functions.md)函數來取得實作的物件的唯一識別碼`IScheduler`介面，您可以使用介面做為方法參數之前提供資源管理員。 您應該會傳回相同的識別項時`GetId`函式會叫用。  
  
 從不同來源取得的識別項可能會導致未定義的行為。  
  
##  <a name="getpolicy"></a>Ischeduler:: Getpolicy 方法  
 傳回排程器原則的複本。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。  
  
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
 陣列`IVirtualProcessorRoot`所在的其他排程器變得忙碌的硬體執行緒相關聯的介面。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 很可能要同時指派給多個排程器的特定的硬體執行緒。 其中一個原因可能是沒有足夠的硬體執行緒於系統中，所有排程器，為滿足最小的並行存取，而不需要共用資源。 另一個可能性是，資源會暫時指派給其他排程器擁有的排程器未使用時，透過已停用該硬體執行緒上的虛擬處理器根。  
  
 啟用與該硬體執行緒相關聯的虛擬處理器根和硬體執行緒的訂用帳戶層級由訂閱的執行緒數目表示。 從特定的排程器的觀點來看，硬體執行緒的外部的訂用帳戶層級是訂用帳戶的其他排程器所參與的部分。 從零到正數領域移硬體執行緒的外部的訂用帳戶層級時，將會傳送到排程器的資源是外部忙碌的通知。  
  
 透過此方法的通知，才會傳送給原則的排程器位置的值`MinConcurrency`原則機碼的值等於`MaxConcurrency`原則機碼。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 排程器會評估符合通知時，取得一組初始的通知而建立，告知到它已指派的資源會從外部忙碌或閒置。  
  
##  <a name="notifyresourcesexternallyidle"></a>Ischeduler:: Notifyresourcesexternallyidle 方法  
 這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`不正由其他排程器。  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>參數  
 `ppVirtualProcessorRoots`  
 陣列`IVirtualProcessorRoot`所在的其他排程器已變成閒置狀態的硬體執行緒相關聯的介面。  
  
 `count`  
 數目`IVirtualProcessorRoot`陣列中的介面。  
  
### <a name="remarks"></a>備註  
 很可能要同時指派給多個排程器的特定的硬體執行緒。 其中一個原因可能是沒有足夠的硬體執行緒於系統中，所有排程器，為滿足最小的並行存取，而不需要共用資源。 另一個可能性是，資源會暫時指派給其他排程器擁有的排程器未使用時，透過已停用該硬體執行緒上的虛擬處理器根。  
  
 啟用與該硬體執行緒相關聯的虛擬處理器根和硬體執行緒的訂用帳戶層級由訂閱的執行緒數目表示。 從特定的排程器的觀點來看，硬體執行緒的外部的訂用帳戶層級是訂用帳戶的其他排程器所參與的部分。 資源是外部忙碌中的通知會傳送至排程器中，當硬體執行緒的外部的訂用帳戶層級降至零，從上一個正數值。  
  
 透過此方法的通知，才會傳送給原則的排程器位置的值`MinConcurrency`原則機碼的值等於`MaxConcurrency`原則機碼。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 排程器會評估符合通知時，取得一組初始的通知而建立，告知到它已指派的資源會從外部忙碌或閒置。  
  
##  <a name="removevirtualprocessors"></a>Ischeduler:: Removevirtualprocessors 方法  
 起始移除先前配置給這個排程器的虛擬處理器根。  
  
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
 資源管理員會叫用`RemoveVirtualProcessors`若要取回一組的虛擬處理器根排程器的方法。 排程器所要叫用[移除](iexecutionresource-structure.md#remove)方法完成時的虛擬處理器根與每個介面上。 請勿使用`IVirtualProcessorRoot`介面一旦已叫用`Remove`方法。  
  
 參數`ppVirtualProcessorRoots`指向之介面的陣列。 要移除的虛擬處理器根物件的集合，之間根目錄有從未啟用可以使用立即傳回`Remove`方法。 根目錄，已啟用和任一個執行的工作，或已遭停用而且正在等候送達時，工作應該會以非同步方式傳回。 排程器必須進行不斷嘗試以便盡快移除虛擬處理器根。 延遲的虛擬處理器根移除可能會導致意外的過度訂閱的排程器內。  
  
##  <a name="statistics"></a>Ischeduler:: Statistics 方法  
 提供工作從抵達到完成率和排程器佇列長度的變更相關資訊。  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pTaskCompletionRate`  
 完成時排程器自上次呼叫這個方法的工作數目。  
  
 `pTaskArrivalRate`  
 自上次呼叫這個方法已到達在排程器的工作數目。  
  
 `pNumberOfTasksEnqueued`  
 所有排程器佇列中的工作總數。  
  
### <a name="remarks"></a>備註  
 若要排程器蒐集統計資料是叫用此方法由資源管理員。 這裡所收集的統計資料將用來動態回應演算法來判斷適當將更多的資源指派給排程器，以及何時會佔用資源的磁碟機。 排程器所提供的值可以是開放式，而且不一定需要精確反映目前的計數。  
  
 如果您希望資源管理員使用像是工作抵達這類事件的意見反應，決定如何在您的排程器與資源管理員中註冊的其他排程器之間平衡資源，則應該實作這個方法。 如果您選擇不蒐集統計資料，您可以設定原則機碼`DynamicProgressFeedback`值`DynamicProgressFeedbackDisabled`在您的排程器原則和資源管理員不會呼叫您的排程器上的這個方法。  
  
 不存在的統計資訊，資源管理員要用來進行資源配置和移轉決策的硬體執行緒訂用帳戶層級。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [SchedulerPolicy 類別](schedulerpolicy-class.md)   
 [IExecutionContext 結構](iexecutioncontext-structure.md)   
 [IThreadProxy 結構](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)   
 [IResourceManager 結構](iresourcemanager-structure.md)
