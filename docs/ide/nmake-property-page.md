---
title: "NMake 屬性頁 (c + + Windows) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs:
- C++
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc9f6dc7c5fec4a184ed189cfaae230df3f1e9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-property-page"></a>NMake 屬性頁
**NMake**屬性頁可讓您指定 NMake 專案的建置設定。  
  
 如需 NMake 專案的詳細資訊，請參閱[建立 Makefile 專案](../ide/creating-a-makefile-project.md)。 Non_Windows MakeFile 專案，請參閱[MakeFile 專案屬性 （Linux c + +）](../linux/prop-pages/makefile-linux.md)，[一般專案屬性 (c + + Android Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page)或[NMake 屬性 （Android c + +）](/visualstudio/cross-platform/nmake-android-prop-page).
  
 **NMake**屬性頁包含下列屬性。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **建置命令列**  
 指定要在執行時命令**建置**按一下**建置**功能表。  
  
 **重建所有的命令列**  
 指定要在執行時命令**全部重建**按一下**建置**功能表。  
  
 **清除命令列**  
 指定要在執行時命令**清除**按一下**建置**功能表。  
  
 **輸出**  
 指定將包含命令列的輸出檔案的名稱。 根據預設，此檔案名稱根據專案名稱。  
  
 **前置處理器定義**  
 指定的來源檔案使用任何前置處理器定義。 預設值取決於目前的平台和組態。  
  
 **包含搜尋路徑**  
 指定在哪裡編譯器搜尋 include 檔的目錄。  
  
 **強制包含**  
 指定前置處理器會自動處理即使它們未包含在專案檔中的檔案。  
  
 **組件搜尋路徑**  
 指定的目錄，.NET Framework 哪裡搜尋時它會解析.NET 組件。  
  
 **強制使用組件**  
 指定自動處理.NET Framework 的組件。  
  
 **其他選項**  
 指定 IntelliSense，它會剖析 c + + 檔案時所要使用任何其他編譯器的參數。  
  
 如需有關如何存取資訊**NMake**屬性頁上，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
 如需如何以程式設計方式存取此物件的成員資訊，請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>。  
  
## <a name="see-also"></a>請參閱  
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [如何：在 Makefile 專案中啟用 IntelliSense](../ide/how-to-enable-intellisense-for-makefile-projects.md)