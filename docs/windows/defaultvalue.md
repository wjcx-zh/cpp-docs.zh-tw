---
title: "defaultvalue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.defaultvalue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "defaultvalue attribute"
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# defaultvalue
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

容許指定型別的選擇性參數的預設值。  
  
## 語法  
  
```  
  
[ defaultvalue= value ]  
```  
  
#### 參數  
 *value*  
 參數的預設值。  
  
## 備註  
 **預設值\]** C\+\+ 屬性具有相同的功能，為[預設值\]](http://msdn.microsoft.com/library/windows/desktop/aa366793) MIDL 屬性。  
  
## 範例  
 下列程式碼會顯示介面方法使用**預設值\]** 屬性：  
  
```  
// cpp_attr_ref_defaultvalue.cpp  
// compile with: /LD  
#include <windows.h>  
  
[export] typedef long HRESULT;  
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;  
  
[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),  
   dual, oleautomation,  
   helpstring("IFireTabCtrl Interface"),  
   helpcontext(122), pointer_default(unique) ]  
  
__interface IFireTabCtrl : IDispatch {  
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);  
   [bindable, propput] HRESULT put_Size([in] int nSize);  
};  
  
[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",  
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];  
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
 [out](../windows/out-cpp.md)   
 [retval](../windows/retval.md)   
 [in](../windows/in-cpp.md)   
 [pointer\_default](../windows/pointer-default.md)   
 [unique](../windows/unique-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)