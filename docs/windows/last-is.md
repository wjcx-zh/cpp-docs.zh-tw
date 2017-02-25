---
title: "last_is | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.last_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "last_is attribute"
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# last_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要傳送的最後一個陣列元素的索引。  
  
## 語法  
  
```  
  
      [ last_is(  
   "expression"  
) ]  
```  
  
#### 參數  
 *expression*  
 一或多個 c 語言的運算式。  允許空白的引數的介面槽。  
  
## 備註  
 **Last\_is** C\+\+ 屬性具有相同的功能，為 [last\_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) MIDL 屬性。  
  
## 範例  
 請參閱 [first\_is](../windows/first-is.md) 如需如何指定陣列中的一個區段的範例。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|欄位`struct`或**等位**、 參數的介面、 介面方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [first\_is](../windows/first-is.md)   
 [max\_is](../windows/max-is.md)   
 [length\_is](../windows/length-is.md)   
 [size\_is](../windows/size-is.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)