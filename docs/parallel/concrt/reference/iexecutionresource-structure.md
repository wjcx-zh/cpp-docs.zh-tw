---
title: IExecutionResource 結構
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141282"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource 結構

硬體執行緒的抽象概念。

## <a name="syntax"></a>語法

```cpp
struct IExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IExecutionResource：： CurrentSubscriptionLevel](#currentsubscriptionlevel)|傳回目前與此執行資源所代表之基礎硬體執行緒相關聯的已啟動虛擬處理器根目錄和訂閱的外部執行緒數目。|
|[IExecutionResource：： GetExecutionResourceId](#getexecutionresourceid)|傳回此執行資源所代表之硬體執行緒的唯一識別碼。|
|[IExecutionResource：： GetNodeId](#getnodeid)|傳回此執行資源所屬之處理器節點的唯一識別碼。|
|[IExecutionResource：： Remove](#remove)|將此執行資源傳回到 Resource Manager。|

## <a name="remarks"></a>備註

執行資源可以是獨立或與虛擬處理器根相關聯。 當應用程式中的執行緒建立執行緒訂用帳戶時，就會建立獨立的執行資源。 方法[ISchedulerProxy：： SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread)和[ISchedulerProxy：： RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)會建立執行緒訂閱，並傳回代表訂用帳戶的 `IExecutionResource` 介面。 建立執行緒訂閱是通知 Resource Manager 給定的執行緒將參與佇列至排程器的工作，以及虛擬處理器根 Resource Manager 指派給排程器的方法。 Resource Manager 會使用此資訊來避免傳承硬體執行緒。

## <a name="inheritance-hierarchy"></a>繼承階層

`IExecutionResource`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="currentsubscriptionlevel"></a>IExecutionResource：： CurrentSubscriptionLevel 方法

傳回目前與此執行資源所代表之基礎硬體執行緒相關聯的已啟動虛擬處理器根目錄和訂閱的外部執行緒數目。

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>傳回值

目前的訂用帳戶層級。

### <a name="remarks"></a>備註

訂用帳戶層級會告訴您有多少執行中的執行緒與硬體執行緒相關聯。 這只包括 Resource Manager 感知的執行緒，以及主動執行執行緒 proxy 的虛擬處理器根的形式。

使用參數呼叫方法[ISchedulerProxy：： SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)或方法[ISchedulerProxy：： RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)時，`doSubscribeCurrentThread` 設定為**true，則**會將硬體執行緒的訂閱等級遞增一。 它們也會傳回表示訂用帳戶的 `IExecutionResource` 介面。 對[IExecutionResource：： Remove](#remove)的對應呼叫會將硬體執行緒的訂用帳戶層級減一。

使用方法[IVirtualProcessorRoot：： Activate 啟動](ivirtualprocessorroot-structure.md#activate)虛擬處理器根的動作，會遞增硬體執行緒的訂用帳戶層級一。 [IVirtualProcessorRoot：:D eactivate](ivirtualprocessorroot-structure.md#deactivate)或[IExecutionResource：： Remove](#remove)方法會在啟動的虛擬處理器根上叫用訂用帳戶層級時，遞減一個。

Resource Manager 會使用訂用帳戶層級資訊，做為判斷何時要在排程器之間移動資源的其中一種方式。

## <a name="getexecutionresourceid"></a>IExecutionResource：： GetExecutionResourceId 方法

傳回此執行資源所代表之硬體執行緒的唯一識別碼。

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>傳回值

此執行資源基礎之硬體執行緒的唯一識別碼。

### <a name="remarks"></a>備註

並行執行階段會將唯一識別碼指派給每個硬體執行緒。 如果有多個執行資源與硬體執行緒相關聯，它們就會有相同的執行資源識別碼。

## <a name="getnodeid"></a>IExecutionResource：： GetNodeId 方法

傳回此執行資源所屬之處理器節點的唯一識別碼。

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>傳回值

處理器節點的唯一識別碼。

### <a name="remarks"></a>備註

並行執行階段代表處理器節點群組中系統上的硬體執行緒。 節點通常是從系統的硬體拓朴衍生而來。 例如，特定通訊端或特定 NUMA 節點上的所有處理器都可能屬於相同的處理器節點。 Resource Manager 會將唯一識別碼指派給這些節點，從 `0` 到，包括 `nodeCount - 1`，其中 `nodeCount` 代表系統上的處理器節點總數。

您可以從函數[GetProcessorNodeCount](concurrency-namespace-functions.md)取得節點計數。

## <a name="remove"></a>IExecutionResource：： Remove 方法

將此執行資源傳回到 Resource Manager。

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>參數

*pScheduler*<br/>
建立排程器的介面，此排程器會提出移除此執行資源的要求。

### <a name="remarks"></a>備註

使用此方法可將獨立執行資源以及與虛擬處理器根關聯的執行資源傳回至 Resource Manager。

如果這是您從任一方法[ISchedulerProxy：： SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)或[ISchedulerProxy：： RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)收到的獨立執行資源，呼叫方法 `Remove` 將會結束建立資源所代表的執行緒訂閱。 在關閉排程器 proxy 之前，您必須結束所有的執行緒訂閱，而且必須從建立訂閱的執行緒呼叫 `Remove`。

虛擬處理器根同樣可以透過叫用 `Remove` 方法傳回至資源管理員，因為介面 `IVirtualProcessorRoot` 繼承自 `IExecutionResource` 介面。 針對[IScheduler：： RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors)方法的呼叫，或當您使用從[ISchedulerProxy：： CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber)方法取得的超額訂閱虛擬處理器根目錄時，您可能需要傳回虛擬處理器根目錄。 針對虛擬處理器根，不會限制哪些執行緒可以叫用 `Remove` 方法。

如果參數 `pScheduler` 設定為 `NULL`，則會擲回 `invalid_argument`。

如果參數 `pScheduler` 與建立此執行資源的排程器不同，或如果目前的執行緒與建立執行緒訂閱的執行緒不同，則會擲回 `invalid_operation`。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
