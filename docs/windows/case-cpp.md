---
title: "case (C++) | Microsoft Docs"
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
  - "vc-attr.case"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "case attribute"
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# case (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

搭配 [switch\_type](../windows/switch-type.md) 屬性上**等位**。  
  
## 語法  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### 參數  
 *value*  
 可能的輸入的值，您要提供的處理作業。  哪種**值**可為下列類型之一：  
  
-   `int`  
  
-   `char`  
  
-   **boolean**  
  
-   `enum`  
  
 或者這種型別的識別項。  
  
## 備註  
 **案例** C\+\+ 屬性具有相同的功能，為 **案例** MIDL 屬性。  這個屬性並只能配合 [switch\_type](../windows/switch-type.md) 屬性。  
  
## 範例  
 下列程式碼範例將示範用法**案例**屬性：  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|成員的**類別**或`struct`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)