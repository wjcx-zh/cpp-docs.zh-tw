---
title: "影像清單中的影像資訊 | Microsoft Docs"
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
  - "CImageList 類別, 其中的影像資訊"
  - "影像清單 [C++], 其中的影像資訊"
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 影像清單中的影像資訊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CImageList](../mfc/reference/cimagelist-class.md) 包含從影像清單中擷取資訊的函式。  [GetImageInfo](../Topic/CImageList::GetImageInfo.md) 成員函式。如需單一影像的資訊填入的 `IMAGEINFO` 結構，包含影像和遮罩點陣圖、數字色彩平面與每像素位元數和影像週框處理影像點陣圖中的。  您可以使用這項資訊來操作影像的點陣圖。  
  
 [GetImageCount](../Topic/CImageList::GetImageCount.md) 成員函式來擷取影像數影像清單的。  
  
 您也可以根據影像和遮罩的圖示會出現在影像清單使用 [ExtractIcon](../Topic/CImageList::ExtractIcon.md) 成員函式。  函式傳回新圖示的控制代碼。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)