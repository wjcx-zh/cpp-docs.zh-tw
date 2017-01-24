---
title: "__unhook | Microsoft Docs"
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
  - "__unhook"
  - "__unhook_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__unhook 關鍵字 [C++]"
  - "事件處理常式, 取消關聯事件"
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __unhook
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

解除處理常式方法與事件的關聯。  
  
## 語法  
  
```  
  
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
  
#### 參數  
 **&** *SourceClass* `::` *EventMethod*  
 事件方法的指標，您會從中解除事件處理常式方法的連結：  
  
-   原生 C\+\+ 事件：*SourceClass* 是事件來源類別，而 *EventMethod* 是事件。  
  
-   COM 事件：*SourceClass* 是事件來源介面，而 *EventMethod* 是其中一個方法。  
  
-   Managed 事件：*SourceClass* 是事件來源類別，而 *EventMethod* 是事件。  
  
 `interface`  
 要從 `receiver` 解除連結的介面名稱，僅適用其中 [event\_receiver](../windows/event-receiver.md) 屬性的 *layout\_dependent* 參數為 **true** 的 COM 事件接收器。  
  
 *source*  
 事件來源執行個體的指標。  根據 **event\_receiver** 中指定的程式碼 `type` 而定，*source* 可以是下列其中一項：  
  
-   原生事件來源物件指標。  
  
-   **IUnknown** 指標 \(COM 來源\)。  
  
-   Managed 物件指標 \(用於 Managed 事件\)。  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 要從事件中解除連結的事件處理常式方法指標。  處理常式會指定為類別的方法或類別的參考，如果您未指定類別名稱，`__unhook` 會假設類別是本身呼叫所在的類別。  
  
-   原生 C\+\+ 事件：*ReceiverClass* 是事件接收器類別，而 `HandlerMethod` 是處理常式。  
  
-   COM 事件：*ReceiverClass* 是事件接收器介面，而 `HandlerMethod` 是其中一個處理常式。  
  
-   Managed 事件：*ReceiverClass* 是事件接收器類別，而 `HandlerMethod` 是處理常式。  
  
 `receiver` \(選擇性\)  
 事件接收器類別執行個體的指標。  如果您未指定接收器，則預設值是呼叫 `__unhook` 所在的接收器類別或結構。  
  
## 使用方式  
 可以在事件接收器類別之外的任何函式範圍中使用，包括 main。  
  
## 備註  
 在事件接收器中使用內建函式 `__unhook` 從事件方法中將處理常式方法中斷關聯或「解除連結」。  
  
 `__unhook` 有三種形式。  大部分情況下可以使用第一種 \(四個引數\) 形式。  `__unhook` 的第二種 \(兩個引數\) 形式只能用於 COM 事件接收器，這種形式會解除整個事件介面的連結。  您可以使用第三種 \(單一引數\) 形式從指定的來源解除所有委派的連結。  
  
 非零的傳回值表示發生錯誤 \(Managed 事件將會擲回例外狀況\)。  
  
 如果您在尚未連結的事件和事件處理常式上呼叫 `__unhook`，它將不會有任何作用。  
  
 在編譯時期，編譯器會驗證事件是否存在，並且對指定的處理常式進行參數類型檢查使。  
  
 除了 COM 事件之外，`__hook` 和 `__unhook` 可以在事件接收器之外呼叫。  
  
 使用 `__unhook` 的替代方式是使用 \-\= 運算子。  
  
 如需新語法中編碼 Managed 事件的相關資訊，請參閱 [event](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## 範例  
 如需範例，請參閱[原生 C\+\+ 中的事件處理](../cpp/event-handling-in-native-cpp.md)和 [COM 中的事件處理](../cpp/event-handling-in-com.md)。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_raise](../cpp/raise.md)