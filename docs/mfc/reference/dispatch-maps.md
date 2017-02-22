---
title: "分派對應 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "分派對應巨集"
  - "分派對應"
  - "分派對應巨集"
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 分派對應
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE Automation 的方式呼叫方法並存取跨應用程式的屬性。  這個機制由分派的這些需求 MFC 程式庫提供了為指定物件函式和屬性內部和外部名稱的「分派對應，」，以及屬性的資料型別和函式引數。  
  
### 分派對應  
  
|||  
|-|-|  
|[DECLARE\_DISPATCH\_MAP](../Topic/DECLARE_DISPATCH_MAP.md)|宣告分派對應來公開類別的方法和屬性 \(必須在類別宣告\)。|  
|[BEGIN\_DISPATCH\_MAP](../Topic/BEGIN_DISPATCH_MAP.md)|啟動分派對應的定義。|  
|[END\_DISPATCH\_MAP](../Topic/END_DISPATCH_MAP.md)|結束分派對應的定義。|  
|[DISP\_FUNCTION](../Topic/DISP_FUNCTION.md)|用來在分派對應定義 OLE Automation 函式。|  
|[DISP\_PROPERTY](../Topic/DISP_PROPERTY.md)|定義 OLE 自動化屬性。|  
|[DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md)|定義 OLE Automation 屬性並命名 Get 和 Set 函式。|  
|[DISP\_PROPERTY\_NOTIFY](../Topic/DISP_PROPERTY_NOTIFY.md)|定義與通知的 OLE 自動化屬性。|  
|[DISP\_PROPERTY\_PARAM](../Topic/DISP_PROPERTY_PARAM.md)|定義接受參數並命名 Get 和 Set 函式的 OLE 自動化屬性。|  
|[DISP\_DEFVALUE](../Topic/DISP_DEFVALUE.md)|將現有的屬性預設值的物件。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)