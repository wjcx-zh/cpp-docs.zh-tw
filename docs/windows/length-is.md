---
title: "length_is | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.length_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "length_is attribute"
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# length_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要傳送的陣列元素數目。  
  
## 語法  
  
```  
  
      [ length_is(  
   "expression"  
) ]  
```  
  
#### 參數  
 *expression*  
 一或多個 c 語言的運算式。  允許空白的引數的介面槽。  
  
## 備註  
 **Length\_is** C\+\+ 屬性具有相同的功能，為 [length\_is](http://msdn.microsoft.com/library/windows/desktop/aa367068) MIDL 屬性。  
  
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
 [last\_is](../windows/last-is.md)   
 [size\_is](../windows/size-is.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)