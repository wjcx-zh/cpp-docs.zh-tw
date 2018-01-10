---
title: "資訊清單工具 （Visual c + +） 的組態屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
dev_langs: C++
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e5e56c823a7a30850e24e393a545f0df6a6637a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>一般、 資訊清單工具、 組態屬性、 &lt;Projectname&gt;屬性頁對話方塊
使用此對話方塊來指定的一般選項[Mt.exe](http://msdn.microsoft.com/library/aa375649)。  
  
 若要存取此屬性頁對話方塊中，開啟您的專案或屬性工作表的屬性頁。 展開**資訊清單工具**節點下的**組態屬性**，然後選取**一般**。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **隱藏程式啟始資訊**  
 **是 (/ nologo)**指定資訊清單工具啟動時，是否將隱藏標準 Microsoft 著作權資料。 使用此選項來隱藏不想要的輸出記錄檔中，當您執行 mt.exe 做為建置程序，或從建置環境的一部分。  
  
 **詳細資訊輸出**  
 **是 (/verbose)**指定其他組建資訊將會顯示在資訊清單產生過程。  
  
 **組件識別**  
 使用 /identity 選項，指定識別字串，其中包含的屬性[ \<assemblyIdentity > 項目](/visualstudio/deployment/assemblyidentity-element-clickonce-application)。 識別字串開頭的值`name`屬性，且後面*屬性* = *值*組。 識別字串中的屬性是以逗號分隔。  
  
 識別字串的範例如下：  
  
 `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)   
 [資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)   
 [使用專案屬性](../ide/working-with-project-properties.md)   