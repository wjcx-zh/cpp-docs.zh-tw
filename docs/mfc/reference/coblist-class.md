---
title: "CObList Class | Microsoft Docs"
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
  - "CObList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObList class"
  - "清單, object"
  - "物件 [C++], lists of"
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CObList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存取非唯一的 `CObject` 的指標支援排序清單循序或由指標的值。  
  
## 語法  
  
```  
class CObList : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CObList::CObList](../Topic/CObList::CObList.md)|建構 `CObject` 指標的空白清單。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CObList::AddHead](../Topic/CObList::AddHead.md)|將項目 \(或另一個檔案中的所有項目清單\) 加入至清單的開頭 \(設定新的開頭\)。|  
|[CObList::AddTail](../Topic/CObList::AddTail.md)|將項目 \(或另一個檔案中的所有項目清單\) 加入至清單的尾端 \(設定一個新的尾端\)。|  
|[CObList::Find](../Topic/CObList::Find.md)|取得指令指標值所指定之項目的位置。|  
|[CObList::FindIndex](../Topic/CObList::FindIndex.md)|取得以零起始的索引所指定之項目的位置。|  
|[CObList::GetAt](../Topic/CObList::GetAt.md)|取得這個項目在指定的位置。|  
|[CObList::GetCount](../Topic/CObList::GetCount.md)|傳回的元素數目。這個清單中的。|  
|[CObList::GetHead](../Topic/CObList::GetHead.md)|傳回清單的標頭項目 \(不可以是 Null\)。|  
|[CObList::GetHeadPosition](../Topic/CObList::GetHeadPosition.md)|傳回清單的標頭項目的位置。|  
|[CObList::GetNext](../Topic/CObList::GetNext.md)|取得可逐一查看的下一個項目。|  
|[CObList::GetPrev](../Topic/CObList::GetPrev.md)|取得可逐一查看的上一個項目。|  
|[CObList::GetSize](../Topic/CObList::GetSize.md)|傳回的元素數目。這個清單中的。|  
|[CObList::GetTail](../Topic/CObList::GetTail.md)|傳回清單的尾端項目 \(不可以是 Null\)。|  
|[CObList::GetTailPosition](../Topic/CObList::GetTailPosition.md)|傳回清單的尾端項目的位置。|  
|[CObList::InsertAfter](../Topic/CObList::InsertAfter.md)|在指定的位置後面插入新的項目。|  
|[CObList::InsertBefore](../Topic/CObList::InsertBefore.md)|在指定位置之前插入新的項目。|  
|[CObList::IsEmpty](../Topic/CObList::IsEmpty.md)|空白清單情況的 \(沒有項目\) 的測試。|  
|[CObList::RemoveAll](../Topic/CObList::RemoveAll.md)|從這份清單中移除所有項目。|  
|[CObList::RemoveAt](../Topic/CObList::RemoveAt.md)|從這份清單中移除項目，由指定位置。|  
|[CObList::RemoveHead](../Topic/CObList::RemoveHead.md)|從清單中移除的項目。|  
|[CObList::RemoveTail](../Topic/CObList::RemoveTail.md)|從清單的尾端移除項目。|  
|[CObList::SetAt](../Topic/CObList::SetAt.md)|設定這個項目在指定的位置。|  
  
## 備註  
 `CObList` 清單的行為就像雙重連結的清單。  
  
 型別 **位置** 的變數是清單中的索引鍵。  您可以使用 **位置** 變數做為 Iterator 循序周遊清單和為書籤保留位置。  但是位置不同於"的索引。  
  
 插入項目非常快速地在清單開頭，在尾部和在已知的 **位置**。  循序搜尋需要依值或索引查閱項目。  如果串列較長，速度，搜尋可能會很慢。  
  
 `CObList` 合併 `IMPLEMENT_SERIAL` 巨集支援序列化和傾印其項目。  如果 `CObject` 指標清單儲存至檔案，具有多載插入運算子的或 `Serialize` 成員函式的 `CObject` ，每個項目依次序列化。  
  
 如果可在清單需要個別項目 `CObject` 傾印，您必須將傾印內容的深度為 1 或更大。  
  
 當 `CObList` 刪除物件，或，在移除其元素，，才會移除參考的 `CObject` 指標，而不是物件。  
  
 您可以從 `CObList`衍生您的類別。  您的新清單類別，其設計是存放指標 `CObject`從取得的物件，將新的資料成員和新的成員函式。  請注意結果清單顯示的內容不完全是型別安全，，因為它允許所有 `CObject` 指標的外掛程式。  
  
> [!NOTE]
>  如果您想要序列化清單，您可以在您的衍生類別的實作必須使用 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 巨集。  
  
 如需使用 `CObList`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CStringList Class](../../mfc/reference/cstringlist-class.md)   
 [CPtrList Class](../../mfc/reference/cptrlist-class.md)