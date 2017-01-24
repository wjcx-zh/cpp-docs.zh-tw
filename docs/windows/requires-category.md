---
title: "requires_category | Microsoft Docs"
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
  - "vc-attr.requires_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "requires_category attribute"
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# requires_category
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定目標類別所需的元件類別的目錄。  
  
## 語法  
  
```  
  
     [ requires_category(   
  requires_category  
) ]  
```  
  
#### 參數  
 *requires\_category*  
 「 必要 」 分類 ID。  
  
## 備註  
 **Requires\_category** C\+\+ 屬性會指定目標類別所需要的元件類別。  如需詳細資訊，請參閱 [REQUIRED\_CATEGORY](../Topic/REQUIRED_CATEGORY.md)。  
  
 這個屬性不能 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性 \(或另一個屬性，表示其中一種\) 也會套用到相同的項目。  
  
## 範例  
 下列程式碼所需的物件實作控制的類別。  
  
```  
// cpp_attr_ref_requires_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLibrary")];  
  
[ coclass, requires_category("CATID_Control"),  
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]  
class CMyClass {};  
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
 [implements\_category](../windows/implements-category.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)