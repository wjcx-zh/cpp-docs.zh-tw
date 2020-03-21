---
title: 資源
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 4f3688da4feb11f673e11372e5df086dc8c7e21a
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078283"
---
# <a name="resources-property-page"></a>資源屬性頁

針對原生 Windows 桌面程式，組建會叫用[資源編譯器（rc）](/windows/win32/menurc/resource-compiler) ，將影像、字串資料表和 *.res*檔案加入至二進位檔。 這個屬性頁中公開的屬性會傳遞給資源編譯器，而不是C++編譯器或連結器。 如需此處所列屬性及其如何對應至 RC 命令列選項的詳細資訊，請參閱[使用 rc （Rc 命令列）](/windows/win32/menurc/using-rc-the-rc-command-line-)。 如需如何存取 [**資源**] 屬性頁的詳細資訊，請參閱[Visual Studio 中的設定C++編譯器和組建屬性](../working-with-project-properties.md)。 若要以程式設計方式存取這些屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>。

/Cli 應用程式中C++.net 資源的屬性會在 [[受控資源] 屬性頁](managed-resources-property-page.md)中公開。

## <a name="preprocessor-definitions"></a>前置處理器定義

指定資源編譯器的一或多個定義。 （/d [宏]）

## <a name="undefine-preprocessor-definitions"></a>取消前置處理器的定義

取消定義符號。 u

## <a name="culture"></a>文化特性

列出資源中所使用的文化特性（例如美式英文或義大利文）。 （/l [num]）

## <a name="additional-include-directories"></a>其他 Include 目錄

指定一或多個要新增至 include 路徑的目錄;如果有一個以上，請使用分號分隔符號。 （/I [路徑]）

## <a name="ignore-standard-include-paths"></a>忽略標準 Include 路徑

防止資源編譯器在 INCLUDE 環境變數中指定的目錄中搜尋 include 檔案。 /X

## <a name="show-progress"></a>顯示進度

將進度訊息傳送至輸出視窗。 停

## <a name="suppress-startup-banner"></a>隱藏啟動橫幅

隱藏啟動橫幅和資訊訊息（/nologo）的顯示

## <a name="resource-file-name"></a>資源檔名稱

指定資源檔的名稱（/fo [file]）

## <a name="null-terminate-strings"></a>Null 終止字串

將 null 附加至字串資料表中的所有字串。 /n

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)