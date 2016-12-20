---
title: "include (C++) | Microsoft Docs"
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
  - "vc-attr.include"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "include attribute"
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# include (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要包含在產生的.idl 檔中的一或多個標頭檔。  
  
## 語法  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### 參數  
 *header\_file*  
 您想要產生的.idl 檔內所包含的檔案名稱。  
  
## 備註  
 **包括** C\+\+ 屬性會造成`#include`陳述式放到以下`import "docobj.idl"`產生的.idl 檔內的陳述式。  
  
 **包括** C\+\+ 屬性具有相同的功能，為 [包括](http://msdn.microsoft.com/library/windows/desktop/aa367052) MIDL 屬性。  
  
## 範例  
 下列程式碼示範如何使用**包括**。  例如，檔案 include.h 只會包含 \# include 陳述式。  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|全螢幕輸入|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [includelib](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)