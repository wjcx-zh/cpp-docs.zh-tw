---
title: "CDefaultCompareTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CDefaultCompareTraits<T>"
  - "ATL::CDefaultCompareTraits"
  - "ATL.CDefaultCompareTraits"
  - "ATL::CDefaultCompareTraits<T>"
  - "CDefaultCompareTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultCompareTraits class"
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDefaultCompareTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供預設項目比較函式。  
  
## 語法  
  
```  
  
      template<  
   typename T  
>  
class CDefaultCompareTraits  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDefaultCompareTraits::CompareElements](../Topic/CDefaultCompareTraits::CompareElements.md)|\(靜態\) 呼叫這個函式比較的兩個項目。|  
|[CDefaultCompareTraits::CompareElementsOrdered](../Topic/CDefaultCompareTraits::CompareElementsOrdered.md)|\(靜態\) 呼叫此函式以判斷大於和 ACE 項目。|  
  
## 備註  
 這個類別包含比較的集合類別物件中項目的兩個靜態函式。  [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)將這個類別。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)