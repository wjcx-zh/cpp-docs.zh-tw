---
title: "iid_is | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.iid_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iid_is attribute"
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# iid_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的介面指標所指向的 COM 介面的 IID。  
  
## 語法  
  
```  
  
      [ iid_is(  
   "expression"  
) ]  
```  
  
#### 參數  
 *expression*  
 指定的 COM 介面的 IID 是 c 語言運算式所指的介面指標。  
  
## 備註  
 **Iid\_is** C\+\+ 屬性具有相同的功能，為 [iid\_is](http://msdn.microsoft.com/library/windows/desktop/aa367044) MIDL 屬性。  
  
## 範例  
 下列程式碼示範如何使用 **iid\_is**：  
  
```  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|介面的參數資料成員|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)