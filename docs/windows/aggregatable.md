---
title: "aggregatable | Microsoft Docs"
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
  - "vc-attr.aggregatable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregatable attribute"
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# aggregatable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示此類別支援彙總。  
  
## 語法  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### 參數  
 *值* \(可省略\)  
 參數，以指出 COM 物件可以彙總：  
  
-   **永遠不會**的 COM 物件無法彙總。  
  
-   **允許**可直接建立的 COM 物件，或可彙總。  這是預設值。  
  
-   **總是**的 COM 物件不能直接建立，並只可彙總。  當您呼叫`CoCreateInstance`對此物件中，您必須指定彙總物件的 **IUnknown** 介面 \(控制 **IUnknown**\)。  
  
## 備註  
 **可集成** C\+\+ 屬性具有相同的功能，為 [可集成](http://msdn.microsoft.com/library/windows/desktop/aa366721) MIDL 屬性。  這表示編譯器會將傳遞**可集成**透過屬性設定為產生的.idl 檔。  
  
 這個屬性不能 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性 \(或另一個屬性，表示其中一種\) 也會套用到相同的項目。  如果使用任何的單一屬性時，會自動套用其他兩個。  比方說，如果 **progid** 被套用的話，  **vi\_progid** 和 **coclass** 也會套用。  
  
 **ATL 專案**  
  
 如果使用 ATL 專案中使用這個屬性，屬性的行為就會變更。  除了先前所說明的行為，屬性也會將加入下列的巨集的其中一個目標類別：  
  
|參數值|插入的巨集|  
|---------|-----------|  
|**永不**|[DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)|  
|**允許**|[DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)|  
|**永遠**|[DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)|  
  
## 範例  
  
```  
// cpp_attr_ref_aggregatable.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="MyModule")];  
  
[ coclass, aggregatable(allowed),  
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]  
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
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Aggregation](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)