---
title: "helpstringcontext | Microsoft Docs"
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
  - "vc-attr.helpstringcontext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpstringcontext attribute [C++]"
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# helpstringcontext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定.hlp 或.chm 檔中的 \[說明\] 主題的識別碼。  
  
## 語法  
  
```  
  
      [ helpstringcontext(  
   contextID  
) ]  
```  
  
#### 參數  
 `contextID`  
 在 \[說明\] 檔案 32 位元說明主題代碼。  
  
## 備註  
 **Helpstringcontext** C\+\+ 屬性具有相同的功能，為 [helpstringcontext](http://msdn.microsoft.com/library/windows/desktop/aa366858) ODL 屬性。  
  
## 範例  
  
```  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**， `interface`，介面方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [module](../windows/module-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)