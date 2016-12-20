---
title: "__hook | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__hook_cpp"
  - "__hook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__hook 關鍵字 [C++]"
  - "事件處理常式, 連接事件至"
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __hook
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立處理常式方法與事件的關聯。  
  
## 語法  
  
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
  
#### 參數  
 **&** *SourceClass* `::` *EventMethod*  
 您用於連結事件處理常式方法的事件方法指標：  
  
-   原生 C\+\+ 事件：*SourceClass* 是事件來源類別，而 *EventMethod* 是事件。  
  
-   COM 事件：*SourceClass* 是事件來源介面，而 *EventMethod* 是其中一個方法。  
  
-   Managed 事件：*SourceClass* 是事件來源類別，而 *EventMethod* 是事件。  
  
 `interface`  
 將連結至 `receiver` 的介面名稱，僅適用於 [event\_receiver](../windows/event-receiver.md) 屬性的 *layout\_dependent* 參數為 **true** 的 COM 事件接收器。  
  
 *source*  
 事件來源執行個體的指標。  根據 **event\_receiver** 中指定的程式碼 `type` 而定，*source* 可以是下列其中一項：  
  
-   原生事件來源物件指標。  
  
-   **IUnknown** 指標 \(COM 來源\)。  
  
-   Managed 物件指標 \(用於 Managed 事件\)。  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 要連結至事件的事件處理常式方法的指標。  處理常式會指定為類別的方法或類別的參考，如果您未指定類別名稱，`__hook` 會假設類別是本身呼叫所在的類別。  
  
-   原生 C\+\+ 事件：*ReceiverClass* 是事件接收器類別，而 `HandlerMethod` 是處理常式。  
  
-   COM 事件：*ReceiverClass* 是事件接收器介面，而 `HandlerMethod` 是其中一個處理常式。  
  
-   Managed 事件：*ReceiverClass* 是事件接收器類別，而 `HandlerMethod` 是處理常式。  
  
 `receiver` \(選擇性\)  
 事件接收器類別執行個體的指標。  如果您未指定接收器，則預設值是呼叫 `__hook` 所在的接收器類別或結構。  
  
## 使用方式  
 可以在事件接收器類別之外的任何函式範圍中使用，包括 main。  
  
## 備註  
 在事件接收器中使用內建函式 `__hook` 關聯或連結處理常式方法與事件方法。  然後，當來源引發指定事件時，就會呼叫指定的處理常式。  您可以將數個處理常式連結至單一事件，也可以將數個事件連結至單一處理常式。  
  
 `__hook` 有三種形式。  多數情況下，您可以使用第一種 \(四個引數\) 形式，尤其適用於 COM 事件接收器 \(其 [event\_receiver](../windows/event-receiver.md) 屬性的 *layout\_dependent* 參數為 **false**\)。  
  
 在這些情況下，您在其中一個方法引發事件之前，不需要連結介面中的所有方法；只需要連結處理該事件的方法即可。  第二種 \(兩個引數\) 形式的 `__hook` 僅適用於 *layout\_dependent***\=true** 的 COM 事件接收器。  
  
 `__hook` 會傳回長數值。  非零傳回值表示已發生錯誤 \(Managed 事件擲回例外狀況\)。  
  
 編譯器會檢查事件是否存在，以及事件簽章與委派簽章是否一致。  
  
 除了 COM 事件之外，`__hook` 和 `__unhook` 可以在事件接收器之外呼叫。  
  
 使用 `__hook` 的替代方式是使用 \+\= 運算子。  
  
 如需新語法中編碼 Managed 事件的相關資訊，請參閱 [event](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## 範例  
 如需範例，請參閱[原生 C\+\+ 中的事件處理](../cpp/event-handling-in-native-cpp.md)和 [COM 中的事件處理](../cpp/event-handling-in-com.md)。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [事件處理](../cpp/event-handling.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [\_\_raise](../cpp/raise.md)