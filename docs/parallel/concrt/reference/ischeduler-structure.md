---
title: IScheduler 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c926589165cbf93bd517612514bc27c88f28e15
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378861"
---
# <a name="ischeduler-structure"></a>IScheduler 結構

工作排程器抽象概念的介面。 並行執行階段的資源管理員會使用這個介面與工作排程器通訊。

## <a name="syntax"></a>語法

```
struct IScheduler;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Ischeduler:: Addvirtualprocessors](#addvirtualprocessors)|提供一組的虛擬處理器根排程器，供其使用。 每個`IVirtualProcessorRoot`介面代表執行單一執行緒可以執行排程器代表工作的權限。|
|[IScheduler::GetId](#getid)|排程器傳回的唯一識別碼。|
|[IScheduler::GetPolicy](#getpolicy)|傳回排程器原則的複本。 如需有關排程器原則的詳細資訊，請參閱 < [SchedulerPolicy](schedulerpolicy-class.md)。|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`現在正由其他排程器。|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`不正由其他排程器。|
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|起始移除的先前配置給這個排程器的虛擬處理器根。|
|[Ischeduler:: Statistics](#statistics)|提供工作從抵達到完成率，以及變更佇列長度的排程器的相關資訊。|

## <a name="remarks"></a>備註

如果您要實作自訂的排程器進行通訊與 Resource Manager 中，您應該提供實作`IScheduler`介面。 這個介面是通訊的雙向的排程器與 Resource Manager 之間通道的一端。 所代表之另一端`IResourceManager`和`ISchedulerProxy`實作資源管理員的介面。

## <a name="inheritance-hierarchy"></a>繼承階層

`IScheduler`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="addvirtualprocessors"></a>  Ischeduler:: Addvirtualprocessors 方法

提供一組的虛擬處理器根排程器，供其使用。 每個`IVirtualProcessorRoot`介面代表執行單一執行緒可以執行排程器代表工作的權限。

```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
陣列`IVirtualProcessorRoot`介面代表虛擬處理器根新增至排程器。

*count*<br/>
數目`IVirtualProcessorRoot`陣列中的介面。

### <a name="remarks"></a>備註

資源管理員會叫用`AddVirtualProcessor`授與一組初始的虛擬處理器根排程器的方法。 它也能叫用的方法來新增至排程器的虛擬處理器根，當重新平衡排程器之間的資源。

##  <a name="getid"></a>  Ischeduler:: Getid 方法

排程器傳回的唯一識別碼。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

的唯一整數識別碼。

### <a name="remarks"></a>備註

您應該使用[GetSchedulerId](concurrency-namespace-functions.md)函式來取得實作之物件的唯一識別碼`IScheduler`介面，才能使用此介面做為方法的參數提供資源管理員。 您應該會傳回相同的識別項時`GetId`函式會叫用。

從不同來源取得的識別碼可能會導致未定義的行為。

##  <a name="getpolicy"></a>  Ischeduler:: Getpolicy 方法

傳回排程器原則的複本。 如需有關排程器原則的詳細資訊，請參閱 < [SchedulerPolicy](schedulerpolicy-class.md)。

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>傳回值

排程器原則的複本。

##  <a name="notifyresourcesexternallybusy"></a>  Ischeduler:: Notifyresourcesexternallybusy 方法

這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`現在正由其他排程器。

```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
陣列`IVirtualProcessorRoot`的其他排程器已變得忙碌的硬體執行緒相關聯的介面。

*count*<br/>
數目`IVirtualProcessorRoot`陣列中的介面。

### <a name="remarks"></a>備註

可以同時指派給多個排程器的特定的硬體執行緒。 這個的其中一個原因可能是沒有足夠的硬體執行緒系統的所有排程器，滿足最小的並行存取，而不會共用資源上。 另一個可能性是，資源會暫時指派給其他排程器擁有的排程器未使用時，透過在已停用該硬體執行緒在其所有的虛擬處理器根。

硬體執行緒的訂用帳戶層級以訂閱的執行緒數目，並啟動該硬體執行緒相關聯的虛擬處理器根。 從特定的排程器的觀點來看，硬體執行緒的外部的訂用帳戶層級會是其他排程器所參與的訂用帳戶的一部分。 資源是外部忙碌的通知會傳送至排程器中，當從零到正數的國家/地區的硬體執行緒的外部的訂用帳戶層級移動時。

透過這種方式的通知只傳送給原則之排程器位置的值`MinConcurrency`原則機碼的值等於`MaxConcurrency`原則金鑰。 如需有關排程器原則的詳細資訊，請參閱 < [SchedulerPolicy](schedulerpolicy-class.md)。

符合資格的訂閱通知的排程器取得一組初始的通知建立時，通知它只被指派的資源是否為外部忙碌或閒置。

##  <a name="notifyresourcesexternallyidle"></a>  Ischeduler:: Notifyresourcesexternallyidle 方法

這個陣列中的虛擬處理器根物件的集合所代表的硬體執行緒的排程器會通知`ppVirtualProcessorRoots`不正由其他排程器。

```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
陣列`IVirtualProcessorRoot`的其他排程器已成為閒置的硬體執行緒相關聯的介面。

*count*<br/>
數目`IVirtualProcessorRoot`陣列中的介面。

### <a name="remarks"></a>備註

可以同時指派給多個排程器的特定的硬體執行緒。 這個的其中一個原因可能是沒有足夠的硬體執行緒系統的所有排程器，滿足最小的並行存取，而不會共用資源上。 另一個可能性是，資源會暫時指派給其他排程器擁有的排程器未使用時，透過在已停用該硬體執行緒在其所有的虛擬處理器根。

硬體執行緒的訂用帳戶層級以訂閱的執行緒數目，並啟動該硬體執行緒相關聯的虛擬處理器根。 從特定的排程器的觀點來看，硬體執行緒的外部的訂用帳戶層級會是其他排程器所參與的訂用帳戶的一部分。 資源是外部忙碌的通知會傳送至排程器中，當硬體執行緒的外部的訂用帳戶層級降為從上一個正值的零。

透過這種方式的通知只傳送給原則之排程器位置的值`MinConcurrency`原則機碼的值等於`MaxConcurrency`原則金鑰。 如需有關排程器原則的詳細資訊，請參閱 < [SchedulerPolicy](schedulerpolicy-class.md)。

符合資格的訂閱通知的排程器取得一組初始的通知建立時，通知它只被指派的資源是否為外部忙碌或閒置。

##  <a name="removevirtualprocessors"></a>  Ischeduler:: Removevirtualprocessors 方法

起始移除的先前配置給這個排程器的虛擬處理器根。

```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>參數

*ppVirtualProcessorRoots*<br/>
陣列`IVirtualProcessorRoot`介面代表要移除的虛擬處理器根。

*count*<br/>
數目`IVirtualProcessorRoot`陣列中的介面。

### <a name="remarks"></a>備註

資源管理員會叫用`RemoveVirtualProcessors`才會傳回一組的虛擬處理器根排程器的方法。 排程器所要叫用[移除](iexecutionresource-structure.md#remove)與虛擬處理器根完成時，每個介面上的方法。 請勿使用`IVirtualProcessorRoot`一旦您有叫用的介面`Remove`在其上的方法。

參數`ppVirtualProcessorRoots`指向之介面的陣列。 要移除的虛擬處理器根組，根憑證永遠不會啟用可立即使用傳回`Remove`方法。 在根目錄中，已啟動和執行工作，或已遭停用且正在等候工作抵達，應該以非同步方式傳回。 排程器必須將每個嘗試盡快移除虛擬處理器根。 延遲移除的虛擬處理器根，可能會導致非預期的過度訂閱，排程器內。

##  <a name="statistics"></a>  Ischeduler:: Statistics 方法

提供工作從抵達到完成率，以及變更佇列長度的排程器的相關資訊。

```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>參數

*pTaskCompletionRate*<br/>
完成時排程器自上次呼叫這個方法的工作數目。

*pTaskArrivalRate*<br/>
自上次呼叫這個方法會進入排程器中的工作數目。

*pNumberOfTasksEnqueued*<br/>
所有的排程器佇列中的工作總數。

### <a name="remarks"></a>備註

若要收集統計資料的排程器是叫用這個方法由資源管理員。 這裡所收集的統計資料將用來動態回應的演算法，來判斷將指派給排程器的 更多資源的適當，以及何時會佔用資源的磁碟機中。 排程器所提供的值可以是開放式，並不一定需要精確反映目前的計數。

如果您希望資源管理員使用像是工作抵達這類事件的意見反應，決定如何在您的排程器與資源管理員中註冊的其他排程器之間平衡資源，則應該實作這個方法。 如果您選擇不要收集統計資料，您可以設定原則金鑰`DynamicProgressFeedback`的值`DynamicProgressFeedbackDisabled`在您的排程器原則和資源管理員不會叫用您的排程器上的這個方法。

如果沒有使用的統計資訊，Resource Manager 會使用硬體執行緒的訂用帳戶層級來決定資源配置和移轉。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy 類別](schedulerpolicy-class.md)<br/>
[IExecutionContext 結構](iexecutioncontext-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
