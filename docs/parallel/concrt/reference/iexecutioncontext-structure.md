---
title: IExecutionContext 結構
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 45d65a5e16121d39233c3ceb801933aa1f5a5f8e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138919"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 結構

執行內容的介面，可於指定的虛擬處理器上執行，也可以合作方式切換內容。

## <a name="syntax"></a>語法

```cpp
struct IExecutionContext;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IExecutionCoNtext：:D ispatch](#dispatch)|當執行緒 proxy 開始執行特定的執行內容時，所呼叫的方法。 這應該是您排程器的主要背景工作角色。|
|[IExecutionCoNtext：： GetId](#getid)|傳回執行內容的唯一識別碼。|
|[IExecutionCoNtext：： GetProxy](#getproxy)|傳回執行此內容的執行緒 proxy 介面。|
|[IExecutionCoNtext：： GetScheduler](#getscheduler)|傳回此執行內容所屬之排程器的介面。|
|[IExecutionCoNtext：： SetProxy](#setproxy)|將執行緒 proxy 與這個執行內容產生關聯。 相關聯的執行緒 proxy 會在開始執行內容的 `Dispatch` 方法之前，先叫用此方法。|

## <a name="remarks"></a>備註

如果您要執行與並行執行階段的 Resource Manager 介面互動的自訂排程器，您將需要執行 `IExecutionContext` 介面。 Resource Manager 所建立的執行緒會藉由執行 `IExecutionContext::Dispatch` 方法，代表您的排程器執行工作。

## <a name="inheritance-hierarchy"></a>繼承階層

`IExecutionContext`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="dispatch"></a>IExecutionCoNtext：:D ispatch 方法

當執行緒 proxy 開始執行特定的執行內容時，所呼叫的方法。 這應該是您排程器的主要背景工作角色。

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>參數

*pDispatchState*<br/>
分派此執行內容之狀態的指標。 如需分派狀態的詳細資訊，請參閱[DispatchState](dispatchstate-structure.md)。

## <a name="getid"></a>IExecutionCoNtext：： GetId 方法

傳回執行內容的唯一識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

唯一的整數識別碼。

### <a name="remarks"></a>備註

在使用介面做為 Resource Manager 所提供之方法的參數之前，您應該使用方法 `GetExecutionContextId` 來取得執行 `IExecutionContext` 介面之物件的唯一識別碼。 叫用 `GetId` 函式時，您應該會傳回相同的識別碼。

從不同來源取得的識別碼可能會導致未定義的行為。

## <a name="getproxy"></a>IExecutionCoNtext：： GetProxy 方法

傳回執行此內容的執行緒 proxy 介面。

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>傳回值

`IThreadProxy` 介面。 如果未使用 `SetProxy`呼叫來初始化執行內容的執行緒 proxy，函數必須傳回 `NULL`。

### <a name="remarks"></a>備註

Resource Manager 會在執行內容上叫用 `SetProxy` 方法，並以 `IThreadProxy` 介面做為參數，然後再于內容上輸入 `Dispatch` 方法。 您應該儲存此引數，並將它傳回給 `GetProxy()`的呼叫。

## <a name="getscheduler"></a>IExecutionCoNtext：： GetScheduler 方法

傳回此執行內容所屬之排程器的介面。

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>傳回值

`IScheduler` 介面。

### <a name="remarks"></a>備註

您必須使用有效的 `IScheduler` 介面來初始化執行內容，才能將它當做 Resource Manager 所提供之方法的參數。

## <a name="setproxy"></a>IExecutionCoNtext：： SetProxy 方法

將執行緒 proxy 與這個執行內容產生關聯。 相關聯的執行緒 proxy 會在開始執行內容的 `Dispatch` 方法之前，先叫用此方法。

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>參數

*pThreadProxy*<br/>
執行緒 proxy 的介面，即將在此執行內容中輸入 `Dispatch` 方法。

### <a name="remarks"></a>備註

您應該將參數儲存 `pThreadProxy`，並在呼叫 `GetProxy` 方法時將它傳回。 Resource Manager 保證當執行緒 proxy 執行 `Dispatch` 方法時，與執行內容相關聯的執行緒 proxy 將不會變更。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)
