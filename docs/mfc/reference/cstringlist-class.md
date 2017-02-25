---
title: "CStringList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringList class"
  - "清單, string"
  - "字串 [C++], 集合"
  - "字串 [C++], 清單"
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CStringList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CString` 物件支援清單。  
  
## 語法  
  
```  
class CStringList : public CObject  
```  
  
## 成員  
 `CStringList` 的成員函式類似於類別 [CObList](../../mfc/reference/coblist-class.md)的成員函式。  因此相似，您可以使用成員的函式特定使用 `CObList` 參考文件。  不論您在何處參閱 `CObject` 指標做為傳回值，請用 `CString` \(不是 `CString` 指標\)。  不論您在何處參閱 `CObject` 指標做為函式參數，請以 `LPCTSTR`。  
  
 `CObject*& CObList::GetHead() const;`  
  
 例如，轉譯  
  
 `CString& CStringList::GetHead() const;`  
  
 和  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 轉譯  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CObList::CObList](../Topic/CObList::CObList.md)|建構空白清單。|  
  
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
 所有比較以傳值方式完成，這表示字串中的字元比較而不是字串的位址。  
  
 `CStringList` 合併 `IMPLEMENT_SERIAL` 巨集支援序列化和傾印其項目。  如果 `CString` 物件清單儲存至檔案，具有多載插入運算子的或 `Serialize` 成員函式的 `CString` ，每個項目依次序列化。  
  
 如果您需要個別項目 `CString` 傾印，您必須將傾印內容的深度為 1 或更大。  
  
 如需使用 `CStringList`的詳細資訊，請參閱本文 [集合](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)