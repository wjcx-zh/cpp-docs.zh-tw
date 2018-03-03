---
title: "event_receiver |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.event_receiver
dev_langs:
- C++
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50ea26172e2f5112e760aa02d9247d07afbead2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventreceiver"></a>event_receiver
建立事件接收器 (接收)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ event_receiver(  
   type   
   [, layout_dependent=false]   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 下列其中一個值的列舉：  
  
-   `native`用於 unmanaged C/c + + 程式碼 （如原生類別的預設值）。  
  
-   COM 程式碼的`com` 。 此值需要您包含下列標頭檔︰  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **layout_dependent**  
 指定*layout_dependent*才`type` = **com**。*layout_dependent*是布林值：  
  
-   **true**表示的委派簽章在事件接收器必須完全符合目標所要攔截在事件來源。 接收器事件處理常式的名稱必須符合在相關的事件來源介面中指定的名稱。 您必須使用**coclass**時*layout_dependent*是**true**。 若要指定稍微更有效率**true**。  
  
-   **false** （預設值） 表示，呼叫慣例和儲存類別 (虛擬、 靜態等等) 不需要符合事件方法和處理常式，或是否需要將事件來源介面方法名稱比對的處理常式的名稱。  
  
## <a name="remarks"></a>備註  
 **Event_receiver** c + + 屬性指定的類別或結構要套用的都是事件接收器，使用 Visual c + + 一致的事件模型。  
  
 **event_receiver**搭配[event_source](../windows/event-source.md)屬性和[__hook](../cpp/hook.md)和[__unhook](../cpp/unhook.md)關鍵字。 使用**event_source**建立事件來源。 使用`__hook`事件接收器的方法產生關聯的事件來源的事件 （「 攔截 」） 事件接收器方法內。 使用`__unhook`中斷與它們的關聯。  
  
 *layout_dependent* ，才指定適用於 COM 事件接收器 (`type`=**com**)。 預設值為*layout_dependent*是**false**。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|**coclass**時*layout_dependent*=**，則為 true**|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [event_source](../windows/event-source.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [類別屬性](../windows/class-attributes.md)   
