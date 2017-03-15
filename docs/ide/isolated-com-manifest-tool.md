---
title: "隔離的 COM、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊 | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.RegistrarScriptFile"
  - "VC.Project.VCManifestTool.ComponentFileName"
  - "VC.Project.VCManifestTool.TypeLibraryFile"
  - "VC.Project.VCManifestTool.ReplacementsFile"
dev_langs: 
  - "C++"
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 隔離的 COM、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個對話方塊可以指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的 \[**Isolated COM**\] 選項。  
  
 若要存取這個屬性頁對話方塊，請開啟專案的屬性頁或屬性工作表。  展開 \[**通用屬性**\] 下的 \[**資訊清單工具**\] 節點，然後選取 \[**隔離的 COM**\]。  
  
## 工作清單  
  
-   [如何：建置隔離的應用程式以使用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## UIElement 清單  
 **型別程式庫檔案**  
 使用 \/tlb 選項，指定資訊清單工具將用來產生資訊清單檔的型別程式庫檔案名稱 \(.tlb 檔\)。  
  
 **登錄器指令碼檔**  
 使用 \/rgs 選項，指定資訊清單工具將用來產生資訊清單檔的登錄器指令碼檔名 \(.rgs 檔\)。  
  
 **元件檔名**  
 使用 \/dll 選項指定資訊清單工具將產生的資源名稱。  若指定了 \[**型別程式庫檔案**\] 或 \[**登錄器指令碼檔**\] 的值，則必須輸入這個屬性的值。  
  
 **取代檔案**  
 使用 \/replacements 選項，指定包含 .rgs 檔中可取代字串值之檔案的完整路徑。  
  
## 請參閱  
 [隔離應用程式](http://msdn.microsoft.com/library/aa375190)   
 [並排組件](_win32_side_by_side_assemblies)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)   
 [如何：編輯專案屬性工作表](../misc/how-to-edit-project-property-sheets.md)