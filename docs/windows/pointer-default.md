---
title: "pointer_default | Microsoft Docs"
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
  - "vc-attr.pointer_default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointer_default attribute"
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# pointer_default
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定所有的指標，除了最上層的指標參數清單中所顯示的預設指標屬性。  
  
## 語法  
  
```  
  
      [ pointer_default(  
   value  
) ]  
```  
  
#### 參數  
 *value*  
 說明指標型別值：  **ptr**， `ref`，或**唯一**。  
  
## 備註  
 **Pointer\_default**  C\+\+ 屬性具有相同的功能，為 [pointer\_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) MIDL 屬性。  
  
## 範例  
 請參閱範例的[預設值&#93;](../windows/defaultvalue.md) 的範例使用 **pointer\_default**。  
  
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
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)