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
ms.openlocfilehash: 869d51144b686dd684f62b337bb90eff8a9a5589
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193948"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 結構

執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。

## <a name="syntax"></a>語法

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[IVirtualProcessorRoot：： Activate](#activate)|使與執行內容介面相關聯的執行緒 proxy `pContext` 開始在此虛擬處理器根目錄上執行。|
|[IVirtualProcessorRoot：:D eactivate](#deactivate)|導致目前在此虛擬處理器根上執行的執行緒 proxy 停止分派執行內容。 執行緒 proxy 會在呼叫方法時繼續執行 `Activate` 。|
|[IVirtualProcessorRoot：： EnsureAllTasksVisible](#ensurealltasksvisible)|讓系統上的所有處理器都可以看到儲存在個別處理器記憶體階層中的資料。 它可確保在方法傳回之前，已在所有處理器上執行完整的記憶體隔離。|
|[IVirtualProcessorRoot：： GetId](#getid)|傳回虛擬處理器根的唯一識別碼。|

## <a name="remarks"></a>備註

每個虛擬處理器根都有相關聯的執行資源。 `IVirtualProcessorRoot`介面繼承自[IExecutionResource](iexecutionresource-structure.md)介面。 多個虛擬處理器根目錄可能對應至相同的基礎硬體執行緒。

Resource Manager 會將虛擬處理器根授與排程器，以回應資源的要求。 排程器可以使用虛擬處理器根來執行工作，方法是透過執行內容來啟用它。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** 並行

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot：： Activate 方法

使與執行內容介面相關聯的執行緒 proxy `pContext` 開始在此虛擬處理器根目錄上執行。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
將在此虛擬處理器根目錄上分派的執行內容介面。

### <a name="remarks"></a>備註

Resource Manager 會提供執行緒 proxy （如果其中一個未與執行內容介面關聯）`pContext`

`Activate`方法可以用來在 Resource Manager 所傳回的新虛擬處理器根上開始執行工作，或在已停用或即將停用的虛擬處理器根上繼續執行緒 proxy。 如需停用的詳細資訊，請參閱[IVirtualProcessorRoot：:D eactivate](#deactivate) 。 當您繼續已停用的虛擬處理器根時，參數必須與用 `pContext` 來停用虛擬處理器根的參數相同。

第一次啟用虛擬處理器根之後，後續對和的呼叫配對 `Deactivate` `Activate` 可能會彼此競爭。 這表示 Resource Manager 可接受對的呼叫，以接收其 `Activate` `Deactivate` 所代表的呼叫。

當您啟動虛擬處理器根時，會向 Resource Manager 表示此虛擬處理器根目前忙碌中的工作。 如果您的排程器找不到任何要在這個根目錄上執行的工作，就應該叫用 `Deactivate` 方法，通知 Resource Manager 虛擬處理器根閒置。 Resource Manager 使用此資料來對系統進行負載平衡。

`invalid_argument`如果引數具有值，則會擲回 `pContext` `NULL` 。

`invalid_operation`如果引數不 `pContext` 代表此虛擬處理器根最近分派的執行內容，則會擲回。

啟用虛擬處理器根的動作會增加基礎硬體執行緒的訂用帳戶層級。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot：:D eactivate 方法

導致目前在此虛擬處理器根上執行的執行緒 proxy 停止分派執行內容。 執行緒 proxy 會在呼叫方法時繼續執行 `Activate` 。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
目前正由這個根分派的內容。

### <a name="return-value"></a>傳回值

布林值。 的值 **`true`** 表示從方法傳回的執行緒 proxy， `Deactivate` 以回應方法的呼叫 `Activate` 。 的值 **`false`** 表示從方法傳回的執行緒 proxy，以回應 Resource Manager 中的通知事件。 在使用者模式可排程（UMS）執行緒排程器上，這表示專案已出現在排程器的完成清單上，而且需要排程器來處理它們。

### <a name="remarks"></a>備註

當您在排程器中找不到任何工作時，請使用這個方法來暫時停止執行虛擬處理器根。 對方法的呼叫 `Deactivate` 必須源自于 `Dispatch` 上次啟動虛擬處理器根之執行內容的方法內。 換句話說，叫用方法的執行緒 proxy `Deactivate` 必須是目前在虛擬處理器根目錄上執行的。 在您未執行的虛擬處理器根目錄上呼叫方法，可能會導致未定義的行為。

已停用的虛擬處理器根可能會透過呼叫方法來喚醒 `Activate` ，並將相同的引數傳遞給 `Deactivate` 方法。 排程器負責確保 `Activate` 和方法的呼叫 `Deactivate` 是配對的，但不一定要以特定順序接收。 Resource Manager 可以在接收到對方法的呼叫 `Activate` 之前，先處理其呼叫方法 `Deactivate` 。

如果虛擬處理器根 awakens 和方法的傳回值 `Deactivate` 為值，則排程器 **`false`** 應該透過方法來查詢 UMS 完成清單 `IUMSCompletionList::GetUnblockNotifications` 、對該資訊採取行動，然後 `Deactivate` 再次呼叫方法。 這應該重複，直到方法傳回值為止 `Deactivate` **`true`** 。

`invalid_argument`如果引數 `pContext` 的值為 Null，則會擲回。

`invalid_operation`如果從未啟動虛擬處理器根，或引數不 `pContext` 代表此虛擬處理器根目錄最近分派的執行內容，則會擲回。

停用虛擬處理器根的動作會降低基礎硬體執行緒的訂用帳戶層級。 如需訂用帳戶層級的詳細資訊，請參閱[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot：： EnsureAllTasksVisible 方法

讓系統上的所有處理器都可以看到儲存在個別處理器記憶體階層中的資料。 它可確保在方法傳回之前，已在所有處理器上執行完整的記憶體隔離。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
目前正由這個虛擬處理器根分派的內容。

### <a name="remarks"></a>備註

當您想要同步處理虛擬處理器根的停用，並將新工作新增至排程器時，您可能會發現這個方法很有用。 基於效能考慮，您可能會決定將工作專案加入至您的排程器，而不執行記憶體屏障，這表示在一個處理器上執行的執行緒所新增的工作專案，不會立即顯示在所有其他處理器上。 藉由使用此方法搭配 `Deactivate` 方法，您可以確保排程器不會停用其所有虛擬處理器根，而工作專案存在於排程器的集合中。

對方法的呼叫 `EnsureAllTasksVisibleThe` 必須源自于 `Dispatch` 上次啟動虛擬處理器根之執行內容的方法內。 換句話說，叫用方法的執行緒 proxy `EnsureAllTasksVisible` 必須是目前在虛擬處理器根目錄上執行的。 在您未執行的虛擬處理器根目錄上呼叫方法，可能會導致未定義的行為。

`invalid_argument`如果引數具有值，則會擲回 `pContext` `NULL` 。

`invalid_operation`如果從未啟動虛擬處理器根，或引數不 `pContext` 代表此虛擬處理器根目錄最近分派的執行內容，則會擲回。

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot：： GetId 方法

傳回虛擬處理器根的唯一識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

整數識別碼。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
