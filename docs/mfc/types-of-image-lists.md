---
title: "影像清單的類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84a2118978d5ebd722d4fe56cdeec2aa0f74a94e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-image-lists"></a>影像清單的類型
有兩種類型的影像清單 ([CImageList](../mfc/reference/cimagelist-class.md)): 非遮罩和遮罩。 「 非遮罩的影像清單 」 包含色彩的點陣圖，其中包含一或多個映像。 「 遮罩的影像清單 」 包含兩個相同大小的點陣圖。 第一個是色彩的點陣圖，其中包含這些影像，以及第二個是單色點陣圖，其中包含一系列的遮罩，其中每個映像中的第一個點陣圖。  
  
 其中一個多載的**建立**成員函式會採用表示是否已遮罩影像清單的旗標。 （其他多載建立遮罩的影像清單）。  
  
 繪製非遮罩的影像時，它只會複製到目標裝置內容。也就是說，它會繪製停留裝置內容的現有的背景色彩。 繪製遮罩的影像時，在影像位元遮罩，通常產生點陣圖中的透明區域的目標裝置內容的背景色彩會透過顯示的位元結合。 繪製遮罩的影像時，您可以指定數個的繪製樣式。 例如，您可以指定影像遞色，表示選取的物件。  
  
## <a name="see-also"></a>請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

