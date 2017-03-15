---
title: "Window Panes (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "graphics editor [C++]"
  - "Image editor [C++], panes"
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Window Panes (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\[影像編輯器\] 視窗通常在兩個以分隔列分隔的窗格內顯示影像。  其中一個檢視畫面為實際大小，另一個檢視畫面為放大圖 \(預設放大因數為 6\)。  在這兩個窗格內的檢視畫面會自動更新：您在一個窗格內所做的變更會立即顯示在另一個窗格內。  這兩個窗格讓您可輕易處理經放大的影像檢視，您可在其中區分個別的像素，同時在影像的實際大小檢視上觀察您變更的效果。  
  
 左窗格可依需要使用任意大小的空間 \(最大可達影像視窗的一半\) 來顯示影像的 1:1 倍率檢視 \(預設值\)。  右窗格顯示經縮放的影像 \(依預設為 6:1 倍率\)。  您可以在每一個窗格[縮放比例倍數](../mfc/changing-the-magnification-factor-image-editor-for-icons.md)，方法為使用[影像編輯器工具列](../mfc/toolbar-image-editor-for-icons.md)上的**放大**工具或使用快速鍵 \(Accelerator\)。  
  
 您可放大 \[影像編輯器\] 視窗的較小窗格，以及使用兩個窗格來顯示大型影像的不同區域。  在窗格內按一下來加以選取。  
  
 您可變更窗格的相對大小，方法為將指標置於分隔列上，然後將分隔列移至右邊或左邊。  如果您只想使用一個窗格，分隔列可一路移至任一邊。  
  
 如果已經以 4 或更大的因數放大了影像編輯器窗格，您可[顯示像素格線](../mfc/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)，來分隔影像中的個別像素。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)