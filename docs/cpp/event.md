---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: c1c9fa5a6df4cbb1c18e5d5406bdde0197d155b2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498818"
---
# <a name="__event"></a>__event

宣告事件。

## <a name="syntax"></a>語法

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>備註

關鍵字 **`__event`** 可以套用至方法宣告、介面宣告或資料成員宣告。 不過，您無法使用 **`__event`** 關鍵字來限定嵌套類別的成員。

根據您的事件來源和接收器是原生 C++，COM 或 Managed (.NET Framework)，您可以將下列建構當做事件使用：

|Native C++|COM|Managed (.NET Framework)|
|------------------|---------|--------------------------------|
|方法|—|method|
|—|interface|—|
|—|—|資料成員|

使用事件接收器中的 [__hook](../cpp/hook.md) ，將處理常式方法與事件方法產生關聯。 請注意，當您建立含有關鍵詞的事件之後 **`__event`** ，呼叫該事件時，將會呼叫稍後與該事件連結的所有事件處理常式。

**`__event`** 方法宣告不能有定義，而是以隱含方式產生定義，因此可以像是任何一般方法一樣呼叫事件方法。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="native-events"></a>原生事件

原生事件是方法。 傳回型別通常是 HRESULT 或 **`void`** ，但可以是任何整數類型，包括 **`enum`** 。 當事件使用整數傳回型別時，會在事件處理常式傳回非零值時定義錯誤條件，在此情況下，所引發的事件會呼叫其他委派。

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

請參閱 [原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md) 以取得範例程式碼。

## <a name="com-events"></a>COM 事件

COM 事件是介面。 事件來源介面中方法的參數應該在參數 (*中* ，但這並不是嚴格強制) ，因為在多播時， *out* 參數並不有用。 如果您使用 *out* 參數，則會發出層級1警告。

傳回型別通常是 HRESULT 或 **`void`** ，但可以是任何整數類型，包括 **`enum`** 。 當事件使用整數傳回類型且事件處理常式傳回非零值時，會是錯誤條件，在此情況下，所引發的事件會中止呼叫其他委派。 請注意，編譯器會自動將事件來源介面標示為產生的 IDL 中的 [來源](../windows/attributes/source-cpp.md) 。

COM 事件來源的之後一律需要 [__interface](../cpp/interface.md) 關鍵字 **`__event`** 。

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

如需範例程式碼，請參閱 [COM 中的事件處理](../cpp/event-handling-in-com.md) 。

## <a name="managed-events"></a>Managed 事件

如需新語法中程式碼撰寫事件的詳細資訊，請參閱 [事件](../extensions/event-cpp-component-extensions.md)。

Managed 事件是資料成員或方法。 搭配事件使用時，委派的傳回型別必須符合 [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components)的規範。 事件處理常式的傳回類型必須符合委派的傳回類型。 如需委派的詳細資訊，請參閱 [委派和事件](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。 如果 Managed 事件是資料成員，其類型必須是委派的指標。

在 .NET Framework 中，您可以將資料成員視同方法本身 (也就是，其對應委派的 `Invoke` 方法)。 您必須預先定義用來宣告 Managed 事件資料成員的委派類型。 相反地，Managed 事件方法會隱含定義對應的 Managed 委派 (如果尚未定義的話)。 例如，您可以將事件的值 (例如 `OnClick`) 宣告為事件，如下所示：

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

隱含宣告 Managed 事件時，您可以指定會在新增或移除事件處理常式時呼叫的 add 和 remove 存取子。 您也可以定義從類別外呼叫 (引發) 事件的方法。

## <a name="example-native-events"></a>範例：原生事件

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>範例：COM 事件

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[事件處理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
