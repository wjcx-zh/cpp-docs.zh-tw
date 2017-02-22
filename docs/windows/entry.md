---
title: "entry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.entry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "entry attribute"
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# entry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用來識別在 DLL 中的進入點在模組中指定的匯出函式或常數。  
  
## 語法  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### 參數  
 `id`  
 進入點的 ID。  
  
## 備註  
 **項目** C\+\+ 屬性具有相同的功能，為 [項目](http://msdn.microsoft.com/library/windows/desktop/aa366815) MIDL 屬性。  
  
## 範例  
 請參閱範例的 [idl\_module](../windows/idl-module.md) 的範例使用**項目**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`idl_module` 屬性|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)