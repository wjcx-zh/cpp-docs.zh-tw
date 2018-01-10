---
title: "資訊清單工具輸入與輸出屬性 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
dev_langs: C++
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77137e9bc0a4af60080234aac85afa59034d2c6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>輸入和輸出、 資訊清單工具、 組態屬性、 &lt;Projectname&gt;屬性頁對話方塊
使用此對話方塊即可指定輸入和輸出選項[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要存取此屬性頁對話方塊中，開啟您的專案或屬性工作表的屬性頁。 展開**資訊清單工具**節點下的**組態屬性**，然後選取**輸入和輸出**。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **其他資訊清單檔**  
 使用**/資訊清單**選項來指定完整路徑的資訊清單工具將會處理的其他資訊清單檔或合併。 完整路徑是以分號分隔。  
  
 **輸入的資源資訊清單**  
 使用**/inputresource**選項來指定資源 RT_MANIFEST，以輸入至資訊清單工具類型的完整路徑。 路徑後面可以接著指定的資源識別碼。 例如:   
  
 `dll_with_manifest.dll;#1`  
  
 資源識別碼是選擇性，預設值為 CREATEPROCESS_MANIFEST_RESOURCE_ID winuser.h 中。  
  
 **內嵌資訊清單**  
 **[是]**指定專案系統會將應用程式資訊清單檔內嵌至組件。  
  
 **否**指定專案系統將會建立為獨立檔案的應用程式資訊清單檔案。  
  
 **輸出資訊清單檔案**  
 指定輸出資訊清單檔案的名稱。 當只有一個資訊清單檔案由資訊清單工具操作時，這個屬性是選擇性的。  
  
 **資訊清單資源檔**  
 指定資源檔用來將資訊清單嵌入專案輸出的輸出。  
  
 **產生目錄檔案**  
 使用**/makecdfs**選項來指定資訊清單工具會產生用來製作目錄的類別目錄定義檔案 （目錄的.cdf 檔）。  
  
 **從 ManagedAssembly 產生資訊清單**  
 從 managed 組件中產生資訊清單。 (**-managedassemblyname:***檔案*)。  
  
 **隱藏相依性項目**  
 搭配**-managedassembly 使用**選項。 此標記不產生的最後一個資訊清單中的相依性項目。  
  
 **產生分類標記**  
 搭配**-managedassembly 使用**選項。 此標記會導致產生分類標記。  
  
 **啟用 DPI 感知**  
 指定是否為 DPI 感知應用程式。 根據預設，此設定是**是**MFC 專案和**否**因為只有 MFC 專案有內建的 DPI 感知，否則為。 您可以覆寫來設定**是**如果您將加入程式碼來處理不同 DPI 設定。 您的應用程式可能在模糊或小型，如果您將它設定為 DPI 感知時，就會顯示。  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)   