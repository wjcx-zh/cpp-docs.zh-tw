---
title: "CDefaultHashTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDefaultHashTraits"
  - "ATL.CDefaultHashTraits<T>"
  - "ATL::CDefaultHashTraits<T>"
  - "ATL.CDefaultHashTraits"
  - "ATL::CDefaultHashTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultHashTraits class"
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDefaultHashTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會計算的雜湊值的靜態函式。  
  
## 語法  
  
```  
  
      template<  
   typename T  
>  
class CDefaultHashTraits  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDefaultHashTraits::Hash](../Topic/CDefaultHashTraits::Hash.md)|\(靜態\) 呼叫這個函式計算指定項目的雜湊值。|  
  
## 備註  
 這個類別包含傳回指定項目的雜湊值的單一靜態函式。  [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)將這個類別。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)