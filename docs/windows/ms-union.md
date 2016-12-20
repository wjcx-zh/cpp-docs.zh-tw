---
title: "ms_union | Microsoft Docs"
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
  - "vc-attr.ms_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ms_union attribute"
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ms_union
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制網路資料表示對齊，nonencapsulated 的聯集。  
  
## 語法  
  
```  
  
[ms_union]  
  
```  
  
## 備註  
 **Ms\_union** C\+\+ 屬性具有相同的功能，為 [ms\_union](http://msdn.microsoft.com/library/windows/desktop/aa367100) MIDL 屬性。  
  
## 範例  
 下列程式碼顯示的位置 **ms\_union**：  
  
```  
// cpp_attr_ref_ms_union.cpp  
// compile with: /LD  
#include <unknwn.h>  
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl {  
   HRESULT DisplayString([in, string] char * p1);  
};  
  
[export, switch_type(short)] union _WILLIE_UNION_TYPE  {  
   [case(24)]  
      float fMays;  
   [case(25)]  
      double dMcCovey;  
   [default]  
      int x;  
 };  
  
[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;  
  
[module(name="ATLFIRELib")];  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|Nonencapsulated 的等位|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|**dispinterface**|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)