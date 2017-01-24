---
title: "noncreatable | Microsoft Docs"
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
  - "vc-attr.noncreatable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "noncreatable attribute"
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noncreatable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義無法單獨執行個體化的物件。  
  
## 語法  
  
```  
  
[noncreatable]  
  
```  
  
## 備註  
 **變成無法建立** C\+\+ 屬性具有相同的功能，為 [變成無法建立](http://msdn.microsoft.com/library/windows/desktop/aa367118) MIDL 屬性，會自動加入產生通過。編譯器的 IDL 檔。  
  
 使用 ATL 專案中使用這個屬性時，便會變更屬性的行為。  除了上述的行為，屬性也會插入 [OBJECT\_ENTRY\_NON\_CREATEABLE\_EX\_AUTO](../Topic/OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.md) 巨集。  此巨集表示 ATL 無法從外部建立的物件。  
  
## 範例  
  
```  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
};  
```  
  
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
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)