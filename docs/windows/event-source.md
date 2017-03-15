---
title: "event_source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.event_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件處理, 屬性"
  - "事件記錄檔, 事件來源"
  - "事件來源, 建立"
  - "event_source 屬性"
  - "事件來源"
  - "事件處理, 建立事件來源"
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# event_source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立事件來源。  
  
## 語法  
  
```  
  
       [ event_source(  
       type,  
optimize=[speed | size],  
decorate=[true | false]) ]  
```  
  
#### 參數  
 `type`  
 下列其中一個值的列舉：  
  
-   Unmanaged C\/C\+\+ 程式碼的 `native` \(Unmanaged 類別的預設值\)。  
  
-   COM 程式碼的 `com`。`type`\=`com` 時，您必須使用 `coclass`。 此值需要您包含下列標頭檔︰  
  
    ```  
    #define _ATL_ATTRIBUTES  
    #include <atlbase.h>  
    #include <atlcom.h>  
    ```  
  
 **optimize**  
 `type` 為 **native** 時，您可以指定 **optimize\=size** 表示類別中所有事件有 4 個位元組的儲存體 \(最小\)，或 **optimize\=speed** \(預設值\) 表示有 4 \* \(事件數目\) 個位元組的儲存體。  
  
 **decorate**  
 `type` 為 **native** 時，您可以指定 **decorate\=false**，表示合併 \(.mrg\) 檔案中的展開名稱不應該包含封入類別名稱。[\/Fx](../build/reference/fx-merge-injected-code.md) 可讓您產生 .mrg 檔案。**decorate\=false** \(預設值\) 會產生合併檔案中的完整類型名稱。  
  
## 備註  
 **event\_source** C\+\+ 屬性指定要套用它的類別或結構將是事件來源。  
  
 **event\_source** 是與 [event\_receiver](../windows/event-receiver.md) 屬性和 [\_\_event](../cpp/event.md) 關鍵字搭配使用。 使用 **event\_receiver** 建立事件接收器。 在事件來源內的方法上使用 `__event`，以將這些方法指定為事件。  
  
> [!NOTE]
>  樣板類別或結構不能包含事件。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、`struct`|  
|**可重複**|否|  
|**必要屬性**|**coclass** \(`type`\=**com** 時\)|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)