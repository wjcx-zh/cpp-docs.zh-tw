---
title: "_ATL_FUNC_INFO Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_FUNC_INFO"
  - "ATL::_ATL_FUNC_INFO"
  - "ATL._ATL_FUNC_INFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_FUNC_INFO structure"
  - "ATL_FUNC_INFO structure"
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_FUNC_INFO Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含型別用於的資訊會描述方法或屬性在分配介面。  
  
## 語法  
  
```  
  
      struct _ATL_FUNC_INFO{  
   CALLCONV cc;  
   VARTYPE vtReturn;  
   SHORT nParams;  
   VARTYPE pVarTypes[_ATL_MAX_VARTYPES];  
};  
```  
  
## Members  
 **cc**  
 呼叫慣例。  當搭配 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 類別中將這個結構中，成員必須是 **CC\_STDCALL**。  `CC_CDECL` 是 `_ATL_FUNC_INFO` 結構的 `CALLCONV` 欄位的 Windows CE 唯一支援的選項。  其他值也是不支援的其未定義的行為。  
  
 **vtReturn**  
 函式傳回值的不同型別。  
  
 **nParams**  
 函式參數的數目。  
  
 **pVarTypes**  
 陣列函式參數的不同型別。  
  
## 備註  
 在內部，使用 ATL 這個結構為 \[資訊從型別程式庫取得。  如果您提供事件處理常式來提供型別資訊所使用的 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 類別和 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md) 巨集，您可能需要直接操作此結構。  
  
## 範例  
 將在 IDL 定義分配介面 \(Dispinterface\) 方法:  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/CPP/atl-func-info-structure_1.idl)]  
  
 您可以定義一 `_ATL_FUNC_INFO` 結構:  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/CPP/atl-func-info-structure_2.h)]  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl Class](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)