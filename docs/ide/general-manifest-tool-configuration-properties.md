---
title: "一般、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊 | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.MergeRulesFile"
  - "VC.Project.VCManifestTool.UseUnicodeResponseFiles"
  - "VC.Project.VCManifestTool.SuppressStartupBanner"
  - "VC.Project.VCManifestTool.UseFAT32Workaround"
  - "VC.Project.VCManifestTool.VerboseOutput"
  - "VC.Project.VCManifestTool.AssemblyIdentity"
dev_langs: 
  - "C++"
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個對話方塊，即可指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的一般選項。  
  
 若要存取這個屬性頁對話方塊，請開啟專案的屬性頁或屬性工作表。  展開 \[**組態屬性**\] 下的 \[**資訊清單工具**\] 節點，然後選取 \[**一般**\]。  
  
## UIElement 清單  
 **隱藏程式啟始資訊**  
 \[**是 \(\/nologo\)**\] 會指定在啟動資訊清單工具時，隱藏標準的 Microsoft 著作權資料。  當您隨建置程序或從建置環境執行 mt.exe 時，請使用這個選項隱藏記錄檔中不要的輸出。  
  
 **詳細資訊輸出**  
 \[**是 \(\/verbose\)**\] 會指定在產生資訊清單期間，顯示其他建置資訊。  
  
 **組件識別**  
 使用 \/identity 選項指定識別字串，它會組成 [\<assemblyIdentity\> 項目](../Topic/%3CassemblyIdentity%3E%20Element%20\(ClickOnce%20Application\).md) 的屬性。  識別字串是以 `name` 屬性的值開頭，後面接著 *attribute* \= *value* 組。  識別字串中的屬性會以逗號 \(,\) 分隔。  
  
 以下為識別字串的範例：  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)   
 [如何：編輯專案屬性工作表](../misc/how-to-edit-project-property-sheets.md)