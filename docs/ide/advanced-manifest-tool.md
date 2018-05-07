---
title: 進階、 資訊清單工具、 組態屬性、 &lt;Projectname&gt;屬性頁對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
dev_langs:
- C++
ms.assetid: 3d587366-05ea-4956-a978-313069660735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47d4dc3ab325a7346d0e787a15d69d646896827d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>進階、 資訊清單工具、 組態屬性、 &lt;Projectname&gt;屬性頁對話方塊
使用此對話方塊即可指定進階的選項[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要存取此屬性頁對話方塊中，開啟您的專案或屬性工作表的屬性頁。 展開**資訊清單工具**節點下的**組態屬性**，然後選取**進階**。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **更新檔案雜湊**  
 會使用 /hashupdate 選項來指定資訊清單工具將會計算中指定檔案的雜湊`<file>`項目，並更新屬性的計算值的雜湊。  
  
 **更新檔案雜湊搜尋路徑**  
 指定檔案中所參考的搜尋路徑`<file>`項目。 此選項也會使用 /hashupdate 選項。  
  
## <a name="see-also"></a>另請參閱  
 [\<檔案 > 項目](/visualstudio/deployment/file-element-clickonce-application)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)   