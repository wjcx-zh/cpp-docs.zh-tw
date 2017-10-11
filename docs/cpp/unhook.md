---
title: "__unhook |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2b1909cf5d7bde440d434bb44ff2276e68679e78
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="unhook"></a>__unhook
解除處理常式方法與事件的關聯。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 **&***SourceClass* `::` *EventMethod*  
 事件方法的指標，您會從中解除事件處理常式方法的連結：  
  
-   原生 c + + 事件： *SourceClass*是事件來源類別和*EventMethod*是事件。  
  
-   COM 事件： *SourceClass*是事件來源介面和*EventMethod*是其中一個方法。  
  
-   Managed 事件： *SourceClass*是事件來源類別和*EventMethod*是事件。  
  
 `interface`  
 從解除連結的介面名稱`receiver`，只適用於 COM 事件接收器的*layout_dependent*參數[event_receiver](../windows/event-receiver.md)屬性是**true**.  
  
 *來源*  
 事件來源執行個體的指標。 取決於程式碼`type`中所指定**event_receiver**，*來源*可以是下列其中之一：  
  
-   原生事件來源物件指標。  
  
-   **IUnknown**-基礎指標 （COM 來源）。  
  
-   Managed 物件指標 (用於 Managed 事件)。  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 要從事件中解除連結的事件處理常式方法指標。 處理常式會指定為類別的方法或類別的參考，如果您未指定類別名稱，`__unhook` 會假設類別是本身呼叫所在的類別。  
  
-   原生 c + + 事件： *ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。  
  
-   COM 事件： *ReceiverClass*是事件接收器介面和`HandlerMethod`是其中一個處理常式。  
  
-   Managed 事件： *ReceiverClass*是事件接收器類別和`HandlerMethod`是處理常式。  
  
 `receiver` (選擇性)  
 事件接收器類別執行個體的指標。 如果您未指定接收器，則預設值是呼叫 `__unhook` 所在的接收器類別或結構。  
  
## <a name="usage"></a>使用方式  
 可以在事件接收器類別之外的任何函式範圍中使用，包括 main。  
  
## <a name="remarks"></a>備註  
 在事件接收器中使用內建函式 `__unhook` 從事件方法中將處理常式方法中斷關聯或「解除連結」。  
  
 `__unhook` 有三種形式。 大部分情況下可以使用第一種 (四個引數) 形式。 `__unhook` 的第二種 (兩個引數) 形式只能用於 COM 事件接收器，這種形式會解除整個事件介面的連結。 您可以使用第三種 (單一引數) 形式從指定的來源解除所有委派的連結。  
  
 非零的傳回值表示發生錯誤 (Managed 事件將會擲回例外狀況)。  
  
 如果您在尚未連結的事件和事件處理常式上呼叫 `__unhook`，它將不會有任何作用。  
  
 在編譯時期，編譯器會驗證事件是否存在，並且對指定的處理常式進行參數類型檢查使。  
  
 除了 COM 事件之外，`__hook` 和 `__unhook` 可以在事件接收器之外呼叫。  
  
 使用 `__unhook` 的替代方式是使用 -= 運算子。  
  
 如需新語法中的 managed 的事件撰寫程式碼，請參閱[事件](../windows/event-cpp-component-extensions.md)。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="example"></a>範例  
 請參閱[原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)和[COM 中的事件處理](../cpp/event-handling-in-com.md)範例。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__raise](../cpp/raise.md)
