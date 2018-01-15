---
title: "排序標題控制項中的項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DS_DRAGDROP
dev_langs: C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 48adbc53ad0e4974edd86d3f8a96d74214093dda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ordering-items-in-the-header-control"></a>排序標題控制項中的項目
一旦您[項目加入至標題控制項](../mfc/adding-items-to-the-header-control.md)，您可以操作或取得與下列函式順序有關的資訊：  
  
-   [Cheaderctrl:: Getorderarray](../mfc/reference/cheaderctrl-class.md#getorderarray)和[cheaderctrl:: Setorderarray](../mfc/reference/cheaderctrl-class.md#setorderarray)  
  
     以由左至右的順序擷取和設定標題項目。  
  
-   [Cheaderctrl:: Ordertoindex](../mfc/reference/cheaderctrl-class.md#ordertoindex)。  
  
     擷取特定標頭項目的索引值。  
  
 除了先前的成員函式之外，`HDS_DRAGDROP` 樣式允許使用者拖放標題控制項內的標題項目。 如需詳細資訊，請參閱[提供為標題項目拖放支援](../mfc/providing-drag-and-drop-support-for-header-items.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

