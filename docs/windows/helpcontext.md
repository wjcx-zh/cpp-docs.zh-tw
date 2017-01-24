---
title: "helpcontext | Microsoft Docs"
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
  - "vc-attr.helpcontext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpcontext attribute"
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# helpcontext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的主題代碼，可讓使用者檢視此說明檔中的項目相關的資訊。  
  
## 語法  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### 參數  
 `id`  
 \[說明\] 主題的內文識別碼。  請參閱[HTML 說明：程式的即時線上說明](../mfc/html-help-context-sensitive-help-for-your-programs.md)如需詳細資訊，用於內文識別碼。  
  
## 備註  
 **Helpcontext** C\+\+ 屬性具有相同的功能，為 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) MIDL 屬性。  
  
## 範例  
 請參閱範例的[預設值&#93;](../windows/defaultvalue.md) 如需如何使用範例 **helpcontext**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface` `typedef`， **類別**，方法、 屬性|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [helpfile](../windows/helpfile.md)   
 [helpstring](../windows/helpstring.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)