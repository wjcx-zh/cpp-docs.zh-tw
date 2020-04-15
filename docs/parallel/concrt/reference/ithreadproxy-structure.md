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
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368134"
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
|[IThread 代理::GetId](#getid)|返回線程代理的唯一標識符。|
|[IThreadProxy::切換出](#switchout)|解除基礎虛擬處理器根內容的關聯。|
|[IThreadProxy::切換到](#switchto)|執行協作上下文從當前執行的上下文切換到其他上下文。|
|[IThreadProxy::屈服到系統](#yieldtosystem)|造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 操作系統選擇要執行的下一個線程。|

## <a name="remarks"></a>備註

線程代理與介面`IExecutionContext`表示的執行上下文耦合,作為調度工作的一種手段。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IThreadProxy`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy:GetId 方法

返回線程代理的唯一標識符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

唯一的整數標識符。

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>IThreadProxy::切換方法

解除基礎虛擬處理器根內容的關聯。

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>參數

*開關狀態*<br/>
指示執行交換機的線程代理的狀態。 參數的型`SwitchingProxyState`態為 。

### <a name="remarks"></a>備註

如果因故需要將內容與其執行所在的虛擬處理器根解除關聯，請使用 `SwitchOut`。 根據您傳遞給 `switchState` 參數的值，以及它是否在虛擬處理器根上執行而定，呼叫會立即傳回或是封鎖與內容相關聯的執行緒 Proxy。 在將參數設定為 `SwitchOut` 的情況下呼叫 `Idle` 是錯誤的做法。 這樣做將導致[invalid_argument](../../../standard-library/invalid-argument-class.md)異常。

無論是因為資源管理員的指示，或是您要求暫時過度訂閱虛擬處理器根，但已經不再需要這樣做，只要您想要減少排程器擁有的虛擬處理器根數目，`SwitchOut` 都會很有用。 在這種情況下,您應該呼叫方法[IVirtualProcessorRoot::刪除](iexecutionresource-structure.md#remove)虛擬處理器根,然後再呼`SwitchOut`叫`switchState`參數`Blocking`設定為 。 這樣將會封鎖執行緒 Proxy，而且它會在排程器中有不同的虛擬處理器根可用於執行時繼續執行。 可以通過調用函`SwitchTo`數 切換到此線程代理的執行上下文來恢復阻塞線程代理。 您還可以使用其關聯的上下文來啟動虛擬處理器根,從而恢復線程代理。 有關如何執行此操作的詳細資訊,請參閱[IVirtualProcessorRoot:::啟動](ivirtualprocessorroot-structure.md#activate)。

當您想要重新初始化虛擬處理器，讓它能夠在未來發生封鎖執行緒 Proxy，或是暫時將它卸離執行所在的虛擬處理器根以及對其分派工作的排程器時可以啟動，您也可以使用 `SwitchOut`。 如果您想要封鎖執行緒 Proxy，請使用 `SwitchOut`，並將 `switchState` 參數設定為 `Blocking`。 之後可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 讓它繼續執行，如上面所述。 當您想要暫時將這個執行緒 Proxy 卸離執行所在的虛擬處理器根，以及與虛擬處理器相關聯的排程器，請使用 `SwitchOut` 並將參數設定為 `Nesting`。 若呼叫 `SwitchOut` 並將 `switchState` 參數設定為 `Nesting` 時，它正在虛擬處理器根上執行，則會造成根重新初始化，而且目前執行緒 Proxy 會繼續執行，不需要根。 線程代理被視為已離開計劃程式,直到它調用[IThreadProxy::switchOut](#switchout)方法,稍後`Blocking`時間點使用。 第二次呼叫 `SwitchOut` 並將參數設定為 `Blocking` 時，該呼叫會將內容返回已封鎖狀態，以便在卸離的排程器中透過 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 繼續執行。 由於它並未在虛擬處理器根上執行，因此不會發生重新初始化。

已重新初始化的虛擬處理器根與資源管理員授與排程器的全新虛擬處理器根並無不同。 您可以在執行內容中使用 `IVirtualProcessorRoot::Activate` 啟用它，這樣就可以用它來執行。

`SwitchOut`必須在表示當前正在執行`IThreadProxy`的線程的介面上調用,否則結果未定義。

在隨附於 Visual Studio 2010 的程式庫和標頭中，這個方法不會使用參數，也不會重新初始化虛擬處理器根。 若要保留舊有行為，可以提供預設參數值 `Blocking`。

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>IThreadProxy::切換到方法

執行協作上下文從當前執行的上下文切換到其他上下文。

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
要協同切換到的執行上下文。

*開關狀態*<br/>
指示執行交換機的線程代理的狀態。 參數的型`SwitchingProxyState`態為 。

### <a name="remarks"></a>備註

使用此方法從第一個執行上下文的[iExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch)方法從一個執行上下文切換到另一個執行上下文。 如果執行上下文尚未與線程`pContext`代理關聯,則該方法將執行上下文與線程代理關聯。 當前線程代理的所有權由您為`switchState`參數指定的值確定。

如果要將當前`Idle`正在執行的線程代理返回到資源管理員,請使用該值。 使用`SwitchTo``switchState`參數設置為調`Idle`用將導致執行上下`pContext`文 開始在基礎執行資源上執行。 此線程代理的所有權將轉移到資源管理員,並且您希望在返回後立即`Dispatch``SwitchTo`從執行上下文的方法返回,以便完成傳輸。 線程代理調度的執行上下文與線程代理分離,調度程式可以自由地重用它或銷毀它,因為它認為合適。

當希望此`Blocking`線程代理進入阻止狀態時,請使用 該值。 使用`SwitchTo``switchState`參數設置為調`Blocking`用 將導致執行`pContext`上下文 開始執行,並阻止當前線程代理,直到恢復它。 當線程代理處於`Blocking`狀態時,計劃程式保留線程代理的擁有權。 可以通過調用函`SwitchTo`數 切換到此線程代理的執行上下文來恢復阻塞線程代理。 您還可以使用其關聯的上下文來啟動虛擬處理器根,從而恢復線程代理。 有關如何執行此操作的詳細資訊,請參閱[IVirtualProcessorRoot:::啟動](ivirtualprocessorroot-structure.md#activate)。

如果要暫時將`Nesting`此線程代理從正在運行的虛擬處理器根和為其調度工作的調度程式分離時,請使用該值。 使用`SwitchTo``switchState`參數設置為調`Nesting`用 將導致執行`pContext`上下文 開始執行,並且當前線程代理也繼續執行,而無需虛擬處理器根。 線程代理被視為已離開計劃程式,直到它在以後的時間點調用[IThreadProxy::SwitchOut](#switchout)方法。 該方法`IThreadProxy::SwitchOut`可以阻止線程代理,直到虛擬處理器根可用於重新計劃它。

`SwitchTo`必須在表示當前正在執行`IThreadProxy`的線程的介面上調用,否則結果未定義。 如果參數`invalid_argument``pContext`設定`NULL`為 ,則將引發該函數。

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>IThreadProxy:屈服到系統方法

造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 操作系統選擇要執行的下一個線程。

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>備註

當由一般 Windows 執行緒支援的線程代理呼`YieldToSystem`叫時, 其執行方式與`SwitchToThread`Windows 函數 完全一樣。 但是,當從使用者模式可分排 (UMS) 線程調`SwitchToThread`用時 ,該函數將選取要運行的下一個線程的任務委派給使用者模式計劃程式,而不是操作系統。 要達到在系統中切換到其他就緒線程的預期效果,請使用`YieldToSystem`。

`YieldToSystem`必須在表示當前正在執行`IThreadProxy`的線程的介面上調用,否則結果未定義。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IExecutionContext 結構](iexecutioncontext-structure.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
