---
title: 在 Visual Studio 中進行 C++ 開發的概觀
description: Visual Studio IDE 支援在 Windows、Linux、Android 和 iOS 上使用程式碼編輯器、偵錯工具、測試架構、靜態分析器和其他程式設計工具以進行 C++ 開發。
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "77415716"
---
# <a name="overview-of-c-development-in-visual-studio"></a>在 Visual Studio 中進行 C++ 開發的概觀

Microsoft C++ (MSVC) 是 Visual Studio 整合式開發環境 (IDE) 的一部分，與其他語言共用許多相同的視窗和工具。 其中許多視窗和工具會在 [Visual Studio IDE](/visualstudio/get-started/visual-studio-ide) 底下提供說明，包括 [方案總管]****、程式碼編輯器和偵錯工具。 這些共用工具或視窗針對 C++ 所提供的功能集，通常會與針對其他語言所提供的功能集稍有不同。 有些視窗或工具只有 Visual Studio Professional 或 Visual Studio Enterprise 版本才會提供。

除了 Visual Studio IDE 中的共用工具之外，MSVC 還有數個專門用來開發機器碼的工具。 本文也會列出這些工具。 如需 Visual Studio 各版本中的可用工具清單，請參閱 [Visual Studio 版本中的 C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="create-projects"></a>建立專案

「專案」** 基本上是一組原始程式碼檔和資源，例如內建於可執行程式或程式庫的影像或資料檔案。

Visual Studio 支援任何專案系統或是您想要使用的自訂建置工具，同時完整支援 IntelliSense、巡覽與偵錯功能：

- **MSBuild** 是 Visual Studio 的原生專案系統。 當您**從主**選單中選擇 **「檔案** > **新專案** > 」時,您將看到許多類型的 MSBuild*專案樣本*,這些範本可説明您快速開始開發不同類型的C++應用程式。

   ::: moniker range="vs-2019"

   ![新項目範本](../build/media/mathclient-project-name-2019.png "視覺化工作室 2019 新項目對話框")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![專案範本](media/vs2017-new-project.png "視覺化工作室 2017 新項目對話框")

   ::: moniker-end

   一般情況下，您應該針對新專案使用這些範本，除非您使用現有 CMake 專案，或是使用其他專案系統。 如需詳細資訊，請參閱[建立和管理 MSBuild 專案](../build/creating-and-managing-visual-cpp-projects.md)。

- **CMake**是一個跨平台構建系統,當您安裝具有C++工作負載的桌面開發時,該系統集成到 Visual Studio IDE 中。 您可以針對新的專案使用 CMake 專案範本，或是只開啟具有 CMakeLists.txt 檔案的資料夾。 如需詳細資訊，請參閱 [Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。

- 任何其他 C++ 建置系統 (包括鬆散的檔案集合) 則會透過**開啟資料夾**功能提供支援。 您可以建立簡單的 JSON 檔案，來叫用您的建置程式並設定偵錯工作階段。 如需詳細資訊，請參閱 [Open Folder projects for C++](../build/open-folder-projects-cpp.md) (適用於 C++ 的開啟資料夾專案)。

## <a name="add-to-source-control"></a>加入原始檔控制

原始檔控制可讓您協調多位開發人員的工作、從生產環境程式碼中找出進行中的工作，以及備份您的原始程式碼。 Visual Studio 可透過其 **Team Explorer** 視窗支援 Git 和 [Team Foundation 版本控制 \(TFVC\)](/azure/devops/repos/tfvc/)。

::: moniker range="vs-2019"

![Team Explorer](media/vs2019-team-explorer.png "視覺工作室 2017 團隊資源管理員")

::: moniker-end

::: moniker range="<=vs-2017"

![Team Explorer](media/vs2017-team-explorer.png "視覺工作室 2017 團隊資源管理員")

::: moniker-end

如需 Git 與 Azure 中存放庫整合的詳細資訊，請參閱[使用 Visual Studio 2017 和 Azure Repos Git 共用程式碼](/azure/devops/repos/git/share-your-code-in-git-vs-2017)。 如需 Git 與 GitHub 整合的資訊，請參閱 [GitHub Extension for Visual Studio](https://visualstudio.github.com/)。

## <a name="obtain-libraries"></a>取得程式庫

若要取得和安裝第三方程式庫，請使用 [vcpkg](../build/vcpkg.md) 套件管理員。 超過 900 個開放原始碼程式庫目前可在目錄中取得。

## <a name="create-user-interfaces-with-designers"></a>使用設計工具建立使用者介面

如果您的程式具有使用者介面，您可以使用設計工具將按鈕、清單方塊等控制項快速填入其中。 當您將控制項從 [工具箱] 視窗拖曳至設計介面時，Visual Studio 會產生正常運作所需的資源和程式碼。 接著，您即可撰寫程式碼來自訂外觀和行為。

![設計師和工具箱](media/vs2017-toolbox-designer.png "視覺工作室 2017 工具箱和設計師")

有關為通用 Windows 平台應用設計使用者介面的詳細資訊,請參閱[設計和 UI](https://developer.microsoft.com/windows/design)。

如需建立 MFC 應用程式之使用者介面的詳細資訊，請參閱 [MFC 傳統型應用程式](../mfc/mfc-desktop-applications.md)。 如需 Win32 Windows 程式的資訊，請參閱 [Windows 傳統型應用程式](../windows/windows-desktop-applications-cpp.md)。

## <a name="write-code"></a>撰寫程式碼

建立專案之後，所有專案檔會都會顯示在 [方案總管]**** 視窗中。 (*解決方案*是一個或多個相關項目的邏輯容器。當您按一下**解決方案資源管理員**中的 .h 或 .cpp 檔時,該檔將在代碼編輯器中打開。

![解決方案資源管理員與程式碼編輯器](media/vs2017-solution-explorer-code-editor.png "視覺化工作室 2017 解決方案資源管理員和代碼編輯器")

程式碼編輯器是 C++ 原始程式碼特有的文書處理器。 它以顏色標示語言關鍵字、方法和變數名稱，以及程式碼的其他項目，以便您更容易閱讀和了解程式碼。 它也會提供工具來重構程式碼、在不同檔案之間巡覽，以及了解如何建構程式碼。 如需詳細資訊，請參閱[撰寫及重構程式碼](../ide/writing-and-refactoring-code-cpp.md)。

## <a name="add-and-edit-resources"></a>新增和編輯資源

Windows 程式或 DLL 通常包括一些*資源*,如對話方塊、圖示、圖像、可本地化字串、初始螢幕、資料庫連接字串或任何任意資料。 Visual Studio 包括用於添加和編輯資源的工具。 關於詳細資訊,請參考[資源檔](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>建置 (編譯和連結)

在功能表列上選擇 > **「構建解決方案**」,或輸入**Ctrl_Shift_B**鍵組合以編譯**Build**和連結專案。 生成錯誤和警告在錯誤清單 **(Ctrl+\\, E**) 中報告。 **輸出**視窗 **(Alt+2**) 顯示有關生成過程的資訊。

![輸出視窗與錯誤清單](media/vs2017-output-error-list.png "視覺化工作室 2017 輸出視窗和錯誤清單")

如需設定組建的詳細資訊，請參閱[使用專案屬性](../build/working-with-project-properties.md)和[專案與建置系統](../build/projects-and-build-systems-cpp.md)。

您也可以直接從命令列使用編譯器 (cl.exe)，以及其他許多與建置相關的獨立工具，例如 NMAKE 和 LIB。 如需詳細資訊，請參閱[在命令列上建置 C/C++ 程式碼](../build/building-on-the-command-line.md)和 [C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)。

## <a name="debug"></a>偵錯

您可以按 **F5** 開始偵錯。 執行暫停您設置的任何斷點(通過按**F9**)。 您還可以一次單行代碼 **(F10),** 查看變數或寄存器的值,甚至在某些情況下對代碼進行更改並繼續調試而不重新編譯。 下圖顯示在中斷點上停止執行的偵錯工作階段。 資料結構成員的值會顯示在**監看式視窗**中。

![除錯工作階段](media/vs2017-debug-watch.png "視覺化工作室 2017 調試會話")

如需詳細資訊，請參閱 [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="test"></a>測試

Visual Studio 包含適用於 C++ 的 Microsoft 單元測試架構，以及 Boost.Test、Google Test 和 CTest 的支援。 從 [測試總管]**** 執行測試：

![測試總管](media/cpp-test-explorer-passed.png "視覺化工作室 2017 測試資源管理員")

如需詳細資訊，請參閱[使用單元測試驗證程式碼](/visualstudio/test/unit-test-your-code)及[在 Visual Studio 中撰寫 C/C++ 的單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp)。

## <a name="analyze"></a>分析

Visual Studio 包含的靜態程式碼分析工具，可在原始程式碼中偵測到潛在問題。 這些工具包括 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) 規則檢查工具的實作。 如需詳細資訊，請參閱 [C/C++ 程式碼分析概觀](/cpp/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="deploy-completed-applications"></a>部署完成的應用程式

您可以透過 Microsoft Store 將傳統桌面應用程式和 UWP 應用程式部署給客戶。 CRT 的部署會在背景自動處理。 如需詳細資訊，請參閱[發行 Windows 應用程式與遊戲](/windows/uwp/publish/)。

您還可以將本機C++桌面部署到另一台電腦。 如需詳細資訊，請參閱[部署傳統型應用程式](../windows/deploying-native-desktop-applications-visual-cpp.md)。

如需部署 C++/CLI 程式的詳細資訊，請參閱[開發人員部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。

## <a name="next-steps"></a>後續步驟

遵循以下其中一篇簡介文章，進一步探索 Visual Studio：

> [!div class="nextstepaction"]
> [了解如何使用程式碼編輯器](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [了解專案與解決方案](/visualstudio/get-started/tutorial-projects-solutions)
