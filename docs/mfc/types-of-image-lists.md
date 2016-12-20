---
title: "影像清單的類型 | Microsoft Docs"
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
  - "CImageList 類別, 類型"
  - "影像清單 [C++], 類型"
  - "清單 [C++], 影像"
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 影像清單的類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得影像清單 \([CImageList](../mfc/reference/cimagelist-class.md)\) 有兩種:nonmasked 和遮罩。  「nonmasked 影像清單包括包含一個或多個影像的色彩點陣圖。  「遮罩影像清單包括兩個大小相等的點陣圖。  第一個是包含影像的色彩點陣圖，，第二個是包含一系列遮罩—一個在第一個點陣圖中每個影像的單色點陣圖。  
  
 其中一個 **Create** 成員函式的多載旗標指示影像清單是否遮罩。\(另一個多載建立遮住了影像清單\)。  
  
 在繪製時一 nonmasked 影像，則會複製到目標裝置內容;即會繪製在裝置內容的現有的背景色彩。  在繪製影像時遮罩，影像的位元結合，通常會在目標裝置內容背景色彩會顯示得的點陣圖位元遮罩的透明區域。  遮罩，在繪製影像時，您可以指定幾個繪製樣式。  例如，您可以指定影像遞色表示選取的物件。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)