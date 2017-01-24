---
title: "implements_category | Microsoft Docs"
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
  - "vc-attr.implements_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "implements_category attribute"
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# implements_category
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的目標類別所實作的元件類別。  
  
## 語法  
  
```  
  
      [ implements_category(  
   implements_category="uuid"  
) ]  
```  
  
#### 參數  
 **implements\_category**  
 已實作的類別 ID。  
  
## 備註  
 **Implements\_category** C\+\+ 屬性會指定目標類別所實作的元件類別。  這是藉由建立類別的對應，並新增個別的項目所指定的 **implements\_category** 屬性。  如需詳細資訊，請參閱[元件類別和如何執行這些工作為何?](http://msdn.microsoft.com/library/windows/desktop/ms694322).  
  
 這個屬性不能 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性 \(或另一個屬性，表示其中一種\) 也會套用到相同的項目。  如果使用任何的單一屬性時，會自動套用其他兩個。  比方說，如果 **progid** 被套用的話，  **vi\_progid** 和 **coclass** 也會套用。  
  
## 範例  
 下列程式碼會指定下列物件會實作 \[控制項\] 類別目錄。  
  
```  
// cpp_attr_ref_implements_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLib")];  
[ coclass, implements_category("CATID_Control"),  
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]  
class CMyClass {};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|是|  
|**必要的屬性**|下列其中一項：  **coclass**，  **progid**，或  **vi\_progid**|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [IMPLEMENTED\_CATEGORY](../Topic/IMPLEMENTED_CATEGORY.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)