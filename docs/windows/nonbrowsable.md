---
title: "nonbrowsable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.nonbrowsable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nonbrowsable attribute"
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# nonbrowsable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示介面成員不會顯示在屬性瀏覽器。  
  
## 語法  
  
```  
  
[nonbrowsable]  
  
```  
  
## 備註  
 **Nonbrowsable** C\+\+ 屬性具有相同的功能，為 [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117) MIDL 屬性。  
  
## 範例  
  
```  
// cpp_attr_ref_nonbrowsable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, helpstring("help string"), helpstringcontext(1),   
uuid="11111111-1111-1111-1111-111111111111"]   
__interface IMyI  
{  
   [nonbrowsable] HRESULT xx();  
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