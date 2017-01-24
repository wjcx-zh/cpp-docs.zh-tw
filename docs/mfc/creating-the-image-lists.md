---
title: "建立影像清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CListCtrl 類別, 建立其影像清單"
  - "影像清單 [C++], 為 CListCtrl 建立"
  - "清單 [C++], 影像"
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立影像清單與則使用 [CListView](../mfc/reference/clistview-class.md) 或 [CListCtrl](../mfc/reference/clistctrl-class.md)。  
  
> [!NOTE]
>  因此，如果您的清單控制項包含 `LVS_ICON` 樣式，您只需要影像清單。  
  
 使用類別建立一個或多個影像清單的 `CImageList` \(為大型圖示、小圖示和狀態\)。  請參閱 [CImageList](../mfc/reference/cimagelist-class.md)，並查看在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [清單檢視影像清單](http://msdn.microsoft.com/library/windows/desktop/bb774736) 。  
  
 每個影像清單的呼叫 [CListCtrl::SetImageList](../Topic/CListCtrl::SetImageList.md) ;將指標傳遞給適當的 `CImageList` 物件。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)