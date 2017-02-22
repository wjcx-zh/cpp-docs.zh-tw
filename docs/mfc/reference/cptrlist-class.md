---
title: "CPtrList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPtrList class"
  - "generic lists"
  - "清單, 泛型"
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援 void 指標的清單。  
  
## 語法  
  
```  
class CPtrList : public CObject  
```  
  
## Members  
 `CPtrList` 的成員函式類似於類別的 [CObList](../../mfc/reference/coblist-class.md)成員函式。  因為此相似，您可以使用成員函式特定使用 `CObList` 參考文件。  無論位於何處參閱 `CObject` 指標做為函式參數或傳回值，請用 `void`的指標。  
  
 `CObject*& CObList::GetHead() const;`  
  
 例如，翻譯為  
  
 `void*& CPtrList::GetHead() const;`  
  
## 備註  
 `CPtrList` 結合 `IMPLEMENT_DYNAMIC` 巨集支援執行階段型別存取和傾印至 `CDumpContext` 物件。  如果您需要個別指標清單項目傾印，您必須設定傾印內容的深度為 1 \(含\) 以上版本。  
  
 指標清單不可序列化。  
  
 當 `CPtrList` 物件被移除，或當自身元素被移除時，才會移除參考的指標，而非它們參考的實體。  
  
 如需有關使用 \[`CPtrList`\] 視窗的詳細資訊，請參閱 [Collections](../../mfc/collections.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## 需求  
 **Header:** afxcoll.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObList Class](../../mfc/reference/coblist-class.md)