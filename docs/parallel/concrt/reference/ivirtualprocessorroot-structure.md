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
ms.openlocfilehash: 25ede76a81a77d489d0f2316bd3ae4cb7f84d704
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268612"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 結構

執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。

## <a name="syntax"></a>語法

```
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IVirtualProcessorRoot::Activate](#activate)|會導致執行內容介面相關聯的執行緒 proxy`pContext`啟動這個虛擬處理器根上執行。|
|[IVirtualProcessorRoot::Deactivate](#deactivate)|造成目前在此停止分派的執行內容的虛擬處理器根上執行的執行緒 proxy。 執行緒 proxy 會繼續執行呼叫`Activate`方法。|
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|會儲存在個別處理器的記憶體階層，就會顯示在系統上的所有處理器的資料。 它可確保完整的記憶體柵欄已經執行的所有處理器上的方法傳回之前。|
|[IVirtualProcessorRoot::GetId](#getid)|傳回的虛擬處理器根的唯一識別碼。|

## <a name="remarks"></a>備註

每個虛擬處理器根有相關聯的執行資源。 `IVirtualProcessorRoot`介面繼承自[IExecutionResource](iexecutionresource-structure.md)介面。 多個虛擬處理器根可以對應到相同的基礎硬體執行緒。

資源管理員授與虛擬處理器根排程器，以回應要求的資源。 排程器可以使用虛擬處理器根，來啟用它的執行內容中執行的工作。

## <a name="inheritance-hierarchy"></a>繼承階層

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="activate"></a>  Ivirtualprocessorroot:: Activate 方法

會導致執行內容介面相關聯的執行緒 proxy`pContext`啟動這個虛擬處理器根上執行。

```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
執行內容，並在此虛擬處理器根上分派介面。

### <a name="remarks"></a>備註

Resource Manager 會提供的執行緒 proxy，如果沒有相關聯的執行內容的介面 `pContext`

`Activate`方法可以用來開始傳回的資源管理員 中，新的虛擬處理器根上執行工作，或繼續執行緒 proxy 已停用訂閱或即將停用的虛擬處理器根上。 請參閱[ivirtualprocessorroot:: Deactivate](#deactivate)如需有關停用。 當您正在繼續已停用的虛擬處理器根，參數`pContext`必須是用來停用的虛擬處理器根參數相同。

第一次，也就是呼叫後續組一經啟用虛擬處理器根`Deactivate`和`Activate`可能會彼此競爭。 這表示它是可接受以接收呼叫，資源管理員`Activate`接收之前`Deactivate`已供的呼叫。

當您啟動虛擬處理器根時，您的訊號至 Resource Manager 中，此虛擬處理器根工作目前忙碌中。 如果您的排程器找不到任何此根上執行的工作，它應該要叫用`Deactivate`通知資源管理員的虛擬處理器根閒置的方法。 Resource Manager 會使用此資料來進行負載平衡系統。

`invalid_argument` 如果擲回引數`pContext`具有值`NULL`。

`invalid_operation` 如果擲回引數`pContext`不代表由這個虛擬處理器根派送最近的執行內容。

啟用虛擬處理器根中的動作會增加 1 基礎硬體執行緒的訂用帳戶層級。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

##  <a name="deactivate"></a>  Ivirtualprocessorroot:: Deactivate 方法

造成目前在此停止分派的執行內容的虛擬處理器根上執行的執行緒 proxy。 執行緒 proxy 會繼續執行呼叫`Activate`方法。

```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
這目前由發送這個根內容。

### <a name="return-value"></a>傳回值

布林值。 值為 **，則為 true**表示從傳回的執行緒 proxy`Deactivate`方法以回應呼叫`Activate`方法。 值為`false`表示執行緒 proxy 傳回回應的通知事件在 Resource Manager 中的方法。 在使用者模式排程 (UMS) 執行緒排程器，這表示，項目會出現在 排程器的完成清單中，排程器，才能處理它們。

### <a name="remarks"></a>備註

若要暫時停止執行虛擬處理器根，在您的排程器中找不到任何工作時使用這個方法。 呼叫`Deactivate`方法必須源自內`Dispatch`方法來執行內容，與上次啟動的虛擬處理器根。 換句話說，叫用的執行緒 proxy`Deactivate`方法必須是目前正在執行的虛擬處理器根的一個。 您不執行的虛擬處理器根上呼叫方法，可能會導致未定義的行為。

已停用的虛擬處理器根可能喚醒藉由呼叫`Activate`方法，並傳遞給相同的引數有`Deactivate`方法。 排程器會負責確保會呼叫`Activate`和`Deactivate`方法配對之後，但它們並不需要以特定順序接收。 Resource Manager 可以處理接收呼叫`Activate`方法之前收到的呼叫`Deactivate`它已用的方法。

如果虛擬處理器根會喚醒並從傳回的值`Deactivate`方法就是值**false**，排程器應該查詢 UMS 完成清單中的，透過`IUMSCompletionList::GetUnblockNotifications`方法，處理該資訊，然後接著再呼叫`Deactivate`方法一次。 這應該在到目前為止，做為重複`Deactivate`方法會傳回值`true`。

`invalid_argument` 如果擲回引數`pContext`有 NULL 值。

`invalid_operation` 如果從未啟用的虛擬處理器根，會擲回引數或`pContext`不代表由這個虛擬處理器根派送最近的執行內容。

中的停用虛擬處理器根動作減一的基礎硬體執行緒的訂用帳戶層級。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

##  <a name="ensurealltasksvisible"></a>  Ivirtualprocessorroot:: Ensurealltasksvisible 方法

會儲存在個別處理器的記憶體階層，就會顯示在系統上的所有處理器的資料。 它可確保完整的記憶體柵欄已經執行的所有處理器上的方法傳回之前。

```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
這目前由發送這個虛擬處理器根內容。

### <a name="remarks"></a>備註

當您想要同步處理停用的虛擬處理器根，加上新的工作排程器，您可能會發現此方法很有用。 基於效能考量，您可以決定要加入排程器中的工作項目，但不會執行的記憶體屏障，這表示工作項目加入一個處理器上執行的執行緒不會立即顯示所有其他處理器。 使用此方法搭配`Deactivate`方法可確保您的排程器不會停用其所有的虛擬處理器根排程器的集合中存在的工作項目時。

呼叫`EnsureAllTasksVisibleThe`方法必須源自內`Dispatch`方法來執行內容，與上次啟動的虛擬處理器根。 換句話說，叫用的執行緒 proxy`EnsureAllTasksVisible`方法必須是目前正在執行的虛擬處理器根的一個。 您不執行的虛擬處理器根上呼叫方法，可能會導致未定義的行為。

`invalid_argument` 如果擲回引數`pContext`具有值`NULL`。

`invalid_operation` 如果從未啟用的虛擬處理器根，會擲回引數或`pContext`不代表由這個虛擬處理器根派送最近的執行內容。

##  <a name="getid"></a>  Ivirtualprocessorroot:: Getid 方法

傳回的虛擬處理器根的唯一識別碼。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

整數識別碼。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
