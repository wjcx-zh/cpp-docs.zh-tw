---
title: 開發 Visual C++ 的 IDE 和工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4e7742afd3fecc4dd115624da0c1650dc662004
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412518"
---
# <a name="ide-and-tools-for-visual-c-development"></a>開發 Visual C++ 的 IDE 和工具

Microsoft Visual C++ (MSVC) 是 Visual Studio 整合式開發環境 (IDE) 的一部分，與其他語言共用許多相同的視窗和工具。 其中許多視窗和工具會在 [Visual Studio IDE](/visualstudio/ide/visual-studio-ide) 底下提供說明，包括 [方案總管]、程式碼編輯器和偵錯工具。 這些共用工具或視窗針對 C++ 所提供的功能集，通常會與針對 .NET 語言或 Javascript 所提供的功能集稍有不同。 有些視窗或工具只有 Visual Studio Pro 或 Visual Studio Enterprise 才會提供。

除了 Visual Studio IDE 中的共用工具之外，MSVC 還有數個專門用來開發機器碼的工具。 本文也會列出這些工具。 如需 Visual Studio 各版本中的可用工具清單，請參閱 [Visual Studio 版本中的 Visual C++ 工具和功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="creating-a-solution-and-projects"></a>建立方案和專案

「專案」基本上是一組原始程式碼檔和資源，例如內建於可執行檔的影像或資料檔案。

Visual Studio 2015 提供 MSBuild 專案的支援。 您可以下載其他組建系統 (例如 Qt 或 CMake) 的 Visual Studio 延伸模組。

Visual Studio 2017 支援任何組建系統或是您想要使用的自訂建置工具，同時完整支援 IntelliSense、瀏覽與偵錯功能：

- MSBuild 是 Visual Studio 的原生建置系統，通常是通用 Windows 平台 (UWP) App 或是使用 MFC 或 ATL 之舊版 Windows 傳統型應用程式的最佳選擇。 如需 MSBuild 型 C++ 專案的詳細資訊，請參閱[建立和管理 MSBuild 型專案](creating-and-managing-visual-cpp-projects.md)。
- CMake 是跨平台建置系統，會在安裝使用 C++ 的桌面開發工作負載時整合到 Visual Studio IDE 中。 如需詳細資訊，請參閱 [Visual C++ 中的 CMake 專案](cmake-tools-for-visual-cpp.md)。
- 任何其他 C++ 建置系統 (包括鬆散的檔案集合) 則會透過「開啟資料夾」功能提供支援。 您可以建立簡單的 JSON 檔案，來叫用您的建置程式並設定偵錯工作階段。 如需詳細資訊，請參閱 [Bring your C++ code to Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/) (將您的 C++ 程式碼整合到 Visual Studio)。

### <a name="project-templates-msbuild"></a>專案範本 (MSBuild)

Visual Studio 隨附數個適用於 MSBuild 型專案的範本，這些範本包含各種基本程式類型所需的起始程式碼和設定。 您一開始通常會選擇 [檔案] > [新增專案]，從專案範本建立專案，然後將新的原始程式碼檔新增至該專案，或開始在提供的檔案中撰寫程式碼。 如需 C++ 專案和專案精靈的特定資訊，請參閱[建立和管理 Visual C++ 專案](../ide/creating-and-managing-visual-cpp-projects.md)。

### <a name="application-wizards-msbuild"></a>應用程式精靈 (MSBuild)

當您選擇 [檔案] > [新增專案] 時，Visual Studio 會提供適用於某些 MSBuild 專案類型的精靈。 該精靈可引導您逐步完成建立新專案的程序。 這對具有許多選項和設定的專案類型會很有幫助。 如需詳細資訊，請參閱[使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)。

## <a name="creating-user-interfaces-with-designers-msbuild"></a>使用設計工具建立使用者介面 (MSBuild)

如果您的程式具有使用者介面，首要工作之一就是將按鈕、清單方塊等控制項填入其中。 Visual Studio 包含針對 C++ 應用程式之各種類別的視覺化設計介面和工具箱。 不論您建立的應用程式類型為何，基本概念都一樣：您會將控制項從工具箱視窗，拖曳至設計介面的所需位置。 Visual Studio 會在背景產生正常運作所需的資源和程式碼。 然後，您會撰寫程式碼將資料填入控制項，或自訂其外觀和行為。

如需設計通用 Windows 平台 App 之使用者介面的詳細資訊，請參閱[設計和 UI](https://developer.microsoft.com/en-us/windows/design)。

如需建立 MFC 應用程式之使用者介面的詳細資訊，請參閱 [MFC 傳統型應用程式](../mfc/mfc-desktop-applications.md)。 如需 Win32 Windows 程式的資訊，請參閱 [Windows 傳統型應用程式](../windows/windows-desktop-applications-cpp.md)。

## <a name="writing-and-editing-code"></a>撰寫和編輯程式碼

### <a name="semantic-colorization"></a>語意顏色標示

建立專案之後，所有專案檔會都會顯示在 [方案總管] 視窗中。 當您按一下 [方案總管] 中的 .h 或 .cpp 檔案時，會在程式碼編輯器中開啟檔案。 程式碼編輯器是 C++ 原始程式碼特有的文書處理器。 它以顏色標示語言關鍵字、方法和變數名稱，以及程式碼的其他項目，以便您更容易閱讀和了解程式碼。

### <a name="intellisense"></a>IntelliSense

程式碼編輯器也支援數項功能，這些功能統稱為 IntelliSense。 您可以將滑鼠指標停留在某個方法上方，以查看該方法的一些基本說明。 輸入類別的變數名稱以及 . 或 -> 之後，該類別的執行個體成員清單隨即出現。 如果您輸入類別名稱，再輸入 ::，則會出現靜態成員清單。 當您開始輸入類別或方法名稱時，程式碼編輯器會提供完成陳述式的建議。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。

### <a name="code-snippets"></a>程式碼片段

您可以使用 IntelliSense 程式碼片段，只要輸入一個快速鍵，就能產生常用或複雜的程式碼建構。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。

## <a name="navigating-code"></a>巡覽程式碼

您可以透過 [檢視] 功能表存取許多視窗和工具，以巡覽程式碼檔案。 如需這些視窗的詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。

### <a name="solution-explorer"></a>底下提供說明，包括方案總管

您可以在所有 Visual Studio 版本中，使用 [方案總管] 窗格來巡覽專案中的檔案。 請展開 .h 或 .cpp 檔案圖示，以檢視檔案中的類別。 然後展開類別，以查看其成員。 按兩下其中一個成員，即可巡覽至檔案中該成員的定義或實作。

### <a name="class-view-and-code-definition-window"></a>類別檢視和程式碼定義視窗

您可以使用 [類別檢視] 窗格來查看所有檔案的命名空間和類別，包括部分類別。 您可以展開每個命名空間或類別，以查看其成員，然後按兩下成員，以巡覽至原始程式檔中的該位置。 如果您開啟 [程式碼定義視窗]，您可以檢視在 [類別檢視] 中所選擇之類型的定義或實作。

### <a name="object-browser"></a>物件瀏覽器

您可以使用 [物件瀏覽器] 來瀏覽 Windows 執行階段元件 (.winmd 檔案)、.NET 組件和 COM 型別程式庫中的類型資訊。 它不適用於 Win32 DLL。

### <a name="go-to-definitiondeclaration"></a>移至定義/宣告

在任何應用程式開發介面名稱或成員變數上按 F12 鍵，即可移至其定義。 如果定義是在 .winmd 檔案中 (若為 UWP 或 Windows 8.x 市集應用程式)，則會在 [物件瀏覽器] 中顯示類型資訊。 您也可以在變數或類型名稱上按一下滑鼠右鍵，然後從操作功能表選擇選項，來選擇 [移至定義] 或 [移至宣告]。

### <a name="find-all-references"></a>尋找所有參考

在原始程式碼檔中，將滑鼠游標停留在類型、方法或變數名稱上方並按一下滑鼠右鍵，然後選擇 [尋找所有參考]，即可傳回檔案、專案或方案中使用該類型的每個位置清單。 [尋找所有參考] 是智慧型功能，只會傳回完全相同之變數的執行個體，包括其他在不同範圍中有相同名稱的變數。

## <a name="add-and-edit-resources--msbuild"></a>新增和編輯資源 (MSBuild)

「資源」一詞在 Visual Studio 桌面專案的內容中，可以是對話方塊、圖示、可當地語系化的字串、啟動顯示畫面、資料庫連接字串，或任何您想要包含在可執行檔中的任意資料。

如需新增和編輯原生桌面 C++ 專案中資源的詳細資訊，請參閱[使用資源檔](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>建置 (編譯和連結)

在功能表列上選擇 [建置] > [建置方案]，或輸入 Ctrl+Shift+B 按鍵組合，以編譯和連結專案。 若要建立可執行程式碼，Visual Studio 使用 [MSBuild](/visualstudio/msbuild/msbuild1)、CMake 或透過 [開啟資料夾] 設定的任何建置環境。 對於 MSBuild 專案，您可以在 [工具] > [選項] > [專案和方案] 下設定一般建置選項，也可以在 [專案] > [屬性] 下設定特定專案的屬性。 建置錯誤和警告會在 [錯誤清單] (Ctrl+\\、E) 中回報。 非 MSBuild 專案會使用您在 [方案總管] 中建立的 JSON 檔案設定。 不論您使用哪種建置系統，[輸出] 視窗 (Alt+2) 都會顯示建置程序的相關資訊。 如需 MSBuild 組態的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)和[在 Visual Studio 中建置 C++ 專案](../ide/building-cpp-projects-in-visual-studio.md)。

您也可以直接從命令列使用編譯器 (cl.exe)，以及其他許多與建置相關的獨立工具，例如 NMAKE 和 LIB。 如需詳細資訊，請參閱[在命令列上建置 C/C++ 程式碼](../build/building-on-the-command-line.md)和 [C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)。

## <a name="test"></a>測試

Visual Studio 包含同時適用於原生 C++ 和 C++/CLI 的單元測試架構。 如需詳細資訊，請參閱[使用單元測試驗證程式碼](/visualstudio/test/unit-test-your-code)和[使用適用於 C++ 的 Microsoft 單元測試架構撰寫適用於 C/C++ 的單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="analyze"></a>分析

Visual Studio 包含 C++ 的靜態程式碼分析工具，包括實作 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) 規則檢查工具。 如需詳細資訊，請參閱 [C/C++ 程式碼分析概觀](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="debug"></a>偵錯

您可以在專案組態設定為 [偵錯] 時，按 **F5** 鍵來偵錯程式。 在偵錯期間，您可以按 **F9** 鍵設定中斷點、按 **F10** 鍵逐步執行程式碼、檢視指定變數或暫存器的值，甚至在某些情況下，您還可以在程式碼中進行變更並繼續偵錯，而不需要重新編譯。 如需詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="deploy-completed-applications"></a>部署完成的應用程式

您可以使用 [專案] > [市集] 功能表選項，透過 Windows 市集將 UWP App 部署給客戶。 CRT 的部署會在背景自動處理。 如需詳細資訊，請參閱[發行 Windows 應用程式與遊戲](/windows/uwp/publish/)。

當您將原生 C++ 桌面應用程式部署至另一部電腦時，您必須安裝該應用程式本身及其相依的所有程式庫檔案。 隨應用程式一起部署通用 C++ 執行階段 (UCRT) 的方式有三種：集中部署、本機部署或靜態連結。 如需詳細資訊，請參閱[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)。

如需部署 C++/CLI 程式的詳細資訊，請參閱[開發人員部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。

## <a name="related-articles"></a>相關文章

|||
|-|-|
|[Visual Studio 版本中的 Visual C++ 工具和功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|顯示各版 Visual Studio 中的可用功能。|
|[建立和管理 MSBuild 型專案](../ide/creating-and-managing-visual-cpp-projects.md)|提供 Visual Studio 中的 C++ MSBuild 型專案概觀，以及說明如何建立和管理這些專案的其他文章連結。|
|[Visual C++ 中的 CMake 專案](cmake-tools-for-visual-cpp.md)。|描述如何在 Visual C++ 中建置 CMake 或其他非 MSBuild 專案。|
|[建置 C/C++ 程式](../build/building-c-cpp-programs.md)|說明如何建置 C++ 專案。|
|[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)|提供 C++ 應用程式的部署概觀，以及詳細說明部署的其他文章連結。|
|[Visual C++ 移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)|如何升級使用舊版 Visual Studio 所建立之 C++ 應用程式，以及如何移轉使用 Visual Studio 以外工具所建立之應用程式的詳細資訊。|
|[Visual C++](../visual-cpp-in-visual-studio.md)|說明 Visual Studio 中的 Visual C++ 主要功能，以及 Visual C++ 文件其餘部分的連結。|
