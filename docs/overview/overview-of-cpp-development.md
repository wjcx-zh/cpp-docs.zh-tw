---
title: 在 Visual Studio 中進行 C++ 開發的概觀
description: Visual Studio IDE 支援在 Windows、Linux、Android 和 iOS 上使用程式碼編輯器、偵錯工具、測試架構、靜態分析器和其他程式設計工具以進行 C++ 開發。
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415716"
---
# <a name="overview-of-c-development-in-visual-studio"></a>在 Visual Studio 中進行 C++ 開發的概觀

Microsoft C++ (MSVC) 是 Visual Studio 整合式開發環境 (IDE) 的一部分，與其他語言共用許多相同的視窗和工具。 其中許多視窗和工具會在 [Visual Studio IDE](/visualstudio/get-started/visual-studio-ide) 底下提供說明，包括 [方案總管]、程式碼編輯器和偵錯工具。 這些共用工具或視窗針對 C++ 所提供的功能集，通常會與針對其他語言所提供的功能集稍有不同。 有些視窗或工具只有 Visual Studio Professional 或 Visual Studio Enterprise 版本才會提供。

除了 Visual Studio IDE 中的共用工具之外，MSVC 還有數個專門用來開發機器碼的工具。 本文也會列出這些工具。 如需 Visual Studio 各版本中的可用工具清單，請參閱 [Visual Studio 版本中的 C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="create-projects"></a>建立專案

「專案」基本上是一組原始程式碼檔和資源，例如內建於可執行程式或程式庫的影像或資料檔案。

Visual Studio 支援任何專案系統或是您想要使用的自訂建置工具，同時完整支援 IntelliSense、巡覽與偵錯功能：

- **MSBuild** 是 Visual Studio 的原生專案系統。 當您從主功能表中選取 [檔案] > [新增] > [專案] 時，您會看到許多種類的 MSBuild「專案範本」，其可協助您快速開始開發不同類型的 C++ 應用程式。

   ::: moniker range="vs-2019"

   ![新增專案範本](../build/media/mathclient-project-name-2019.png "Visual Studio 2019 [新增專案] 對話方塊")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![專案範本](media/vs2017-new-project.png "Visual Studio 2017 [新增專案] 對話方塊")

   ::: moniker-end

   一般情況下，您應該針對新專案使用這些範本，除非您使用現有 CMake 專案，或是使用其他專案系統。 如需詳細資訊，請參閱[建立和管理 MSBuild 專案](../build/creating-and-managing-visual-cpp-projects.md)。

- **CMake** 是一種跨平台建置系統，會在安裝使用 C++ 的桌面開發工作負載時整合到 Visual Studio IDE 中。 您可以針對新的專案使用 CMake 專案範本，或是只開啟具有 CMakeLists.txt 檔案的資料夾。 如需詳細資訊，請參閱 [Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。

- 任何其他 C++ 建置系統 (包括鬆散的檔案集合) 則會透過**開啟資料夾**功能提供支援。 您可以建立簡單的 JSON 檔案，來叫用您的建置程式並設定偵錯工作階段。 如需詳細資訊，請參閱 [Open Folder projects for C++](../build/open-folder-projects-cpp.md) (適用於 C++ 的開啟資料夾專案)。

## <a name="add-to-source-control"></a>加入原始檔控制

原始檔控制可讓您協調多位開發人員的工作、從生產環境程式碼中找出進行中的工作，以及備份您的原始程式碼。 Visual Studio 可透過其 **Team Explorer** 視窗支援 Git 和 [Team Foundation 版本控制 \(TFVC\)](/azure/devops/repos/tfvc/)。

::: moniker range="vs-2019"

![Team Explorer](media/vs2019-team-explorer.png "Visual Studio 2017 Team Explorer")

::: moniker-end

::: moniker range="<=vs-2017"

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

::: moniker-end

如需 Git 與 Azure 中存放庫整合的詳細資訊，請參閱[使用 Visual Studio 2017 和 Azure Repos Git 共用程式碼](/azure/devops/repos/git/share-your-code-in-git-vs-2017)。 如需 Git 與 GitHub 整合的資訊，請參閱 [GitHub Extension for Visual Studio](https://visualstudio.github.com/)。

## <a name="obtain-libraries"></a>取得程式庫

若要取得和安裝第三方程式庫，請使用 [vcpkg](../build/vcpkg.md) 套件管理員。 超過 900 個開放原始碼程式庫目前可在目錄中取得。

## <a name="create-user-interfaces-with-designers"></a>使用設計工具建立使用者介面

如果您的程式具有使用者介面，您可以使用設計工具將按鈕、清單方塊等控制項快速填入其中。 當您將控制項從 [工具箱] 視窗拖曳至設計介面時，Visual Studio 會產生正常運作所需的資源和程式碼。 接著，您即可撰寫程式碼來自訂外觀和行為。

![設計工具和工具箱](media/vs2017-toolbox-designer.png "Visual Studio 2017 工具箱和設計工具")

如需設計通用 Windows 平臺應用程式之使用者介面的詳細資訊，請參閱[設計和 UI](https://developer.microsoft.com/windows/design)。

如需建立 MFC 應用程式之使用者介面的詳細資訊，請參閱 [MFC 傳統型應用程式](../mfc/mfc-desktop-applications.md)。 如需 Win32 Windows 程式的資訊，請參閱 [Windows 傳統型應用程式](../windows/windows-desktop-applications-cpp.md)。

## <a name="write-code"></a>撰寫程式碼

建立專案之後，所有專案檔會都會顯示在 [方案總管] 視窗中。 (「方案」是指一或多個相關專案的邏輯容器。)當您按一下 [方案總管] 中的 .h 或 .cpp 檔案時，會在程式碼編輯器中開啟檔案。

![方案總管和程式碼編輯器](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 方案總管和程式碼編輯器")

程式碼編輯器是 C++ 原始程式碼特有的文書處理器。 它以顏色標示語言關鍵字、方法和變數名稱，以及程式碼的其他項目，以便您更容易閱讀和了解程式碼。 它也會提供工具來重構程式碼、在不同檔案之間巡覽，以及了解如何建構程式碼。 如需詳細資訊，請參閱[撰寫及重構程式碼](../ide/writing-and-refactoring-code-cpp.md)。

## <a name="add-and-edit-resources"></a>新增和編輯資源

Windows 程式或 DLL 通常會包含一些*資源*，例如對話方塊、圖示、影像、可當地語系化的字串、啟動顯示畫面、資料庫連接字串，或任何任意資料。 Visual Studio 包括新增和編輯資源的工具。 如需詳細資訊，請參閱[使用資源檔](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>建置 (編譯和連結)

選擇功能表列上的 [**組建** > **組建方案**]，或輸入**Ctrl + Shift + B**按鍵組合來編譯和連結專案。 組建錯誤和警告會在錯誤清單（**Ctrl +\\、E**）中回報。 [**輸出**] 視窗（**Alt + 2**）會顯示有關組建進程的資訊。

![輸出視窗和錯誤清單](media/vs2017-output-error-list.png "Visual Studio 2017 輸出視窗和錯誤清單")

如需設定組建的詳細資訊，請參閱[使用專案屬性](../build/working-with-project-properties.md)和[專案與建置系統](../build/projects-and-build-systems-cpp.md)。

您也可以直接從命令列使用編譯器 (cl.exe)，以及其他許多與建置相關的獨立工具，例如 NMAKE 和 LIB。 如需詳細資訊，請參閱[在命令列上建置 C/C++ 程式碼](../build/building-on-the-command-line.md)和 [C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)。

## <a name="debug"></a>偵錯

您可以按 **F5** 開始偵錯。 執行會在您已設定的任何中斷點上暫停（藉由按**F9**）。 您也可以逐步執行一行程式碼（**F10**）、查看變數或暫存器的值，甚至在某些情況下，在程式碼中進行變更並繼續進行偵錯工具，而不需要重新編譯。 下圖顯示在中斷點上停止執行的偵錯工作階段。 資料結構成員的值會顯示在**監看式視窗**中。

![調試進程](media/vs2017-debug-watch.png "Visual Studio 2017 的調試階段")

如需詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="test"></a>測試

Visual Studio 包含適用於 C++ 的 Microsoft 單元測試架構，以及 Boost.Test、Google Test 和 CTest 的支援。 從 [測試總管] 執行測試：

![測試總管](media/cpp-test-explorer-passed.png "Visual Studio 2017 測試瀏覽器")

如需詳細資訊，請參閱[使用單元測試驗證程式碼](/visualstudio/test/unit-test-your-code)及[在 Visual Studio 中撰寫 C/C++ 的單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp)。

## <a name="analyze"></a>分析

Visual Studio 包含的靜態程式碼分析工具，可在原始程式碼中偵測到潛在問題。 這些工具包括 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) 規則檢查工具的實作。 如需詳細資訊，請參閱 [C/C++ 程式碼分析概觀](/cpp/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="deploy-completed-applications"></a>部署完成的應用程式

您可以透過 Microsoft Store 將傳統桌面應用程式和 UWP 應用程式部署給客戶。 CRT 的部署會在背景自動處理。 如需詳細資訊，請參閱[發行 Windows 應用程式與遊戲](/windows/uwp/publish/)。

您也可以將原生C++桌面部署到另一部電腦。 如需詳細資訊，請參閱[部署傳統型應用程式](../windows/deploying-native-desktop-applications-visual-cpp.md)。

如需部署 C++/CLI 程式的詳細資訊，請參閱[開發人員部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。

## <a name="next-steps"></a>後續步驟

遵循以下其中一篇簡介文章，進一步探索 Visual Studio：

> [!div class="nextstepaction"]
> [了解如何使用程式碼編輯器](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [了解專案與解決方案](/visualstudio/get-started/tutorial-projects-solutions)
