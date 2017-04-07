---
title: "ISchedulerProxy 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs:
- C++
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 3dd95150022ad94f50b456c84f7dacd2d3cef7c5
ms.lasthandoff: 03/17/2017

---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 結構
排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。  
  
## <a name="syntax"></a>語法  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Ischedulerproxy:: Bindcontext](#bindcontext)|如果它尚未與一個，關聯的執行緒 proxy，將執行內容。|  
|[Ischedulerproxy:: Createoversubscriber](#createoversubscriber)|建立新的虛擬處理器根上現有的執行資源相關聯的硬體執行緒。|  
|[Ischedulerproxy:: Requestinitialvirtualprocessors](#requestinitialvirtualprocessors)|要求初始配置的虛擬處理器根。 每個虛擬處理器根代表執行一個執行緒可以執行的工作排程器的能力。|  
|[Ischedulerproxy:: Shutdown](#shutdown)|排程器正在關閉通知資源管理員。 這將導致立即回收所有資源排程器授與資源管理員。|  
|[Ischedulerproxy:: Subscribecurrentthread](#subscribecurrentthread)|註冊目前的執行緒與資源管理員，將它與此排程器產生關聯。|  
|[Ischedulerproxy:: Unbindcontext](#unbindcontext)|從所指定的執行內容的執行緒 proxy 會解除關聯`pContext`參數，並返回執行緒 proxy factory 可用集區。 這個方法只能呼叫執行內容是透過繫結[ischedulerproxy:: Bindcontext](#bindcontext)方法和尚未透過正在開始`pContext`參數[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法呼叫。|  
  
## <a name="remarks"></a>備註  
 資源管理員會將`ISchedulerProxy`介面來使用它會向每個排程器[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="bindcontext"></a>Ischedulerproxy:: Bindcontext 方法  
 如果它尚未與一個，關聯的執行緒 proxy，將執行內容。  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 執行緒 proxy 與相關聯的執行內容的介面。  
  
### <a name="remarks"></a>備註  
 一般來說， [ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法會依需求執行內容項目繫結的執行緒 proxy。 有，不過，就必須將內容預先以確保繫結的情況下`SwitchTo`方法切換至已繫結的內容。 這是用於 UMS 排程內容時，它不能呼叫方法，配置記憶體，而繫結的執行緒 proxy 可能涉及記憶體配置，如果執行緒 proxy 不是隨手可得可用的集區執行緒 proxy 處理站。  
  
 `invalid_argument`如果擲回參數`pContext`值`NULL`。  
  
##  <a name="createoversubscriber"></a>Ischedulerproxy:: Createoversubscriber 方法  
 建立新的虛擬處理器根上現有的執行資源相關聯的硬體執行緒。  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pExecutionResource`  
 `IExecutionResource`代表您想要過度訂閱的硬體執行緒的介面。  
  
### <a name="return-value"></a>傳回值  
 `IVirtualProcessorRoot` 介面。  
  
### <a name="remarks"></a>備註  
 當您的排程器要過度訂閱一段有限的時間內的特定硬體執行緒，請使用這個方法。 在您完成與虛擬處理器根，您應該會傳回它對資源管理員藉由呼叫[移除](iexecutionresource-structure.md#remove)方法`IVirtualProcessorRoot`介面。  
  
 因為 `IVirtualProcessorRoot` 介面繼承自 `IExecutionResource` 介面，所以您甚至可以過度訂閱現有的虛擬處理器根。  
  
##  <a name="requestinitialvirtualprocessors"></a>Ischedulerproxy:: Requestinitialvirtualprocessors 方法  
 要求初始配置的虛擬處理器根。 每個虛擬處理器根代表執行一個執行緒可以執行的工作排程器的能力。  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>參數  
 `doSubscribeCurrentThread`  
 是否要訂閱目前的執行緒，並在資源配置時考量。  
  
### <a name="return-value"></a>傳回值  
 `IExecutionResource`介面目前的執行緒，如果參數`doSubscribeCurrentThread`值`true`。 如果值為`false`，方法會傳回`NULL`。  
  
### <a name="remarks"></a>備註  
 排程器會執行任何工作之前，它應該使用這個方法來從資源管理員要求的虛擬處理器根。 資源管理員會存取的排程器原則使用[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy) ，並使用值的原則機碼`MinConcurrency`，`MaxConcurrency`和`TargetOversubscriptionFactor`來判斷多少個硬體執行緒一開始將指派給排程器，為每個硬體執行緒建立多少虛擬處理器根。 如需有關如何使用排程器原則來判斷排程器的初始配置的詳細資訊，請參閱[PolicyElementKey](concurrency-namespace-enums.md)。  
  
 資源管理員會授與資源排程器所呼叫的方法[ischeduler:: Addvirtualprocessors](ischeduler-structure.md#addvirtualprocessors)一份虛擬處理器根。 方法會叫用當做回呼至排程器之前，這個方法會傳回。  
  
 如果排程器要求訂用帳戶目前的執行緒將參數設定`doSubscribeCurrentThread`至`true`，方法會傳回`IExecutionResource`介面。 訂閱必須終止於稍後使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。  
  
 在決定選取哪一個硬體執行緒，資源管理員會嘗試最佳化處理器節點親和性。 如果目前執行緒要求訂用帳戶時，則表示目前執行緒想要參與工作指派給這個排程器。 在這種情況下，配置虛擬處理器根項目位於目前的執行緒正在執行，盡可能在處理器節點上。  
  
 訂閱執行緒的動作都會增加一個基礎硬體執行緒的訂閱層級。 訂閱層級數目減少一個終止訂閱時。 如需有關訂閱層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="shutdown"></a>Ischedulerproxy:: Shutdown 方法  
 排程器正在關閉通知資源管理員。 這將導致立即回收所有資源排程器授與資源管理員。  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>備註  
 所有`IExecutionContext`介面結果訂閱外部執行緒使用的方法所得的排程器`ISchedulerProxy::RequestInitialVirtualProcessors`或`ISchedulerProxy::SubscribeCurrentThread`必須傳回至資源管理員使用`IExecutionResource::Remove`排程器自行關閉之前。  
  
 如果您的排程器有任何停用虛擬處理器根，您必須啟用它們使用[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)，而且有保留在其上執行的執行緒 proxy`Dispatch`方法的執行內容，他們會分派之前叫用`Shutdown`排程器 proxy 上。  
  
 排程器不需要透過呼叫 `Remove` 方法的方式，分別傳回資源管理員授與它的所有虛擬處理器根，因為所有虛擬處理器根都會在關閉時傳回資源管理員。  
  
##  <a name="subscribecurrentthread"></a>Ischedulerproxy:: Subscribecurrentthread 方法  
 註冊目前的執行緒與資源管理員，將它與此排程器產生關聯。  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 `IExecutionResource`介面代表執行階段中目前的執行緒。  
  
### <a name="remarks"></a>備註  
 如果您希望資源管理員目前的執行緒排程器和其他排程器配置資源時的考量，請使用這個方法。 當排程器中，排程器會接收從資源管理員的虛擬處理器根以及排入佇列的執行緒計劃參與工作，它是特別有用。 資源管理員會使用以避免不必要的系統上的硬體執行緒的過度訂閱資訊。  
  
 透過這種方式收到的執行資源應該傳回至資源管理員使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。 呼叫的執行緒`Remove`方法必須是相同的執行緒，先前稱為`SubscribeCurrentThread`方法。  
  
 訂閱執行緒的動作都會增加一個基礎硬體執行緒的訂閱層級。 訂閱層級數目減少一個終止訂閱時。 如需有關訂閱層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="unbindcontext"></a>Ischedulerproxy:: Unbindcontext 方法  
 從所指定的執行內容的執行緒 proxy 會解除關聯`pContext`參數，並返回執行緒 proxy factory 可用集區。 這個方法只能呼叫執行內容是透過繫結[ischedulerproxy:: Bindcontext](#bindcontext)方法和尚未透過正在開始`pContext`參數[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法呼叫。  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 若要取消其執行緒 proxy 與執行內容。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IScheduler 結構](ischeduler-structure.md)   
 [IThreadProxy 結構](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)   
 [IResourceManager 結構](iresourcemanager-structure.md)

