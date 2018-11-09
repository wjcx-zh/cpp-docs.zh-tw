---
title: NMake 屬性頁 (Windows C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: 7d890794d706a687b9cf945022aa4c230684131d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473537"
---
# <a name="nmake-property-page"></a>NMake 屬性頁

**NMake** 屬性頁可讓您指定 NMake 專案的建置設定。

如需 NMake 專案的詳細資訊，請參閱[建立 Makefile 專案](../ide/creating-a-makefile-project.md)。 對於非 Windows MakeFile 專案，請參閱 [MakeFile 專案屬性 (Linux C++)](../linux/prop-pages/makefile-linux.md)、[一般專案屬性 (Android C++ Makefile)](/visualstudio/cross-platform/general-makefile-android-prop-page) 或 [NMake 屬性 (Android C++)](/visualstudio/cross-platform/nmake-android-prop-page)。

[NMake] 屬性頁包含下列屬性。

## <a name="uielement-list"></a>UIElement 清單

- **Build 命令列**

   指定在 [建置] 功能表上按一下 [Build] 時要執行的命令。

- **Rebuild All 命令列**

   指定在 [建置] 功能表上按一下 [Rebuild All] 時要執行的命令。

- **Clean 命令列**

   指定在 [建置] 功能表上按一下 [Clean] 時要執行的命令。

- **輸出**

   指定將包含命令列輸出之檔案的名稱。 根據預設，這個檔案名稱是根據專案名稱。

- **前置處理器定義**

   指定原始程式檔使用的任何前置處理器定義。 預設值取決於目前的平台和組態。

- **Include 搜尋路徑**

   指定編譯器搜尋 Include 檔的目錄。

- **強制包含**

   指定前置處理器會自動處理的檔案，即使它們未包含在專案檔中。

- **組件搜尋路徑**

   指定 .NET Framework 嘗試解析 .NET 組件時搜尋的目錄。

- **強制使用組件**

   指定 .NET Framework 自動處理的組件。

- **其他選項**

   指定 IntelliSense 剖析 C++ 檔案時要使用的任何其他編譯器參數。

如需如何存取 [NMake] 屬性頁的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

如需如何以程式設計方式存取此物件成員的資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>。

## <a name="see-also"></a>請參閱

[屬性頁](../ide/property-pages-visual-cpp.md)<br>
[如何：在 Makefile 專案中啟用 IntelliSense](../ide/how-to-enable-intellisense-for-makefile-projects.md)