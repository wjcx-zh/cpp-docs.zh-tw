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
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337556"
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

**&***SourceClass* `::` *eventMethod*指向從中取消掛鉤的事件處理程式方法的指標:

- 本機C++事件:*來源*是事件來源類,*事件方法*是事件。

- COM 事件 *:SourceClass*是事件源介面,*事件方法*是其方法之一。

- 託管事件:*來源*是事件來源類,*事件方法*是事件。

*interface*<br/>
介面名稱從接收器取消掛接 *,* 僅適用於[EVENT_RECEIVER屬性](../windows/attributes/event-receiver.md)*的layout_dependent*參數為**true**的 COM 事件接收器。

*源*<br/>
事件來源執行個體的指標。 依中`event_receiver`指定的`type`代碼 *,原始碼*可以是以下代碼之一:

- 原生事件來源物件指標。

- 基於`IUnknown`指標 (COM 源)。

- Managed 物件指標 (用於 Managed 事件)。

**&***接收器類*`::``HandlerMethod`A 指向事件處理程式方法的指標,以便從事件中取消掛接。 處理程式被指定為類的方法或對同一類的引用;如果不指定類名稱 **,__unhook**假定該類是調用該類的類。

- 本機C++事件:*接收方類*是事件接收`HandlerMethod`者類 ,是處理程式。

- COM 事件:*接收器類*是事件接收`HandlerMethod`器介面, 是其處理程式之一。

- 託管事件:*接收方類*是事件接收方`HandlerMethod`類 ,是處理程式。

*接收器*(可選)指向事件接收器類實例的指標。 如果不指定接收器,則預設值為調用 **__unhook**的接收器類或結構。

## <a name="usage"></a>使用量

可以在事件接收器類別之外的任何函式範圍中使用，包括 main。

## <a name="remarks"></a>備註

使用事件接收器中的內在函數 **__unhook**將處理程式方法與事件方法分離或"取消挂鉤」。

有三種 **__unhook**形式。 大部分情況下可以使用第一種 (四個引數) 形式。 只能對 COM 事件接收器使用第二種(兩參數 **)__unhook**形式;這將取消掛接整個事件介面。 您可以使用第三種 (單一引數) 形式從指定的來源解除所有委派的連結。

非零的傳回值表示發生錯誤 (Managed 事件將會擲回例外狀況)。

如果在尚未掛接的事件和事件處理程式上調用 **__unhook,** 它將不起作用。

在編譯時期，編譯器會驗證事件是否存在，並且對指定的處理常式進行參數類型檢查使。

除 COM 事件外 **,__hook**和 **__unhook**可以在事件接收器外部呼叫。

使用 **__unhook**的替代方法是使用 -# 運算子。

有關在新語法中編碼託管事件的資訊,請參閱[事件](../extensions/event-cpp-component-extensions.md)。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="example"></a>範例

有關範例[,請參閱本機C++中的事件處理](../cpp/event-handling-in-native-cpp.md)與[COM 中的事件處理](../cpp/event-handling-in-com.md)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
