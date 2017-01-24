---
title: "object (C++) | Microsoft Docs"
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
  - "vc-attr.object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "object attribute"
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# object (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

識別自訂介面。  
  
## 語法  
  
```  
  
[object]  
  
```  
  
## 備註  
 當之前的介面定義， **物件** C\+\+ 屬性會造成.idl 檔，做為自訂介面放到介面。  
  
 任何標示著物件的介面必須繼承自 **IUnknown**。  這種情況成立，如果您從任何基底介面繼承 **IUnknown**。  如果沒有基底介面繼承自 **IUnknown**，編譯器將會以標記介面 **物件** 為衍生自  **IUnknown**。  
  
## 範例  
 請參閱 [nonbrowsable](../windows/nonbrowsable.md) 如需如何使用範例**物件**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [dual](../windows/dual.md)   
 [dispinterface](../windows/dispinterface.md)   
 [custom](../windows/custom-cpp.md)   
 [\_\_interface](../cpp/interface.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)