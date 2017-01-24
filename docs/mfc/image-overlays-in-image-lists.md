---
title: "影像清單中的影像覆疊 | Microsoft Docs"
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
  - "CImageList 類別, 其中的影像覆疊"
  - "影像清單 [C++], 其中的影像覆疊"
  - "覆疊"
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 影像清單中的影像覆疊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個影像清單 \([CImageList](../mfc/reference/cimagelist-class.md)\) 包含會用於覆疊遮罩的影像清單。  「覆疊遮罩」是影像以透明方式繪製在另一個影像。  所有影像都可以當做覆疊遮罩。  您可以指定每個影像清單最多四個覆疊遮罩。  
  
 使用 [SetOverlayImage](../Topic/CImageList::SetOverlayImage.md) 成員函式，加入影像的索引至覆疊遮罩清單，影像的索引和覆疊遮罩的索引。  請注意覆疊遮罩的索引是以一起始而不是以零起始。  
  
 您由單一呼叫 **Draw** 繪製影像的覆疊遮罩。  參數包含影像的索引和繪製覆疊遮罩的索引。  您必須使用 [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) 巨集指定覆疊遮罩的索引。  此外，呼叫 [DrawIndirect](../Topic/CImageList::DrawIndirect.md) 成員函式時，您也可以指定覆疊影像。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)