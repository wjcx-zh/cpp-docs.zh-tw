---
title: "CList Class | Microsoft Docs"
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
  - "CList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CList class"
  - "清單"
  - "清單, base class for"
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存取非唯一的物件支援排序清單循序或傳值。  
  
## 語法  
  
```  
template< class TYPE, class ARG_TYPE = const TYPE& >   
class CList : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CList::CList](../Topic/CList::CList.md)|建構空白的排序清單。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CList::AddHead](../Topic/CList::AddHead.md)|將項目 \(或另一個檔案中的所有項目清單\) 加入至清單的開頭 \(設定新的開頭\)。|  
|[CList::AddTail](../Topic/CList::AddTail.md)|將項目 \(或另一個檔案中的所有項目清單\) 加入至清單的尾端 \(設定一個新的尾端\)。|  
|[CList::Find](../Topic/CList::Find.md)|取得指令指標值所指定之項目的位置。|  
|[CList::FindIndex](../Topic/CList::FindIndex.md)|取得以零起始的索引所指定之項目的位置。|  
|[CList::GetAt](../Topic/CList::GetAt.md)|取得這個項目在指定的位置。|  
|[CList::GetCount](../Topic/CList::GetCount.md)|傳回的元素數目。這個清單中的。|  
|[CList::GetHead](../Topic/CList::GetHead.md)|傳回清單的標頭項目 \(不可以是 Null\)。|  
|[CList::GetHeadPosition](../Topic/CList::GetHeadPosition.md)|傳回清單的標頭項目的位置。|  
|[CList::GetNext](../Topic/CList::GetNext.md)|取得可逐一查看的下一個項目。|  
|[CList::GetPrev](../Topic/CList::GetPrev.md)|取得可逐一查看的上一個項目。|  
|[CList::GetSize](../Topic/CList::GetSize.md)|傳回的元素數目。這個清單中的。|  
|[CList::GetTail](../Topic/CList::GetTail.md)|傳回清單的尾端項目 \(不可以是 Null\)。|  
|[CList::GetTailPosition](../Topic/CList::GetTailPosition.md)|傳回清單的尾端項目的位置。|  
|[CList::InsertAfter](../Topic/CList::InsertAfter.md)|在指定的位置後面插入新的項目。|  
|[CList::InsertBefore](../Topic/CList::InsertBefore.md)|在指定位置之前插入新的項目。|  
|[CList::IsEmpty](../Topic/CList::IsEmpty.md)|空白清單情況的 \(沒有項目\) 的測試。|  
|[CList::RemoveAll](../Topic/CList::RemoveAll.md)|從這份清單中移除所有項目。|  
|[CList::RemoveAt](../Topic/CList::RemoveAt.md)|從這份清單中移除項目，由指定位置。|  
|[CList::RemoveHead](../Topic/CList::RemoveHead.md)|從清單中移除的項目。|  
|[CList::RemoveTail](../Topic/CList::RemoveTail.md)|從清單的尾端移除項目。|  
|[CList::SetAt](../Topic/CList::SetAt.md)|設定這個項目在指定的位置。|  
  
#### 參數  
 `TYPE`  
 在清單中之物件的型別。  
  
 `ARG` *\_* `TYPE`  
 用於型別參考清單中儲存的物件。  可以是參考。  
  
## 備註  
 `CList` 清單的行為就像雙重連結的清單。  
  
 型別 **位置** 的變數是清單中的索引鍵。  您可以使用 **位置** 變數做為 Iterator 循序周遊清單和為書籤保留位置。  但是位置不同於"的索引。  
  
 插入項目非常快速地在清單開頭，在尾部和在已知的 **位置**。  循序搜尋需要依值或索引查閱項目。  如果串列較長，速度，搜尋可能會很慢。  
  
 如果可在清單需要個別項目傾印，您必須將傾印內容的深度為 1 或更大。  
  
 這個類別的某些成員函式的呼叫必須自訂為 `CList` 的大部分類別會使用全域的 Helper 函式。  請參閱「巨集和全域變數\>一節的 [集合類別 Helper](../../mfc/reference/collection-class-helpers.md) 。  
  
 如需使用 `CList`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 範例  
 [!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/CPP/clist-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## 需求  
 **Header:** afxtempl.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMap Class](../../mfc/reference/cmap-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)