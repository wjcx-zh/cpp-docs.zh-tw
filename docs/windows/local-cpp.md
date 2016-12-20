---
title: "local (C++) | Microsoft Docs"
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
  - "vc-attr.local"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "local attribute"
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# local (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介面標頭中使用時，可讓您使用 MIDL 編譯器，做標頭的產生器。  個別函式中使用時，會指定產生的任何虛設常式區域的程序。  
  
## 語法  
  
```  
  
[local]  
  
```  
  
## 備註  
 `local` C \+ \+ 屬性具有相同的功能，為[本機](http://msdn.microsoft.com/library/windows/desktop/aa367071) MIDL 屬性。  
  
## 範例  
 請參閱 [call\_as](../windows/call-as.md) 如需如何使用範例`local`。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`介面方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|**dispinterface**|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [call\_as](../windows/call-as.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)