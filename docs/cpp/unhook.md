---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: e8f42c35024995c026ae10fc7f0ab3db77d1e5dc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769520"
---
# <a name="unhook"></a>__unhook

解除處理常式方法與事件的關聯。

## <a name="syntax"></a>語法

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>參數

**&** *SourceClass* `::` *EventMethod*從中解除連結事件處理常式方法的事件方法指標：

- 原生 c + + 事件：*SourceClass*是事件來源類別以及*EventMethod*是事件。

- COM 事件：*SourceClass*是事件來源介面和*EventMethod*是其中一個方法。

- Managed 的事件：*SourceClass*是事件來源類別以及*EventMethod*是事件。

*interface*<br/>
從解除連結的介面名稱*接收者*，只會針對在其中的 COM 事件接收器*layout_dependent*參數[event_receiver](../windows/attributes/event-receiver.md)屬性是 **，則為 true**。

*source*<br/>
事件來源執行個體的指標。 根據程式碼`type`中指定`event_receiver`，*來源*可以是下列其中之一：

- 原生事件來源物件指標。

- `IUnknown`-基礎指標 （COM 來源）。

- Managed 物件指標 (用於 Managed 事件)。

**&** *ReceiverClass* `::` `HandlerMethod`瑢髍廒事件之事件處理常式方法的指標。 做為類別或參考相同的方法指定的處理常式如果您未指定類別名稱， **__unhook**假設要在其中已呼叫該方法的類別。

- 原生 c + + 事件：*ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。

- COM 事件：*ReceiverClass*是事件接收器介面和`HandlerMethod`是其中一個處理常式。

- Managed 的事件：*ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。

*接收者*（選擇性） 的事件接收器類別執行個體的指標。 如果您未指定接收器，預設值是接收器類別或結構所在 **__unhook**呼叫。

## <a name="usage"></a>使用量

可以在事件接收器類別之外的任何函式範圍中使用，包括 main。

## <a name="remarks"></a>備註

使用內建函式 **__unhook**中斷關聯或 「 解除連結 」 從事件方法的處理常式方法的事件接收器中。

有三種形式 **__unhook**。 大部分情況下可以使用第一種 (四個引數) 形式。 您可以使用第二個 （兩個引數） 形式 **__unhook**這只能用於 COM 事件接收器中，取消攔截整個事件介面。 您可以使用第三種 (單一引數) 形式從指定的來源解除所有委派的連結。

非零的傳回值表示發生錯誤 (Managed 事件將會擲回例外狀況)。

如果您呼叫 **__unhook**上的事件和尚未連結的事件處理常式，它會有任何作用。

在編譯時期，編譯器會驗證事件是否存在，並且對指定的處理常式進行參數類型檢查使。

除了 COM 事件之外 **__hook**並 **__unhook**可以在事件接收器之外呼叫。

使用替代 **__unhook**是使用-= 運算子。

如需新語法中編碼 managed 的事件資訊，請參閱[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
>  樣板類別或結構不能包含事件。

## <a name="example"></a>範例

請參閱[原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)並[COM 中的事件處理](../cpp/event-handling-in-com.md)範例。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)