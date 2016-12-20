---
title: "version (C++) | Microsoft Docs"
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
  - "vc-attr.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "version attribute"
  - "version information, version attribute"
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# version (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

識別類別的多個版本之間的特定版本。  
  
## 語法  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### 參數  
 *Version \- 版本*  
 Coclass 的版本號碼。  如果未指定，則將.idl 檔內放置 1.0。  
  
## 備註  
 **版本** C\+\+ 屬性具有相同的功能，為 [版本](http://msdn.microsoft.com/library/windows/desktop/aa367306) MIDL 屬性，並會傳遞至產生的.idl 檔。  
  
## 範例  
 請參閱[可繫結](../windows/bindable.md) 的範例用法的範例 **版本**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|否|  
|**必要的屬性**|**coclass**|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)