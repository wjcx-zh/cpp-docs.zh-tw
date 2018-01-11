---
title: "event_source |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.event_source
dev_langs: C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05371b5c2d9acd091adcbdf81d2994f205e36ef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventsource"></a>event_source
建立事件來源。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ event_source(  
   type,  
   optimize=[speed | size],  
   decorate=[true | false]  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 下列其中一個值的列舉：  
  
-   Unmanaged C/C++ 程式碼的`native` (Unmanaged 類別的預設值)。  
  
-   COM 程式碼的`com` 。 您必須使用`coclass`時`type` = `com`。 此值需要您包含下列標頭檔︰  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optimize**  
 `type` 為 **native**時，您可以指定 **optimize=size**表示類別中所有事件有 4 個位元組的儲存體 (最小)，或 **optimize=speed** (預設值) 表示有 4 * (事件數目) 個位元組的儲存體。  
  
 **decorate**  
 `type` 為 **native**時，您可以指定 **decorate=false**，表示合併 (.mrg) 檔案中的展開名稱不應該包含封入類別名稱。 [/Fx](../build/reference/fx-merge-injected-code.md) 可讓您產生 .mrg 檔案。 **decorate=false**(預設值) 會產生合併檔案中的完整類型名稱。  
  
## <a name="remarks"></a>備註  
 **event_source** C++ 屬性指定要套用它的類別或結構將是事件來源。  
  
 **event_source** 是與 [event_receiver](../windows/event-receiver.md) 屬性和 [__event](../cpp/event.md) 關鍵字搭配使用。 使用 **event_receiver** 建立事件接收器。 在事件來源內的方法上使用 `__event` ，以將這些方法指定為事件。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|**type** = `type`=**com**|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [類別屬性](../windows/class-attributes.md)   
