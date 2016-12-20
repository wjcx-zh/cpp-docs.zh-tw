---
title: "range (C++) | Microsoft Docs"
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
  - "vc-attr.range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range attribute"
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定引數，或是在 run time 設定其值的欄位的允許值的範圍。  
  
## 語法  
  
```  
  
      [ range(  
   low,   
   high  
) ]  
```  
  
#### 參數  
 *低*  
 低範圍值。  
  
 *高*  
 高範圍值。  
  
## 備註  
 **範圍** C\+\+ 屬性具有相同的功能，為 [範圍](http://msdn.microsoft.com/library/windows/desktop/aa367151) MIDL 屬性。  
  
## 範例  
  
```  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|介面方法，介面參數|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Data Member Attributes](../windows/data-member-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)