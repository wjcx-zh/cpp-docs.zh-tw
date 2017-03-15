---
title: "transmit_as | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.transmit_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transmit_as attribute"
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# transmit_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示編譯器將呈現的型別，用戶端和伺服器應用程式操作，相關聯的傳輸類型。  
  
## 語法  
  
```  
  
      [ transmit_as(  
   type  
) ]  
```  
  
#### 參數  
 `type`  
 指定用戶端和伺服器之間傳輸的資料型別。  
  
## 備註  
 **Transmit\_as** C\+\+ 屬性具有相同的功能，為 [transmit\_as](http://msdn.microsoft.com/library/windows/desktop/aa367286) MIDL 屬性。  
  
## 範例  
 下列程式碼範例將示範用法 **transmit\_as** 屬性：  
  
```  
// cpp_attr_ref_transmit_as.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export] typedef struct _TREE_NODE_TYPE {  
unsigned short data;   
struct _TREE_NODE_TYPE * left;  
struct _TREE_NODE_TYPE * right;   
} TREE_NODE_TYPE;  
  
[export] struct PACKED_NODE {  
   unsigned short data;   // same as normal node  
   int index;   // array index of parent  
};  
  
// A left node recursive built array of  
// the nodes in the tree.  Can be unpacked with  
// that knowledge  
[export] typedef struct _TREE_XMIT_TYPE {  
   int count;  
   [size_is(count)] PACKED_NODE node[];  
} TREE_XMIT_TYPE;  
  
[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`typedef`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)