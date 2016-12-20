---
title: "lcid | Microsoft Docs"
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
  - "vc-attr.lcid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LCID attribute"
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lcid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可讓您傳遞至函式的地區設定識別項。  
  
## 語法  
  
```  
  
[lcid]  
  
```  
  
## 備註  
 **Lcid** C\+\+ 屬性實作的功能 [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) MIDL 屬性。  如果您想要實作的程式庫區塊的地區設定，使用 **lcid \=**`lcid`參數，以[模組](../windows/module-cpp.md)屬性。  
  
## 範例  
  
```  
// cpp_attr_ref_lcid.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
typedef long HRESULT;  
  
[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]  
__interface IStatic {  
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)