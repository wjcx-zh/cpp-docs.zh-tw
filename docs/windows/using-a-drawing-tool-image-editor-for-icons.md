---
title: "Using a Drawing Tool (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.drawing"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], selecting drawing tools"
  - "Image editor [C++], toolbar"
  - "drawing tools"
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using a Drawing Tool (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

影像編輯器的徒手繪製和清除工具的運作方式都相同，您必須選取工具，然後[選取前景和背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)以及大小和形狀選項。  然後將指標移至影像，按一下或拖曳來繪製及清除。  
  
 當您選取**橡皮擦**工具、**筆刷**工具或**噴槍**工具時，選項選取器即顯示該工具的選項。  
  
> [!TIP]
>  您可能會發現，使用其中一種繪圖工具在背景色彩上繪圖，會比使用**橡皮擦**工具更為方便。  
  
 您可以從 \[影像編輯器\] 工具列或 \[影像\] 功能表中選擇繪圖工具。  
  
### 若要自影像編輯器工具列中選取並使用繪圖工具  
  
1.  按一下 \[影像編輯器\] 工具列上的按鈕。  
  
    -   **橡皮擦**工具在您按下滑鼠左鍵時，會以目前的背景色彩塗滿影像。  
  
    -   **鉛筆**工具會以一個像素的固定寬度任意繪圖。  
  
    -   選項選取器會決定筆刷工具的形狀和大小。  
  
    -   **噴槍**工具會在筆刷中央的周圍隨意散佈色彩像素。  
  
        > [!TIP]
        >  當您將游標移到[影像編輯器工具列](../mfc/toolbar-image-editor-for-icons.md)的按鈕上時，即出現工具提示。  這些提示將會協助您識別此處提及的按鈕。  
  
2.  如果需要，可以選取色彩和筆刷：  
  
    -   在[調色盤](../windows/colors-window-image-editor-for-icons.md)中，按一下滑鼠左鍵來選取前景色彩，或按一下滑鼠右鍵來選取背景色彩。  
  
    -   在[選項選取器](../mfc/toolbar-image-editor-for-icons.md)中，按一下您要使用之筆刷的形狀。  
  
3.  指向影像中您要開始繪圖或塗刷的位置。  指標會根據您所選取的工具改變形狀。  
  
4.  按住滑鼠左鍵 \(使用前景色彩\) 或滑鼠右鍵 \(使用背景色彩\)，進行繪圖。  
  
### 若要自影像功能表中選取並使用繪圖工具列  
  
1.  按一下 \[影像\] 功能表，然後選取 \[工具\] 命令。  
  
2.  在階層式的子功能表中，選擇您想要使用的工具。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)