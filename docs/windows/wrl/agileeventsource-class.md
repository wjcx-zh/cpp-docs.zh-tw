---
title: AgileEventSource 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: a18b4fd7873bcc0895354186dc9b0cc7e6b71bd4
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335714"
---
# <a name="agileeventsource-class"></a>AgileEventSource 類別

代表敏捷式軟體開發的元件，也就是可以從任何執行緒存取的元件引發的事件。 繼承自[EventSource](eventsource-class.md) ，並覆寫`Add`成員函式，使用其他的型別參數來指定如何叫用事件，敏捷式軟體開發的選項。

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
要委派，表示事件處理常式的介面。

*TEventSourceOptions*<br/>
[InvokeModeOptions](invokemodeoptions-structure.md)結構，其 invokeMode 欄位設為`InvokeMode::StopOnFirstError`或`InvokeMode::FireAll`。

## <a name="remarks"></a>備註

大部分的 Windows 執行階段中的元件是敏捷式軟體開發的元件。 如需詳細資訊，請參閱 <<c0> [ 執行緒和封送處理 (C + + /CX)](../../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft:: wrl

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[AgileEventSource::Add 方法](#add)|將附加的敏捷式軟體開發的事件處理常式，以指定的委派介面來表示目前的事件處理常式的集合**AgileEventSource**物件。|

## <a name="add"></a> AgileEventSource::Add 方法

將附加事件處理常式，以指定的委派介面來表示目前的事件處理常式的集合[EventSource](eventsource-class.md)物件。

### <a name="syntax"></a>語法

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>參數

*delegateInterface*<br/>
要委派物件，代表事件處理常式的介面。

*token*<br/>
這項作業完成時，代表事件的控制代碼。 使用此權杖做為參數`Remove()`捨棄的事件處理常式的方法。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)