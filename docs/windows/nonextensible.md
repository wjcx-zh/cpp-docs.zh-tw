---
title: "nonextensible | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.nonextensible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nonextensible attribute"
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# nonextensible
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的`IDispatch`實作包括僅屬性以及方法介面描述中所列，並不能與其他成員在執行階段擴充。  
  
## 語法  
  
```  
  
[nonextensible]  
  
```  
  
## 備註  
 **Nonextensible** C\+\+ 屬性具有相同的功能，為 [nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) MIDL 屬性。  
  
 使用 **nonextensible** 也需要 [oleautomation](../windows/oleautomation.md) 屬性。  
  
## 範例  
 下列程式碼範例將示範一個用法 **nonextensible** 屬性：  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`|  
|**可重複**|否|  
|**必要的屬性**|**雙重** 和  **oleautomation**，或 **分配介面**|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)