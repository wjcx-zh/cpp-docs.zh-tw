---
title: "建立影像清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfb42dc2c14b5092aeb667ea22008abe4d581a6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-image-lists"></a>建立影像清單
建立影像清單是相同無論您是使用[CListView](../mfc/reference/clistview-class.md)或[CListCtrl](../mfc/reference/clistctrl-class.md)。  
  
> [!NOTE]
>  您只需要影像清單如果清單控制項包含`LVS_ICON`樣式。  
  
 使用類別`CImageList`建立 （適用於完整大小圖示、 小圖示和狀態） 的一或多個映像清單。 請參閱[CImageList](../mfc/reference/cimagelist-class.md)，並查看[清單檢視影像清單](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。  
  
 呼叫[CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist)每個映像清單，則將指標傳遞至適當`CImageList`物件。  
  
## <a name="see-also"></a>請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

