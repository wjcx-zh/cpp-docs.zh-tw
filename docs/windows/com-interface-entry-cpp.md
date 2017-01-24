---
title: "com_interface_entry (C++) | Microsoft Docs"
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
  - "vc-attr.com_interface_entry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "com_interface_entry attribute"
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# com_interface_entry (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

新增到目標類別的 COM 對應的介面項目。  
  
## 語法  
  
```  
  
     [ com_interface_entry(   
  com_interface_entry  
) ]  
```  
  
#### 參數  
 *com\_interface\_entry*  
 字串，包含項目的實際的文字。  如需可能值的清單，請參閱 [COM\_INTERFACE\_ENTRY 巨集](../Topic/COM_INTERFACE_ENTRY%20Macros.md)。  
  
## 備註  
 `com_interface_entry` C \+ \+ 屬性插入的目標物件的 COM 介面對應的字元字串的完整的內容。  如果這個屬性套用至目標物件的一次，項目插入現有的介面對應的開頭。  如果屬性重複套用相同的目標物件，這些項目會插入介面對應已接收順序的開頭。  
  
 這個屬性不能 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性 \(或另一個屬性，表示其中一種\) 也會套用到相同的項目。  如果使用任何的單一屬性時，會自動套用其他兩個。  比方說，如果 **progid** 被套用的話，  **vi\_progid** 和 **coclass** 也會套用。  
  
 因為第一個的使用方式的`com_interface_entry`會使新的介面的介面對應，開頭插入它必須是下列的 COM\_INTERFACE\_ENTRY 類型其中一項：  
  
-   COM\_INTERFACE\_ENTRY  
  
-   COM\_INTERFACE\_ENTRY\_IID  
  
-   COM\_INTERFACE\_ENTRY2  
  
-   COM\_INTERFACE\_ENTRY2\_IID  
  
 額外的使用方式的`com_interface_entry`屬性可以使用所有支援的 COM\_INTERFACE\_ENTRY 型別。  
  
 這項限制是必要的因為 ATL 使用介面對應中第一個項目，做為 **IUnknown**。 因此，此項目必須是有效的介面。  比方說下, 面的程式碼不正確，因為介面對應中的第一個項目不會指定實際的 COM 介面。  
  
```  
[ coclass, com_interface_entry =  
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"  
]  
   class CMyClass  
   {  
   };  
```  
  
## 範例  
 下列程式碼會將兩個項目加入至現有的 COM 介面對應的 **CMyBaseClass**。  第一種是標準的介面，並隱藏第二個 **IDebugTest** 介面。  
  
```  
// cpp_attr_ref_com_interface_entry.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name ="ldld")];  
  
[ object,  
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]  
__interface IDebugTest{};  
  
[ object,  
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]  
__interface IMyClass{};  
  
[ coclass,  
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),  
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),  
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")  
]  
  
class CMyClass: public IMyClass, public IDebugTest  
{  
};  
```  
  
 產生的 COM 物件對應的 **CMyBaseClass** 如下：  
  
```  
BEGIN_COM_MAP(CMyClass)  
    COM_INTERFACE_ENTRY (IMyClass)  
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)  
    COM_INTERFACE_ENTRY(IMyClass)  
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)  
    COM_INTERFACE_ENTRY(IDebugTest)  
    COM_INTERFACE_ENTRY(IProvideClassInfo)  
END_COM_MAP()  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|是|  
|**必要的屬性**|一或多項動作：  **coclass**，  **progid**，或  **vi\_progid**。|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)