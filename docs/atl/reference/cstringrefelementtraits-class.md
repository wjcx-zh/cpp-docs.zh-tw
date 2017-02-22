---
title: "CStringRefElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringRefElementTraits"
  - "ATL.CStringRefElementTraits"
  - "ATL::CStringRefElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringRefElementTraits class"
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CStringRefElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供靜態函式與集合類別儲存在物件中的資料相關。  字串物件處理做為參考。  
  
## 語法  
  
```  
  
      template<   
   typename T  
>  
class CStringRefElementTraits : public CElementTraitsBase< T >  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStringRefElementTraits::CompareElements](../Topic/CStringRefElementTraits::CompareElements.md)|呼叫這個靜態函式比較的兩個字串項目。|  
|[CStringRefElementTraits::CompareElementsOrdered](../Topic/CStringRefElementTraits::CompareElementsOrdered.md)|呼叫這個靜態函式比較兩個字串項目。|  
|[CStringRefElementTraits::Hash](../Topic/CStringRefElementTraits::Hash.md)|呼叫這個靜態函式計算指定資料項目的雜湊值。|  
  
## 備註  
 這個類別會提供靜態函式來比較字串來建立雜湊值。  使用時，集合類別儲存字串架構的資料，這些功能會很有用。  不同於 [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) 和 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)， `CStringRefElementTraits` 造成 `CString` 引數做為 **const CString\_&** 傳址方式傳遞。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)