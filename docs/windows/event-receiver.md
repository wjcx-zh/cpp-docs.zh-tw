---
title: "event_receiver | Microsoft Docs"
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
  - "vc-attr.event_receiver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "event_receiver attribute"
  - "event receivers"
  - "events [C++], event receivers (sinks)"
  - "event handling [C++], attributes"
  - "event handling [C++], creating receiver"
  - "event sinks, creating"
  - "event sinks"
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# event_receiver
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立將事件接收器 \(接收\)。  
  
## 語法  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### 參數  
 `type`  
 其中一個下列值的列舉型別：  
  
-   `native`未受管理的 C\/C\+\+ 程式碼 \(原生類別的預設值\)。  
  
-   `com`COM 的程式碼。  這個值必須包含下列標頭檔：  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout\_dependent**  
 指定 *layout\_dependent* 才`type`\=**com**。  *layout\_dependent* 是布林值：  
  
-   **真**表示委派的簽章在事件接收者必須完全符合的它們所被攔截到事件來源。  事件接收者處理常式的名稱必須符合相關的事件來源介面中所指定的名稱。  您必須使用 **coclass** 時 *layout\_dependent* 是 **，則為 true**。  若要指定稍微更有效率 **，則為 true**。  
  
-   **false** \(預設值\) 表示該呼叫慣例和存放裝置的類別 \(虛擬、 靜態的等等\) 並沒有符合的事件方法與處理常式。 也不要事件來源介面的方法名稱符合需要的處理常式的名稱。  
  
## 備註  
 **Event\_receiver** C\+\+ 屬性指定之類別或結構所套用的事件接收者使用 Visual C\+\+ 統一的事件模型。  
  
 **event\_receiver** 搭配 [event\_source](../windows/event-source.md) 屬性，並 [\_\_hook](../cpp/hook.md) 和 [\_\_unhook](../cpp/unhook.md) 關鍵字。  使用 **event\_source** 來建立事件來源。  使用`__hook`事件接收者的方法產生關聯之事件的事件來源 \(「 攔截 」\) 事件接收器方法中。  使用`__unhook`以關聯它們。  
  
 *layout\_dependent* 只指定了 COM 事件接收者 \(`type`\=**com**\)。  預設值為 *layout\_dependent* 是 **，則為 false**。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|否|  
|**必要的屬性**|**coclass** 時 *layout\_dependent*\=**，則為 true**|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [event\_source](../windows/event-source.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)