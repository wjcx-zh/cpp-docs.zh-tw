---
title: "vararg | Microsoft Docs"
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
  - "vc-attr.vararg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vararg attribute"
ms.assetid: 20fc3244-18e9-411c-990e-d5b4fa29a570
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vararg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定函式接收不定個數的引數。  
  
## 語法  
  
```  
  
[vararg]  
  
```  
  
## 備註  
 **Vararg**  C\+\+ 屬性具有相同的功能，為 [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) MIDL 屬性。  
  
## 範例  
 下列程式碼範例將示範用法 **vararg**：  
  
```  
// cpp_attr_ref_vararg.cpp  
// compile with: /LD  
#include "unknwn.h"  
#include "oaidl.h"  
[module(name="MyLibrary")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface X : public IUnknown   
{  
   [vararg] HRESULT Button([in, satype(VARIANT)]SAFEARRAY *psa);  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|介面方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)