---
title: "CElementTraitsBase Class | Microsoft Docs"
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
  - "CElementTraitsBase"
  - "ATL::CElementTraitsBase"
  - "ATL.CElementTraitsBase<T>"
  - "ATL::CElementTraitsBase<T>"
  - "ATL.CElementTraitsBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CElementTraitsBase class"
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CElementTraitsBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供預設的複本，並移動集合的方法。  
  
## 語法  
  
```  
  
      template<  
   typename T  
>  
class CElementTraitsBase  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CElementTraitsBase::INARGTYPE](../Topic/CElementTraitsBase::INARGTYPE.md)|使用的資料型別會將項目加入至集合類別物件。|  
|[CElementTraitsBase::OUTARGTYPE](../Topic/CElementTraitsBase::OUTARGTYPE.md)|使用資料型別來擷取項目從集合類別物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CElementTraitsBase::CopyElements](../Topic/CElementTraitsBase::CopyElements.md)|呼叫這個方法複製集合類別儲存在物件中的項目。|  
|[CElementTraitsBase::RelocateElements](../Topic/CElementTraitsBase::RelocateElements.md)|呼叫這個方法會配置在集合類別儲存在物件中的項目。|  
  
## 備註  
 這個基底類別會定義重複的方法，並在集合的重新定位項目分類。  類別會使用它 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)、 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)和 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)