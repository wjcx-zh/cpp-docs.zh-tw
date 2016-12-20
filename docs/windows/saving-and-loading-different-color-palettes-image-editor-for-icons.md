---
title: "Saving and Loading Different Color Palettes (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.image.color"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "color palettes [C++]"
  - "palettes"
  - "palettes, Image editor"
  - "colors [C++], Image editor"
  - "Image editor [C++], palettes"
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Saving and Loading Different Color Palettes (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以儲存及載入色彩調色盤，其中包含[自訂色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  \(根據預設，啟動 Visual Studio 時，會自動載入最近使用的色彩調色盤。\)  
  
> [!TIP]
>  由於影像編輯器沒有任何方法來還原預設色彩調色盤，您應該以 standard.pal 或 default.pal 這類名稱儲存預設色彩調色盤，好讓您可以輕鬆地還原預設設定。  
  
### 若要儲存自訂色彩調色盤  
  
1.  從 \[**影像**\] 功能表中，選擇 \[**儲存調色盤**\]。  
  
2.  瀏覽至您要儲存調色盤的目錄，然後輸入調色盤的名稱。  
  
3.  按一下 \[**儲存**\]。  
  
### 若要載入自訂色彩調色盤  
  
1.  從 \[**影像**\] 功能表中，選擇 \[**載入調色盤**\]。  
  
2.  在 \[[載入色彩調色盤](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)\] 對話方塊中，瀏覽至正確的目錄，然後選取您想要載入的調色盤。  即會以 .pal 副檔名儲存色彩調色盤。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 無  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)