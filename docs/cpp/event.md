---
title: "__event | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__event_cpp"
  - "__event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__event 關鍵字 [C++]"
  - "事件 [C++], __event"
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __event
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告事件。  
  
## 語法  
  
```  
  
      __event   
      method-declarator  
      ;  
__event __interface interface-specifier;  
__event member-declarator;  
```  
  
## 備註  
 關鍵字 `__event` 可以套用至方法宣告、介面宣告或資料成員宣告。  不過，您無法使用 `__event` 關鍵字限定巢狀類別的成員。  
  
 根據您的事件來源和接收器是原生 C\+\+，COM 或 Managed \(.NET Framework\)，您可以將下列建構當做事件使用：  
  
|原生 C\+\+|COM|Managed \(.NET Framework\)|  
|--------------|---------|--------------------------------|  
|方法|—|方法|  
|—|介面|—|  
|—|—|資料成員|  
  
 在事件接收器中使用 [\_\_hook](../cpp/hook.md) 建立處理常式方法與事件方法的關聯。  請注意，在您使用 `__event` 關鍵字建立事件後，每當呼叫該事件時，會一併呼叫後續攔截到該事件的所有事件處理常式。  
  
 `__event` 方法宣告不能有定義；定義會隱含產生，因此可以將事件方法當做任何一般方法予以呼叫。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## 原生事件  
 原生事件是方法。  傳回類型通常是 `HRESULT` 或 `void`，不過可以是任何整數類型，包括 `enum`。  當事件使用整數傳回類型時，會在事件處理常式傳回非零值時定義錯誤條件，在此情況下，所引發的事件會呼叫其他委派。  
  
```  
// Examples of native C++ events:  
__event void OnDblClick();  
__event HRESULT OnClick(int* b, char* s);  
```  
  
 如需範例程式碼，請參閱[原生 C\+\+ 中的事件處理](../cpp/event-handling-in-native-cpp.md)。  
  
## COM 事件  
 COM 事件是介面。  事件來源介面中的方法參數應該是 **in** 參數 \(但不會強制執行\)，因為多點傳送時不適用 **out** 參數。  如果您使用 **out** 參數，會發出層級 1 警告。  
  
 傳回類型通常是 `HRESULT` 或 `void`，但可以是任何整數類型，包括 `enum`。  當事件使用整數傳回類型且事件處理常式傳回非零值時，會是錯誤條件，在此情況下，所引發的事件會中止呼叫其他委派。  請注意，編譯器會在所產生的 IDL 中自動將事件來源介面標記為[來源](../windows/source-cpp.md)。  
  
 COM 事件來源的 `__event` 之後，一定要有 [\_\_interface](../cpp/interface.md) 關鍵字。  
  
```  
// Example of a COM event:  
__event __interface IEvent1;  
```  
  
 如需範例程式碼，請參閱 [COM 中的事件處理](../cpp/event-handling-in-com.md)。  
  
## Managed 事件  
 如需新語法中編碼事件的相關資訊，請參閱[event](../windows/event-cpp-component-extensions.md)。  
  
 Managed 事件是資料成員或方法。  搭配事件使用時，委派的傳回類型必須符合 [Common Language Specification](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  事件處理常式的傳回類型必須符合委派的傳回類型。  如需委派的詳細資訊，請參閱 [\_\_delegate](../misc/delegate.md)。  如果 Managed 事件是資料成員，其類型必須是委派的指標。  
  
 在 .NET Framework 中，您可以將資料成員視同方法本身 \(也就是，其對應委派的 `Invoke` 方法\)。  您必須預先定義用來宣告 Managed 事件資料成員的委派類型。  相反地，Managed 事件方法會隱含定義對應的 Managed 委派 \(如果尚未定義的話\)。  例如，您可以將事件的值 \(例如 `OnClick`\) 宣告為事件，如下所示：  
  
```  
// Examples of managed events:  
__event ClickEventHandler* OnClick;  // data member as event  
__event void OnClick(String* s);  // method as event  
```  
  
 隱含宣告 Managed 事件時，您可以指定會在新增或移除事件處理常式時呼叫的 add 和 remove 存取子。  您也可以定義從類別外呼叫 \(引發\) 事件的方法。  
  
## 範例：原生事件  
  
```  
// EventHandling_Native_Event.cpp  
// compile with: /c  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
```  
  
## 範例：COM 事件  
  
```  
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
  
## 範例：Managed 事件  
  
```  
// EventHandling_Managed_Event.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
[event_source(managed)]  
public __gc class CPSource {  
  
public:  
   __event void MyEvent(Int16 nValue);  
};  
```  
  
 將屬性套用至事件時，您可以指定將該屬性套用至產生的方法或產生的委派的叫用方法。預設 \(`event:`\) 是將屬性套用至事件。  
  
```  
// EventHandling_Managed_Event_2.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
[attribute(All, AllowMultiple=true)]  
public __gc class Attr {};  
  
public __delegate void D();  
  
public __gc class X {  
public:  
   [method:Attr] __event D* E;  
   [returnvalue:Attr] __event void noE();  
};  
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [事件處理](../cpp/event-handling.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [\_\_raise](../cpp/raise.md)