---
title: "Editing Parts of an Image (Image Editor for Icons) | Microsoft Docs"
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
  - "Image editor [C++], editing images"
  - "Clipboard [C++], pasting"
  - "images [C++], editing"
  - "images [C++], deleting selected parts"
  - "images [C++], copying selected parts"
  - "images [C++], moving selected parts"
  - "images [C++], dragging and replicating selected parts"
  - "images [C++], pasting into"
  - "graphics [C++], editing"
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Editing Parts of an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可對某個[選取範圍](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md) \(無論是整個影像或只是影像的一部分\) 執行標準的編輯作業 — 剪下、複製、清除及移動。  由於影像編輯器使用 Windows 剪貼簿，您可以將影像在影像編輯器和其他應用程式之間的視窗。  
  
 此外，無論選取範圍是包含整個影像或只是一部分，您都可調整其大小。  
  
### 若要剪下目前的選取範圍並將其移至剪貼簿  
  
1.  按一下 \[編輯\] 功能表上的 \[剪下\]。  
  
### 若要複製選取範圍  
  
1.  將指標置於選取範圍框線內或其上的任何位置 \(縮放控點除外\)。  
  
2.  按住 **CTRL** 鍵，同時將選取範圍拖曳至新的位置。  原有的選取範圍區域不變。  
  
3.  若要在其目前的位置將選取範圍複製到影像中，請在選取範圍游標外按一下。  
  
### 若要將剪貼簿內容貼到影像中  
  
1.  在 \[編輯\] 功能表上選擇 \[貼上\]。  
  
     剪貼簿內容 \(以選取範圍框線框住\) 會出現在窗格的左上角。  
  
2.  將指標置於選取範圍框線內，並將影像拖曳到影像上的理想位置。  
  
3.  若要將影像錨定於其新位置，請在選取範圍框線外按一下。  
  
### 若要在未移入剪貼簿的情況下刪除目前的選取範圍  
  
1.  從 \[編輯\] 功能表中選擇 \[刪除\]。  
  
     選取範圍的原始區域會填滿目前的背景色彩。  
  
    > [!NOTE]
    >  您可以在 \[資源檢視\] 視窗內按一下滑鼠右鍵，存取 \[剪下\]、\[複製\]、\[貼上\] 及 \[刪除\] 等命令。  
  
### 若要移動選取範圍  
  
1.  將指標置於選取範圍框線內或其上的任何位置 \(縮放控點除外\)。  
  
2.  將選取範圍拖曳到其新位置。  
  
3.  若要將影像中的選取範圍錨定其新位置上，請在選取範圍框線外按一下。  
  
 如需繪製選取範圍的詳細資訊，請參閱[建立自訂筆刷](../mfc/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)