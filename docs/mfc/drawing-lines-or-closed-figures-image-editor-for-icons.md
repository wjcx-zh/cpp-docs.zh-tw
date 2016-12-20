---
title: "Drawing Lines or Closed Figures (Image Editor for Icons) | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "closed figures, drawing"
  - "lines [C++], painting"
  - "lines [C++], drawing"
  - "Image editor [C++], drawing lines"
  - "shapes, drawing"
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Drawing Lines or Closed Figures (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

影像編輯器工具在繪製線條和封閉圖形的運作方式上是相同的：將插入點置於一點，然後拖曳到另一點。  就線條而言，這些點是結束點。  就封閉圖形而言，這些點是含括圖形之矩形的對角。  
  
 線條會以目前筆刷選取的寬度繪製，而帶框圖形會以目前寬度選取的寬度繪製。  如果您按下滑鼠左鍵，線條和所有圖形 \(都帶框並填滿色彩\) 會以目前的前景色彩繪製，如果按下滑鼠右鍵，則是以目前的背景色彩繪製。  
  
### 若要繪製線條  
  
1.  在[影像編輯器工具列](../mfc/toolbar-image-editor-for-icons.md) \(或從 \[影像\] 功能表的 \[工具\] 命令\)，按一下 \[直線\] 工具。  
  
2.  如果需要，可以選取色彩和筆刷：  
  
    -   在[調色盤](../windows/colors-window-image-editor-for-icons.md)中，按一下滑鼠左鍵來選取前景色彩，或按一下滑鼠右鍵來選取背景色彩。  
  
    -   在[選項選取器](../mfc/toolbar-image-editor-for-icons.md)中，按一下代表您要使用之筆刷的形狀。  
  
3.  將指標置於線條的起點。  
  
4.  拖曳至線條的結束點。  
  
### 繪製封閉圖形  
  
1.  在 \[影像編輯器\] 工具列 \(或從 \[影像\] 功能表的 \[工具\] 命令\)，按一下**封閉圖形繪製**的工具。  
  
     **封閉圖形繪製**工具會建立其個別按鈕上所示的圖形。  
  
2.  如果需要，可以選取色彩和線條寬度。  
  
3.  將指標移至要在其中繪製圖形之矩形區域的其中一個角落。  
  
4.  將指標拖曳至反向對角的角落。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)