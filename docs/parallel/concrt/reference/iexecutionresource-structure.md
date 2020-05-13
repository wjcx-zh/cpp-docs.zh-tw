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
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377304"
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
|[I 執行資源:目前訂閱等級](#currentsubscriptionlevel)|返回當前與此執行資源表示的基礎硬體線程關聯的已啟動的虛擬處理器根和已訂閱的外部線程的數量。|
|[I 執行資源:抓取資源識別碼](#getexecutionresourceid)|返回此執行資源表示的硬體線程的唯一標識碼。|
|[I 執行資源::取得NodeId](#getnodeid)|返回此執行資源所屬的處理器節點的唯一標識碼。|
|[I 執行資源:刪除](#remove)|將此執行資源返回到資源管理員。|

## <a name="remarks"></a>備註

執行資源可以是獨立的或與虛擬處理器根關聯的。 當應用程式中的線程創建線程訂閱時,將創建獨立的執行資源。 方法[I計劃代理:訂閱線程](ischedulerproxy-structure.md#subscribecurrentthread)和[I 計劃代理:請求初始虛擬處理器](ischedulerproxy-structure.md#requestinitialvirtualprocessors)創建線程訂閱,`IExecutionResource`並返回表示訂閱的介面。 創建線程訂閱是通知資源管理器給定線程將參與排隊到計劃程式的工作以及分配給計劃程式的虛擬處理器根資源管理器的一種方式。 資源管理器使用這些資訊來避免在可以的地方過度訂閱硬體線程。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IExecutionResource`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>I 執行資源::當前訂閱等級方法

返回當前與此執行資源表示的基礎硬體線程關聯的已啟動的虛擬處理器根和已訂閱的外部線程的數量。

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>傳回值

當前訂閱級別。

### <a name="remarks"></a>備註

訂閱等級告訴您與硬體線程關聯的正在運行的線程數。 這僅包括資源管理器以訂閱線程的形式知道的線程,以及正在積極執行線程代理的虛擬處理器根。

調用方法[I-計劃代理::訂閱CurrentThread](ischedulerproxy-structure.md#subscribecurrentthread),或方法[I-計劃代理:請求初始虛擬處理器](ischedulerproxy-structure.md#requestinitialvirtualprocessors),參數`doSubscribeCurrentThread`設置為值**true**將硬體線程的訂閱級別增加一個。 它們還會返回表示`IExecutionResource`訂閱的介面。 對[I執行資源::將](#remove)硬體線程的訂閱級別除以一次。

使用[IVirtualProcessorRoot::啟動](ivirtualprocessorroot-structure.md#activate)虛擬處理器根的行為將硬體線程的訂閱級別增加一個。 當在啟動的虛擬處理器根目錄上調用時,方法[IVirtualProcessorRoot::Deeactivate,](ivirtualprocessorroot-structure.md#deactivate)[或 I執行資源:在](#remove)啟動的虛擬處理器根上調用時,將訂閱級別除以一。

資源管理器使用訂閱等級資訊作為確定何時在計劃程序之間移動資源的方法之一。

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>I 執行資源:抓取資源代碼

返回此執行資源表示的硬體線程的唯一標識碼。

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>傳回值

此執行資源的基礎硬體線程的唯一標識碼。

### <a name="remarks"></a>備註

每個硬體線程由併發運行時分配一個唯一標識符。 如果多個執行資源是關聯的硬體線程,則它們都將具有相同的執行資源標識符。

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>I 執行資源:getNodeId 方法

返回此執行資源所屬的處理器節點的唯一標識碼。

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>傳回值

處理器節點的唯一標識符。

### <a name="remarks"></a>備註

併發運行時以處理器節點組表示系統上的硬體線程。 節點通常派生自系統的硬體拓撲。 例如,特定套接字或特定 NUMA 節點上的所有處理器可能屬於同一處理器節點。 資源管理器為這些節點分配唯一標識符,從`0`最多和`nodeCount - 1`包括 開始`nodeCount`,其中 表示系統上的處理器節點總數。

節點計數可以從函數[GetProcessorNodeCount](concurrency-namespace-functions.md)獲得。

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>I 執行資源::刪除方法

將此執行資源返回到資源管理員。

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>參數

*p 時間*<br/>
向計畫程式發出刪除此執行資源的請求的介面。

### <a name="remarks"></a>備註

使用此方法將獨立執行資源以及與虛擬處理器根關聯的執行資源返回到資源管理器。

如果這是從其中一種方法[I-計劃代理::訂閱電流線程](ischedulerproxy-structure.md#subscribecurrentthread)或[I-計劃代理:請求初始虛擬處理器](ischedulerproxy-structure.md#requestinitialvirtualprocessors)接收的獨立執行資源,則`Remove`調用該方法 將結束創建資源表示的線程訂閱。 您需要在關閉計畫程式代理之前結束所有線程訂閱,並且必須從建立訂閱的線程呼叫`Remove`。

虛擬處理器根同樣可以透過叫用 `Remove` 方法傳回至資源管理員，因為介面 `IVirtualProcessorRoot` 繼承自 `IExecutionResource` 介面。 您可能需要返回虛擬處理器根,以回應對[I-計劃器:::刪除虛擬處理器](ischeduler-structure.md#removevirtualprocessors)方法的呼叫,或者當您使用從[I-計劃代理代理:create 超額訂閱方法](ischedulerproxy-structure.md#createoversubscriber)獲取的超額訂閱虛擬處理器根時。 對於虛擬處理器根,沒有限制哪個線程可以呼叫該方法`Remove`。

`invalid_argument`如果參數`pScheduler`設定`NULL`為 ,則引發 。

`invalid_operation`如果參數`pScheduler`不同於為此執行資源創建的計畫程式,或者使用獨立執行資源(如果當前線程與創建線程訂閱的線程不同),則引發該參數。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
