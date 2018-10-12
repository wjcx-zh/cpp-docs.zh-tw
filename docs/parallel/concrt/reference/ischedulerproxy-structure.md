---
title: ISchedulerProxy 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72fa49d763159385607330231994d15952f0c771
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163136"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 結構

排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。

## <a name="syntax"></a>語法

```
struct ISchedulerProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|如果它尚未與其中一個相關聯，則您可以關聯的執行緒 proxy，執行內容。|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|建立新的虛擬處理器根上現有的執行資源相關聯的硬體執行緒。|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|要求的初始配置的虛擬處理器根。 每個虛擬處理器根代表執行一個執行緒可以執行的工作排程器的能力。|
|[ISchedulerProxy::Shutdown](#shutdown)|通知資源管理員排程器正在關閉。 這會導致立即回收授與給排程器的所有資源，資源管理員。|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|目前的執行緒與 Resource Manager 註冊，將它與這個排程器相關聯。|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|取消關聯從指定的執行內容的執行緒 proxy`pContext`參數並傳回到執行緒 proxy 處理站的可用集區。 這個方法 lze volat pouze 上透過繫結執行內容[ischedulerproxy:: Bindcontext](#bindcontext)方法而且尚未啟動透過正在`pContext`參數[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法呼叫。|

## <a name="remarks"></a>備註

Resource Manager 交給`ISchedulerProxy`介面來使用它向每個排程器[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`ISchedulerProxy`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="bindcontext"></a>  Ischedulerproxy:: Bindcontext 方法

如果它尚未與其中一個相關聯，則您可以關聯的執行緒 proxy，執行內容。

```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要將關聯的執行緒 proxy 的執行內容的介面。

### <a name="remarks"></a>備註

通常[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法會依需求執行內容項目繫結的執行緒 proxy。 有，不過，就必須繫結的內容，以確認的情況下`SwitchTo`方法切換至已繫結的內容。 UMS 排程內容，因為它不能呼叫方法，配置記憶體時，在此情況下，並繫結的執行緒 proxy 可能會牽涉記憶體配置，如果執行緒 proxy 不是隨手可得中可用的集區的執行緒 proxy 處理站。

`invalid_argument` 如果擲回參數`pContext`具有值`NULL`。

##  <a name="createoversubscriber"></a>  Ischedulerproxy:: Createoversubscriber 方法

建立新的虛擬處理器根上現有的執行資源相關聯的硬體執行緒。

```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>參數

*pExecutionResource*<br/>
`IExecutionResource`表示您想要過度訂閱的硬體執行緒的介面。

### <a name="return-value"></a>傳回值

`IVirtualProcessorRoot` 介面。

### <a name="remarks"></a>備註

當您的排程器想要過度訂閱有限的一段時間的特定硬體執行緒，請使用這個方法。 一旦您已完成的虛擬處理器根，您應該讓它返回與資源管理員藉由呼叫[移除](iexecutionresource-structure.md#remove)方法`IVirtualProcessorRoot`介面。

因為 `IVirtualProcessorRoot` 介面繼承自 `IExecutionResource` 介面，所以您甚至可以過度訂閱現有的虛擬處理器根。

##  <a name="requestinitialvirtualprocessors"></a>  Ischedulerproxy:: Requestinitialvirtualprocessors 方法

要求的初始配置的虛擬處理器根。 每個虛擬處理器根代表執行一個執行緒可以執行的工作排程器的能力。

```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>參數

*doSubscribeCurrentThread*<br/>
是否要訂閱目前的執行緒，並在資源配置期間負責。

### <a name="return-value"></a>傳回值

`IExecutionResource`介面目前的執行緒，如果參數`doSubscribeCurrentThread`具有值 **，則為 true**。 如果值為**false**，此方法會傳回 NULL。

### <a name="remarks"></a>備註

排程器執行任何工作之前，它應該使用這個方法來要求從 Resource Manager 中的虛擬處理器根。 Resource Manager 將會存取排程器原則使用[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)的原則機碼中使用的值`MinConcurrency`，`MaxConcurrency`和`TargetOversubscriptionFactor`來判斷將指派給多少硬體執行緒排程器一開始並建立每個硬體執行緒的幾個虛擬處理器根。 如需有關如何使用排程器原則來判斷排程器的初始配置的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md)。

資源管理員授與資源排程器透過呼叫方法[ischeduler:: Addvirtualprocessors](ischeduler-structure.md#addvirtualprocessors)一份虛擬處理器根。 方法會叫用作為回呼至排程器之前，這個方法會傳回。

如果排程器會藉由設定參數要求訂用帳戶目前的執行緒`doSubscribeCurrentThread`要 **，則為 true**，則方法會傳回`IExecutionResource`介面。 訂用帳戶必須結束於稍後使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。

在決定選取哪一個硬體執行緒時，Resource Manager 會嘗試針對處理器節點親和性進行最佳化。 如果目前執行緒要求的訂用帳戶時，就表示目前執行緒想要參與 指派給這個排程器的工作。 在此情況下，配置的虛擬處理器根憑證位於目前的執行緒執行，盡可能在處理器節點上。

訂閱的執行緒中的動作會增加 1 基礎硬體執行緒的訂用帳戶層級。 訂用帳戶層級會減 1 的訂用帳戶結束時。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

##  <a name="shutdown"></a>  Ischedulerproxy:: Shutdown 方法

通知資源管理員排程器正在關閉。 這會導致立即回收授與給排程器的所有資源，資源管理員。

```
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>備註

所有`IExecutionContext`介面接收結果訂閱使用的方法外部執行緒排程器`ISchedulerProxy::RequestInitialVirtualProcessors`或是`ISchedulerProxy::SubscribeCurrentThread`必須傳回至 Resource Manager 中使用`IExecutionResource::Remove`排程器便自行關機之前。

如果您的排程器有任何停用虛擬處理器根，您必須啟用它們使用[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)，並已保留在其上執行的執行緒 proxy`Dispatch`執行的方法它們會分派再叫用的內容`Shutdown`排程器 proxy 上。

排程器不需要透過呼叫 `Remove` 方法的方式，分別傳回資源管理員授與它的所有虛擬處理器根，因為所有虛擬處理器根都會在關閉時傳回資源管理員。

##  <a name="subscribecurrentthread"></a>  Ischedulerproxy:: Subscribecurrentthread 方法

目前的執行緒與 Resource Manager 註冊，將它與這個排程器相關聯。

```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>傳回值

`IExecutionResource`互動代表目前的執行緒在執行階段。

### <a name="remarks"></a>備註

若要讓資源管理員要負責目前的執行緒，同時將資源配置給您的排程器和其他排程器，請使用這個方法。 排程器中，排程器會接收從 Resource Manager 中的虛擬處理器根以及執行緒打算參與工作排入佇列時，它是特別有用。 Resource Manager 會使用以避免不必要的系統上的硬體執行緒的過度訂閱的資訊。

透過這種方式收到的執行資源應該傳回至 Resource Manager 中使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。 呼叫的執行緒`Remove`方法必須是相同的執行緒，先前稱為`SubscribeCurrentThread`方法。

訂閱的執行緒中的動作會增加 1 基礎硬體執行緒的訂用帳戶層級。 訂用帳戶層級會減 1 的訂用帳戶結束時。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

##  <a name="unbindcontext"></a>  Ischedulerproxy:: Unbindcontext 方法

取消關聯從指定的執行內容的執行緒 proxy`pContext`參數並傳回到執行緒 proxy 處理站的可用集區。 這個方法 lze volat pouze 上透過繫結執行內容[ischedulerproxy:: Bindcontext](#bindcontext)方法而且尚未啟動透過正在`pContext`參數[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法呼叫。

```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要自其執行緒 proxy 取消關聯的執行內容。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
