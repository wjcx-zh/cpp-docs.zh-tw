---
title: "source (C++) | Microsoft Docs"
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
  - "vc-attr.source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source attribute"
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# source (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在類別上指定的連接點的 COM 物件的來源介面。  在屬性或方法中，指出成員傳回一個物件或 VARIANT 是一個事件的來源。  
  
## 語法  
  
```  
  
      [ source(  
   interfaces  
) ]  
```  
  
#### 參數  
 `interfaces`  
 一或多個介面您可指定當您套用的來源屬性至類別。  未在原始檔套用至屬性或方法時，會使用這個參數。  
  
## 備註  
 **來源** C\+\+ 屬性具有相同的功能，為 [來源](http://msdn.microsoft.com/library/windows/desktop/aa367166) MIDL 屬性。  
  
 您可以使用[預設](../windows/default-cpp.md)屬性來指定物件的預設值來源介面。  
  
## 範例  
  
```  
// cpp_attr_ref_source.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]  
   HRESULT get_I([out, retval]long *i);  
};  
  
[object, uuid(11111111-1111-1111-1111-111111111131)]  
__interface c  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]   
   HRESULT et_I([out, retval]long *i);  
};  
  
[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]  
class N : public b  
{  
};  
  
[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]  
class NN : public b  
{  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**, `struct`,`interface`|  
|**可重複**|否|  
|**必要的屬性**|**coclass** \(當套用到類別或結構\)|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [coclass](../windows/coclass.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)