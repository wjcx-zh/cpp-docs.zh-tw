---
title: "async_uuid | Microsoft Docs"
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
  - "vc-attr.async_uuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "async_uuid attribute"
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# async_uuid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定指示 MIDL 編譯器，將定義 COM 介面的同步和非同步版本的 UUID。  
  
## 語法  
  
```  
  
      [async_uuid (  
   uuid  
)]  
```  
  
#### 參數  
 *uuid*  
 UUID，識別介面的版本。  
  
## 備註  
 **Async\_uuid** C\+\+ 屬性具有相同的功能，為 [async\_uuid](http://msdn.microsoft.com/library/windows/desktop/aa366735) MIDL 屬性。  
  
## 範例  
  
```  
// cpp_attr_ref_async_uuid.cpp  
// compile with: /LD  
#include <Windows.h>  
[module(name="Test")];  
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),   
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|**雙重**， **分配介面**|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)