---
title: AgileEventSource 類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7412968069963679db769cc2ce68169e7a8799b9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462065"
---
# <a name="agileeventsource-class"></a>AgileEventSource 類別

代表敏捷式軟體開發的元件，也就是可以從任何執行緒存取的元件引發的事件。 繼承自[EventSource](eventsource-class.md) ，並覆寫`Add`成員函式，使用其他的型別參數來指定如何叫用事件，敏捷式軟體開發的選項。

## <a name="syntax"></a>語法

```
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>參數  
 *TDelegateInterface*  

 要委派，表示事件處理常式的介面。

 *TEventSourceOptions*  
 [InvokeModeOptions](invokemodeoptions-structure.md)結構，其 invokeMode 欄位設為`InvokeMode::StopOnFirstError`或`InvokeMode::FireAll`。

## <a name="remarks"></a>備註

大部分的 Windows 執行階段中的元件是敏捷式軟體開發的元件。 如需詳細資訊，請參閱 <<c0> [ 執行緒和封送處理 (C + + /CX)](../cppcx/threading-and-marshaling-c-cx.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

 `EventSource` `AgileEventSource`

## <a name="requirements"></a>需求

 **標頭：** event.h

 **命名空間：** Microsoft::WRL

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[AgileEventSource::Add 方法](#add)|將附加至所指定的委派介面代表目前 AgileEventSource 物件的事件處理常式集合的敏捷式軟體開發的事件處理常式。|

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

*delegateInterface*  
要委派物件，代表事件處理常式的介面。

*語彙基元*  
這項作業完成時，代表事件的控制代碼。 若要捨棄的事件處理常式，做為 remove （） 方法的參數使用此權杖。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。


## <a name="see-also"></a>另請參閱
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)