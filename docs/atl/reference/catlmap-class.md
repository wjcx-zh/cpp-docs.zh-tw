---
title: "CAtlMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlMap"
  - "CAtlMap"
  - "ATL::CAtlMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlMap class"
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAtlMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立和管理對應物件的方法。  
  
## 語法  
  
```  
  
      template<  
   typename K,  
   typename V,  
   class KTraits = CElementTraits< K >,  
   class VTraits = CElementTraits< V >  
>  
class CAtlMap  
```  
  
#### 參數  
 `K`  
 按鍵字元型別。  
  
 V  
 值項目型別。  
  
 `KTraits`  
 使用的程式碼複製或移動的要素。  如需的詳細資訊請參閱 [CElementTraits 類別](../../atl/reference/celementtraits-class.md) 。  
  
 `VTraits`  
 使用的程式碼複製或移動的項目值。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CAtlMap::KINARGTYPE](../Topic/CAtlMap::KINARGTYPE.md)|使用的型別，當金鑰傳遞做為輸入引數|  
|[CAtlMap::KOUTARGTYPE](../Topic/CAtlMap::KOUTARGTYPE.md)|使用的型別，當索引鍵會傳回當做輸出引數。|  
|[CAtlMap::VINARGTYPE](../Topic/CAtlMap::VINARGTYPE.md)|使用的型別時，值就會當做輸入引數。|  
|[CAtlMap::VOUTARGTYPE](../Topic/CAtlMap::VOUTARGTYPE.md)|使用的型別時，值就會當做輸出引數。|  
  
### 公用類別  
  
|名稱|描述|  
|--------|--------|  
|[CAtlMap::CPair Class](../Topic/CAtlMap::CPair%20Class.md)|包含索引鍵和值的項目的類別。|  
  
### CPair 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPair::m\_key](../Topic/CAtlMap::CPair::m_key.md)|儲存金鑰字元的資料成員。|  
|[CPair::m\_value](../Topic/CAtlMap::CPair::m_value.md)|將值儲存項目的資料成員。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlMap::CAtlMap](../Topic/CAtlMap::CAtlMap.md)|建構函式。|  
|[CAtlMap::~CAtlMap](../Topic/CAtlMap::~CAtlMap.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlMap::AssertValid](../Topic/CAtlMap::AssertValid.md)|呼叫這個方法會判斷提示 `CAtlMap` 是否無效。|  
|[CAtlMap::DisableAutoRehash](../Topic/CAtlMap::DisableAutoRehash.md)|呼叫這個方法會停用自動重新複合 `CAtlMap` 物件。|  
|[CAtlMap::EnableAutoRehash](../Topic/CAtlMap::EnableAutoRehash.md)|呼叫這個方法會啟用自動重新複合 `CAtlMap` 物件。|  
|[CAtlMap::GetAt](../Topic/CAtlMap::GetAt.md)|呼叫這個方法會傳回這個項目是在對應中指定的位置。|  
|[CAtlMap::GetCount](../Topic/CAtlMap::GetCount.md)|呼叫這個方法會擷取項目數目對應的。|  
|[CAtlMap::GetHashTableSize](../Topic/CAtlMap::GetHashTableSize.md)|呼叫這個方法會設定容器的數目對應的雜湊資料表中。|  
|[CAtlMap::GetKeyAt](../Topic/CAtlMap::GetKeyAt.md)|呼叫這個方法會擷取金鑰儲存在 `CAtlMap` 物件的指定位置。|  
|[CAtlMap::GetNext](../Topic/CAtlMap::GetNext.md)|呼叫這個方法以取得指向在 `CAtlMap` 物件中的下一個項目為。|  
|[CAtlMap::GetNextAssoc](../Topic/CAtlMap::GetNextAssoc.md)|取得可逐一查看的下一個項目。|  
|[CAtlMap::GetNextKey](../Topic/CAtlMap::GetNextKey.md)|呼叫這個方法會從物件擷取 `CAtlMap` 下的機碼。|  
|[CAtlMap::GetNextValue](../Topic/CAtlMap::GetNextValue.md)|呼叫這個方法會從 `CAtlMap` 物件取得下一個值。|  
|[CAtlMap::GetStartPosition](../Topic/CAtlMap::GetStartPosition.md)|呼叫這個方法會啟動對應反覆項目。|  
|[CAtlMap::GetValueAt](../Topic/CAtlMap::GetValueAt.md)|呼叫這個方法會擷取值儲存在 `CAtlMap` 物件的指定位置。|  
|[CAtlMap::InitHashTable](../Topic/CAtlMap::InitHashTable.md)|呼叫這個方法會初始化雜湊資料表。|  
|[CAtlMap::IsEmpty](../Topic/CAtlMap::IsEmpty.md)|呼叫這個方法測試是否為空的對應物件。|  
|[CAtlMap::Lookup](../Topic/CAtlMap::Lookup.md)|呼叫這個方法會查閱索引鍵或值。 `CAtlMap` 物件。|  
|[CAtlMap::Rehash](../Topic/CAtlMap::Rehash.md)|呼叫這個方法會將 `CAtlMap` 至物件。|  
|[CAtlMap::RemoveAll](../Topic/CAtlMap::RemoveAll.md)|呼叫這個方法會從 `CAtlMap` 物件移除所有項目。|  
|[CAtlMap::RemoveAtPos](../Topic/CAtlMap::RemoveAtPos.md)|呼叫這個方法會移除這個項目是在 `CAtlMap` 物件的指定位置。|  
|[CAtlMap::RemoveKey](../Topic/CAtlMap::RemoveKey.md)|呼叫這個方法會從物件移除項目 `CAtlMap` 指定關鍵值。|  
|[CAtlMap::SetAt](../Topic/CAtlMap::SetAt.md)|呼叫這個方法插入項目至至對應。|  
|[CAtlMap::SetOptimalLoad](../Topic/CAtlMap::SetOptimalLoad.md)|呼叫這個方法會設定物件的 `CAtlMap` 最佳載入。|  
|[CAtlMap::SetValueAt](../Topic/CAtlMap::SetValueAt.md)|呼叫這個方法會將值儲存在 `CAtlMap` 物件的指定位置。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAtlMap::operator](../Topic/CAtlMap::operator.md)|取代或加入新的項目加入至 `CAtlMap`。|  
  
## 備註  
 `CAtlMap` 為對應的任何指定型別的支援，處理未按順序的主要項目和其關聯的值。  項目 \(包含索引鍵和值\) 使用雜湊演算法，儲存，允許大量資料有效率地儲存和擷取。  
  
 `KTraits` 和 `VTraits` 參數是包含必要的所有補充程式碼複製或移動項目特性類別。  
  
 [CRBMap](../../atl/reference/crbmap-class.md) 類別提供對 `CAtlMap` 的選項。  也`CRBMap` 儲存索引鍵\/值組，但是，只顯示不同的效能特性。  所花費的時間插入項目，查閱索引鍵或刪除 `CRBMap` 物件中的索引鍵是命令記錄 *\(n\)*，其中 *n* 是中的項目數。  如需 `CAtlMap`，這些作業通常會花費常數時間，不過，最壞的情況可能是順序 *n。* 因此，在典型的案例中， `CAtlMap` 速度較快。  
  
 在逐一查看中的項目時，在 `CRBMap` 和 `CAtlMap` 之間的另一個差異很明顯。  在 `CRBMap`，項目排序順序已瀏覽過的。  在 `CAtlMap`，項目不會進行排序，且順序，不可以推斷。  
  
 當需要儲存時有少數項目，請考慮使用 [CSimpleMap](../../atl/reference/csimplemap-class.md) 類別。  
  
 如需詳細資訊，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [Marquee 範例](../../top/visual-cpp-samples.md)   
 [UpdatePV 範例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)