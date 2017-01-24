---
title: "helpstring | Microsoft Docs"
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
  - "vc-attr.helpstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpstring attribute [C++]"
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# helpstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定用來描述所套用之項目的字元字串，  
  
## 語法  
  
```  
  
      [ helpstring(  
   "string"  
) ]  
```  
  
#### 參數  
 `string`  
 說明字串的文字。  
  
## 備註  
 **Helpstring** C\+\+ 屬性具有相同的功能，為 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) MIDL 屬性。  
  
## 範例  
 請參閱範例的[預設值&#93;](../windows/defaultvalue.md) 如需如何使用範例 **helpstring**。  
  
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
 [helpcontext](../windows/helpcontext.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)