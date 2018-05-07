---
title: 資訊清單工具隔離的 COM 屬性 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
dev_langs:
- C++
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c425a71f8bb8a7972ade29fb0d18cf3eab7debb5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>隔離的 COM、 資訊清單工具、 組態屬性、 &lt;Projectname&gt;屬性頁對話方塊
使用此對話方塊來指定**隔離的 COM**選項[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要存取此屬性頁對話方塊中，開啟您的專案或屬性工作表的屬性頁。 展開**資訊清單工具**節點下的**通用屬性**，然後選取**隔離的 COM**。  
  
## <a name="task-list"></a>工作清單  
  
-   [如何：建置隔離的應用程式以使用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **類型程式庫檔案**  
 您可以使用 /tlb 選項來指定資訊清單工具將用來產生資訊清單檔案的類型程式庫檔案 （.tlb 檔） 的名稱。  
  
 **登錄器指令碼檔**  
 您可以使用 /rgs 選項來指定資訊清單工具將用來產生資訊清單檔案的登錄器指令碼檔案 （.rgs 檔案） 的名稱。  
  
 **元件的檔案名稱**  
 您可以使用 /dll 選項來指定資訊清單工具會產生資源的名稱。 您必須輸入此屬性的值時的可能值**類型程式庫檔案**或**登錄器指令碼檔**所指定。  
  
 **取代檔案**  
 您可以使用 /replacements 選項來指定檔案，其中包含可取代.rgs 檔中的字串值的完整路徑。  
  
## <a name="see-also"></a>另請參閱  
 [隔離的應用程式](http://msdn.microsoft.com/library/aa375190)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)   