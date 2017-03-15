---
title: "custom (C++) | Microsoft Docs"
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
  - "vc-attr.custom"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "custom attributes, defining"
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# custom (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在型別程式庫中定義之物件的中繼資料。  
  
## 語法  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### 參數  
 *uuid*  
 唯一的 ID。  
  
 *value*  
 值，這個值可以設為 variant。  
  
## 備註  
 **自訂** C\+\+ 屬性將會造成資訊放入型別程式庫。  您將需要讀取型別程式庫中的自訂值的工具。  
  
 **自訂** 屬性具有相同的功能，為 [自訂](http://msdn.microsoft.com/library/windows/desktop/aa366766) MIDL 屬性。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|非 COM `interface`， **類別**， `enum`s， `idl_module`方法、 介面成員、 介面參數， `typedef`s， **等位**s， `struct`s|  
|**可重複**|是|  
|**必要的屬性**|**coclass** \(如果在類別上使用\)|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)