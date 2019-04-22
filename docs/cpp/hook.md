---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: c4887d85e01344c171fb0fdfe957f2d8a669ff6a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58771665"
---
# <a name="hook"></a>__hook

建立處理常式方法與事件的關聯。

## <a name="syntax"></a>語法

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>參數

*&SourceClass::EventMethod*<br/>
您用於連結事件處理常式方法的事件方法指標：

- 原生C++事件：*SourceClass*是事件來源類別以及*EventMethod*是事件。

- COM 事件：*SourceClass*是事件來源介面和*EventMethod*是其中一個方法。

- Managed 的事件：*SourceClass*是事件來源類別以及*EventMethod*是事件。

*interface*<br/>
介面名稱連結至*接收者*，只會針對在其中的 COM 事件接收器*layout_dependent*參數[event_receiver](../windows/attributes/event-receiver.md)屬性是 **，則為 true**。

*source*<br/>
事件來源執行個體的指標。 根據程式碼`type`中指定`event_receiver`，*來源*可以是下列其中之一：

- 原生事件來源物件指標。

- `IUnknown`-基礎指標 （COM 來源）。

- Managed 物件指標 (用於 Managed 事件)。

*&ReceiverClass::HandlerMethod*<br/>
要連結至事件的事件處理常式方法的指標。 做為類別或參考相同的方法指定的處理常式如果您未指定類別名稱， **__hook**假設要在其中已呼叫該方法的類別。

- 原生C++事件：*ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。

- COM 事件：*ReceiverClass*是事件接收器介面和`HandlerMethod`是其中一個處理常式。

- Managed 的事件：*ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。

*receiver*<br/>
（選擇性）事件接收器類別的執行個體的指標。 如果您未指定接收器，預設值是接收器類別或結構所在 **__hook**呼叫。

## <a name="usage"></a>使用量

可以在事件接收器類別之外的任何函式範圍中使用，包括 main。

## <a name="remarks"></a>備註

使用內建函式 **__hook**關聯或連結處理常式方法與事件方法的事件接收器中。 然後，當來源引發指定事件時，就會呼叫指定的處理常式。 您可以將數個處理常式連結至單一事件，也可以將數個事件連結至單一處理常式。

有兩種形式 **__hook**。 可用於大部分情況下，第一種 （四個引數） 形式具體來說，在其中的 COM 事件接收器*event_receiver*的參數[event_receiver](../windows/attributes/event-receiver.md)屬性是**false**.

在這些情況下，您在其中一個方法引發事件之前，不需要連結介面中的所有方法；只需要連結處理該事件的方法即可。 您可以使用第二個 （兩個引數） 形式 **__hook**只會針對在其中的 COM 事件接收器*layout_dependent* **= true**。

**__hook**傳回長數值。 非零傳回值表示已發生錯誤 (Managed 事件擲回例外狀況)。

編譯器會檢查事件是否存在，以及事件簽章與委派簽章是否一致。

除了 COM 事件之外 **__hook**並 **__unhook**可以在事件接收器之外呼叫。

使用替代 **__hook**是使用 + = 運算子。

如需新語法中編碼 managed 的事件資訊，請參閱[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="example"></a>範例

請參閱[原生中的事件處理C++](../cpp/event-handling-in-native-cpp.md)並[COM 中的事件處理](../cpp/event-handling-in-com.md)範例。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[事件處理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
