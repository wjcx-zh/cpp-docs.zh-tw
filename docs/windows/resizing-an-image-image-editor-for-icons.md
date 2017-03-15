---
title: "Resizing an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.editing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], resizing images"
  - "graphics [C++], resizing"
  - "images [C++], resizing"
  - "resizing images"
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Resizing an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

影像編輯器在調整影像大小時的行為，視您是[選取](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md)整個影像或只是一部分影像而定。  
  
 當選取範圍只包含影像的一部分時，影像編輯器會縮小選取範圍，其作法為刪除幾列或幾欄的像素，並以目前的背景色彩填滿空白的區域，或是藉由複製幾列或幾欄的像素來延伸選取範圍。  
  
 當選取範圍包含整個影像時，影像編輯器會縮小及延伸影像，或是加以裁剪及擴充。  
  
 有兩項調整影像大小的機制：縮放控點 \(Sizing Handle\) 和[屬性視窗](../Topic/Properties%20Window.md)。  您可拖曳縮放控點來變更影像的全部或部分大小。  可拖曳的縮放控點為實心。  您無法拖曳中空的控點。  使用 \[屬性\] 視窗只能調整整個影像的大小，不能調整選定部分的大小。  
  
 ![點陣圖上的縮放控點](../mfc/media/vcimageeditorsizinghandles.png "vcImageEditorSizingHandles")  
調整控點大小  
  
> [!NOTE]
>  如果您選取了[格線設定對話方塊](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)中的 \[磚狀格線\] 選項，調整大小會貼齊下一條磚狀格線。  如果只選取了 \[像素格線\] 選項 \(預設設定\)，則調整大小會貼齊至下一個可用的像素。  
  
-   [調整整個影像大小](../mfc/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [裁剪或擴充整個影像](../mfc/cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [縮小或延伸整個影像](../mfc/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [縮小或延伸影像的一部分](../mfc/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)