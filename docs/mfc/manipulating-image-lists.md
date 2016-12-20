---
title: "管理影像清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList 類別, 操作"
  - "影像清單 [C++], 操作"
  - "清單 [C++], 影像"
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 管理影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[取代](../Topic/CImageList::Replace.md) 成員函式用新的影像取代影像清單 \([CImageList](../mfc/reference/cimagelist-class.md)\) 的影像。  如果需要動態加入的影像數。影像清單的物件，這個函式也很有用。  [SetImageCount](../Topic/CImageList::SetImageCount.md) 函式會動態變更影像清單中的影像數目。  如果您將影像清單的大小，要加入影像的呼叫 **Replace** 對新的影像位置。  如果您取消影像清單的大小，以新的大小之外的影像會釋放。  
  
 [移除](../Topic/CImageList::Remove.md) 成員函式從影像清單中的影像。  [複製](../Topic/CImageList::Copy.md) 成員函式可以複製或交換影像內的影像清單。  這個函式可讓您指出應該複製來源影像到目的索引或應該交換來源和目的地影像。  
  
 透過結合兩個影像清單中建立新的影像清單，請使用 [建立](../Topic/CImageList::Create.md) 成員函式的適當多載。  **Create** 這個多載組合現有的影像清單中的第一個影像，以產生影像在新的影像清單物件。  新的影像來繪製第二個影像建立透明在第一個。  新的影像的遮罩是執行、邏輯 OR 運算的結果遮罩中的位元兩個現有影像的。  
  
 這個迴圈會一直重複直到所有影像合併並加入新的影像清單物件。  
  
 您可以將封存寫入影像資訊藉由呼叫 [寫入](../Topic/CImageList::Write.md) 成員函式和呼叫 [讀取](../Topic/CImageList::Read.md) 成員函式傳回讀取它。  
  
 [GetSafeHandle](../Topic/CImageList::GetSafeHandle.md)、 [附加](../Topic/CImageList::Attach.md)和 [中斷連結](../Topic/CImageList::Detach.md) 成員函式可讓您管理影像清單的控制代碼附加至 `CImageList` 物件，則為，而 [DeleteImageList](../Topic/CImageList::DeleteImageList.md) 成員函式來刪除影像清單，而不會終結 `CImageList` 物件。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)