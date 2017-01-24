---
title: "satype | Microsoft Docs"
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
  - "vc-attr.satype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "satype attribute"
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# satype
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的資料型別**安全陣列時發生**結構。  
  
## 語法  
  
```  
  
      [ satype(  
   data_type  
) ]  
```  
  
#### 參數  
 *data\_type*  
 資料型別**安全陣列時發生**做為參數傳遞至某個介面方法的資料結構。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數，介面方法|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
## 備註  
 **Satype** C\+\+ 屬性指定的資料型別**安全陣列時發生**。  
  
> [!NOTE]
>  一個間接層次會從卸除**安全陣列時發生**在產生的.idl 檔案的方式在.cpp 檔中宣告的指標。  
  
## 範例  
  
```  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [id](../windows/id.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)