---
title: IThreadProxy 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c7b60ed7f3fef39d7ecd9a7bb9580acc6b1cf91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439597"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 結構

執行緒的抽象概念。 視您所建立之排程器的 `SchedulerType` 原則機碼而定，資源管理員會授與您支援一般 Win32 執行緒或可使用者模式排程 (UMS) 執行緒的執行緒 Proxy。 安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。

## <a name="syntax"></a>語法

```
struct IThreadProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IThreadProxy::GetId](#getid)|執行緒 proxy 傳回的唯一識別碼。|
|[IThreadProxy::SwitchOut](#switchout)|解除基礎虛擬處理器根內容的關聯。|
|[IThreadProxy::SwitchTo](#switchto)|從目前正在執行的內容，執行將合作內容切換至另一個。|
|[IThreadProxy::YieldToSystem](#yieldtosystem)|造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 作業系統會選擇下一個要執行的執行緒。|

## <a name="remarks"></a>備註

執行緒 proxy 會結合介面所表示的執行內容`IExecutionContext`來分派工作。

## <a name="inheritance-hierarchy"></a>繼承階層

`IThreadProxy`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="getid"></a>  Ithreadproxy:: Getid 方法

執行緒 proxy 傳回的唯一識別碼。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

的唯一整數識別碼。

##  <a name="switchout"></a>  Ithreadproxy:: Switchout 方法

解除基礎虛擬處理器根內容的關聯。

```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>參數

*switchState*<br/>
表示執行緒 proxy 正在執行的切換狀態。 參數的類型是`SwitchingProxyState`。

### <a name="remarks"></a>備註

如果因故需要將內容與其執行所在的虛擬處理器根解除關聯，請使用 `SwitchOut`。 根據您傳遞給 `switchState` 參數的值，以及它是否在虛擬處理器根上執行而定，呼叫會立即傳回或是封鎖與內容相關聯的執行緒 Proxy。 在將參數設定為 `SwitchOut` 的情況下呼叫 `Idle` 是錯誤的做法。 這樣會導致[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

無論是因為資源管理員的指示，或是您要求暫時過度訂閱虛擬處理器根，但已經不再需要這樣做，只要您想要減少排程器擁有的虛擬處理器根數目，`SwitchOut` 都會很有用。 在此情況下應該叫用方法[IVirtualProcessorRoot::Remove](iexecutionresource-structure.md#remove)上的虛擬處理器根，再呼叫`SwitchOut`搭配參數`switchState`設定為`Blocking`。 這樣將會封鎖執行緒 Proxy，而且它會在排程器中有不同的虛擬處理器根可用於執行時繼續執行。 封鎖執行緒 proxy 可以藉由呼叫此函式繼續`SwitchTo`切換到此執行緒 proxy 的執行內容。 您也可以繼續執行緒 proxy，使用其相關聯的內容，若要啟用虛擬處理器根。 如需有關如何執行這項操作的詳細資訊，請參閱 < [ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。

當您想要重新初始化虛擬處理器，讓它能夠在未來發生封鎖執行緒 Proxy，或是暫時將它卸離執行所在的虛擬處理器根以及對其分派工作的排程器時可以啟動，您也可以使用 `SwitchOut`。 如果您想要封鎖執行緒 Proxy，請使用 `SwitchOut`，並將 `switchState` 參數設定為 `Blocking`。 之後可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 讓它繼續執行，如上面所述。 當您想要暫時將這個執行緒 Proxy 卸離執行所在的虛擬處理器根，以及與虛擬處理器相關聯的排程器，請使用 `SwitchOut` 並將參數設定為 `Nesting`。 若呼叫 `SwitchOut` 並將 `switchState` 參數設定為 `Nesting` 時，它正在虛擬處理器根上執行，則會造成根重新初始化，而且目前執行緒 Proxy 會繼續執行，不需要根。 執行緒 proxy 會被視為已離開排程器，直到它會呼叫[ithreadproxy:: Switchout](#switchout)方法`Blocking`在稍後的時間。 第二次呼叫 `SwitchOut` 並將參數設定為 `Blocking` 時，該呼叫會將內容返回已封鎖狀態，以便在卸離的排程器中透過 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 繼續執行。 由於它並未在虛擬處理器根上執行，因此不會發生重新初始化。

已重新初始化的虛擬處理器根與資源管理員授與排程器的全新虛擬處理器根並無不同。 您可以在執行內容中使用 `IVirtualProcessorRoot::Activate` 啟用它，這樣就可以用它來執行。

`SwitchOut` 必須在呼叫`IThreadProxy`是未定義的介面，表示目前執行中執行緒或結果。

在隨附於 Visual Studio 2010 的程式庫和標頭中，這個方法不會使用參數，也不會重新初始化虛擬處理器根。 若要保留舊有行為，可以提供預設參數值 `Blocking`。

##  <a name="switchto"></a>  Ithreadproxy:: Switchto 方法

從目前正在執行的內容，執行將合作內容切換至另一個。

```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
若要以合作方式切換至執行內容。

*switchState*<br/>
表示執行緒 proxy 正在執行的切換狀態。 參數的類型是`SwitchingProxyState`。

### <a name="remarks"></a>備註

使用這個方法，從一個執行內容切換至另一個，從[iexecutioncontext:: Dispatch](iexecutioncontext-structure.md#dispatch)方法的第一個執行內容。 此方法將相關聯的執行內容`pContext`如果它尚未與其中一個相關聯的執行緒 proxy。 目前的執行緒 proxy 的擁有權取決於您指定的值`switchState`引數。

使用值`Idle`想要傳回目前正在執行的執行緒 proxy 至 Resource Manager 時。 呼叫`SwitchTo`搭配參數`switchState`設為`Idle`會導致執行內容`pContext`啟動的基礎執行資源上執行。 這個執行緒 proxy 的擁有權轉移給 Resource Manager，並想要傳回的執行內容`Dispatch`方法之後`SwitchTo`傳回時，才能完成轉移。 已分派執行緒 proxy 的執行內容解除關聯的執行緒 proxy，而且排程器可以自由地重複使用或終結它，因為其認為適合。

使用值`Blocking`當您想要這個執行緒 proxy 會進入封鎖的狀態。 呼叫`SwitchTo`搭配參數`switchState`設為`Blocking`會導致執行內容`pContext`開始執行，並繼續之前會封鎖目前的執行緒 proxy。 執行緒 proxy 時，排程器會保留擁有權的執行緒 proxy`Blocking`狀態。 封鎖執行緒 proxy 可以藉由呼叫此函式繼續`SwitchTo`切換到此執行緒 proxy 的執行內容。 您也可以繼續執行緒 proxy，使用其相關聯的內容，若要啟用虛擬處理器根。 如需有關如何執行這項操作的詳細資訊，請參閱 < [ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。

使用值`Nesting`當您想要暫時卸離執行所在的虛擬處理器根這個執行緒 proxy，而排程器其分派工作。 呼叫`SwitchTo`搭配參數`switchState`設為`Nesting`會導致執行內容`pContext`開始執行，而且目前的執行緒 proxy 也會繼續執行而不需要虛擬處理器根。 執行緒 proxy 會被視為已離開排程器，直到它會呼叫[ithreadproxy::](#switchout)方法，在稍後的時間。 `IThreadProxy::SwitchOut`方法無法封鎖執行緒 proxy，直到虛擬處理器根可用於重新排定。

`SwitchTo` 必須在呼叫`IThreadProxy`是未定義的介面，表示目前執行中執行緒或結果。 此函式會擲回`invalid_argument`如果參數`pContext`設定為`NULL`。

##  <a name="yieldtosystem"></a>  Ithreadproxy:: Yieldtosystem 方法

造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。 作業系統會選擇下一個要執行的執行緒。

```
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>備註

呼叫一般的 Windows 執行緒，所支援的執行緒 proxy 時`YieldToSystem`完全相同的 Windows 函式的行為`SwitchToThread`。 不過，當從使用者模式排程 (UMS) 執行緒呼叫`SwitchToThread`函式會將委派挑選下一個要執行以使用者模式排程器，不是作業系統執行緒的工作。 若要達成的系統中切換至不同的就緒執行緒所需的效果，請使用`YieldToSystem`。

`YieldToSystem` 必須在呼叫`IThreadProxy`是未定義的介面，表示目前執行中執行緒或結果。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IExecutionContext 結構](iexecutioncontext-structure.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
