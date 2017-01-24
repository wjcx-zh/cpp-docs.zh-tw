---
title: "CTypedPtrList Class | Microsoft Docs"
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
  - "CTypedPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrList class"
  - "linked lists [C++]"
  - "lists [C++]"
  - "pointer lists"
  - "template classes, CTypedPtrList class"
  - "type-safe collections"
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTypedPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為類別提供型別安全的「包裝函式」 `CPtrList`物件。  
  
## 語法  
  
```  
template< class BASE_CLASS, class TYPE >  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### 參數  
 `BASE_CLASS`  
 具型別指標清單類別的基底類別，必須是指標清單類別 \(`CObList` 或 `CPtrList`\)。  
  
 `TYPE`  
 在類別清單中的項目型別。  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTypedPtrList::AddHead](../Topic/CTypedPtrList::AddHead.md)|將項目 \(或另一個檔案中的所有項目清單\) 加入至清單的開頭 \(設定新的開頭\)。|  
|[CTypedPtrList::AddTail](../Topic/CTypedPtrList::AddTail.md)|將項目 \(或另一個檔案中的所有項目清單\) 加入至清單的尾端 \(設定一個新的尾端\)。|  
|[CTypedPtrList::GetAt](../Topic/CTypedPtrList::GetAt.md)|取得這個項目在指定的位置。|  
|[CTypedPtrList::GetHead](../Topic/CTypedPtrList::GetHead.md)|傳回清單的標頭項目 \(不可以是 Null\)。|  
|[CTypedPtrList::GetNext](../Topic/CTypedPtrList::GetNext.md)|取得可逐一查看的下一個項目。|  
|[CTypedPtrList::GetPrev](../Topic/CTypedPtrList::GetPrev.md)|取得可逐一查看的上一個項目。|  
|[CTypedPtrList::GetTail](../Topic/CTypedPtrList::GetTail.md)|傳回清單的尾端項目 \(不可以是 Null\)。|  
|[CTypedPtrList::RemoveHead](../Topic/CTypedPtrList::RemoveHead.md)|從清單中移除的項目。|  
|[CTypedPtrList::RemoveTail](../Topic/CTypedPtrList::RemoveTail.md)|從清單的尾端移除項目。|  
|[CTypedPtrList::SetAt](../Topic/CTypedPtrList::SetAt.md)|設定這個項目在指定的位置。|  
  
## 備註  
 當您使用 `CTypedPtrList` 而不是 `CObList` 或 `CPtrList`時， C\+\+ 型別檢查的安裝有助於排除不相符的指標型別所造成的錯誤。  
  
 此外， `CTypedPtrList` 包裝函式執行所需的大部分轉型您是否已經使用 `CObList` 或 `CPtrList`。  
  
 由於所有 `CTypedPtrList` 函式內嵌，此範本就不會明顯影響您程式碼的大小或速度。  
  
 從 `CObList` 衍生清單中還原序列化，但是，從 `CPtrList` 衍生的那些不行。  
  
 當 `CTypedPtrList` 刪除物件，或，在移除其元素，，才會移除參考的指標，而不是實體。  
  
 如需使用 `CTypedPtrList`的相關資訊，請參閱 Microsoft 知識庫文件 [集合](../../mfc/collections.md) 和 [樣板類別](../../mfc/template-based-classes.md)。  
  
## 範例  
 這個範例會建立 `CTypedPtrList`執行個體，將物件序列化，清單儲存至磁碟，然後刪除物件:  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/CPP/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/CPP/ctypedptrlist-class_2.cpp)]  
  
## 繼承階層架構  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## 需求  
 **Header:** afxtempl.h  
  
## 請參閱  
 [MFC 範例收集](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPtrList Class](../../mfc/reference/cptrlist-class.md)   
 [CObList Class](../../mfc/reference/coblist-class.md)