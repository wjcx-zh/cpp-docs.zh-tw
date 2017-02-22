---
title: "Creating an Icon or Other Image (Image Editor for Icons) | Microsoft Docs"
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
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitmaps [C++]"
  - "images [C++], creating"
  - "resource toolbars"
  - "resources [Visual Studio], creating images"
  - "bitmaps [C++], creating"
  - "graphics [C++], creating"
  - "Image editor [C++], creating images"
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Creating an Icon or Other Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可建立新的影像 \(點陣圖、圖示、游標或工具列\)，然後使用影像編輯器來自訂其外觀。  您也可以仿傚[範本](../windows/how-to-use-resource-templates.md)建立新的點陣圖圖樣。  
  
### 若要將新的影像資源加入至 Unmanaged C\+\+ 專案  
  
1.  在[資源檢視](../windows/resource-view-window.md)中，於您的 .rc 檔上按一下滑鼠右鍵，然後從捷徑功能表中選擇 \[插入資源\]   \(如果您的 .rc 檔中已經有現有的影像資源 \(例如游標\)，則只要在 \[游標\] 資料夾上按一下滑鼠右鍵，然後從捷徑功能表中選取 \[插入游標\] 即可\)。  
  
    > [!NOTE]
    >  **請注意**：如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入資源對話方塊](../windows/add-resource-dialog-box.md)中，選取您想建立的影像資源類型 \(例如 \[點陣圖\]\)，然後按一下 \[新增\]。  
  
     如果 \[插入資源\] 對話方塊中的影像資源類型旁邊出現一個加號 \(**\+**\)，表示可以使用工具列範本。  按一下加號可展開範本清單，請選取一個範本，然後按一下 \[新增\]。  
  
### 若要將新的影像資源加入至以 .NET 程式語言撰寫的專案  
  
1.  **方案總管**中，在專案資料夾 \(例如 **WindowsApplication1**\) 上按一下滑鼠右鍵。  
  
2.  從捷徑功能表中按一下 \[加入\]，再按一下 \[加入新項目\]。  
  
3.  在 \[類別\] 窗格，展開 \[本機專案項目\] 資料夾，再選擇 \[資源\]。  
  
4.  在 \[範本\] 窗格，選擇您想要加入至專案的資源類型。  
  
     該項資源將會加入至 \[方案總管\] 中的專案，並會在[影像編輯器](../mfc/image-editor-for-icons.md)中開啟。  現在，您可以使用影像編輯器中的所有工具來修改影像。  如需將影像加入至 Managed 專案的詳細資訊，請參閱[在設計階段載入圖片](../Topic/How%20to:%20Load%20a%20Picture%20Using%20the%20Designer%20\(Windows%20Forms\).md)。  
  
    > [!NOTE]
    >  您想要編輯的任何 Managed 資源皆必須為連結的資源。  Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  如需詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[建立資源檔](../Topic/Creating%20Resource%20Files%20for%20Desktop%20Apps.md)章節。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Converting Bitmaps to Toolbars](../mfc/converting-bitmaps-to-toolbars.md)   
 [Creating New Toolbars](../mfc/creating-new-toolbars.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)