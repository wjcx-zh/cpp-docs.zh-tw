---
title: "Creating a 256-Color Icon or Cursor (Image Editor for Icons) | Microsoft Docs"
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
helpviewer_keywords: 
  - "256-color palette"
  - "cursors, color"
  - "colors, icons"
  - "colors, cursors"
  - "icons, color"
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a 256-Color Icon or Cursor (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

藉由使用影像編輯器，您可以使用能夠從中選取的 256 色調色，將圖示和游標調整為大型圖示和游標 \(64 × 64\)。  在建立資源之後，即選取了裝置影像樣式。  
  
### 若要建立 256 色圖示或游標  
  
1.  在[資源檢視](../windows/resource-view-window.md)中，於您的 .rc 檔上按一下滑鼠右鍵，然後從捷徑功能表中選擇 \[插入資源\]   \(如果您的 .rc 檔中已經有現有的影像資源 \(例如游標\)，則只要在 \[游標\] 資料夾上按一下滑鼠右鍵，然後從捷徑功能表中選取 \[插入游標\] 即可\)。  
  
     **請注意**：如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入資源對話方塊](../windows/add-resource-dialog-box.md)中，選取 \[圖示\] 或 \[游標\]，然後按一下 \[新增\]。  
  
3.  在 \[影像\] 功能表上，按一下 \[新增影像類型\]。  
  
4.  選取您要的 256 色影像樣式。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 None  
  
## 請參閱  
 [Using the 256\-Color Palette](../mfc/using-the-256-color-palette-image-editor-for-icons.md)   
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)