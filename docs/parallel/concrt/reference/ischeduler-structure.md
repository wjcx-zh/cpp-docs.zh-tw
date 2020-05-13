---
title: IScheduler 結構
ms.date: 11/04/2016
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
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368165"
---
# <a name="ischeduler-structure"></a>IScheduler 結構

工作排程器抽象概念的介面。 並行執行階段的資源管理員會使用這個介面與工作排程器通訊。

## <a name="syntax"></a>語法

```cpp
struct IScheduler;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 計劃::新增虛擬處理器](#addvirtualprocessors)|提供一組帶有一組虛擬處理器根的調度程式,供其使用。 每個`IVirtualProcessorRoot`介面表示執行單個線程的權利,該線程可以代表計劃程式執行工作。|
|[I時程表::取得 Id](#getid)|返回計劃程式的唯一標識符。|
|[I計劃::取得策略](#getpolicy)|返回計劃程式策略的副本。 有關計劃程式原則的詳細資訊,請參閱[計畫程式原則](schedulerpolicy-class.md)。|
|[I計劃::通知資源外部忙](#notifyresourcesexternallybusy)|通知此計畫程式,陣列`ppVirtualProcessorRoots`中虛擬處理器根集表示的硬體線程現在正由其他計劃程式使用。|
|[I計劃::通知資源外部空閒](#notifyresourcesexternallyidle)|通知此計畫程式,陣列`ppVirtualProcessorRoots`中虛擬處理器根集表示的硬體線程不由其他計劃程式使用。|
|[I 計劃::刪除虛擬處理器](#removevirtualprocessors)|啟動刪除以前分配給此計劃程式的虛擬處理器根。|
|[I時程表::統計](#statistics)|提供與任務到達率和完成率以及計劃程式佇列長度更改相關的資訊。|

## <a name="remarks"></a>備註

如果要實現與資源管理器通信的自定義計劃程式,則應提供介面的`IScheduler`實現。 此介面是調度程式與資源管理器之間的雙向通信通道的一端。 另一端由資源管理器實現的`IResourceManager``ISchedulerProxy`和介面表示。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IScheduler`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>I 計劃::新增虛擬處理器方法

提供一組帶有一組虛擬處理器根的調度程式,供其使用。 每個`IVirtualProcessorRoot`介面表示執行單個線程的權利,該線程可以代表計劃程式執行工作。

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*虛擬處理器根*<br/>
表示要添加到`IVirtualProcessorRoot`計劃程式的虛擬處理器根的介面陣組。

*count*<br/>
陣列中的`IVirtualProcessorRoot`介面數。

### <a name="remarks"></a>備註

資源管理員調用`AddVirtualProcessor`方法 將一組初始的虛擬處理器根授予計劃程式。 當計劃程序之間重新平衡資源時,它還可以調用方法將虛擬處理器根添加到計劃程式。

## <a name="ischedulergetid-method"></a><a name="getid"></a>I 計劃::GetId 方法

返回計劃程式的唯一標識符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

唯一的整數標識符。

### <a name="remarks"></a>備註

在將介面用作資源管理員提供的方法的參數之前,應使用[Get-計劃rId](concurrency-namespace-functions.md)`IScheduler`函數為實現介面的對象獲取唯一識別符。 調用`GetId`函數時,應返回相同的標識符。

從其他源獲取的標識符可能會導致未定義的行為。

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>I計劃::取得策略方法

返回計劃程式策略的副本。 有關計劃程式原則的詳細資訊,請參閱[計畫程式原則](schedulerpolicy-class.md)。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>傳回值

計劃程式策略的副本。

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>I計劃::通知資源外部忙法

通知此計畫程式,陣列`ppVirtualProcessorRoots`中虛擬處理器根集表示的硬體線程現在正由其他計劃程式使用。

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*虛擬處理器根*<br/>
與其他計畫程式`IVirtualProcessorRoot`已忙的硬體線程關聯的介面陣組。

*count*<br/>
陣列中的`IVirtualProcessorRoot`介面數。

### <a name="remarks"></a>備註

可以將特定硬體線程同時分配給多個計劃程式。 原因之一可能是系統上沒有足夠的硬體線程來滿足所有計劃程式的最低併發性,而無需分享資源。 另一種可能性是,當擁有的計劃程式不使用資源時,資源會臨時分配給其他計劃程式,方法是通過停用該硬體線程上的所有虛擬處理器根。

硬體線程的訂閱級別由與該硬體線程關聯的訂閱線程數和啟動的虛擬處理器根表示。 從特定計劃程式的角度來看,硬體線程的外部訂閱級別是其他計劃程式貢獻的訂閱部分。 當硬體線程的外部訂閱級別從零移動到正區域時,資源在外部忙的通知將發送到計劃程式。

通過此方法發送的通知僅發送到具有策略的調度程式,其中`MinConcurrency`策略鍵的值等於`MaxConcurrency`策略鍵的值。 有關計劃程式原則的詳細資訊,請參閱[計畫程式原則](schedulerpolicy-class.md)。

符合通知條件的計劃程式會在創建通知時獲取一組初始通知,通知它剛剛分配的資源是外部忙還是空閒。

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>I計劃::通知資源外部空閒方法

通知此計畫程式,陣列`ppVirtualProcessorRoots`中虛擬處理器根集表示的硬體線程不由其他計劃程式使用。

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*虛擬處理器根*<br/>
與硬體線程`IVirtualProcessorRoot`關聯的介面陣列,其他計畫程式已處於空閒狀態。

*count*<br/>
陣列中的`IVirtualProcessorRoot`介面數。

### <a name="remarks"></a>備註

可以將特定硬體線程同時分配給多個計劃程式。 原因之一可能是系統上沒有足夠的硬體線程來滿足所有計劃程式的最低併發性,而無需分享資源。 另一種可能性是,當擁有的計劃程式不使用資源時,資源會臨時分配給其他計劃程式,方法是通過停用該硬體線程上的所有虛擬處理器根。

硬體線程的訂閱級別由與該硬體線程關聯的訂閱線程數和啟動的虛擬處理器根表示。 從特定計劃程式的角度來看,硬體線程的外部訂閱級別是其他計劃程式貢獻的訂閱部分。 當硬體線程的外部訂閱級別從以前的正值降至零時,資源在外部忙的通知將發送到計劃程式。

通過此方法發送的通知僅發送到具有策略的調度程式,其中`MinConcurrency`策略鍵的值等於`MaxConcurrency`策略鍵的值。 有關計劃程式原則的詳細資訊,請參閱[計畫程式原則](schedulerpolicy-class.md)。

符合通知條件的計劃程式會在創建通知時獲取一組初始通知,通知它剛剛分配的資源是外部忙還是空閒。

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>I計劃時間::刪除虛擬處理器方法

啟動刪除以前分配給此計劃程式的虛擬處理器根。

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*虛擬處理器根*<br/>
表示要刪除`IVirtualProcessorRoot`的虛擬處理器根的介面陣列。

*count*<br/>
陣列中的`IVirtualProcessorRoot`介面數。

### <a name="remarks"></a>備註

資源管理器調用`RemoveVirtualProcessors`方法從計劃程式收回一組虛擬處理器根。 當使用虛擬處理器根時,計劃程式應調用每個介面上的[Remove](iexecutionresource-structure.md#remove)方法。 呼叫介面上的方法`IVirtualProcessorRoot`後`Remove`, 請勿使用介面。

該參數`ppVirtualProcessorRoots`指向介面陣列。 在要刪除的虛擬處理器根集中,從未啟動過根,可以使用 該`Remove`方法立即返回。 已啟動且正在執行工作或已停用並正在等待工作到達的根應異步返回。 計劃程序必須進行每一次嘗試,以儘快刪除虛擬處理器根。 延遲刪除虛擬處理器根可能會導致計劃程式內意外過度訂閱。

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>I計劃::統計方法

提供與任務到達率和完成率以及計劃程式佇列長度更改相關的資訊。

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>參數

*p 工作完成率*<br/>
自上次調用此方法以來,計劃程式已完成的任務數。

*p 工作到達率*<br/>
自上次調用此方法以來到達計劃程式的任務數。

*已排入的工作編號*<br/>
所有計劃程式佇列中的任務總數。

### <a name="remarks"></a>備註

資源管理員調用此方法以收集計劃程序的統計資訊。 此處收集的統計資訊將用於驅動動態反饋演演演算法,以確定何時適合為計劃程式分配更多資源以及何時獲取資源。 計劃程式提供的值可以是樂觀的,不一定必須準確反映當前計數。

如果您希望資源管理員使用像是工作抵達這類事件的意見反應，決定如何在您的排程器與資源管理員中註冊的其他排程器之間平衡資源，則應該實作這個方法。 如果選擇不收集統計資訊,則可以將策略鍵`DynamicProgressFeedback`設置為計劃程式策略中的`DynamicProgressFeedbackDisabled`值 ,並且資源管理器不會在計劃程序上調用此方法。

在沒有統計資訊的情況下,資源管理器將使用硬體線程訂閱級別來做出資源分配和遷移決策。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[策略元素鍵](concurrency-namespace-enums.md)<br/>
[計劃策略類](schedulerpolicy-class.md)<br/>
[IExecutionContext 結構](iexecutioncontext-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
