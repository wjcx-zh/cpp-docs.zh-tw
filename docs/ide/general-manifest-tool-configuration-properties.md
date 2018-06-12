---
title: 資訊清單工具組態屬性 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs:
- C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1953e7c37c07f66845510efe037015a537aa7baa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329084"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>一般、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊
使用此對話方塊即可指定 [Mt.exe](http://msdn.microsoft.com/library/aa375649) 的一般選項。  
  
 若要存取此屬性頁對話方塊，請開啟您專案或屬性工作表的屬性頁。 展開 [組態屬性] 下的 [資訊清單工具] 節點，然後選取 [一般]。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **隱藏啟動橫幅**  
 [是 (/ nologo)] 指定資訊清單工具啟動時，要隱藏標準 Microsoft 著作權資料。 當您執行 mt.exe 作為建置程序的一部分，或從建置環境執行時，使用此選項來隱藏記錄檔中不想要的輸出。  
  
 **詳細資訊輸出**  
 [是 (/verbose)] 指定在資訊清單產生過程將會顯示其他組建資訊。  
  
 **組件識別**  
 使用 /identity 選項指定識別字串，其中包含 [\<assemblyIdentity> 項目](/visualstudio/deployment/assemblyidentity-element-clickonce-application)的屬性。 識別字串開頭為 `name` 屬性的值，後面接著 *attribute* = *value* 組。 識別字串中的屬性是以逗號分隔。  
  
 以下為範例識別字串：  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)   