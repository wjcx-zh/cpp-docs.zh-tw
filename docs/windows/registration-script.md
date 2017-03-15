---
title: "registration_script | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.registration_script"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registration_script attribute"
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# registration_script
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行指定的自訂註冊指令碼。  
  
## 語法  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### 參數  
 *script*  
 自訂註冊指令碼 \(.rgs\) 檔案的完整路徑。  值為**無**，例如`script = "none"`，表示 coclass 有沒有註冊的需求。  
  
## 備註  
 **Registration\_script** C\+\+ 屬性執行自訂的註冊指令碼所指定的**指令碼**。  如果未指定這個屬性，則會使用標準的.rgs 檔案 \(包含的元件登錄資訊\)。  如需有關.rgs 檔案的詳細資訊，請參閱[的 ATL 登錄元件 \(域名註冊商\)](../atl/atl-registry-component-registrar.md)。  
  
 這個屬性不能 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性 \(或另一個屬性，表示其中一種\) 也會套用到相同的項目。  
  
## 範例  
 下列程式碼會指定元件有一個稱為 cpp\_attr\_ref\_registration\_script.rgs 的登錄指令碼。  
  
```  
// cpp_attr_ref_registration_script.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="REG")];  
  
[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]  
__interface IFace {};  
  
// requires "cpp_attr_ref_registration_script.rgs"  
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist  
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),  
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]  
class CMyClass:public IFace {};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|否|  
|**必要的屬性**|一或多項動作：  **coclass**，  **progid**，或  **vi\_progid**。|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [rdx](../windows/rdx.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)