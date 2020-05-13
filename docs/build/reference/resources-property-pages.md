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
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336082"
---
# <a name="resources-property-page"></a>資源屬性頁

對於本機 Windows 桌面程式,生成呼叫[資源編譯器 (rc.exe)](/windows/win32/menurc/resource-compiler)將圖像、字串表和 *.res*檔案添加到二進位檔案。 此屬性頁中公開的屬性將傳遞給資源編譯器,而不是C++編譯器或連結器。 有關此處列出的屬性及其映射到RC命令列選項的詳細資訊,請參閱[使用RC(RC 命令列)。](/windows/win32/menurc/using-rc-the-rc-command-line-) 有關如何存**取 參考資料**屬性頁的資訊,請參閱[在 Visual Studio 中設定 C++編譯器和產生屬性](../working-with-project-properties.md)。 若要以程式設計方式存取這些屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>。

C++/CLI 應用程式中的 .NET 資源的屬性在[「託管資源屬性頁](managed-resources-property-page.md)」中公開。

## <a name="preprocessor-definitions"></a>前置處理器定義

為資源編譯器指定一個或多個定義。 (/d[宏])

## <a name="undefine-preprocessor-definitions"></a>取消前置處理器的定義

取消定義符號。 (/u)

## <a name="culture"></a>文化特性

列出資源中使用的區域性(如美國英語或義大利文)。 (/l [數位])

## <a name="additional-include-directories"></a>其他 Include 目錄

指定要添加到包含路徑的一個或多個目錄;如果有多個,請使用分號分隔符。 (/I[路徑])

## <a name="ignore-standard-include-paths"></a>忽略標準包含路徑

防止資源編譯器在 INCLUDE 環境變數中指定的目錄中搜索包含檔。 (/X)

## <a name="show-progress"></a>顯示進度

將進度訊息發送到輸出視窗。 (/v)

## <a name="suppress-startup-banner"></a>隱藏啟動橫幅

禁止顯示啟動橫幅和資訊消息 (/nologo)

## <a name="resource-file-name"></a>資源檔名

指定資源檔案 (/fo_file_)的名稱

## <a name="null-terminate-strings"></a>空終止字串

將 null 追加到字串表中的所有字串。 (/n)

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)
