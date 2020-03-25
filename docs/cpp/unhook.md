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
ms.openlocfilehash: 2a259b80b941e37e0c3040ad55894c114fe4bc82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160524"
---
# <a name="__unhook"></a>__unhook

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

**&** *SourceClass* `::` 會*EventMethod*事件方法的指標，您可以在其中解除連結事件處理常式方法：

- 原C++生事件： *SourceClass*是事件來源類別，而*EventMethod*是事件。

- COM 事件： *SourceClass*是事件來源介面，而*EventMethod*是它的其中一個方法。

- Managed 事件： *SourceClass*是事件來源類別，而*EventMethod*是事件。

*interface*<br/>
要從*接收者*解除掛鉤的介面名稱，僅適用于[event_receiver](../windows/attributes/event-receiver.md)屬性的*LAYOUT_DEPENDENT*參數為**true**的 COM 事件接收器。

*來源*<br/>
事件來源執行個體的指標。 根據 `event_receiver`中指定的程式碼 `type`， *source*可以是下列其中一項：

- 原生事件來源物件指標。

- 以 `IUnknown`為基礎的指標（COM 來源）。

- Managed 物件指標 (用於 Managed 事件)。

**&** *ReceiverClass* `::` `HandlerMethod` 要從事件解除掛鉤的事件處理常式方法指標。 處理常式會指定為類別的方法或相同的參考;如果您未指定類別名稱， **__unhook**會假設類別是在其中呼叫它的類別。

- 原C++生事件： *ReceiverClass*是事件接收器類別，`HandlerMethod` 是處理常式。

- COM 事件： *ReceiverClass*是事件接收器介面，`HandlerMethod` 是它的其中一個處理常式。

- Managed 事件： *ReceiverClass*是事件接收器類別，`HandlerMethod` 是處理常式。

*接收者*（選擇性）事件接收器類別實例的指標。 如果您未指定接收者，預設值就是呼叫 **__unhook**的接收器類別或結構。

## <a name="usage"></a>使用量

可以在事件接收器類別之外的任何函式範圍中使用，包括 main。

## <a name="remarks"></a>備註

在事件接收器中使用內建函式 **__unhook** ，從事件方法中斷關聯或「解除關聯」處理常式方法。

**__Unhook**有三種形式。 大部分情況下可以使用第一種 (四個引數) 形式。 您可以使用第二個（兩個引數）形式的 **__unhook**僅適用于 COM 事件接收器;這會解除整個事件介面的掛鉤。 您可以使用第三種 (單一引數) 形式從指定的來源解除所有委派的連結。

非零的傳回值表示發生錯誤 (Managed 事件將會擲回例外狀況)。

如果您在尚未進行連結的事件和事件處理常式上呼叫 **__unhook** ，就不會有任何作用。

在編譯時期，編譯器會驗證事件是否存在，並且對指定的處理常式進行參數類型檢查使。

除了 COM 事件以外， **__hook**和 **__unhook**可以在事件接收器外部呼叫。

使用 **__unhook**的替代方法是使用-= 運算子。

如需在新語法中編碼 managed 事件的詳細資訊，請參閱[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
>  樣板類別或結構不能包含事件。

## <a name="example"></a>範例

如需範例，請參閱 COM[中的原C++生](../cpp/event-handling-in-native-cpp.md)和[事件處理](../cpp/event-handling-in-com.md)中的事件處理。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
