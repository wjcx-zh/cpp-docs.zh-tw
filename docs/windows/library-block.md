---
title: "library_block | Microsoft Docs"
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
  - "vc-attr.library_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "library_block attribute"
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# library_block
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將放置在 IDL 文件庫區塊中的建構函式。  
  
## 語法  
  
```  
  
[library_block]  
  
```  
  
## 備註  
 當您將文件庫區塊內的建構函式時，您確定它會傳遞至型別程式庫，不論是否會參考它。  只有建構修改預設的情況下，  [coclass](../windows/coclass.md)， [分配介面](../windows/dispinterface.md)，以及  [idl\_module](../windows/idl-module.md) 屬性放在文件庫區塊中。  
  
## 範例  
 下列程式碼，自訂介面放置於文件庫的區塊。  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
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
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)