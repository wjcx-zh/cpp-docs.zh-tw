---
title: "CAtlList Class | Microsoft Docs"
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
  - "ATL.CAtlList"
  - "CAtlList"
  - "ATL::CAtlList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlList class"
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立和管理清單物件的方法。  
  
## 語法  
  
```  
  
      template<  
   typename E,  
   class ETraits = CElementTraits< E >  
>  
class CAtlList  
```  
  
#### 參數  
 `E`  
 元素型別。  
  
 `ETraits`  
 程式碼會在執行複製或移動項目。  如需的詳細資訊請參閱 [CElementTraits 類別](../../atl/reference/celementtraits-class.md) 。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CAtlList::INARGTYPE](../Topic/CAtlList::INARGTYPE.md)||  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlList::CAtlList](../Topic/CAtlList::CAtlList.md)|建構函式。|  
|[CAtlList::~CAtlList](../Topic/CAtlList::~CAtlList.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlList::AddHead](../Topic/CAtlList::AddHead.md)|呼叫這個方法將項目加入至清單的開頭。|  
|[CAtlList::AddHeadList](../Topic/CAtlList::AddHeadList.md)|呼叫這個方法會將現有的清單加入至清單的開頭。|  
|[CAtlList::AddTail](../Topic/CAtlList::AddTail.md)|呼叫這個方法將項目加入此清單的尾端。|  
|[CAtlList::AddTailList](../Topic/CAtlList::AddTailList.md)|呼叫這個方法會將現有的清單加入至這份清單尾端。|  
|[CAtlList::AssertValid](../Topic/CAtlList::AssertValid.md)|呼叫這個方法會檢查清單中有效。|  
|[CAtlList::Find](../Topic/CAtlList::Find.md)|呼叫這個方法會搜尋清單中指定的項目。|  
|[CAtlList::FindIndex](../Topic/CAtlList::FindIndex.md)|呼叫這個方法會取得項目的位置將索引值。|  
|[CAtlList::GetAt](../Topic/CAtlList::GetAt.md)|呼叫這個方法會傳回這個項目在  清單中指定的位置。|  
|[CAtlList::GetCount](../Topic/CAtlList::GetCount.md)|呼叫這個方法會傳回物件的數目的清單。|  
|[CAtlList::GetHead](../Topic/CAtlList::GetHead.md)|呼叫這個方法會傳回這個項目在清單的開頭。|  
|[CAtlList::GetHeadPosition](../Topic/CAtlList::GetHeadPosition.md)|呼叫這個方法會取得清單的開頭的位置。|  
|[CAtlList::GetNext](../Topic/CAtlList::GetNext.md)|呼叫這個方法會從清單中的下一個項目。|  
|[CAtlList::GetPrev](../Topic/CAtlList::GetPrev.md)|呼叫這個方法會從清單中前一個項目。|  
|[CAtlList::GetTail](../Topic/CAtlList::GetTail.md)|呼叫這個方法會傳回這個項目在清單的尾端。|  
|[CAtlList::GetTailPosition](../Topic/CAtlList::GetTailPosition.md)|呼叫這個方法會取得清單的尾端的位置。|  
|[CAtlList::InsertAfter](../Topic/CAtlList::InsertAfter.md)|呼叫這個方法會將新的項目插入至清單中的指定位置之後。|  
|[CAtlList::InsertBefore](../Topic/CAtlList::InsertBefore.md)|呼叫這個方法會將新的項目插入至清單中的指定位置之前。|  
|[CAtlList::IsEmpty](../Topic/CAtlList::IsEmpty.md)|呼叫這個方法會決定清單是否為 null。|  
|[CAtlList::MoveToHead](../Topic/CAtlList::MoveToHead.md)|呼叫這個方法會將指定的項目移至清單的開頭。|  
|[CAtlList::MoveToTail](../Topic/CAtlList::MoveToTail.md)|呼叫這個方法會將指定的項目移至清單的尾端。|  
|[CAtlList::RemoveAll](../Topic/CAtlList::RemoveAll.md)|呼叫這個方法會從清單移除所有項目。|  
|[CAtlList::RemoveAt](../Topic/CAtlList::RemoveAt.md)|呼叫這個方法從清單中移除單一項目。|  
|[CAtlList::RemoveHead](../Topic/CAtlList::RemoveHead.md)|呼叫這個方法會移除這個項目在清單的開頭。|  
|[CAtlList::RemoveHeadNoReturn](../Topic/CAtlList::RemoveHeadNoReturn.md)|呼叫這個方法會移除這個項目在清單的開頭，而不會傳回值。|  
|[CAtlList::RemoveTail](../Topic/CAtlList::RemoveTail.md)|呼叫這個方法會移除這個項目在清單的尾端。|  
|[CAtlList::RemoveTailNoReturn](../Topic/CAtlList::RemoveTailNoReturn.md)|呼叫這個方法會移除這個項目在清單的尾端，而不會傳回值。|  
|[CAtlList::SetAt](../Topic/CAtlList::SetAt.md)|呼叫這個方法會將項目的值在清單中的特定位置。|  
|[CAtlList::SwapElements](../Topic/CAtlList::SwapElements.md)|呼叫這個方法會交換清單中的項目。|  
  
## 備註  
 `CAtlList` 類別會依序支援可存取非唯一的物件排序清單或傳值。  `CAtlList` 清單的行為就像雙向連結串列。  每個清單具有開頭與尾端，一行，而在其他情況下新項目的項目 \(或清單\) 可以加入任一端的清單或在特定項目前後插入。  
  
 大部分 `CAtlList` 方法可用位置的值。  方法會使用這個值來參考項目中的實際記憶體位置，且不應直接計算或預測。  如果存取清單中的 *第 n 個*項目是必須的， [CAtlList::FindIndex](../Topic/CAtlList::FindIndex.md) 方法會傳回指定索引中的對應位置的值。  方法 [CAtlList::GetNext](../Topic/CAtlList::GetNext.md) 和 [CAtlList::GetPrev](../Topic/CAtlList::GetPrev.md) 物件可用於逐一查看清單中逐一查看的物件。  
  
 如需集合類別的詳細資訊可供 ATL，請參閱 [ATL 集合類別。](../../atl/atl-collection-classes.md)。  
  
## 需求  
 **Header:** atlcoll.h  
  
## 請參閱  
 [CList Class](../../mfc/reference/clist-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)