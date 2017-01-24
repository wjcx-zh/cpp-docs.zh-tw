---
title: "helpstringdll | Microsoft Docs"
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
  - "vc-attr.helpstringdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpstringdll attribute [C++]"
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# helpstringdll
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要用來執行文件字串查閱 \(當地語系化\) 之 DLL 的名稱。  
  
## 語法  
  
```  
  
      [ helpstringdll(  
   "string"  
) ]  
```  
  
#### 參數  
 `string`  
 要用來執行文件字串查閱 DLL。  
  
## 備註  
 **Helpstringdll** C\+\+ 屬性具有相同的功能，為 [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) MIDL 屬性。  
  
## 範例  
  
```  
// cpp_attr_ref_helpstringdll.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib", helpstringdll="xx.dll")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI   
{  
   HRESULT xxx();  
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
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)