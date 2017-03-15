---
title: "uidefault | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.uidefault"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uidefault attribute"
ms.assetid: 200de0e0-2e34-40a2-bae4-8d485a62264d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# uidefault
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示型別資訊成員是在使用者介面中顯示的預設成員。  
  
## 語法  
  
```  
  
[uidefault]  
  
```  
  
## 備註  
 **Uidefault** C\+\+ 屬性具有相同的功能，為 [uidefault](http://msdn.microsoft.com/library/windows/desktop/aa367292) MIDL 屬性。  
  
## 範例  
 下列程式碼顯示的範例 **uidefault**：  
  
```  
// cpp_attr_ref_uidefault.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom{  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   [uidefault]HRESULT id0([in] long l);  
   [uidefault]HRESULT id1([in] long l);  
  
   [uidefault, propget] HRESULT get_y(int *y);  
   [uidefault, propput] HRESULT put_y(int y);  
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