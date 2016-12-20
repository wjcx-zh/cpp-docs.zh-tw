---
title: "CStringElementTraits Class | Microsoft Docs"
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
  - "ATL.CStringElementTraits<T>"
  - "ATL::CStringElementTraits<T>"
  - "CStringElementTraits"
  - "ATL.CStringElementTraits"
  - "ATL::CStringElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringElementTraits class"
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供集合類別使用的靜態函式 `CString` 儲存物件。  
  
## 語法  
  
```  
  
      template<  
   typename T   
>  
class CStringElementTraits  
```  
  
#### 參數  
 `T`  
 要在集合中所儲存之資料的型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CStringElementTraits::INARGTYPE](../Topic/CStringElementTraits::INARGTYPE.md)|使用的資料型別會將項目加入至集合類別物件。|  
|[CStringElementTraits::OUTARGTYPE](../Topic/CStringElementTraits::OUTARGTYPE.md)|使用資料型別來擷取項目從集合類別物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStringElementTraits::CompareElements](../Topic/CStringElementTraits::CompareElements.md)|\(靜態\) 呼叫這個函式比較的兩個字串項目。|  
|[CStringElementTraits::CompareElementsOrdered](../Topic/CStringElementTraits::CompareElementsOrdered.md)|\(靜態\) 呼叫這個函式會比較兩個字串項目。|  
|[CStringElementTraits::CopyElements](../Topic/CStringElementTraits::CopyElements.md)|\(靜態\) 呼叫這個函式會複製集合類別儲存在物件中的 `CString` 項目。|  
|[CStringElementTraits::Hash](../Topic/CStringElementTraits::Hash.md)|\(靜態\) 呼叫這個函式會計算指定資料項目的雜湊值。|  
|[CStringElementTraits::RelocateElements](../Topic/CStringElementTraits::RelocateElements.md)|\(靜態\) 呼叫這個函式重新定位在集合類別儲存在物件中的 `CString` 項目。|  
  
## 備註  
 這個類別會提供靜態函式，用於複製、移動和比較字串來建立雜湊值。  使用時，集合類別儲存字串架構的資料，這些功能會很有用。  如果需要，請使用 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) 不區分大小寫的比較。  字串，當物件要處理為參考時，請使用 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) 。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** cstringt.h  
  
## 請參閱  
 [CElementTraitsBase Class](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI Class](../../atl/reference/cstringelementtraitsi-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)