---
title: "XML 文件產生器工具屬性頁 | Microsoft Docs"
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
  - "VC.Project.VCXDCMakeTool.ValidateIntelliSense"
  - "VC.Project.VCXDCMakeTool.SuppressStartupBanner"
  - "VC.Project.VCXDCMakeTool.DocumentLibraryDependencies"
  - "VC.Project.VCXDCMakeTool.OutputDocumentFile"
  - "VC.Project.VCXDCMakeTool.AdditionalDocumentFiles"
dev_langs: 
  - "C++"
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# XML 文件產生器工具屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\[XML 文件產生器工具\] 屬性頁會公開 xdcmake.exe 功能。  當您的原始程式碼包含文件註解，並指定 [\/doc \(處理文件註解\)](../build/reference/doc-process-documentation-comments-c-cpp.md) 時，xdcmake.exe 將 .xdc 檔案合併到 .xml 檔案。  請參閱[建議使用的文件註解標籤](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)，以取得在原始程式碼中加入文件註解的資訊。  
  
> [!NOTE]
>  在開發環境中的 xdcmake.exe 選項 \(屬性頁\) 與 xdcmake.exe 在命令列下所能使用的選項不同。  如需在命令列下使用 xdcmake.exe 的資訊，請參閱 [XDCMake 參考](../ide/xdcmake-reference.md)。  
  
## UIElement 清單  
 **隱藏程式啟始資訊**  
 隱藏著作權訊息。  
  
 **其他文件檔**  
 您要讓專案系統尋找 .xdc 檔案的其他目錄。  xdcmake 會永遠尋找由專案所產生的 .xdc 檔案。  您可以指定多個目錄。  
  
 **輸出文件檔**  
 .xml 輸出檔的名稱和目錄位置。  請參閱[建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)，以取得使用巨集來指定目錄位置的資訊。  
  
 **文件程式庫相依性**  
 如果您的專案對方案中的 .lib 專案具有相依性，您可以從 .lib 專案將 .xdc 檔案處理到目前專案的 .xml 檔案中。  
  
## 請參閱  
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [屬性頁](../ide/property-pages-visual-cpp.md)