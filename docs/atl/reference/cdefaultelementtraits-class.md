---
title: "CDefaultElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDefaultElementTraits<T>"
  - "ATL.CDefaultElementTraits"
  - "ATL::CDefaultElementTraits"
  - "ATL.CDefaultElementTraits<T>"
  - "CDefaultElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultElementTraits class"
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDefaultElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供預設方法，以及集合的功能分類。  
  
## 語法  
  
```  
  
      template<  
   typename T  
>  
class CDefaultElementTraits : public CElementTraitsBase< T >,  
   public CDefaultHashTraits< T >,  
   public CDefaultCompareTraits< T >  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## 備註  
 這個類別會提供預設的靜態函式，並且移動，複製，比較和集合類別所儲存的雜湊的項目的方法。  從 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)、 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)和 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)衍生它的函式和方法和 [CElementTraits](../../atl/reference/celementtraits-class.md)、 [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)和 [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)將這個類別。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)