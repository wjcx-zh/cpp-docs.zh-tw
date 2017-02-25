---
title: "Creating a Custom Brush (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "colors [C++], brush"
  - "brushes, colors"
  - "brushes, creating custom"
  - "images [C++], creating custom brushes"
  - "graphics [C++], custom brushes"
  - "custom brushes"
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating a Custom Brush (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂筆刷是您揀選的影像矩形部分，用法如同其中一個影像編輯器備妥的筆刷。  您對選取範圍執行的所有作業也都可對自訂筆刷執行。  
  
### 若要從影像的一部分建立自訂筆刷  
  
1.  [選取影像的一部分](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md) \(要用於筆刷的部分\)。  
  
2.  按住 **SHIFT** 鍵、在選取範圍內按一下，然後將它拖曳穿過影像。  
  
     \-或\-  
  
3.  自 \[影像\] 功能表選擇 \[將選取範圍當做筆刷使用\]。  
  
     您的選取範圍即成為自訂筆刷，將色彩散佈於影像的選取範圍內。  選取範圍的複本會沿著拖曳路徑留存。  拖曳的速度越慢，製作的複本越多。  
  
     **注意** 若沒有先選取影像的一部分，就按一下 \[將選取範圍當做筆刷使用\] 選項，將會使用整個影像做為筆刷。  使用自訂筆刷的結果也將視您是否選取了[不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)而定。  
  
 自訂筆刷中符合目前背景色彩的像素通常是透明的：它們不會覆蓋現有的影像。  您可變更這項行為，讓背景色彩像素蓋過現有的影像。  
  
 您可使用如同戳記 \(Stamp\) 或模板 \(Stencil\) 般使用自訂筆刷來建立各式各樣的特殊效果。  
  
#### 若要以背景色彩繪製自訂筆刷形狀  
  
1.  [選取不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
2.  [設定背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)為您想繪製的色彩。  
  
3.  將自訂筆刷置於要加以繪製的位置。  
  
4.  按一下滑鼠右鍵。  自訂筆刷的任何不透明區域都會以背景色彩繪製。  
  
#### 若要加倍或減半自訂筆刷大小  
  
1.  按加號 \(**\+**\) 鍵來加倍筆刷大小，或按減號 \(**–**\) 鍵來減半大小。  
  
#### 若要取消自訂筆刷  
  
1.  按 **ESC** 或選擇另一種繪圖工具。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)