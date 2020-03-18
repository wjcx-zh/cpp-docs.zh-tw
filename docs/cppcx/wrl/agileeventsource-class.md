---
title: AgileEventSource 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: 7a919c0b2aa778ba1db19c3bfc3871542e8f9569
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441263"
---
# <a name="agileeventsource-class"></a>AgileEventSource 類別

表示 agile 元件所引發的事件，這是可從任何執行緒存取的元件。 繼承自[EventSource](eventsource-class.md) ，並以額外的類型參數覆寫 `Add` 成員函式，以指定如何叫用 agile 事件的選項。

## <a name="syntax"></a>語法

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>參數

*TDelegateInterface*<br/>
委派的介面，表示事件處理常式。

*TEventSourceOptions*<br/>
其 invokeMode 欄位設定為 `InvokeMode::StopOnFirstError` 或 `InvokeMode::FireAll`的[InvokeModeOptions](invokemodeoptions-structure.md)結構。

## <a name="remarks"></a>備註

Windows 執行階段中的大部分元件都是 agile 元件。 如需詳細資訊，請參閱[執行緒和C++封送處理（/cx）](../../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>需求

**Header：** 事件。h

**命名空間：** Microsoft::WRL

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[AgileEventSource：： Add 方法](#add)|將指定的委派介面所表示的 agile 事件處理常式附加至目前**AgileEventSource**物件的事件處理常式集合。|

## <a name="add"></a>AgileEventSource：： Add 方法

將指定的委派介面所表示的事件處理常式附加至目前[EventSource](eventsource-class.md)物件的事件處理常式集合。

### <a name="syntax"></a>語法

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>參數

*delegateInterface*<br/>
委派物件的介面，表示事件處理常式。

*token*<br/>
當此作業完成時，表示事件的控制碼。 使用此 token 做為 `Remove()` 方法的參數，以捨棄事件處理常式。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)