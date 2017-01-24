---
title: "Converting Bitmaps to Toolbars | Microsoft Docs"
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
  - "bitmaps [C++], converting to toolbars"
  - "Toolbar editor, converting bitmaps"
  - "toolbars [C++], converting bitmaps"
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Converting Bitmaps to Toolbars
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可透過轉換點陣圖來建立新的工具列，  點陣圖中的圖形會轉換成工具列的按鈕影像。  通常一張點陣圖會包含多個按鈕影像，每個按鈕都對應到一個影像。  影像可以是任意大小；預設值是寬度為 16 像素，高度為影像的高度。  您可在影像編輯器中選擇 \[影像\] 功能表內的 \[工具列編輯器\]，然後在[新增工具列資源對話方塊](../mfc/new-toolbar-resource-dialog-box.md)中指定按鈕影像的大小。  
  
### 若要將點陣圖轉換為工具列  
  
1.  在[影像編輯器](../mfc/image-editor-for-icons.md)內開啟現有的點陣圖資源   \(如果點陣圖尚未出現在您的 .rc 檔內，請在 .rc 檔上按一下滑鼠右鍵，在捷徑功能表內選擇 \[匯入\]，巡覽至想要加入 .rc 檔內的點陣圖，然後按 \[開啟\]\)。  
  
2.  在 \[影像\] 功能表內選擇 \[工具列編輯器\]。  
  
     [新增工具列資源對話方塊](../mfc/new-toolbar-resource-dialog-box.md)將出現。  您可變更圖示影像的寬度和長度，以便和點陣圖一致。  接著工具列影像就會顯示在工具列編輯器內。  
  
3.  若要完成轉換，請使用[屬性視窗](../Topic/Properties%20Window.md)來變更按鈕的命令 **ID**。  輸入新的 **ID**，或由下拉式清單 \(Drop\-Down List\) 中選取一個 **ID**。  
  
    > [!TIP]
    >  \[屬性\] 視窗的標題列中包含一個圖釘按鈕。  按一下此按鈕可啟用或停用視窗的自動隱藏功能。  若要迅速地輪流顯示所有的工具列按鈕的屬性，而不想重新開啟個別的屬性視窗，請關閉自動隱藏，以便讓屬性視窗保持不動。  
  
 您也可使用[屬性視窗](../Topic/Properties%20Window.md)來變更新工具列內的按鈕命令 ID。  如需編輯新工具列的資訊，請參閱[建立、移動和編輯工具列按鈕](../mfc/creating-moving-and-editing-toolbar-buttons.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 MFC 或 ATL  
  
## 請參閱  
 [Creating New Toolbars](../mfc/creating-new-toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)