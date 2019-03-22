---
title: 為 Visual C++ 專案建立的檔案類型
ms.date: 11/04/2016
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: 7ef8127b829b60d84af72874292c33ae1c7c4636
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58327577"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>為 Visual Studio c + + 專案建立的檔案類型

本主題描述所有類型的傳統桌面應用程式的 Visual Studio 專案相關聯的檔案。 您的專案中包含的實際檔案取決於專案類型以及您使用精靈時選取的選項。

- [專案和方案檔](project-and-solution-files.md)

- [CLR 專案](files-created-for-clr-projects.md)

- [ATL 程式或控制項原始程式檔和標頭檔](atl-program-or-control-source-and-header-files.md)

- [MFC 程式或控制項原始程式檔和標頭檔](mfc-program-or-control-source-and-header-files.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

- [資源檔](resource-files-cpp.md)

- [說明檔 (WinHelp)](help-files-winhelp.md)

- [提示檔案](hint-files.md)

當您建立 Visual Studio 專案時，您可以建立新的方案，或您可能會將專案加入方案。 非一般應用程式通常是與方案中的多個專案一起開發。

專案通常會產生 EXE 或 DLL。 專案可以是依存於彼此;在建置過程中，Visual Studio 環境會檢查內以及專案之間的相依性。 每個專案都有核心原始程式碼，並且根據專案類型，它可能有許多包含專案各個層面的其他檔案。 這些檔案的內容會以副檔名表示。 Visual Studio 開發環境使用副檔名來決定如何在建置期間處理檔案內容。

下表顯示常見的檔案在 Visual Studio 專案中，並以其副檔名來識別它們。

|副檔名|類型|內容|
|--------------------|----------|--------------|
|.asmx|原始程式檔|部署檔案。|
|.asp|原始程式檔|Active Server Page 檔。|
|.atp|專案|應用程式範本專案檔。|
|.bmp、.dib、.gif、.jpg、.jpe、.png|資源|一般影像檔。|
|.bsc|編譯|瀏覽器程式碼檔。|
|.cpp.c|原始程式檔|您的應用程式的主要原始程式碼檔。|
|.cur|資源|資料指標點陣圖形檔。|
|.dbp|專案|資料庫專案檔。|
|.disco|原始程式檔|動態探索文件檔。 處理 XML Web 服務探索。|
|.exe、.dll|專案|可執行檔或動態連結程式庫檔。|
|.h|原始程式檔|標頭 (Include) 檔。|
|.htm、.html、.xsp、.asp、.htc、.hta、.xml|資源|一般 Web 檔案。|
|.HxC|專案|說明專案檔。|
|.ico|資源|圖示點陣圖形檔。|
|.idb|編譯|狀態檔，其中包含原始程式檔與類別定義之間的相依性資訊，編譯器可以在最少重建和累加編譯期間使用該資訊。 使用 [/Fd](fd-program-database-file-name.md) 編譯器選項以指定 .idb 檔的名稱。 如需詳細資訊，請參閱 [/Gm (啟用最少重建)](gm-enable-minimal-rebuild.md) 。|
|.idl|編譯|介面定義語言檔。 如需詳細資訊，請參閱 Windows SDK 中的 [Interface Definition (IDL) File](/windows/desktop/Rpc/the-interface-definition-language-idl-file) (介面定義 (IDL) 檔)。|
|.ilk|連結|累加連結檔案。 如需詳細資訊，請參閱 [/INCREMENTAL](incremental-link-incrementally.md) 。|
|.map|連結|包含連結器資訊的文字檔。 使用 [/Fm](fm-name-mapfile.md) 編譯器選項來命名對應檔。 如需詳細資訊，請參閱 [/MAP](map-generate-mapfile.md) 。|
|.mfcribbon-ms|資源|資源檔，其中包含定義功能區按鈕、控制項和屬性的 XML 程式碼。 如需詳細資訊，請參閱 [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md)。|
|.obj、.o||目的檔，已編譯但尚未連結。|
|.pch|偵錯|先行編譯標頭檔。|
|.rc、.rc2|資源|用以產生資源的[資源指令碼檔](../../windows/working-with-resource-files.md) 。|
|.sbr|編譯|原始程式瀏覽器中繼檔案。 [BSCMAKE](bscmake-options.md)的輸入檔。|
|.sln|方案|[「方案」](/visualstudio/ide/solutions-and-projects-in-visual-studio)檔。|
|.suo|方案|方案選項檔。|
|.txt|資源|文字檔，通常是「讀我」檔案。|
|.vap|專案|Visual Studio Analyzer 專案檔。|
|.vbg|方案|相容專案群組檔。|
|.vbp、.vip、.vbproj|專案|Visual Basic 專案檔。|
|.vcxitems|專案|用於在多個 C++ 專案之間共用程式碼檔的共用項目專案。 請參閱[專案和方案檔](project-and-solution-files.md)如需詳細資訊。|
|.vcxproj|專案|Visual Studio 專案檔中。 請參閱[專案和方案檔](project-and-solution-files.md)如需詳細資訊。|
|.vcxproj.filters|專案|使用方案總管將檔案加入專案時，篩選檔會根據檔案的副檔名，定義要在方案總管樹狀檢視中的哪個位置加入檔案。|
|.vdproj|專案|Visual Studio 部署專案檔。|
|.vmx|專案|巨集專案檔。|
|.vup|專案|公用程式專案檔。|

如需與 Visual Studio 相關聯之其他檔案的相關資訊，請參閱 [Visual Studio .NET 中的檔案類型與副檔名](/visualstudio/ide/reference/project-and-solution-file-types)。

專案檔會組織成方案總管中的資料夾。 Visual Studio 會建立原始程式檔、 標頭檔和資源檔的資料夾，但您可以重新組織這些資料夾，或建立新的。 您可以使用資料夾在專案階層內明確地組織檔案邏輯叢集。 例如，您可以建立資料夾，以包含所有使用者介面原始程式檔，或是包含規格、文件或測試套件。 所有的檔案資料夾名稱必須是唯一的。

當您將項目加入專案時，您會將該項目加入該專案的所有組態中，不論項目是否可建置。 例如，如果您有名稱為 MyProject 的專案，加入項目會將其加入偵錯和發行專案組態。

## <a name="see-also"></a>另請參閱

[建立和管理 Visual Studio c + + 專案](../creating-and-managing-visual-cpp-projects.md)<br>
[Visual Studio c + + 專案類型](visual-cpp-project-types.md)<br>