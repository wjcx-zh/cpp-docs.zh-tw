---
title: "helpfile | Microsoft Docs"
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
  - "vc-attr.helpfile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpfile attribute"
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# helpfile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定型別程式庫的 \[說明\] 檔案名稱。  
  
## 語法  
  
```  
  
      [ helpfile(  
   "filename"  
) ]  
```  
  
#### 參數  
 *filename*  
 包含 \[說明\] 主題的檔案名稱。  
  
## 備註  
 **說明檔案** C\+\+ 屬性具有相同的功能，為 [說明檔案](http://msdn.microsoft.com/library/windows/desktop/aa366853) MIDL 屬性。  
  
## 範例  
 請參閱範例的[模組](../windows/module-cpp.md) 如需如何使用範例 **說明檔案**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface` `typedef`， **類別**，方法、 屬性|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [helpcontext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)