---
title: "Saving Bitmaps as GIFs or JPEGs (Image Editor for Icons) | Microsoft Docs"
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
  - ".gif files, saving bitmaps as"
  - "jpg files, saving bitmaps as"
  - "jpeg files, saving bitmaps as"
  - ".jpg files, saving bitmaps as"
  - "Image editor [C++], converting image formats"
  - "gif files, saving bitmaps as"
  - "bitmaps [C++], converting formats"
  - ".jpeg files, saving bitmaps as"
  - "graphics [C++], converting formats"
  - "images [C++], converting formats"
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Saving Bitmaps as GIFs or JPEGs (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立點陣圖時，影像是以點陣圖格式 \(.bmp\) 建立的。  不過，您可將影像儲存為 GIF 或 JPEG 或是其他圖形格式。  
  
> [!NOTE]
>  這項程序不適用於圖示和游標。  
  
### 若要建立點陣圖並將其儲存為 .gif 或 .jpeg  
  
1.  在 \[檔案\] 功能表上，選擇 \[開啟\]，再按一下 \[檔案\]。  
  
2.  在 \[**新增檔案**\] 對話方塊中，按一下 \[Visual C\+\+\] 資料夾，然後在 \[範本\] 方塊內選取 \[點陣圖檔 \(.bmp\)\]，接著按一下 \[開啟\]。  
  
     點陣圖即開啟於 \[影像\] 編輯器內。  
  
3.  依需要變更新的點陣圖。  
  
4.  在點陣圖仍開啟於 \[影像編輯器\] 內時，按一下 \[檔案\] 功能表上的 \[另存 filename.bmp 為\]。  
  
5.  在 \[另存新檔\] 對話方塊中，於 \[檔名\] 方塊內輸入代表您要的檔案格式之檔名和副檔名，  例如 myfile.gif。  
  
     **注意**：您必須在專案外建立或開啟點陣圖，才能將它儲存為另一種檔案格式。  如果您在專案內建立或開啟它，則將無法使用 \[另存新檔\] 命令。  如需詳細資訊，請參閱[在專案外 \(獨立式\) 檢視資源指令碼檔中的資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
6.  按一下 \[**儲存**\]。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 請參閱  
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)