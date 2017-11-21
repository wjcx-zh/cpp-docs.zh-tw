---
title: "ISchedulerProxy 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d650df9c77b6a99c7ee9982caa88e8eb7c1b8d9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 結構
排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。  
  
## <a name="syntax"></a>語法  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Ischedulerproxy:: Bindcontext](#bindcontext)|如果它尚未與一個，關聯的執行緒 proxy，將執行內容。|  
|[Ischedulerproxy:: Createoversubscriber](#createoversubscriber)|建立新的虛擬處理器根上現有的執行資源相關聯的硬體執行緒。|  
|[Ischedulerproxy:: Requestinitialvirtualprocessors](#requestinitialvirtualprocessors)|要求的初始配置的虛擬處理器根。 每個虛擬處理器根代表執行一個執行緒可以執行工作排程器的能力。|  
|[Ischedulerproxy:: Shutdown](#shutdown)|向資源管理員通知排程器正在關閉。 這會導致立即回收授與給排程器的所有資源的資源管理員。|  
|[Ischedulerproxy:: Subscribecurrentthread](#subscribecurrentthread)|註冊目前的執行緒與資源管理員，將它與這個排程器產生關聯。|  
|[Ischedulerproxy:: Unbindcontext](#unbindcontext)|從所指定的執行內容的執行緒 proxy 會解除關聯`pContext`參數並傳回至執行緒 proxy 處理站可用集區。 這個方法只能呼叫執行內容是透過繫結[ischedulerproxy:: Bindcontext](#bindcontext)方法而且尚未啟動透過正在`pContext`參數[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法呼叫。|  
  
## <a name="remarks"></a>備註  
 資源管理員交給`ISchedulerProxy`介面，以註冊使用每一個排程器[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="bindcontext"></a>Ischedulerproxy:: Bindcontext 方法  
 如果它尚未與一個，關聯的執行緒 proxy，將執行內容。  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 要與執行緒 proxy 的執行內容的介面。  
  
### <a name="remarks"></a>備註  
 一般來說， [ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法會依需求執行內容項目繫結的執行緒 proxy。 有，不過，情況就必須繫結內容，事先才能確保`SwitchTo`方法切換至已繫結的內容。 這是在 UMS 排程內容，因為它無法呼叫方法，以配置記憶體的案例，而繫結的執行緒 proxy 可能涉及記憶體配置，如果執行緒 proxy 不便於使用的執行緒 proxy 處理站可用集區中。  
  
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
 當您的排程器要過度訂閱有限的一段時間的特定硬體執行緒時，請使用這個方法。 在您完成與虛擬處理器根，也應該傳回資源管理員藉由呼叫[移除](iexecutionresource-structure.md#remove)方法`IVirtualProcessorRoot`介面。  
  
 因為 `IVirtualProcessorRoot` 介面繼承自 `IExecutionResource` 介面，所以您甚至可以過度訂閱現有的虛擬處理器根。  
  
##  <a name="requestinitialvirtualprocessors"></a>Ischedulerproxy:: Requestinitialvirtualprocessors 方法  
 要求的初始配置的虛擬處理器根。 每個虛擬處理器根代表執行一個執行緒可以執行工作排程器的能力。  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>參數  
 `doSubscribeCurrentThread`  
 是否要訂閱目前的執行緒，並在資源配置時負責。  
  
### <a name="return-value"></a>傳回值  
 `IExecutionResource`介面目前的執行緒，如果參數`doSubscribeCurrentThread`值`true`。 如果值為`false`，方法會傳回`NULL`。  
  
### <a name="remarks"></a>備註  
 排程器會執行任何工作之前，它應該使用這個方法來從資源管理員要求虛擬處理器根。 資源管理員會存取的排程器原則使用[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)和使用的原則機碼的值`MinConcurrency`，`MaxConcurrency`和`TargetOversubscriptionFactor`來判斷多少的硬體執行緒指派給排程器一開始並建立每個硬體執行緒數目的虛擬處理器根。 如需有關如何排程器原則可用來判斷排程器的初始配置的詳細資訊，請參閱[PolicyElementKey](concurrency-namespace-enums.md)。  
  
 資源管理員會授與資源排程器透過呼叫方法[ischeduler:: Addvirtualprocessors](ischeduler-structure.md#addvirtualprocessors)虛擬處理器根的清單。 方法會叫用做為回呼至排程器此方法傳回之前。  
  
 如果排程器會藉由設定參數要求訂用帳戶目前的執行緒`doSubscribeCurrentThread`至`true`，方法會傳回`IExecutionResource`介面。 訂用帳戶必須終止於稍後使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。  
  
 在決定選取哪一個硬體執行緒時，資源管理員會嘗試最佳化處理器節點親和性。 如果目前執行緒要求訂用帳戶時，就表示目前執行緒打算參與指派給這個排程器的工作。 在這種情況下，配置虛擬處理器根位於目前的執行緒正在執行，盡可能在處理器節點上。  
  
 指訂閱執行緒會增加 1 基礎硬體執行緒的訂用帳戶層級。 訂用帳戶層級會減 1 結束訂用帳戶時。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="shutdown"></a>Ischedulerproxy:: Shutdown 方法  
 向資源管理員通知排程器正在關閉。 這會導致立即回收授與給排程器的所有資源的資源管理員。  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>備註  
 所有`IExecutionContext`介面接收結果訂閱使用的方法外部執行緒排程器`ISchedulerProxy::RequestInitialVirtualProcessors`或`ISchedulerProxy::SubscribeCurrentThread`必須傳回資源管理員使用`IExecutionResource::Remove`排程器自行關閉之前。  
  
 如果您的排程器有任何停用虛擬處理器根，您必須啟用它們使用[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)，而且有將保留在其上執行的執行緒 proxy`Dispatch`執行的方法它們會分派之前您叫用的內容`Shutdown`排程器 proxy 上。  
  
 排程器不需要透過呼叫 `Remove` 方法的方式，分別傳回資源管理員授與它的所有虛擬處理器根，因為所有虛擬處理器根都會在關閉時傳回資源管理員。  
  
##  <a name="subscribecurrentthread"></a>Ischedulerproxy:: Subscribecurrentthread 方法  
 註冊目前的執行緒與資源管理員，將它與這個排程器產生關聯。  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 `IExecutionResource` Critical 代表執行階段中目前的執行緒。  
  
### <a name="remarks"></a>備註  
 如果您希望資源管理員，以說明目前的執行緒時將資源配置到您的排程器和其他排程器，請使用這個方法。 當排程器中，排程器會接收從資源管理員的虛擬處理器根以及佇列參與工作的執行緒計劃時，它會特別有用。 資源管理員會使用以避免不必要的過度訂閱的系統上的硬體執行緒的資訊。  
  
 透過此方法接收的執行資源應該傳回資源管理員使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。 呼叫的執行緒`Remove`方法必須是相同的執行緒，先前稱為`SubscribeCurrentThread`方法。  
  
 指訂閱執行緒會增加 1 基礎硬體執行緒的訂用帳戶層級。 訂用帳戶層級會減 1 結束訂用帳戶時。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="unbindcontext"></a>Ischedulerproxy:: Unbindcontext 方法  
 從所指定的執行內容的執行緒 proxy 會解除關聯`pContext`參數並傳回至執行緒 proxy 處理站可用集區。 這個方法只能呼叫執行內容是透過繫結[ischedulerproxy:: Bindcontext](#bindcontext)方法而且尚未啟動透過正在`pContext`參數[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法呼叫。  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pContext`  
 要解除其執行緒 proxy 的執行內容。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IScheduler 結構](ischeduler-structure.md)   
 [IThreadProxy 結構](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)   
 [IResourceManager 結構](iresourcemanager-structure.md)
