---
title: IThreadProxy 結構
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854132"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 結構

執行緒的抽象概念。 視您所建立之排程器的 `SchedulerType` 原則機碼而定，資源管理員會授與您支援一般 Win32 執行緒或可使用者模式排程 (UMS) 執行緒的執行緒 Proxy。 安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。

## <a name="syntax"></a>語法

```cpp
struct IThreadProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IThreadProxy：： GetId](#getid)|傳回執行緒 proxy 的唯一識別碼。|
|[IThreadProxy：： SwitchOut](#switchout)|解除基礎虛擬處理器根內容的關聯。|
|[IThreadProxy：： SwitchTo](#switchto)|執行合作內容切換，從目前執行的內容切換到另一個。|
|[IThreadProxy：： YieldToSystem](#yieldtosystem)|造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 作業系統會選取要執行的下一個執行緒。|

## <a name="remarks"></a>備註

執行緒 proxy 結合了介面所表示的執行內容 `IExecutionContext` 做為分派工作的手段。

## <a name="inheritance-hierarchy"></a>繼承階層

`IThreadProxy`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="getid"></a>IThreadProxy：： GetId 方法

傳回執行緒 proxy 的唯一識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

唯一的整數識別碼。

## <a name="switchout"></a>IThreadProxy：： SwitchOut 方法

解除基礎虛擬處理器根內容的關聯。

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>參數

*switchState*<br/>
指出執行參數之執行緒 proxy 的狀態。 參數的類型為 `SwitchingProxyState`。

### <a name="remarks"></a>備註

如果因故需要將內容與其執行所在的虛擬處理器根解除關聯，請使用 `SwitchOut`。 根據您傳遞給 `switchState` 參數的值，以及它是否在虛擬處理器根上執行而定，呼叫會立即傳回或是封鎖與內容相關聯的執行緒 Proxy。 在將參數設定為 `SwitchOut` 的情況下呼叫 `Idle` 是錯誤的做法。 這麼做會導致[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

無論是因為資源管理員的指示，或是您要求暫時過度訂閱虛擬處理器根，但已經不再需要這樣做，只要您想要減少排程器擁有的虛擬處理器根數目，`SwitchOut` 都會很有用。 在此情況下，您應該先在虛擬處理器根目錄上叫用[IVirtualProcessorRoot：： Remove](iexecutionresource-structure.md#remove)方法，再使用參數 `switchState` 設定為 `Blocking`來呼叫 `SwitchOut`。 這樣將會封鎖執行緒 Proxy，而且它會在排程器中有不同的虛擬處理器根可用於執行時繼續執行。 封鎖執行緒 proxy 可以藉由呼叫函式 `SwitchTo` 來繼續，以切換至這個執行緒 proxy 的執行內容。 您也可以使用相關聯的內容來啟動虛擬處理器根，以繼續執行緒 proxy。 如需如何執行此動作的詳細資訊，請參閱[IVirtualProcessorRoot：： Activate](ivirtualprocessorroot-structure.md#activate)。

當您想要重新初始化虛擬處理器，讓它能夠在未來發生封鎖執行緒 Proxy，或是暫時將它卸離執行所在的虛擬處理器根以及對其分派工作的排程器時可以啟動，您也可以使用 `SwitchOut`。 如果您想要封鎖執行緒 Proxy，請使用 `SwitchOut`，並將 `switchState` 參數設定為 `Blocking`。 之後可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 讓它繼續執行，如上面所述。 當您想要暫時將這個執行緒 Proxy 卸離執行所在的虛擬處理器根，以及與虛擬處理器相關聯的排程器，請使用 `SwitchOut` 並將參數設定為 `Nesting`。 若呼叫 `SwitchOut` 並將 `switchState` 參數設定為 `Nesting` 時，它正在虛擬處理器根上執行，則會造成根重新初始化，而且目前執行緒 Proxy 會繼續執行，不需要根。 執行緒 proxy 會被視為已離開排程器，直到它使用 `Blocking` 在稍後的時間點呼叫[IThreadProxy：： SwitchOut](#switchout)方法為止。 第二次呼叫 `SwitchOut` 並將參數設定為 `Blocking` 時，該呼叫會將內容返回已封鎖狀態，以便在卸離的排程器中透過 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 繼續執行。 由於它並未在虛擬處理器根上執行，因此不會發生重新初始化。

已重新初始化的虛擬處理器根與資源管理員授與排程器的全新虛擬處理器根並無不同。 您可以在執行內容中使用 `IVirtualProcessorRoot::Activate` 啟用它，這樣就可以用它來執行。

必須在代表目前執行中線程的 `IThreadProxy` 介面上呼叫 `SwitchOut`，否則不會定義結果。

在隨附於 Visual Studio 2010 的程式庫和標頭中，這個方法不會使用參數，也不會重新初始化虛擬處理器根。 若要保留舊有行為，可以提供預設參數值 `Blocking`。

## <a name="switchto"></a>IThreadProxy：： SwitchTo 方法

執行合作內容切換，從目前執行的內容切換到另一個。

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要以合作方式切換的執行內容。

*switchState*<br/>
指出執行參數之執行緒 proxy 的狀態。 參數的類型為 `SwitchingProxyState`。

### <a name="remarks"></a>備註

使用這個方法，從第一個執行內容的[IExecutionCoNtext：:D ispatch](iexecutioncontext-structure.md#dispatch)方法切換到另一個執行內容。 方法會將執行內容與執行緒 proxy `pContext` 相關聯（如果它尚未與它關聯）。 目前線程 proxy 的擁有權取決於您為 `switchState` 引數指定的值。

當您想要將目前執行的執行緒 proxy 傳回至 Resource Manager 時，請使用 `Idle` 值。 使用參數 `switchState` 設定為 `Idle` 呼叫 `SwitchTo`，會使執行內容 `pContext` 開始在基礎執行資源上執行。 此執行緒 proxy 的擁有權會傳送至 Resource Manager，而且您應該會在 `SwitchTo` 傳回之後，立即從執行內容的 `Dispatch` 方法傳回，以便完成傳輸。 執行緒 proxy 所分派的執行內容與執行緒 proxy 解除關聯，而且排程器可以自由地重複使用它，或在它看到的情況下損毀。

當您想要讓此執行緒 proxy 進入封鎖狀態時，請使用值 `Blocking`。 使用參數呼叫 `SwitchTo` `switchState` 設定為 `Blocking` 會使執行內容 `pContext` 開始執行，並封鎖目前的執行緒 proxy，直到它繼續進行為止。 當執行緒 proxy 處於 `Blocking` 狀態時，排程器會保留執行緒 proxy 的擁有權。 封鎖執行緒 proxy 可以藉由呼叫函式 `SwitchTo` 來繼續，以切換至這個執行緒 proxy 的執行內容。 您也可以使用相關聯的內容來啟動虛擬處理器根，以繼續執行緒 proxy。 如需如何執行此動作的詳細資訊，請參閱[IVirtualProcessorRoot：： Activate](ivirtualprocessorroot-structure.md#activate)。

當您想要暫時將此執行緒 proxy 從其執行所在的虛擬處理器根目錄中斷連結時，請使用 `Nesting` 值，並將其分派工作的排程器設為正在執行的排程器。 使用參數呼叫 `SwitchTo` `switchState` 設定為 `Nesting` 會使執行內容 `pContext` 開始執行，而目前的執行緒 proxy 也會繼續執行，而不需要虛擬處理器根。 執行緒 proxy 會被視為已離開排程器，直到它在稍後的時間點呼叫[IThreadProxy：： SwitchOut](#switchout)方法為止。 `IThreadProxy::SwitchOut` 方法可能會封鎖執行緒 proxy，直到虛擬處理器根目錄可供重新排定為止。

必須在代表目前執行中線程的 `IThreadProxy` 介面上呼叫 `SwitchTo`，否則不會定義結果。 如果參數 `pContext` 設定為 `NULL`，則函式會擲回 `invalid_argument`。

## <a name="yieldtosystem"></a>IThreadProxy：： YieldToSystem 方法

造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 作業系統會選取要執行的下一個執行緒。

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>備註

由一般 Windows 執行緒支援的執行緒 proxy 呼叫時，`YieldToSystem` 的行為與 Windows 函數 `SwitchToThread`完全相同。 不過，從使用者模式可排程（UMS）執行緒呼叫時，`SwitchToThread` 函式會將挑選下一個執行緒的工作委派給使用者模式排程器，而不是作業系統。 若要達成切換至系統中不同就緒執行緒的預期效果，請使用 `YieldToSystem`。

必須在代表目前執行中線程的 `IThreadProxy` 介面上呼叫 `YieldToSystem`，否則不會定義結果。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IExecutionContext 結構](iexecutioncontext-structure.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
