---
title: ISchedulerProxy 結構
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: dcb6d175fa84e33f6a5af974eb76f1e1246bdc35
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226694"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 結構

排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。

## <a name="syntax"></a>語法

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[ISchedulerProxy：： BindCoNtext](#bindcontext)|將執行內容與執行緒 proxy 產生關聯（如果尚未與它相關聯的話）。|
|[ISchedulerProxy：： CreateOversubscriber](#createoversubscriber)|在與現有執行資源相關聯的硬體執行緒上建立新的虛擬處理器根。|
|[ISchedulerProxy：： RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|要求虛擬處理器根的初始配置。 每個虛擬處理器根目錄都代表能夠執行一個可執行排程器工作的執行緒。|
|[ISchedulerProxy：： Shutdown](#shutdown)|通知 Resource Manager 排程器正在關閉中。 這會導致 Resource Manager 立即回收所有授與排程器的資源。|
|[ISchedulerProxy：： SubscribeCurrentThread](#subscribecurrentthread)|向 Resource Manager 註冊目前的執行緒，並將其與此排程器產生關聯。|
|[ISchedulerProxy：： UnbindCoNtext](#unbindcontext)|解除執行緒 proxy 與參數所指定之執行內容的比對 `pContext` ，並將它傳回給執行緒 proxy factory 的可用集區。 這個方法只能在透過[ISchedulerProxy：： BindCoNtext](#bindcontext)方法所系結的執行內容上呼叫，而且尚未透過 `pContext` [IThreadProxy：： SwitchTo](ithreadproxy-structure.md#switchto)方法呼叫的參數啟動。|

## <a name="remarks"></a>備註

Resource Manager `ISchedulerProxy` 使用[IResourceManager：： RegisterScheduler](iresourcemanager-structure.md#registerscheduler)方法，將介面交給向它註冊的每個排程器。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ISchedulerProxy`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** 並行

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy：： BindCoNtext 方法

將執行內容與執行緒 proxy 產生關聯（如果尚未與它相關聯的話）。

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要與執行緒 proxy 產生關聯之執行內容的介面。

### <a name="remarks"></a>備註

一般來說， [IThreadProxy：： SwitchTo](ithreadproxy-structure.md#switchto)方法會視需要將執行緒 proxy 系結至執行內容。 不過，在某些情況下，必須事先系結內容，以確保 `SwitchTo` 方法會切換至已經系結的內容。 這是在 UMS 排程內容上的情況，因為它無法呼叫配置記憶體的方法，而且如果執行緒 proxy 無法線上程 proxy 處理站的可用集區中輕鬆使用，則系結執行緒 proxy 可能會牽涉到記憶體配置。

`invalid_argument`如果參數具有值，則會擲回 `pContext` `NULL` 。

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>ISchedulerProxy：： CreateOversubscriber 方法

在與現有執行資源相關聯的硬體執行緒上建立新的虛擬處理器根。

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>參數

*pExecutionResource*<br/>
`IExecutionResource`介面，代表您想要超額訂閱的硬體執行緒。

### <a name="return-value"></a>傳回值

`IVirtualProcessorRoot` 介面。

### <a name="remarks"></a>備註

當您的排程器想要在有限的時間內超額訂閱特定硬體執行緒時，請使用這個方法。 當您完成虛擬處理器根之後，您應該在介面上呼叫[Remove](iexecutionresource-structure.md#remove)方法，將它傳回給資源管理員 `IVirtualProcessorRoot` 。

因為 `IVirtualProcessorRoot` 介面繼承自 `IExecutionResource` 介面，所以您甚至可以過度訂閱現有的虛擬處理器根。

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>ISchedulerProxy：： RequestInitialVirtualProcessors 方法

要求虛擬處理器根的初始配置。 每個虛擬處理器根目錄都代表能夠執行一個可執行排程器工作的執行緒。

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>參數

*doSubscribeCurrentThread*<br/>
在資源配置期間，是否要訂閱目前的執行緒並加以考慮。

### <a name="return-value"></a>傳回值

`IExecutionResource`如果參數具有值，則為目前線程的介面 `doSubscribeCurrentThread` **`true`** 。 如果值為 **`false`** ，則方法會傳回 Null。

### <a name="remarks"></a>備註

在排程器執行任何工作之前，應該使用這個方法來要求 Resource Manager 的虛擬處理器根。 Resource Manager 會使用[IScheduler：： GetPolicy](ischeduler-structure.md#getpolicy)存取排程器的原則，並使用原則金鑰的值 `MinConcurrency` ， `MaxConcurrency` 並 `TargetOversubscriptionFactor` 判斷要一開始指派給排程器的硬體執行緒數量，以及要為每個硬體執行緒建立多少個虛擬處理器根。 如需排程器原則如何用來判斷排程器初始配置的詳細資訊，請參閱[PolicyElementKey](concurrency-namespace-enums.md)。

Resource Manager 會藉由呼叫[IScheduler：： AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors)方法與虛擬處理器根目錄清單來將資源授與排程器。 在這個方法傳回之前，會叫用方法做為對排程器的回呼。

如果排程器藉由將參數設定為來要求目前線程的訂閱 `doSubscribeCurrentThread` **`true`** ，則方法會傳回 `IExecutionResource` 介面。 您必須使用[IExecutionResource：： Remove](iexecutionresource-structure.md#remove)方法，在稍後結束訂用帳戶。

判斷哪些硬體執行緒已選取時，Resource Manager 會嘗試針對處理器節點親和性進行優化。 如果要求目前線程的訂閱，則表示目前的執行緒想要參與指派給此排程器的工作。 在這種情況下，已配置的虛擬處理器根會位於目前線程執行所在的處理器節點上（如果可能的話）。

訂閱執行緒的動作會增加基礎硬體執行緒的訂用帳戶層級一。 當訂閱終止時，訂用帳戶層級會縮減一個。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy：： Shutdown 方法

通知 Resource Manager 排程器正在關閉中。 這會導致 Resource Manager 立即回收所有授與排程器的資源。

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>備註

排程器 `IExecutionContext` 由於使用方法訂閱外部執行緒而收到的所有介面，必須在排程器 `ISchedulerProxy::RequestInitialVirtualProcessors` 自行關閉之前， `ISchedulerProxy::SubscribeCurrentThread` 使用傳回給 Resource Manager `IExecutionResource::Remove` 。

如果您的排程器具有任何已停用的虛擬處理器根，您必須使用[IVirtualProcessorRoot：： activate](ivirtualprocessorroot-structure.md#activate)來啟用它們，並讓執行緒 proxy 在其上執行，並在 `Dispatch` 您于排程器 proxy 上叫用之前，保留所分派的執行內容的方法 `Shutdown` 。

排程器不需要透過呼叫 `Remove` 方法的方式，分別傳回資源管理員授與它的所有虛擬處理器根，因為所有虛擬處理器根都會在關閉時傳回資源管理員。

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy：： SubscribeCurrentThread 方法

向 Resource Manager 註冊目前的執行緒，並將其與此排程器產生關聯。

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>傳回值

在 `IExecutionResource` 執行時間中代表目前線程的介面。

### <a name="remarks"></a>備註

如果您想要 Resource Manager 在將資源配置給排程器和其他排程器時，將目前線程的帳戶加以考慮，請使用這個方法。 當執行緒計畫參與佇列至排程器的工作，以及排程器從 Resource Manager 接收的虛擬處理器根時，此功能特別有用。 Resource Manager 會使用資訊來防止系統上的硬體執行緒不必要的過度訂閱。

透過這個方法所收到的執行資源應該使用[IExecutionResource：： Remove](iexecutionresource-structure.md#remove)方法傳回給 Resource Manager。 呼叫方法的執行緒 `Remove` 必須是先前呼叫方法的同一個執行緒 `SubscribeCurrentThread` 。

訂閱執行緒的動作會增加基礎硬體執行緒的訂用帳戶層級一。 當訂閱終止時，訂用帳戶層級會縮減一個。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>ISchedulerProxy：： UnbindCoNtext 方法

解除執行緒 proxy 與參數所指定之執行內容的比對 `pContext` ，並將它傳回給執行緒 proxy factory 的可用集區。 這個方法只能在透過[ISchedulerProxy：： BindCoNtext](#bindcontext)方法所系結的執行內容上呼叫，而且尚未透過 `pContext` [IThreadProxy：： SwitchTo](ithreadproxy-structure.md#switchto)方法呼叫的參數啟動。

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要與執行緒 proxy 解除關聯的執行內容。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
