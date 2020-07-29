---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: 5a0eaf0a3bc0617dbcd1f43805af8a95291e7e47
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188163"
---
# <a name="__hook"></a>__hook

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

*&SourceClass：： EventMethod*<br/>
您用於連結事件處理常式方法的事件方法指標：

- 原生 c + + 事件： *SourceClass*是事件來源類別，而*EventMethod*是事件。

- COM 事件： *SourceClass*是事件來源介面，而*EventMethod*是它的其中一個方法。

- Managed 事件： *SourceClass*是事件來源類別，而*EventMethod*是事件。

*interface*<br/>
要與*接收者*連結的介面名稱，僅適用于[event_receiver](../windows/attributes/event-receiver.md)屬性的*layout_dependent*參數為的 COM 事件接收器 **`true`** 。

*source*<br/>
事件來源執行個體的指標。 根據 `type` 中指定的程式碼 `event_receiver` 而定， *source*可以是下列其中一項：

- 原生事件來源物件指標。

- 以為 `IUnknown` 基礎的指標（COM 來源）。

- Managed 物件指標 (用於 Managed 事件)。

*&ReceiverClass：： HandlerMethod*<br/>
要連結至事件的事件處理常式方法的指標。 處理常式會指定為類別的方法或相同的參考;如果您未指定類別名稱， **`__hook`** 會假設類別是在其中呼叫它的。

- 原生 c + + 事件： *ReceiverClass*是事件接收器類別，而 `HandlerMethod` 是處理常式。

- COM 事件： *ReceiverClass*是事件接收器介面，而且 `HandlerMethod` 是它的其中一個處理常式。

- Managed 事件： *ReceiverClass*是事件接收器類別，而 `HandlerMethod` 是處理常式。

*放*<br/>
選擇性事件接收器類別之實例的指標。 如果您未指定接收者，預設值就是呼叫的接收器類別或結構 **`__hook`** 。

## <a name="usage"></a>使用方式

可以在事件接收器類別之外的任何函式範圍中使用，包括 main。

## <a name="remarks"></a>備註

**`__hook`** 在事件接收器中使用內建函式，可讓處理常式方法與事件方法產生關聯或連結。 然後，當來源引發指定事件時，就會呼叫指定的處理常式。 您可以將數個處理常式連結至單一事件，也可以將數個事件連結至單一處理常式。

有兩種形式 **`__hook`** 。 在大部分情況下，您可以使用第一種（四個引數）形式，特別是針對[event_receiver](../windows/attributes/event-receiver.md)屬性的*layout_dependent*參數為的 COM 事件接收器 **`false`** 。

在這些情況下，您在其中一個方法引發事件之前，不需要連結介面中的所有方法；只需要連結處理該事件的方法即可。 您 **`__hook`** 只能針對*layout_dependent* **= true**的 COM 事件接收器，使用第二個（兩個引數）形式的。

**`__hook`** 傳回 long 值。 非零傳回值表示已發生錯誤 (Managed 事件擲回例外狀況)。

編譯器會檢查事件是否存在，以及事件簽章與委派簽章是否一致。

除了 COM 事件 **`__hook`** 之外，也可以在 **`__unhook`** 事件接收器外部呼叫。

使用的替代方法 **`__hook`** 是使用 + = 運算子。

如需在新語法中編碼 managed 事件的詳細資訊，請參閱[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="example"></a>範例

如需範例，請參閱[原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件處理](../cpp/event-handling-in-com.md)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[事件處理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
