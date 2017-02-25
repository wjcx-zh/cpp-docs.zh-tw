---
title: "CStringElementTraitsI Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CStringElementTraitsI"
  - "CStringElementTraitsI"
  - "ATL.CStringElementTraitsI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringElementTraitsI class"
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CStringElementTraitsI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供靜態函式與集合類別儲存在物件中的資料相關。  它與相似，但 [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，執行不區分大小寫的比較。  
  
## 語法  
  
```  
  
      template<  
   typename T,  
   class CharTraits = CDefaultCharTraits< T::XCHAR >  
>  
class CStringElementTraitsI : public CElementTraitsBase< T >  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CStringElementTraitsI::INARGTYPE](../Topic/CStringElementTraitsI::INARGTYPE.md)|使用的資料型別會將項目加入至集合類別物件。|  
|[CStringElementTraitsI::OUTARGTYPE](../Topic/CStringElementTraitsI::OUTARGTYPE.md)|使用資料型別來擷取項目從集合類別物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStringElementTraitsI::CompareElements](../Topic/CStringElementTraitsI::CompareElements.md)|呼叫這個靜態函式比較的兩個字串項目，忽略差異，以免。|  
|[CStringElementTraitsI::CompareElementsOrdered](../Topic/CStringElementTraitsI::CompareElementsOrdered.md)|呼叫這個靜態函式比較兩個字串項目，忽略差異，以免。|  
|[CStringElementTraitsI::Hash](../Topic/CStringElementTraitsI::Hash.md)|呼叫這個靜態函式計算指定資料項目的雜湊值。|  
  
## 備註  
 這個類別會提供靜態函式來比較字串來建立雜湊值。  使用時，集合類別儲存字串架構的資料，這些功能會很有用。  字串，當物件會得到處理做為參考時，請使用 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) 。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CStringElementTraits Class](../../atl/reference/cstringelementtraits-class.md)