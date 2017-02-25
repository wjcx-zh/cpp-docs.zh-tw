---
title: "bindable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.bindable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bindable attribute"
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# bindable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示屬性支援資料繫結。  
  
## 語法  
  
```  
  
[bindable]  
  
```  
  
## 備註  
 **可繫結** C\+\+ 屬性具有相同的功能，為 [可繫結](http://msdn.microsoft.com/library/windows/desktop/aa366738) MIDL 屬性。  您可以將屬性定義為 [propget 而言](../windows/propget.md)，  [propput](../windows/propput.md)，或  [propputref](../windows/propputref.md) 屬性，或者您可以手動定義可繫結的方法。  
  
 下列的 MFC 範例顯示使用**可繫結**：  
  
-   [控制項的範例： 以 MFC 為基礎的 ActiveX 控制項](http://msdn.microsoft.com/zh-tw/a44adf86-0ba0-4504-bedb-512b6cba2e63)  
  
-   [CIRC 範例：ActiveX 控制項](http://msdn.microsoft.com/zh-tw/9ba34d04-280e-49f4-90ae-41a6be44c95b)  
  
-   [TESTHELP 範例：擁有工具提示和說明的 ActiveX 控制項](http://msdn.microsoft.com/zh-tw/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)  
  
## 範例  
 下列程式碼將示範如何使用**可繫結**屬性：  
  
```  
// cpp_attr_ref_bindable.cpp  
// compile with: /LD  
#include <windows.h>  
[  
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),  
   dispinterface,  
   helpstring("property demo Interface")  
]  
__interface IPropDemo : IDispatch {  
  
   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);  
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);  
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);     
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();  
};  
  
[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];  
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
 [defaultbind](../windows/defaultbind.md)   
 [displaybind](../windows/displaybind.md)   
 [immediatebind](../windows/immediatebind.md)   
 [requestedit](../windows/requestedit.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)