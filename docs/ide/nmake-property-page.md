---
title: "NMake 屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.ReBuildCommandLine"
  - "VC.Project.VCNMakeTool.CleanCommandLine"
  - "VC.Project.VCNMakeTool.Output"
  - "VC.Project.VCNMakeTool.BuildCommandLine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMake 屬性頁"
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# NMake 屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\[**NMake**\] 屬性頁可讓您指定 NMake 專案的建置設定。  
  
 如需 NMake 專案的詳細資訊，請參閱[建立 Makefile 專案](../ide/creating-a-makefile-project.md)。  
  
 \[**NMake**\] 屬性頁包含下列屬性。  
  
## UIElement 清單  
 **建置命令列**  
 指定按一下 \[**建置**\] 功能表上的 \[**建置**\] 時要執行的命令。  
  
 **全部重建命令列**  
 指定按一下 \[**建置**\] 功能表上的 \[**全部重建**\] 時要執行的命令。  
  
 **清除命令列**  
 指定按一下 \[**建置**\] 功能表上的 \[**清除**\] 時要執行的命令。  
  
 **Output**  
 指定將包含命令列輸出的檔名。  這個檔名依照預設是根據專案名稱來命名。  
  
 **前置處理器定義**  
 指定原始程式檔使用的任何前置處理器定義。  預設值是由目前的平台和組態決定。  
  
 **包含搜尋路徑**  
 指定編譯器會於其中搜尋包含檔案的目錄。  
  
 **強制包含**  
 指定即使沒有包含在專案檔中，前置處理器也會自動處理的檔案。  
  
 **組件搜尋路徑**  
 指定 .NET Framework 嘗試解析 .NET 組件時所搜尋的目錄。  
  
 **強制使用組件**  
 指定 .NET Framework 會自動處理的組件。  
  
 **其他選項**  
 為 IntelliSense 指定剖析 C\+\+ 檔案時使用的其他任何編譯器參數。  
  
 如需如何存取 \[**NMake**\] 屬性頁的詳細資訊，請參閱 [如何：使用屬性頁指定專案屬性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
 如需如何以程式設計方式存取此物件之成員的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>。  
  
## 請參閱  
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [如何：在 Makefile 專案中啟用 IntelliSense](../ide/how-to-enable-intellisense-for-makefile-projects.md)