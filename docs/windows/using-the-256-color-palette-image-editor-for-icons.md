---
title: "Using the 256-Color Palette (Image Editor for Icons) | Microsoft Docs"
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
  - "256-color palette"
  - "colors, icons and cursors"
  - "cursors, color"
  - "color palettes, 256-color"
  - "palettes, 256-color"
  - "icons, color"
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Using the 256-Color Palette (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用從 256 色調色盤中選取的色彩來繪圖，您必須從[色彩視窗](../windows/colors-window-image-editor-for-icons.md)中的調色盤中選取色彩。  
  
### 若要從 256 色調色盤中選擇大型圖示的色彩  
  
1.  選取大型圖示或游標，或是建立新的大型圖示或游標。  
  
2.  從 \[色彩\] 視窗中的調色盤所顯示的 256 個色彩中，選擇一個色彩。  
  
     所選取的色彩將會成為 \[色彩\] 視窗中調色盤目前的色彩。  
  
    > [!NOTE]
    >  用於 256 色影像的初始調色盤符合 CreateHalftonePalette Windows API 所傳回的調色盤。  所有供 Windows Shell 使用的圖示都應使用此調色盤來防止調色盤實體化期間發生重繪 \(Flicker\)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Creating a 256\-Color Icon or Cursor](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)