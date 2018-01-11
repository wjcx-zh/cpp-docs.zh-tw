---
title: "使用 CImageList |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CImageList
dev_langs: C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 053e670b5a6d932c50e2f967ee38cf9191710ff4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-cimagelist"></a>使用 CImageList
影像清單，類別所代表[CImageList](../mfc/reference/cimagelist-class.md)，是相同大小的影像，其中每一個都可以參考它的索引集合。 影像清單用來有效管理大量圖示或點陣圖。 影像清單因為它們不是視窗; 將本身不是控制項不過，這些認證用於多種不同類型的控制項，包括清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md))，樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))，和索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))。  
  
 在一個影像清單中的所有影像會以螢幕裝置格式包含在單一的寬點陣圖中。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 `CImageList` 提供成員函式，可讓您繪製影像、建立和終結影像清單、加入和移除影像、取代影像、合併影像和拖曳影像。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [影像清單的類型](../mfc/types-of-image-lists.md)  
  
-   [使用影像清單](../mfc/using-an-image-list.md)  
  
-   [管理影像清單](../mfc/manipulating-image-lists.md)  
  
-   [從影像清單描繪影像](../mfc/drawing-images-from-an-image-list.md)  
  
-   [影像清單中的影像覆疊](../mfc/image-overlays-in-image-lists.md)  
  
-   [從影像清單拖曳影像](../mfc/dragging-images-from-an-image-list.md)  
  
-   [影像清單中的影像資訊](../mfc/image-information-in-image-lists.md)  
  
## <a name="see-also"></a>請參閱  
 [控制項](../mfc/controls-mfc.md)

