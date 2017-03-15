---
title: "synchronize | Microsoft Docs"
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
  - "vc-attr.synchronize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "synchronize attribute"
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# synchronize
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步處理對目標方法的存取。  
  
## 語法  
  
```  
  
[synchronize]  
  
```  
  
## 備註  
 **同步處理** C\+\+ 屬性實作同步處理物件的目標方法的支援。  同步處理控制目標方法的存取，以允許使用一般的資源 \(例如類別的方法\) 的多個物件。  
  
 這個屬性所插入的程式碼會呼叫適當的`Lock` \(由執行緒模型\) 的目標方法的開頭的方法。  當方法結束時， `Unlock`會自動呼叫。  如需有關這些函式的詳細資訊，請參閱 [CComAutoThreadModule::Lock](../Topic/CComAutoThreadModule::Lock.md)  
  
 這個屬性不能 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性 \(或另一個屬性，表示其中一種\) 也會套用到相同的項目。  如果使用任何的單一屬性時，會自動套用其他兩個。  比方說，如果 **progid** 被套用的話，  **vi\_progid** 和 **coclass** 也會套用。  
  
## 範例  
 下列程式碼提供同步處理`UpdateBalance`方法的`CMyClass`物件。  
  
```  
// cpp_attr_ref_synchronize.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="SYNC")];  
  
[coclass,  
 threading(both),  
 vi_progid("MyProject.MyClass"),  
 progid("MyProject.MyClass.1"),  
 uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]  
class CMyClass {  
   float m_nBalance;  
  
   [synchronize]  
   void UpdateBalance(float nAdjust) {  
      m_nBalance += nAdjust;  
   }  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|類別方法方法|  
|**可重複**|否|  
|**必要的屬性**|一或多項動作：  **coclass**，  **progid**，或  **vi\_progid**。|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)