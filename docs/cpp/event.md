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
ms.openlocfilehash: f8935408c6e9b43347d4ad6088505a461e254ae2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366295"
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

關鍵字 **__event**可以應用於方法聲明、介面聲明或數據成員聲明。 但是,不能使用 **__event**關鍵字來限定嵌套類的成員。

根據您的事件來源和接收器是原生 C++，COM 或 Managed (.NET Framework)，您可以將下列建構當做事件使用：

|Native C++|COM|Managed (.NET Framework)|
|------------------|---------|--------------------------------|
|方法|—|method|
|—|interface|—|
|—|—|資料成員|

在事件接收器中使用[__hook](../cpp/hook.md)將處理程式方法與事件方法相關聯。 請注意,使用 **__event**關鍵字創建事件後,調用該事件時將調用隨後掛接該事件的所有事件處理程式。

**__event**方法聲明不能具有定義;因此,方法聲明不能具有定義。定義是隱式生成的,因此可以調用事件方法,就好像它是任何普通方法一樣。

> [!NOTE]
> 樣板類別或結構不能包含事件。

## <a name="native-events"></a>原生事件

原生事件是方法。 傳回類型通常是 HRESULT 或**void**,但可以是任何積分類型,包括**enp。** 當事件使用整數傳回型別時，會在事件處理常式傳回非零值時定義錯誤條件，在此情況下，所引發的事件會呼叫其他委派。

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

有關範例代碼[,請參閱本機C++的事件處理](../cpp/event-handling-in-native-cpp.md)。

## <a name="com-events"></a>COM 事件

COM 事件是介面。 事件源介面中方法的參數應*位於參數中*(但未嚴格強制實施),因為*out*參數在多播時沒有用處。 如果使用*out*參數,將發出級別 1 警告。

傳回型態通常是 HRESULT 或**void,** 但是可以是任何積分類型,包括**enRESULT**。 當事件使用整數傳回類型且事件處理常式傳回非零值時，會是錯誤條件，在此情況下，所引發的事件會中止呼叫其他委派。 請注意,編譯器將自動將事件源介面標記為產生的 IDL 中的[來源](../windows/attributes/source-cpp.md)。

對於 COM 事件源 **__event**後,始終需要[__interface](../cpp/interface.md)關鍵字。

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

有關範例代碼,請參考[COM 中的事件處理](../cpp/event-handling-in-com.md)。

## <a name="managed-events"></a>Managed 事件

有關新語法中編碼事件的資訊,請參閱[事件](../extensions/event-cpp-component-extensions.md)。

Managed 事件是資料成員或方法。 當與事件一起使用時,委託的傳回類型必須符合[通用語言規範](/dotnet/standard/language-independence-and-language-independent-components)。 事件處理常式的傳回類型必須符合委派的傳回類型。 有關委託的詳細資訊,請參閱[委託和事件](../dotnet/delegates-and-events.md)。 如果 Managed 事件是資料成員，其類型必須是委派的指標。

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
