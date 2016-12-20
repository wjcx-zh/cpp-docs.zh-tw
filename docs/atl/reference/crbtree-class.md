---
title: "CRBTree Class | Microsoft Docs"
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
  - "ATL.CRBTree"
  - "CRBTree"
  - "ATL::CRBTree"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRBTree class"
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRBTree Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別以建立和執行以紅色黑色樹狀結構的方法。  
  
## 語法  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
> class CRBTree  
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
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CRBTree::KINARGTYPE](../Topic/CRBTree::KINARGTYPE.md)|輸入使用索引鍵時傳遞做為輸入引數。|  
|[CRBTree::KOUTARGTYPE](../Topic/CRBTree::KOUTARGTYPE.md)|使用的型別，當索引鍵會傳回當做輸出引數。|  
|[CRBTree::VINARGTYPE](../Topic/CRBTree::VINARGTYPE.md)|使用的型別時，值就會當做輸入引數。|  
|[CRBTree::VOUTARGTYPE](../Topic/CRBTree::VOUTARGTYPE.md)|使用的型別時，值就會當做輸出引數。|  
  
### 公用類別  
  
|名稱|描述|  
|--------|--------|  
|[CRBTree::CPair Class](../Topic/CRBTree::CPair%20Class.md)|包含索引鍵和值的項目的類別。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRBTree::~CRBTree](../Topic/CRBTree::~CRBTree.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRBTree::FindFirstKeyAfter](../Topic/CRBTree::FindFirstKeyAfter.md)|呼叫這個方法會尋找使用下一個可用的索引鍵之項目的位置。|  
|[CRBTree::GetAt](../Topic/CRBTree::GetAt.md)|呼叫這個方法會取得這個項目在樹狀目錄中的指定位置。|  
|[CRBTree::GetCount](../Topic/CRBTree::GetCount.md)|呼叫這個方法會取得項目數目的樹狀結構。|  
|[CRBTree::GetHeadPosition](../Topic/CRBTree::GetHeadPosition.md)|呼叫這個方法會取得這個項目的位置值在樹狀目錄的開頭。|  
|[CRBTree::GetKeyAt](../Topic/CRBTree::GetKeyAt.md)|呼叫這個方法會從樹狀目錄中的指定位置取得索引鍵。|  
|[CRBTree::GetNext](../Topic/CRBTree::GetNext.md)|呼叫這個方法以取得指向在 `CRBTree` 物件中的項目，並將讀取這個位置為下一個項目。|  
|[CRBTree::GetNextAssoc](../Topic/CRBTree::GetNextAssoc.md)|呼叫這個方法會取得在對應中所儲存之項目的索引鍵和值與這個位置前移至下一個項目。|  
|[CRBTree::GetNextKey](../Topic/CRBTree::GetNextKey.md)|呼叫這個方法會取得在樹狀結構中之項目的索引鍵和這個位置前移至下一個項目。|  
|[CRBTree::GetNextValue](../Topic/CRBTree::GetNextValue.md)|呼叫這個方法會取得在樹狀目錄中儲存的元素值和進階這個位置為下一個項目。|  
|[CRBTree::GetPrev](../Topic/CRBTree::GetPrev.md)|呼叫這個方法以取得指向在 `CRBTree` 物件中的項目，然後更新這個位置對應至上一個項目。|  
|[CRBTree::GetTailPosition](../Topic/CRBTree::GetTailPosition.md)|呼叫這個方法可取得項目的位置值樹狀目錄的尾端。|  
|[CRBTree::GetValueAt](../Topic/CRBTree::GetValueAt.md)|呼叫這個方法會擷取值儲存在 `CRBTree` 物件的指定位置。|  
|[CRBTree::IsEmpty](../Topic/CRBTree::IsEmpty.md)|呼叫這個方法測試是否為空的樹狀結構物件。|  
|[CRBTree::RemoveAll](../Topic/CRBTree::RemoveAll.md)|呼叫這個方法會從 **CRBTree** 物件移除所有項目。|  
|[CRBTree::RemoveAt](../Topic/CRBTree::RemoveAt.md)|呼叫這個方法會移除這個項目是在 **CRBTree** 物件的指定位置。|  
|[CRBTree::SetValueAt](../Topic/CRBTree::SetValueAt.md)|呼叫這個方法會將值儲存在 `CRBTree` 物件的指定位置。|  
  
## 備註  
 而紅色黑色樹狀結構是使用額外的資訊可確保每個節點的二進位樹狀結構會維持「平衡」，也就是樹狀高度不增加不均衡地大並不會影響效能。  
  
 這個範本類別是設計來供 [CRBMap](../../atl/reference/crbmap-class.md) 和 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)使用。  構成這些衍生類別 `CRBTree`提供的大部分方法。  
  
 如需各種集合類別和其功能和效能特性的更完整的討論，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)