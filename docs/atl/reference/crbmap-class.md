---
title: "CRBMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CRBMap"
  - "CRBMap"
  - "ATL::CRBMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBMap class"
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CRBMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用紅色粗體二進位樹狀目錄，這個類別表示對應結構，。  
  
## 語法  
  
```  
  
      template<   
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >   
> class CRBMap : public CRBTree< K, V, KTraits, VTraits >  
```  
  
#### 參數  
 `K`  
 按鍵字元型別。  
  
 *V*  
 值項目型別。  
  
 `KTraits`  
 使用的程式碼複製或移動的要素。  如需的詳細資訊請參閱 [CElementTraits 類別](../../atl/reference/celementtraits-class.md) 。  
  
 `VTraits`  
 使用的程式碼複製或移動的項目值。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRBMap::CRBMap](../Topic/CRBMap::CRBMap.md)|建構函式。|  
|[CRBMap::~CRBMap](../Topic/CRBMap::~CRBMap.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRBMap::Lookup](../Topic/CRBMap::Lookup.md)|呼叫這個方法會查閱索引鍵或值。 `CRBMap` 物件。|  
|[CRBMap::RemoveKey](../Topic/CRBMap::RemoveKey.md)|呼叫這個方法會從物件移除項目 `CRBMap` 指定關鍵值。|  
|[CRBMap::SetAt](../Topic/CRBMap::SetAt.md)|呼叫這個方法插入項目至至對應。|  
  
## 備註  
 `CRBMap` 為對應的任何指定型別的支援，管理已排序的主要項目和其關聯的值。  每個索引鍵只能有一個關聯的值。  項目 \(包含索引鍵和值\) 使用 [CRBMap::SetAt](../Topic/CRBMap::SetAt.md) 方法，在二進位樹狀目錄樹狀結構中，。  使用方法， [CRBMap::RemoveKey](../Topic/CRBMap::RemoveKey.md) 項目可移除，刪除與指定之索引鍵值的項目。  
  
 周遊樹狀結構允許以方法 \(例如、和 [CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)[CRBTree::GetNext](../Topic/CRBTree::GetNext.md)[CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)。  
  
 `KTraits` 和 `VTraits` 參數是包含必要的所有補充程式碼複製或移動項目特性類別。  
  
 `CRBMap` 從 [CRBTree](../../atl/reference/crbtree-class.md)衍生，使用紅色粗體演算法，實作二進位樹狀目錄。  [CRBMultiMap](../../atl/reference/crbmultimap-class.md) 是允許每個索引鍵的多個值的變化。  它會從 `CRBTree`也衍生自和 `CRBMap`做有許多相同的功能。  
  
 [CAtlMap](../../atl/reference/catlmap-class.md) 類別會提供兩 `CRBMap` 和 `CRBMultiMap` 的選項。  當需要儲存時只能有少數項目，請考慮使用 [CSimpleMap](../../atl/reference/csimplemap-class.md) 類別。  
  
 如需各種集合類別和其功能和效能特性的更完整的討論，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CRBTree Class](../../atl/reference/crbtree-class.md)   
 [CAtlMap Class](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap Class](../../atl/reference/crbmultimap-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)