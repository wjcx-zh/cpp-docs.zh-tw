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
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368152"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 結構

排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。

## <a name="syntax"></a>語法

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I計劃代理::綁定上下文](#bindcontext)|如果執行上下文尚未與線程代理關聯,則將其關聯為線程代理。|
|[I 計劃代理::建立超額訂閱者](#createoversubscriber)|在與現有執行資源關聯的硬體線程上創建新的虛擬處理器根。|
|[I 計劃代理::請求初始虛擬處理器](#requestinitialvirtualprocessors)|請求初始分配虛擬處理器根。 每個虛擬處理器根表示能夠執行一個線程,該線程可以執行計劃程式的工作。|
|[I 計劃代理::關閉](#shutdown)|通知資源管理員計劃程式正在關閉。 這將導致資源管理器立即回收授予計劃程式的所有資源。|
|[I 計劃代理::訂閱目前的線程](#subscribecurrentthread)|將當前線程註冊到資源管理器,將其與此計劃程序關聯。|
|[I計劃代理::取消綁定上下文](#unbindcontext)|將執行緒代理與參數指定的執行上下文分離,`pContext`並將其傳回到線程代理工廠的可用池。 此方法只能在通過[I-計劃代理::綁定上下文](#bindcontext)綁定的執行上下文中調用,並且尚未通過[IThreadProxy:::switchto](ithreadproxy-structure.md#switchto)`pContext`方法調用的 參數啟動。|

## <a name="remarks"></a>備註

資源管理器使用`ISchedulerProxy`[IResourceManager ::註冊計劃器](iresourcemanager-structure.md#registerscheduler)方法將接給與其一起註冊的每個計劃程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ISchedulerProxy`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>I計劃代理::綁定上下文方法

如果執行上下文尚未與線程代理關聯,則將其關聯為線程代理。

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要與線程代理關聯的執行上下文的介面。

### <a name="remarks"></a>備註

通常[,IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto)方法將按需將線程代理綁定到執行上下文。 但是,在某些情況下,需要提前綁定上下文,以確保`SwitchTo`方法切換到已綁定的上下文。 UMS 調度上下文中就是這種情況,因為它無法調用分配記憶體的方法,如果線程代理在線程代理工廠的可用池中不容易可用,則綁定線程代理可能涉及記憶體分配。

`invalid_argument`如果參數`pContext`有`NULL`值 ,則引發 。

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>I計劃代理::建立超額訂閱者方法

在與現有執行資源關聯的硬體線程上創建新的虛擬處理器根。

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>參數

*p 執行資源*<br/>
表示`IExecutionResource`要超額訂閱的硬體線程的介面。

### <a name="return-value"></a>傳回值

`IVirtualProcessorRoot` 介面。

### <a name="remarks"></a>備註

當您的計劃程式想要在有限的時間內超額訂閱特定硬體線程時,請使用此方法。 使用虛擬處理器根后,應通過在`IVirtualProcessorRoot`介面上調用[Remove](iexecutionresource-structure.md#remove)方法將其返回到資源管理器。

因為 `IVirtualProcessorRoot` 介面繼承自 `IExecutionResource` 介面，所以您甚至可以過度訂閱現有的虛擬處理器根。

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>I 計劃代理::請求初始虛擬處理器方法

請求初始分配虛擬處理器根。 每個虛擬處理器根表示能夠執行一個線程,該線程可以執行計劃程式的工作。

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>參數

*完成訂閱目前的線程*<br/>
是否訂閱當前線程並在資源分配期間對它進行帳戶處理。

### <a name="return-value"></a>傳回值

如果`IExecutionResource`參數`doSubscribeCurrentThread`的值**為 true**,則當前線程的介面。 如果值為**false,** 則該方法將傳回 NULL。

### <a name="remarks"></a>備註

在計劃程式執行任何工作之前,它應該使用此方法從資源管理員請求虛擬處理器根。 資源管理器將使用[I-計劃器::getPolicy](ischeduler-structure.md#getpolicy)訪問計畫程式的策略,並使用`MinConcurrency`策略鍵的`MaxConcurrency`值,`TargetOversubscriptionFactor`並確定最初要分配給計畫程式的硬體線程數以及為每個硬體線程創建多少個虛擬處理器根。 有關如何使用計畫程式策略來確定計畫程式的初始配置的詳細資訊,請參閱[策略元素鍵](concurrency-namespace-enums.md)。

資源管理員通過調用方法[I-計劃器::添加](ischeduler-structure.md#addvirtualprocessors)具有虛擬處理器根的清單,將資源授予計劃程式。 在此方法返回之前,將該方法作為回調調用到計劃程式。

如果計劃程式通過將參數`doSubscribeCurrentThread`設置為**true**請求當前線程的訂閱,則該方法將`IExecutionResource`返回一個介面。 必須使用[I執行資源::刪除](iexecutionresource-structure.md#remove)方法在稍後某個點終止訂閱。

確定選擇哪些硬體線程時,資源管理器將嘗試優化處理器節點相關性。 如果為當前線程請求訂閱,則表示當前線程打算參與分配給此計劃程式的工作。 在這種情況下,分配的虛擬處理器根位於當前線程執行的處理器節點上(如果可能)。

訂閱線程的行為將基礎硬體線程的訂閱級別增加一個。 終止訂閱時,訂閱級別將降低 1。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>I 計劃代理::關閉方法

通知資源管理員計劃程式正在關閉。 這將導致資源管理器立即回收授予計劃程式的所有資源。

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>備註

計劃`IExecutionContext`程式使用`ISchedulerProxy::RequestInitialVirtualProcessors`方法 訂閱外部線程后收到的所有介面`ISchedulerProxy::SubscribeCurrentThread`,或者必須在計劃程式關閉`IExecutionResource::Remove`之前使用返回到資源管理器。

如果計劃程式具有任何已停用的虛擬處理器根,則必須使用[IVirtualProcessorRoot:::activate](ivirtualprocessorroot-structure.md#activate)啟動它們啟動它們,並且讓線程代理在它們上`Dispatch`執行,`Shutdown`在調用 計劃程式代理之前,將離開它們正在調度的執行上下文的方法。

排程器不需要透過呼叫 `Remove` 方法的方式，分別傳回資源管理員授與它的所有虛擬處理器根，因為所有虛擬處理器根都會在關閉時傳回資源管理員。

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>I計劃代理::訂閱電流線程方法

將當前線程註冊到資源管理器,將其與此計劃程序關聯。

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>傳回值

在`IExecutionResource`運行時表示當前線程的介面。

### <a name="remarks"></a>備註

如果希望資源管理員在將資源分配給計劃程式和其他計劃程式時考慮當前線程,請使用此方法。 當線程計劃參與排隊到計劃程式的工作以及計劃程式從資源管理器接收的虛擬處理器根時,它特別有用。 資源管理器使用資訊來防止系統上硬體線程的不必要的過度訂閱。

應使用[I 執行資源::刪除](iexecutionresource-structure.md#remove)方法將通過此方法接收的執行資源返回到資源管理器。 調用方法的`Remove`線程必須與以前調`SubscribeCurrentThread`用 該方法的線程相同。

訂閱線程的行為將基礎硬體線程的訂閱級別增加一個。 終止訂閱時,訂閱級別將降低 1。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>I計劃代理::取消綁定上下文方法

將執行緒代理與參數指定的執行上下文分離,`pContext`並將其傳回到線程代理工廠的可用池。 此方法只能在通過[I-計劃代理::綁定上下文](#bindcontext)綁定的執行上下文中調用,並且尚未通過[IThreadProxy:::switchto](ithreadproxy-structure.md#switchto)`pContext`方法調用的 參數啟動。

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要與其線程代理取消關聯的執行上下文。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
