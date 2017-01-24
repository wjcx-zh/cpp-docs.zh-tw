---
title: "switch_type | Microsoft Docs"
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
  - "vc-attr.switch_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "switch_type attribute"
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# switch_type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

識別做為聯合判別變數的型別。  
  
## 語法  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### 參數  
 `type`  
 參數類型而定，可以是整數、 字元、 布林值或列舉型別。  
  
## 備註  
 **Switch\_type** C\+\+ 屬性具有相同的功能，為 [switch\_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL 屬性。  
  
 C \+ \+ 屬性不支援[封裝的等位](http://msdn.microsoft.com/library/windows/desktop/aa366811)。  [Nonencapsulated 的等位](http://msdn.microsoft.com/library/windows/desktop/aa367119)只支援下列格式：  
  
```  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## 範例  
 請參閱[案例](../windows/case-cpp.md) 的範例用法的範例  **switch\_type**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`typedef`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)