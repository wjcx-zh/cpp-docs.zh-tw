---
title: IVirtualProcessorRoot 結構
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139887"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 結構

執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。

## <a name="syntax"></a>語法

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IVirtualProcessorRoot：： Activate](#activate)|使與執行內容介面相關聯的執行緒 proxy `pContext` 在此虛擬處理器根目錄上開始執行。|
|[IVirtualProcessorRoot：:D eactivate](#deactivate)|導致目前在此虛擬處理器根上執行的執行緒 proxy 停止分派執行內容。 執行緒 proxy 會在呼叫 `Activate` 方法時繼續執行。|
|[IVirtualProcessorRoot：： EnsureAllTasksVisible](#ensurealltasksvisible)|讓系統上的所有處理器都可以看到儲存在個別處理器記憶體階層中的資料。 它可確保在方法傳回之前，已在所有處理器上執行完整的記憶體隔離。|
|[IVirtualProcessorRoot：： GetId](#getid)|傳回虛擬處理器根的唯一識別碼。|

## <a name="remarks"></a>備註

每個虛擬處理器根都有相關聯的執行資源。 `IVirtualProcessorRoot` 介面會繼承自[IExecutionResource](iexecutionresource-structure.md)介面。 多個虛擬處理器根目錄可能對應至相同的基礎硬體執行緒。

Resource Manager 會將虛擬處理器根授與排程器，以回應資源的要求。 排程器可以使用虛擬處理器根來執行工作，方法是透過執行內容來啟用它。

## <a name="inheritance-hierarchy"></a>繼承階層

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="activate"></a>IVirtualProcessorRoot：： Activate 方法

使與執行內容介面相關聯的執行緒 proxy `pContext` 在此虛擬處理器根目錄上開始執行。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
將在此虛擬處理器根目錄上分派的執行內容介面。

### <a name="remarks"></a>備註

Resource Manager 會提供執行緒 proxy （如果其中一個未與執行內容介面相關聯） `pContext`

`Activate` 方法可以用來開始在 Resource Manager 所傳回的新虛擬處理器根上執行工作，或在已停用或即將停用的虛擬處理器根上繼續執行緒 proxy。 如需停用的詳細資訊，請參閱[IVirtualProcessorRoot：:D eactivate](#deactivate) 。 當您繼續已停用的虛擬處理器根時，參數 `pContext` 必須與用來停用虛擬處理器根的參數相同。

第一次啟動虛擬處理器根之後，對 `Deactivate` 和 `Activate` 進行的後續呼叫，可能會彼此競爭。 這表示 Resource Manager 可以接受 `Activate` 的呼叫，然後才收到其所適用的 `Deactivate` 呼叫。

當您啟動虛擬處理器根時，會向 Resource Manager 表示此虛擬處理器根目前忙碌中的工作。 如果您的排程器找不到任何要在此根節點上執行的工作，則應該叫用 `Deactivate` 方法，以通知 Resource Manager 虛擬處理器根處於閒置狀態。 Resource Manager 使用此資料來對系統進行負載平衡。

如果引數 `pContext` 具有 `NULL`值，則會擲回 `invalid_argument`。

如果引數 `pContext` 不代表此虛擬處理器根目錄最近分派的執行內容，則會擲回 `invalid_operation`。

啟用虛擬處理器根的動作會增加基礎硬體執行緒的訂用帳戶層級。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="deactivate"></a>IVirtualProcessorRoot：:D eactivate 方法

導致目前在此虛擬處理器根上執行的執行緒 proxy 停止分派執行內容。 執行緒 proxy 會在呼叫 `Activate` 方法時繼續執行。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
目前正由這個根分派的內容。

### <a name="return-value"></a>傳回值

布林值。 值為**true**時，表示從 `Deactivate` 方法傳回的執行緒 proxy，以回應 `Activate` 方法的呼叫。 值為 `false` 表示從方法傳回的執行緒 proxy，以回應 Resource Manager 中的通知事件。 在使用者模式可排程（UMS）執行緒排程器上，這表示專案已出現在排程器的完成清單上，而且需要排程器來處理它們。

### <a name="remarks"></a>備註

當您在排程器中找不到任何工作時，請使用這個方法來暫時停止執行虛擬處理器根。 `Deactivate` 方法的呼叫必須源自于上次啟動虛擬處理器根之執行內容的 `Dispatch` 方法中。 換句話說，叫用 `Deactivate` 方法的執行緒 proxy 必須是目前在虛擬處理器根上執行的。 在您未執行的虛擬處理器根目錄上呼叫方法，可能會導致未定義的行為。

已停用的虛擬處理器根可能會喚醒呼叫 `Activate` 方法，並將相同的引數傳入 `Deactivate` 方法。 排程器負責確保對 `Activate` 和 `Deactivate` 方法的呼叫都是配對的，但不一定要以特定順序接收。 Resource Manager 可以在收到 `Activate` 方法的呼叫之前，先處理它的呼叫，然後才接收到它所代表的 `Deactivate` 方法。

如果虛擬處理器根 awakens 和來自 `Deactivate` 方法的傳回值為**false**值，則排程器應該透過 `IUMSCompletionList::GetUnblockNotifications` 方法來查詢 UMS 完成清單、對該資訊採取行動，然後再次呼叫 `Deactivate` 方法。 這應該重複，直到 `Deactivate` 方法傳回 `true`的值為止。

如果引數 `pContext` 的值為 Null，則會擲回 `invalid_argument`。

如果從未啟動虛擬處理器根，或引數 `pContext` 不代表此虛擬處理器根目錄最近分派的執行內容，就會擲回 `invalid_operation`。

停用虛擬處理器根的動作會降低基礎硬體執行緒的訂用帳戶層級。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot：： EnsureAllTasksVisible 方法

讓系統上的所有處理器都可以看到儲存在個別處理器記憶體階層中的資料。 它可確保在方法傳回之前，已在所有處理器上執行完整的記憶體隔離。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
目前正由這個虛擬處理器根分派的內容。

### <a name="remarks"></a>備註

當您想要同步處理虛擬處理器根的停用，並將新工作新增至排程器時，您可能會發現這個方法很有用。 基於效能考慮，您可能會決定將工作專案加入至您的排程器，而不執行記憶體屏障，這表示在一個處理器上執行的執行緒所新增的工作專案，不會立即顯示在所有其他處理器上。 藉由搭配使用此方法與 `Deactivate` 方法，您可以確保排程器不會停用其所有虛擬處理器根，而工作專案存在於排程器的集合中。

`EnsureAllTasksVisibleThe` 方法的呼叫必須源自于上次啟動虛擬處理器根之執行內容的 `Dispatch` 方法中。 換句話說，叫用 `EnsureAllTasksVisible` 方法的執行緒 proxy 必須是目前在虛擬處理器根上執行的。 在您未執行的虛擬處理器根目錄上呼叫方法，可能會導致未定義的行為。

如果引數 `pContext` 具有 `NULL`值，則會擲回 `invalid_argument`。

如果從未啟動虛擬處理器根，或引數 `pContext` 不代表此虛擬處理器根目錄最近分派的執行內容，就會擲回 `invalid_operation`。

## <a name="getid"></a>IVirtualProcessorRoot：： GetId 方法

傳回虛擬處理器根的唯一識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

整數識別碼。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
