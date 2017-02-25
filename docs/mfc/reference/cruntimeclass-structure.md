---
title: "CRuntimeClass Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRuntimeClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRuntimeClass structure"
  - "dynamic class information"
  - "run-time class, CRuntimeClass structure"
  - "執行階段, class information"
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CRuntimeClass Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CObject` 從衍生的每個類別與您用來取得有關物件的資訊或其基底類別在執行階段的 `CRuntimeClass` 結構。  
  
## 語法  
  
```  
struct CRuntimeClass  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRuntimeClass::CreateObject](../Topic/CRuntimeClass::CreateObject.md)|在執行階段期間，建立物件。|  
|[CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md)|使用熟悉的類別名稱，在執行階段建立物件時。|  
|[CRuntimeClass::IsDerivedFrom](../Topic/CRuntimeClass::IsDerivedFrom.md)|判斷類別是否衍生自指定的類別衍生。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRuntimeClass::m\_lpszClassName](../Topic/CRuntimeClass::m_lpszClassName.md)|類別的名稱。|  
|[CRuntimeClass::m\_nObjectSize](../Topic/CRuntimeClass::m_nObjectSize.md)|單位為位元組的物件大小。|  
|[CRuntimeClass::m\_pBaseClass](../Topic/CRuntimeClass::m_pBaseClass.md)|對基底類別的 `CRuntimeClass` 結構的指標。|  
|[CRuntimeClass::m\_pfnCreateObject](../Topic/CRuntimeClass::m_pfnCreateObject.md)|若要動態地建立物件的函式指標。|  
|[CRuntimeClass::m\_pfnGetBaseClass](../Topic/CRuntimeClass::m_pfnGetBaseClass.md)|傳回 `CRuntimeClass` 結構 \(只有，在以動態方式連結\)。|  
|[CRuntimeClass::m\_wSchema](../Topic/CRuntimeClass::m_wSchema.md)|類別的結構描述數目。|  
  
## 備註  
 `CRuntimeClass` 是結構也沒有基底類別。  
  
 可判斷物件的類別在執行階段時很有用，當函式引數的額外型別檢查需要時，或者，如果您必須將會根據物件的類別中的程式碼。  執行階段類別資訊不會直接由 C\+\+ 語言支援。  
  
 `CRuntimeClass` 在 C\+\+ 物件提供相關資訊，例如指標給基底類別和相關類別的 ASCII 類別名稱的 `CRuntimeClass` 。  這個結構也必須實作可以用來動態建立物件，指定物件的型別會使用熟悉的名稱和識別的各種功能相關類別是否從特定類別衍生。  
  
 如需使用 `CRuntimeClass`的詳細資訊，請參閱本文 [存取的執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
## 繼承階層架構  
 `CRuntimeClass`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../Topic/CObject::GetRuntimeClass.md)   
 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md)   
 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)   
 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)   
 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md)   
 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)