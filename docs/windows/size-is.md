---
title: "size_is | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.size_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_is attribute"
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# size_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的記憶體大小配置大小的指標、 調整大小來調整大小的指標，以及單或多維陣列的指標。  
  
## 語法  
  
```  
  
      [ size_is(  
   "expression"  
) ]  
```  
  
#### 參數  
 *expression*  
 調整大小的指標配置的記憶體大小。  
  
## 備註  
 **Size\_is** C\+\+ 屬性具有相同的功能，為 [size\_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) MIDL 屬性。  
  
## 範例  
 請參閱範例的 [first\_is](../windows/first-is.md) 的方式來指定陣列中的一個區段的範例。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|欄位`struct`或**等位**、 參數的介面、 介面方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|**max\_is**|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [first\_is](../windows/first-is.md)   
 [last\_is](../windows/last-is.md)   
 [max\_is](../windows/max-is.md)   
 [length\_is](../windows/length-is.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)