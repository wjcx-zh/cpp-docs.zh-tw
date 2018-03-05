---
title: "__hook |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __hook_cpp
dev_langs:
- C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dfc9112c79279e3e5c419efbd12f5883349c0e94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hook"></a>__hook
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
  
#### <a name="parameters"></a>參數  
 **&***SourceClass* `::` *EventMethod*  
 您用於連結事件處理常式方法的事件方法指標：  
  
-   原生 c + + 事件： *SourceClass*是事件來源類別和*EventMethod*是事件。  
  
-   COM 事件： *SourceClass*是事件來源介面和*EventMethod*是其中一個方法。  
  
-   Managed 事件： *SourceClass*是事件來源類別和*EventMethod*是事件。  
  
 `interface`  
 介面名稱連結至`receiver`，只適用於 COM 事件接收器的*layout_dependent*參數[event_receiver](../windows/event-receiver.md)屬性是**true**.  
  
 *來源*  
 事件來源執行個體的指標。 取決於程式碼`type`中所指定**event_receiver**，*來源*可以是下列其中之一：  
  
-   原生事件來源物件指標。  
  
-   **IUnknown**-基礎指標 （COM 來源）。  
  
-   Managed 物件指標 (用於 Managed 事件)。  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 要連結至事件的事件處理常式方法的指標。 處理常式會指定為類別的方法或類別的參考，如果您未指定類別名稱，`__hook` 會假設類別是本身呼叫所在的類別。  
  
-   原生 c + + 事件： *ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。  
  
-   COM 事件： *ReceiverClass*是事件接收器介面和`HandlerMethod`是其中一個處理常式。  
  
-   Managed 事件： *ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。  
  
 `receiver` (選擇性)  
 事件接收器類別執行個體的指標。 如果您未指定接收器，則預設值是呼叫 `__hook` 所在的接收器類別或結構。  
  
## <a name="usage"></a>使用量  
 可以在事件接收器類別之外的任何函式範圍中使用，包括 main。  
  
## <a name="remarks"></a>備註  
 在事件接收器中使用內建函式 `__hook` 關聯或連結處理常式方法與事件方法。 然後，當來源引發指定事件時，就會呼叫指定的處理常式。 您可以將數個處理常式連結至單一事件，也可以將數個事件連結至單一處理常式。  
  
 `__hook` 有三種形式。 您可以使用第一種 （四個引數） 形式在大部分情況下，尤其適用於 COM 事件接收器的*layout_dependent*參數[event_receiver](../windows/event-receiver.md)屬性是**false**.  
  
 在這些情況下，您在其中一個方法引發事件之前，不需要連結介面中的所有方法；只需要連結處理該事件的方法即可。 您可以使用第二種 （兩個引數） 形式的`__hook`只能用於 COM 事件接收器中*layout_dependent***= true**。  
  
 `__hook` 會傳回長數值。 非零傳回值表示已發生錯誤 (Managed 事件擲回例外狀況)。  
  
 編譯器會檢查事件是否存在，以及事件簽章與委派簽章是否一致。  
  
 除了 COM 事件之外，`__hook` 和 `__unhook` 可以在事件接收器之外呼叫。  
  
 使用 `__hook` 的替代方式是使用 += 運算子。  
  
 如需新語法中的 managed 的事件撰寫程式碼，請參閱[事件](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="example"></a>範例  
 請參閱[原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件處理](../cpp/event-handling-in-com.md)範例。  
  
## <a name="see-also"></a>請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [事件處理](../cpp/event-handling.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)