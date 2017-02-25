---
title: "CRBMultiMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRBMultiMap"
  - "ATL.CRBMultiMap"
  - "ATL::CRBMultiMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBMultiMap class"
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CRBMultiMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示使用紅色粗體二進位樹狀目錄\)，讓每個索引鍵可以與多個值，這個值的對應結構。  
  
## 語法  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
> class CRBMultiMap : public CRBTree< K, V, KTraits, VTraits >  
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
|[CRBMultiMap::CRBMultiMap](../Topic/CRBMultiMap::CRBMultiMap.md)|建構函式。|  
|[CRBMultiMap::~CRBMultiMap](../Topic/CRBMultiMap::~CRBMultiMap.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRBMultiMap::FindFirstWithKey](../Topic/CRBMultiMap::FindFirstWithKey.md)|呼叫這個方法會尋找第一個項目的位置與指定索引鍵相關聯的。|  
|[CRBMultiMap::GetNextValueWithKey](../Topic/CRBMultiMap::GetNextValueWithKey.md)|呼叫這個方法會取得與相關聯的值指定機碼，並更新位置值。|  
|[CRBMultiMap::GetNextWithKey](../Topic/CRBMultiMap::GetNextWithKey.md)|呼叫這個方法會取得這個項目與指定的索引鍵，並更新位置值。|  
|[CRBMultiMap::Insert](../Topic/CRBMultiMap::Insert.md)|呼叫這個方法插入項目至至對應。|  
|[CRBMultiMap::RemoveKey](../Topic/CRBMultiMap::RemoveKey.md)|呼叫這個方法會移除任何特定索引鍵的索引鍵\/值組的項目。|  
  
## 備註  
 `CRBMultiMap` 為對應的任何指定型別的支援，管理已排序的按鍵字元和值。  不同於 [CRBMap](../../atl/reference/crbmap-class.md) 類別，每一個索引鍵可以與多個值。  
  
 項目 \(包含索引鍵和值\) 使用 [CRBMultiMap::Insert](../Topic/CRBMultiMap::Insert.md) 方法，在二進位樹狀目錄樹狀結構中，。  使用方法， [CRBMultiMap::RemoveKey](../Topic/CRBMultiMap::RemoveKey.md) 項目可移除，刪除所有項目是否符合指定的索引鍵。  
  
 周遊樹狀結構允許以方法 \(例如、和 [CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)[CRBTree::GetNext](../Topic/CRBTree::GetNext.md)[CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)。  存取可能有多個值的每個索引鍵使用 [CRBMultiMap::FindFirstWithKey](../Topic/CRBMultiMap::FindFirstWithKey.md)、 [CRBMultiMap::GetNextValueWithKey](../Topic/CRBMultiMap::GetNextValueWithKey.md)和 [CRBMultiMap::GetNextWithKey](../Topic/CRBMultiMap::GetNextWithKey.md) 方法。  為這個的圖例中 [CRBMultiMap::CRBMultiMap](../Topic/CRBMultiMap::CRBMultiMap.md) 實際上請參閱範例。  
  
 `KTraits` 和 `VTraits` 參數是包含必要的所有補充程式碼複製或移動項目特性類別。  
  
 `CRBMultiMap` 從 [CRBTree](../../atl/reference/crbtree-class.md)衍生，使用紅色粗體演算法，實作二進位樹狀目錄。  [CAtlMap](../../atl/reference/catlmap-class.md) 類別提供對 `CRBMultiMap` 和 `CRBMap` 的選項。  當需要儲存時只能有少數項目，請考慮使用 [CSimpleMap](../../atl/reference/csimplemap-class.md) 類別。  
  
 如需各種集合類別和其功能和效能特性的更完整的討論，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 繼承階層架構  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMultiMap`  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CRBTree Class](../../atl/reference/crbtree-class.md)   
 [CAtlMap Class](../../atl/reference/catlmap-class.md)   
 [CRBMap Class](../../atl/reference/crbmap-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)