---
title: "進階、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊 | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.KeyFile"
  - "VC.Project.VCManifestTool.UpdateFileHashes"
  - "VC.Project.VCManifestTool.UpdateFileHashesSearchPath"
  - "VC.Project.VCManifestTool.ValidateSignature"
  - "VC.Project.VCManifestTool.KeyContainer"
dev_langs: 
  - "C++"
ms.assetid: 3d587366-05ea-4956-a978-313069660735
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 進階、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個對話方塊可以指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的進階選項。  
  
 若要存取這個屬性頁對話方塊，請開啟專案的屬性頁或屬性工作表。  展開 \[**組態屬性**\] 下的 \[**資訊清單工具**\] 節點，然後選取 \[**進階**\]。  
  
## UIElement 清單  
 **更新檔案雜湊**  
 使用 \/hashupdate 選項指定，資訊清單工具將計算 `<file>` 項目中所指定檔案的雜湊，然後使用計算出的值更新雜湊屬性。  
  
 **更新檔案雜湊搜尋路徑**  
 指定 `<file>` 項目中所參考檔案的搜尋路徑。  這個選項也使用 \/hashupdate 選項。  
  
## 請參閱  
 [\<file\> 項目](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)   
 [如何：編輯專案屬性工作表](../misc/how-to-edit-project-property-sheets.md)