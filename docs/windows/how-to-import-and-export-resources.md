---
title: "How to: Import and Export Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resvw.resource.importing"
  - "vc.resvw.resource.importing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], exporting"
  - "graphics [C++], exporting"
  - "graphics [C++], importing"
  - "resources [Visual Studio], importing"
  - "bitmaps [C++], importing and exporting"
  - "toolbars [C++], importing"
  - "images [C++], importing"
  - "toolbars [C++], exporting"
  - "cursors [C++], importing and exporting"
  - "images [C++], exporting"
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# How to: Import and Export Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以匯入圖形資源 \(點陣圖、圖示、游標和工具列\)、HTML 檔案，及在 Visual C\+\+ 中使用的自訂資源。  您可以從 Visual C\+\+ 專案匯出相同類型的檔案，分隔可以在開發環境外部使用的檔案。  
  
> [!NOTE]
>  資源類型 \(例如加速器、對話方塊和字串資料表\) 無法匯入或匯出，因為它們不是獨立的檔案類型。  
  
### 將個別的資源匯入目前的資源檔  
  
1.  在[資源檢視](../windows/resource-view-window.md)中，在要將資源新增到的資源指令碼 \(\*.rc\) 檔案的節點上按一下滑鼠右鍵。  
  
2.  在捷徑功能表上按一下 \[**匯入**\]。  
  
3.  找出並選取點陣圖 \(.bmp\)、圖示 \(.ico\)、游標 \(.cur\)、Html 檔案 \(.htm\)，或是您要匯入的其他檔案的檔案名稱。  
  
4.  按一下 \[**確定**\]，將資源新增到 \[**資源**\] 檢視中選取的檔案。  
  
    > [!NOTE]
    >  無論選取哪一種特定的資源類型，匯入程序都會以相同的方式運作。  會針對該資源類型，將匯入的資源自動加入至正確的節點。  
  
### 匯出點陣圖、圖示或游標做為個別的檔案 \(在 Visual C\+\+ 外部使用\)  
  
1.  在 \[**資源**\] 檢視中，在要匯出的資源按一下滑鼠右鍵。  
  
2.  在捷徑功能表上按一下 \[**匯出**\]。  
  
3.  在 \[**匯出資源**\] 對話方塊中，接受目前的檔案名稱或輸入一個新名稱。  
  
4.  瀏覽至要儲存檔案的資料夾，然後按一下 \[**匯出**\]。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)