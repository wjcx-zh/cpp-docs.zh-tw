---
title: 為 Visual Studio C++專案所建立的檔案類型
ms.date: 04/08/2019
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
ms.openlocfilehash: 078c83a9c95c1b143af2037240d5cc0a16211827
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492876"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>為 Visual Studio C++專案所建立的檔案類型

許多類型的檔案都與傳統桌面應用程式的 Visual Studio 專案相關聯。 您的專案中包含的實際檔案取決於專案類型以及您使用精靈時選取的選項。

- [專案和方案檔](project-and-solution-files.md)

- [CLR 專案](files-created-for-clr-projects.md)

- [ATL 程式或控制項原始程式檔和標頭檔](atl-program-or-control-source-and-header-files.md)

- [MFC 程式或控制項原始程式檔和標頭檔](mfc-program-or-control-source-and-header-files.md)

- [先行編譯標頭檔](../creating-precompiled-header-files.md)

- [資源檔](resource-files-cpp.md)

- [說明檔 (WinHelp)](help-files-winhelp.md)

- [提示檔案](hint-files.md)

當您建立 Visual Studio 專案時, 您可以在新的方案中建立它, 也可以將專案加入現有的方案中。 非一般應用程式通常是與方案中的多個專案一起開發。

專案通常會產生 EXE 或 DLL。 專案可以彼此相依;在建立過程中, Visual Studio 環境會檢查項目內和之間的相依性。 每個專案通常都有核心原始程式碼。 視專案類型而定, 可能會有許多其他檔案包含專案的各個層面。 這些檔案的內容會以副檔名表示。 Visual Studio 開發環境使用副檔名來決定如何在建置期間處理檔案內容。

下表顯示 Visual Studio 專案中的一般檔案, 並以其副檔名加以識別。

|副檔名|類型|內容|
|--------------------|----------|--------------|
|.asmx|原始程式檔|部署檔案。|
|.asp|Source|Active Server Page 檔。|
|.atp|專案|應用程式範本專案檔。|
|.bmp、.dib、.gif、.jpg、.jpe、.png|Resource|一般影像檔。|
|.bsc|編譯|瀏覽器程式碼檔。|
|.cpp、。c|Source|您的應用程式的主要原始程式碼檔。|
|.cur|Resource|資料指標點陣圖形檔。|
|.dbp|專案|資料庫專案檔。|
|.disco|Source|動態探索文件檔。 處理 XML Web 服務探索。|
|.exe、.dll|專案|可執行檔或動態連結程式庫檔。|
|.h|Source|標頭 (Include) 檔。|
|.htm、.html、.xsp、.asp、.htc、.hta、.xml|Resource|一般 Web 檔案。|
|.HxC|專案|說明專案檔。|
|.ico|Resource|圖示點陣圖形檔。|
|.idb|編譯|狀態檔案, 其中包含來源檔案與類別定義之間的相依性資訊。 編譯器可在累加式編譯期間使用它。 使用 [/Fd](fd-program-database-file-name.md) 編譯器選項以指定 .idb 檔的名稱。|
|.idl|編譯|介面定義語言檔。 如需詳細資訊，請參閱 Windows SDK 中的 [Interface Definition (IDL) File](/windows/win32/Rpc/the-interface-definition-language-idl-file) (介面定義 (IDL) 檔)。|
|.ilk|連結|累加連結檔案。 如需詳細資訊, 請參閱[/INCREMENTAL](incremental-link-incrementally.md)。|
|.map|連結|包含連結器資訊的文字檔。 使用 [/Fm](fm-name-mapfile.md) 編譯器選項來命名對應檔。 如需詳細資訊, 請參閱[/MAP](map-generate-mapfile.md)。|
|.mfcribbon-ms|Resource|資源檔, 其中包含定義功能區中 MFC 按鈕、控制項和屬性的 XML 程式碼。 如需詳細資訊，請參閱 [Ribbon Designer](../../mfc/ribbon-designer-mfc.md)。|
|.obj、.o||目的檔，已編譯但尚未連結。|
|.pch|偵錯|先行編譯標頭檔。|
|.rc、.rc2|Resource|用以產生資源的[資源指令碼檔](../../windows/working-with-resource-files.md) 。|
|.sbr|編譯|原始程式瀏覽器中繼檔案。 [BSCMAKE](bscmake-options.md)的輸入檔。|
|.sln|方案|[「方案」](/visualstudio/ide/solutions-and-projects-in-visual-studio)檔。|
|.suo|方案|方案選項檔。|
|.txt|Resource|文字檔，通常是「讀我」檔案。|
|.vap|專案|Visual Studio Analyzer 專案檔。|
|.vbg|方案|相容專案群組檔。|
|.vbp、.vip、.vbproj|專案|Visual Basic 專案檔。|
|.vcxitems|專案|用於在多個 C++ 專案之間共用程式碼檔的共用項目專案。 如需詳細資訊, 請參閱[專案和方案](project-and-solution-files.md)檔。|
|.vcxproj|專案|Visual Studio 專案檔案。 如需詳細資訊, 請參閱[專案和方案](project-and-solution-files.md)檔。|
|.vcxproj.filters|專案|當您使用方案總管將檔案新增至專案時使用。 篩選檔案會根據檔案的副檔名, 定義要在方案總管樹狀檢視中新增檔案的位置。|
|.vdproj|專案|Visual Studio 部署專案檔。|
|.vmx|專案|巨集專案檔。|
|.vup|專案|公用程式專案檔。|

如需與 Visual Studio 相關聯之其他檔案的相關資訊，請參閱 [Visual Studio .NET 中的檔案類型與副檔名](/visualstudio/ide/reference/project-and-solution-file-types)。

專案檔會組織成方案總管中的資料夾。 Visual Studio 會建立原始程式檔、標頭檔和資源檔的資料夾, 但您可以重新組織這些資料夾或建立新的資料夾。 您可以使用資料夾在專案階層內明確地組織檔案邏輯叢集。 例如, 您可以建立資料夾來包含所有的使用者介面來源檔案。 或者, 適用于規格、檔或測試套件的資料夾。 所有的檔案資料夾名稱必須是唯一的。

當您將專案加入至專案時, 會將專案加入至該專案的所有設定。 會加入專案, 不論其是否為可建置。 例如，如果您有名稱為 MyProject 的專案，加入項目會將其加入偵錯和發行專案組態。

## <a name="see-also"></a>另請參閱

[建立和管理 Visual Studio C++專案](../creating-and-managing-visual-cpp-projects.md)<br>
[Visual Studio C++專案類型](visual-cpp-project-types.md)<br>