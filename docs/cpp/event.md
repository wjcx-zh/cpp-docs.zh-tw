---
title: __event |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __event_cpp
- __event
dev_langs:
- C++
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74b79edb24396896a6c8a50965081e9466720ca4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407821"
---
# <a name="event"></a>__event
宣告事件。  
  
## <a name="syntax"></a>語法  
  
```  
__event method-declarator;  
__event __interface interface-specifier;  
__event member-declarator;  
```  
  
## <a name="remarks"></a>備註  
 關鍵字 **__event**可以套用至方法宣告、 介面宣告或資料成員宣告。 不過，您無法使用 **__event**關鍵字限定巢狀類別的成員。  
  
 根據您的事件來源和接收器是原生 C++，COM 或 Managed (.NET Framework)，您可以將下列建構當做事件使用：  
  
|原生 C++|COM|Managed (.NET Framework)|  
|------------------|---------|--------------------------------|  
|方法|—|方法|  
|—|interface|—|  
|—|—|資料成員|  
  
 使用[__hook](../cpp/hook.md)在事件接收器事件方法相關聯的處理常式方法中。 請注意，在您建立的事件之後 **__event**時呼叫該事件時，所有後續攔截到該事件的事件處理常式會呼叫的關鍵字。  
  
 **__Event**方法宣告不能有定義; 定義會隱含產生，因此可以呼叫事件的方法，如同它是任何一般方法。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="native-events"></a>原生事件  
 原生事件是方法。 傳回的型別通常是 HRESULT 或**void**，但可以是任何整數類型，包括**enum**。 當事件使用整數傳回型別時，會在事件處理常式傳回非零值時定義錯誤條件，在此情況下，所引發的事件會呼叫其他委派。  
  
```cpp 
// Examples of native C++ events:  
__event void OnDblClick();  
__event HRESULT OnClick(int* b, char* s);  
```  
  
 請參閱[原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)範例程式碼。  
  
## <a name="com-events"></a>COM 事件  
 COM 事件是介面。 在 事件來源介面方法的參數應該是*中*參數 （但這不會嚴格強制執行），因為*出*參數不是多點傳送時很有用。 如果您使用，就會發出層級 1 警告*出*參數。  
  
 傳回的型別通常是 HRESULT 或**void**，但可以是任何整數類型，包括**enum**。 當事件使用整數傳回型別且事件處理常式傳回非零值時，會是錯誤條件，在此情況下，所引發的事件會中止呼叫其他委派。 請注意，編譯器會自動將標示為事件來源介面[來源](../windows/source-cpp.md)所產生的 IDL 中。  
  
 [__Interface](../cpp/interface.md)關鍵字之後至少須 **__event** COM 事件來源。  
  
```cpp 
// Example of a COM event:  
__event __interface IEvent1;  
```  
  
 請參閱[COM 中的事件處理](../cpp/event-handling-in-com.md)範例程式碼。  
  
## <a name="managed-events"></a>Managed 事件  
 如需新語法中編碼事件的詳細資訊，請參閱[事件](../windows/event-cpp-component-extensions.md)。  
  
 Managed 事件是資料成員或方法。 委派的傳回型別事件搭配使用時，必須遵守[Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components)。 事件處理常式的傳回型別必須符合委派的傳回型別。 如需有關委派的詳細資訊，請參閱 <<c0> [ 委派和事件](../dotnet/delegates-and-events.md)。 如果 Managed 事件是資料成員，其類型必須是委派的指標。  
  
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
 [關鍵字](../cpp/keywords-cpp.md)   
 [事件處理](../cpp/event-handling.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)