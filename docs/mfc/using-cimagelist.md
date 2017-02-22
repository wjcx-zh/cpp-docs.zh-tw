---
title: "使用 CImageList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CImageList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList 類別, 使用"
  - "影像清單控制項"
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用 CImageList
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一個影像清單，由類別 [CImageList](../mfc/reference/cimagelist-class.md) 顯示，是一個相同大小影像的集合，其中每個物件都可以由其索引參考。  影像清單用來有效管理大量圖示或點陣圖。  因為它們不是視窗，影像清單不是自己的控制項；但是，它們是與幾種不同型別的控制項一起使用，包括清單控制項 \([CListCtrl](../mfc/reference/clistctrl-class.md)\)、樹狀控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 和索引標籤控制項 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\)。  
  
 在一個影像清單中的所有影像會以螢幕裝置格式包含在單一的寬點陣圖中。  影像清單也可以包括一個包含遮罩 \(用來以透明方式繪製影像 \) 的單色點陣圖 \(圖示樣式\)。  `CImageList` 提供成員函式，可讓您繪製影像、建立和終結影像清單、加入和移除影像、取代影像、合併影像和拖曳影像。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [影像清單的類型](../mfc/types-of-image-lists.md)  
  
-   [使用影像清單](../mfc/using-an-image-list.md)  
  
-   [管理影像清單](../mfc/manipulating-image-lists.md)  
  
-   [從影像清單描繪影像](../mfc/drawing-images-from-an-image-list.md)  
  
-   [影像清單中的影像覆疊](../mfc/image-overlays-in-image-lists.md)  
  
-   [從影像清單拖曳影像](../mfc/dragging-images-from-an-image-list.md)  
  
-   [影像清單中的影像資訊](../mfc/image-information-in-image-lists.md)  
  
## 請參閱  
 [控制項](../mfc/controls-mfc.md)