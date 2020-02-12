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
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142324"
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
|[IScheduler：： AddVirtualProcessors](#addvirtualprocessors)|提供具有一組虛擬處理器根的排程器，供其使用。 每個 `IVirtualProcessorRoot` 介面都代表執行可代表排程器執行工作之單一執行緒的許可權。|
|[IScheduler：： GetId](#getid)|傳回排程器的唯一識別碼。|
|[IScheduler：： GetPolicy](#getpolicy)|傳回排程器原則的複本。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。|
|[IScheduler：： NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|通知此排程器，由 `ppVirtualProcessorRoots` 陣列中的虛擬處理器根集合所代表的硬體執行緒目前正由其他排程器使用中。|
|[IScheduler：： NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|通知此排程器，由 `ppVirtualProcessorRoots` 陣列中的虛擬處理器根集合所代表的硬體執行緒，不是由其他排程器所使用。|
|[IScheduler：： RemoveVirtualProcessors](#removevirtualprocessors)|起始移除先前配置給此排程器的虛擬處理器根。|
|[IScheduler：： Statistics](#statistics)|提供工作抵達和完成率的相關資訊，以及排程器的佇列長度變更。|

## <a name="remarks"></a>備註

如果您要執行與 Resource Manager 通訊的自訂排程器，您應該提供 `IScheduler` 介面的執行。 這個介面是排程器與 Resource Manager 之間通訊雙向通道的一端。 另一端則是由 Resource Manager 所執行的 `IResourceManager` 和 `ISchedulerProxy` 介面所表示。

## <a name="inheritance-hierarchy"></a>繼承階層

`IScheduler`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="addvirtualprocessors"></a>IScheduler：： AddVirtualProcessors 方法

提供具有一組虛擬處理器根的排程器，供其使用。 每個 `IVirtualProcessorRoot` 介面都代表執行可代表排程器執行工作之單一執行緒的許可權。

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot` 介面的陣列，代表要加入至排程器的虛擬處理器根。

*計數*<br/>
陣列中的 `IVirtualProcessorRoot` 介面數目。

### <a name="remarks"></a>備註

Resource Manager 會叫用 `AddVirtualProcessor` 方法，將初始的虛擬處理器根集合授與排程器。 它也可以叫用方法，以便在排程器之間重新平衡資源時，將虛擬處理器根新增至排程器。

## <a name="getid"></a>IScheduler：： GetId 方法

傳回排程器的唯一識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

唯一的整數識別碼。

### <a name="remarks"></a>備註

在使用介面做為 Resource Manager 所提供之方法的參數之前，您應該使用[GetSchedulerId](concurrency-namespace-functions.md)函式來取得用來執行 `IScheduler` 介面之物件的唯一識別碼。 叫用 `GetId` 函式時，您應該會傳回相同的識別碼。

從不同來源取得的識別碼可能會導致未定義的行為。

## <a name="getpolicy"></a>IScheduler：： GetPolicy 方法

傳回排程器原則的複本。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>傳回值

排程器原則的複本。

## <a name="notifyresourcesexternallybusy"></a>IScheduler：： NotifyResourcesExternallyBusy 方法

通知此排程器，由 `ppVirtualProcessorRoots` 陣列中的虛擬處理器根集合所代表的硬體執行緒目前正由其他排程器使用中。

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
與其他排程器已忙碌之硬體執行緒相關聯 `IVirtualProcessorRoot` 介面的陣列。

*計數*<br/>
陣列中的 `IVirtualProcessorRoot` 介面數目。

### <a name="remarks"></a>備註

可以同時將特定硬體執行緒指派給多個排程器。 其中一個原因可能是系統上沒有足夠的硬體執行緒可滿足所有排程器的最小並行處理，而不需要共用資源。 另一個可能的原因是，當擁有的排程器未使用這些資源時，就會暫時將其指派給其他排程器，方法是將該硬體執行緒上的所有虛擬處理器根都停用。

硬體執行緒的訂用帳戶層級是以訂閱的執行緒數目表示，並已啟動與該硬體執行緒相關聯的虛擬處理器根。 從特定排程器的觀點來看，硬體執行緒的外部訂用帳戶層級是其他排程器所貢獻之訂用帳戶的一部分。 當硬體執行緒的外部訂用帳戶層級從零移到正面的區域時，系統會將資源在外部忙碌的通知傳送至排程器。

透過此方法的通知只會傳送至具有原則的排程器，其中 `MinConcurrency` 原則索引鍵的值等於 `MaxConcurrency` 原則索引鍵的值。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。

合格通知的排程器會在建立時取得一組初始通知，通知它剛指派的資源是否為外部忙碌或閒置。

## <a name="notifyresourcesexternallyidle"></a>IScheduler：： NotifyResourcesExternallyIdle 方法

通知此排程器，由 `ppVirtualProcessorRoots` 陣列中的虛擬處理器根集合所代表的硬體執行緒，不是由其他排程器所使用。

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
與其他排程器已閒置之硬體執行緒相關聯 `IVirtualProcessorRoot` 介面的陣列。

*計數*<br/>
陣列中的 `IVirtualProcessorRoot` 介面數目。

### <a name="remarks"></a>備註

可以同時將特定硬體執行緒指派給多個排程器。 其中一個原因可能是系統上沒有足夠的硬體執行緒可滿足所有排程器的最小並行處理，而不需要共用資源。 另一個可能的原因是，當擁有的排程器未使用這些資源時，就會暫時將其指派給其他排程器，方法是將該硬體執行緒上的所有虛擬處理器根都停用。

硬體執行緒的訂用帳戶層級是以訂閱的執行緒數目表示，並已啟動與該硬體執行緒相關聯的虛擬處理器根。 從特定排程器的觀點來看，硬體執行緒的外部訂用帳戶層級是其他排程器所貢獻之訂用帳戶的一部分。 當硬體執行緒的外部訂用帳戶層級從先前的正值降到零時，系統會將資源從外部忙碌的通知傳送至排程器。

透過此方法的通知只會傳送至具有原則的排程器，其中 `MinConcurrency` 原則索引鍵的值等於 `MaxConcurrency` 原則索引鍵的值。 如需排程器原則的詳細資訊，請參閱[SchedulerPolicy](schedulerpolicy-class.md)。

合格通知的排程器會在建立時取得一組初始通知，通知它剛指派的資源是否為外部忙碌或閒置。

## <a name="removevirtualprocessors"></a>IScheduler：： RemoveVirtualProcessors 方法

起始移除先前配置給此排程器的虛擬處理器根。

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot` 介面的陣列，代表要移除的虛擬處理器根。

*計數*<br/>
陣列中的 `IVirtualProcessorRoot` 介面數目。

### <a name="remarks"></a>備註

Resource Manager 會叫用 `RemoveVirtualProcessors` 方法，從排程器中取回一組虛擬處理器根。 排程器應該在每個介面上使用虛擬處理器根完成時，叫用[Remove](iexecutionresource-structure.md#remove)方法。 一旦您在其上叫用了 `Remove` 方法，請不要使用 `IVirtualProcessorRoot` 介面。

參數 `ppVirtualProcessorRoots` 指向介面的陣列。 在要移除的虛擬處理器根集合中，永遠都不會使用 `Remove` 方法來立即傳回根。 應該以非同步方式傳回已啟用且正在執行工作，或已停用並等候工作抵達的根。 排程器必須每次嘗試移除虛擬處理器根，才能儘快進行。 延遲移除虛擬處理器根可能會導致排程器內有意外的過度訂閱。

## <a name="statistics"></a>IScheduler：： Statistics 方法

提供工作抵達和完成率的相關資訊，以及排程器的佇列長度變更。

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>參數

*pTaskCompletionRate*<br/>
排程器自上次呼叫這個方法之後已經完成的工作數目。

*pTaskArrivalRate*<br/>
自上次呼叫這個方法之後，已抵達排程器的工作數目。

*pNumberOfTasksEnqueued*<br/>
所有排程器佇列中的工作總數。

### <a name="remarks"></a>備註

這個方法是由 Resource Manager 叫用，以便收集排程器的統計資料。 此處收集的統計資料將用來驅動動態的意見演算法，以判斷何時適當地將更多資源指派給排程器，以及何時要讓資源消失。 排程器所提供的值可以是開放式的，不一定需要正確反映目前的計數。

如果您希望資源管理員使用像是工作抵達這類事件的意見反應，決定如何在您的排程器與資源管理員中註冊的其他排程器之間平衡資源，則應該實作這個方法。 如果您選擇不收集統計資料，您可以將原則索引鍵 `DynamicProgressFeedback` 設定為排程器原則中 `DynamicProgressFeedbackDisabled` 值，而 Resource Manager 不會在您的排程器上叫用此方法。

如果沒有統計資訊，Resource Manager 將會使用硬體執行緒訂用帳戶層級來進行資源配置和遷移決策。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy 類別](schedulerpolicy-class.md)<br/>
[IExecutionContext 結構](iexecutioncontext-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
