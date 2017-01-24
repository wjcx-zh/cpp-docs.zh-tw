---
title: "輸入和輸出、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊 | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.OutputManifestFile"
  - "VC.Project.VCManifestTool.InputResourceManifests"
  - "VC.Project.VCManifestTool.EmbedManifest"
  - "VC.Project.VCManifestTool.AdditionalManifestFiles"
  - "VC.Project.VCManifestTool.DependencyInformationFile"
  - "VC.Project.VCManifestTool.OutputResourceManifest"
  - "VC.Project.VCManifestTool.GenerateCatalogFiles"
dev_langs: 
  - "C++"
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 輸入和輸出、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個對話方塊，即可指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的輸入和輸出選項。  
  
 若要存取這個屬性頁對話方塊，請開啟專案的屬性頁或屬性工作表。  展開 \[**組態屬性**\] 下的 \[**資訊清單工具**\] 節點，然後選取 \[**輸入和輸出**\]。  
  
## UIElement 清單  
 **其他資訊清單檔**  
 使用 **\/manifest** 選項指定資訊清單工具將處理或合併的其他資訊清單檔的完整路徑。  完整路徑會以分號 \(;\) 分隔。  
  
 **輸入資源資訊清單**  
 使用 **\/inputresource** 選項指定 RT\_MANIFEST 型別資源的完整路徑，以輸入至資訊清單工具中。  這個路徑後面可以接著指定的資源 ID。  例如：  
  
 `dll_with_manifest.dll;#1`  
  
 資源 ID 是選擇性的，在 winuser.h 中預設值為 CREATEPROCESS\_MANIFEST\_RESOURCE\_ID。  
  
 **內嵌資訊清單**  
 \[**是**\] 會指定專案系統在組件中內嵌應用程式資訊清單檔。  
  
 \[**否**\] 會指定專案系統將應用程式資訊清單檔建立為獨立檔案。  
  
 **輸出資訊清單檔**  
 指定輸出資訊清單檔名稱。  當資訊清單工具只在一個資訊清單檔上操作時，這個屬性才是選擇性的。  
  
 **資訊清單資源檔**  
 指定用來將資訊清單內嵌到專案輸出的輸出資源檔案。  
  
 **產生目錄檔**  
 使用 **\/makecdfs** 選項指定資訊清單工具將產生用來製作目錄的目錄定義檔 \(.cdf 檔\)。  
  
 **從 ManagedAssembly 產生資訊清單**  
 從 Managed 組件產生資訊清單。  \(**\-managedassemblyname:***file*\)。  
  
 **抑制相依性項目**  
 搭配 **\-managedassembly** 選項使用。  這個標記會抑制在最終資訊清單中產生相依性項目。  
  
 **產生分類標記**  
 搭配 **\-managedassembly** 選項使用。  這個標記會產生分類標記。  
  
 **啟用 DPI 感知**  
 指定應用程式是否為 DPI 感知。  預設情況下，MFC 專案的設定為 \[**是**\]，其他專案則為 \[**否**\]，因為只有 MFC 專案具有內建的 DPI 感知。  如果您加入程式碼以處理不同的 DPI 設定，即可將設定覆寫為 \[**是**\]。  如果您的應用程式沒有 DPI 感知，而您卻將其設定為 DPI 感知，便可能出現模糊或變小的情形。  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)   
 [如何：編輯專案屬性工作表](../misc/how-to-edit-project-property-sheets.md)