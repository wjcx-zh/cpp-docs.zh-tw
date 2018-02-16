---
title: "IDE 和適用於 Visual c + + 開發工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c0ae9514736b66be104198c95c3764772a87ef8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ide-and-tools-for-visual-c-development"></a>開發 Visual C++ 的 IDE 和工具

一部分的 Visual Studio 整合式開發環境 (IDE) 時，Microsoft Visual c + + (MSVC) 會共用許多視窗和工具與其他語言。 其中，包括許多**方案總管 中**，程式碼編輯器和偵錯工具，記載下[Visual Studio IDE](/visualstudio/ide/visual-studio-ide)。 這些共用工具或視窗針對 C++ 所提供的功能集，通常會與針對 .NET 語言或 Javascript 所提供的功能集稍有不同。 有些視窗或工具只有 Visual Studio Pro 或 Visual Studio Enterprise 才會提供。

除了 Visual Studio IDE 中的共用工具，MSVC 都有數個專門用來開發機器碼的工具。 本文也會列出這些工具。 如需工具的每一個版本的 Visual Studio 中可用的清單，請參閱[Visual c + + 工具和 Visual Studio 版本中的功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)。

## <a name="creating-a-solution-and-projects"></a>建立方案和專案

A*專案*基本上是一組原始程式檔和資源，例如影像或資料全都會建置到可執行檔的檔案。 任何建置系統或您想要使用 Intellisense、 瀏覽和偵錯的完整支援的自訂建置工具，可支援 visual Studio 2017:

- MSBuild 是 Visual Studio 的原生的建置系統，和通常是最佳選擇的通用 Windows 平台 (UWP) 應用程式或舊版的 Windows 桌面應用程式使用 MFC 或 atl。 如需 MSBuild 為基礎的 c + + 專案的詳細資訊，請參閱[建立和管理 MSBuild 為基礎的專案](creating-and-managing-visual-cpp-projects.md)。
- CMake 是跨平台建置已整合至 Visual Studio IDE 中，當您安裝桌面開發搭配 c + + 的工作負載的系統。 如需詳細資訊，請參閱 [Visual C++ 中的 CMake 專案](cmake-tools-for-visual-cpp.md)。
- 任何其他 c + + 建置系統，包括鬆散檔案的集合，可支援透過開啟資料夾功能。 您建立簡單的 JSON 檔案，以叫用您的組建程式並設定偵錯工作階段。 如需詳細資訊，請參閱[帶入 Visual Studio 中的 c + + 程式](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/)。

### <a name="project-templates-msbuild"></a>專案範本 (MSBuild)

Visual Studio 隨附幾個範本，MSBuild 型的專案。這些範本包含起始程式碼和各種基本程式類型所需的設定。 您一開始通常會選擇**檔案** > **新專案**從專案範本建立專案，然後將新的原始程式碼檔案加入至該專案，或開始撰寫程式碼中提供的檔案。 C + + 專案和專案精靈的特定資訊，請參閱[建立和管理 Visual c + + 專案](../ide/creating-and-managing-visual-cpp-projects.md)。

### <a name="application-wizards-msbuild"></a>應用程式精靈 (MSBuild)

Visual Studio 精靈針對某些 MSBuild 專案類型時提供您選擇**檔案** > **新專案**。 該精靈可引導您逐步完成建立新專案的程序。 這對具有許多選項和設定的專案類型會很有幫助。 如需詳細資訊，請參閱[建立桌面專案所使用的應用程式精靈](../ide/creating-desktop-projects-by-using-application-wizards.md)。

## <a name="creating-user-interfaces-with-designers-msbuild"></a>建立使用者介面與設計工具 (MSBuild)

如果您的程式具有使用者介面，首要工作之一就是將按鈕、清單方塊等控制項填入其中。 Visual Studio 包含針對 C++ 應用程式之各種類別的視覺化設計介面和工具箱。 不論您建立的應用程式類型為何，基本概念都一樣：您會將控制項從工具箱視窗，拖曳至設計介面的所需位置。 Visual Studio 會在背景產生正常運作所需的資源和程式碼。 然後您撰寫程式碼以填入資料的控制項或自訂其外觀和行為。

如需設計通用 Windows 平台應用程式的使用者介面的詳細資訊，請參閱[設計和 UI](https://developer.microsoft.com/en-us/windows/design)。

如需建立 MFC 應用程式的使用者介面的詳細資訊，請參閱[MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)。 如需 Win32 Windows 程式的資訊，請參閱[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)。

## <a name="writing-and-editing-code"></a>撰寫和編輯程式碼

### <a name="semantic-colorization"></a>語意顏色標示

在您建立專案之後，會顯示所有專案檔**方案總管 中**視窗。 當您按一下中的.h 或.cpp 檔案**方案總管 中**，程式碼編輯器中開啟檔案。 程式碼編輯器是 C++ 原始程式碼特有的文書處理器。 它以顏色標示語言關鍵字、方法和變數名稱，以及程式碼的其他項目，以便您更容易閱讀和了解程式碼。

### <a name="intellisense"></a>Intellisense

程式碼編輯器也支援數項功能，這些功能統稱為 Intellisense。 您可以將滑鼠指標停留在某個方法上方，以查看該方法的一些基本說明。 輸入類別的變數名稱以及 . 或 -> 之後，該類別的執行個體成員清單隨即出現。 如果您輸入類別名稱，再輸入 ::，則會出現靜態成員清單。 當您開始輸入類別或方法名稱時，程式碼編輯器會提供完成陳述式的建議。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。

### <a name="code-snippets"></a>程式碼片段

您可以使用 Intellisense 程式碼片段，只要輸入一個快速鍵，就能產生常用或複雜的程式碼建構。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。

## <a name="navigating-code"></a>巡覽程式碼

**檢視**功能表存取許多視窗和工具以巡覽程式碼檔案中。 如需這些視窗的詳細資訊，請參閱[檢視程式碼結構](/visualstudio/ide/viewing-the-structure-of-code)。

### <a name="solution-explorer"></a>底下提供說明，包括方案總管

在所有版本的 Visual Studio 中，使用**方案總管 中**窗格來巡覽專案中的檔案。 請展開 .h 或 .cpp 檔案圖示，以檢視檔案中的類別。 然後展開類別，以查看其成員。 按兩下其中一個成員，即可巡覽至檔案中該成員的定義或實作。

### <a name="class-view-and-code-definition-window"></a>類別檢視和程式碼定義視窗

使用**類別檢視**窗格，即可查看所有檔案，包括部分類別中的命名空間和類別。 您可以展開每個命名空間或類別，以查看其成員，然後按兩下成員，以巡覽至原始程式檔中的該位置。 如果您開啟**程式碼定義視窗**，您可以檢視您選擇在定義或類型實作**類別檢視**。

### <a name="object-browser"></a>物件瀏覽器

使用**物件瀏覽器**瀏覽 Windows 執行階段元件 （.winmd 檔案） 中的類型資訊，.NET 組件和 COM 類型程式庫。 它不適用於 Win32 DLL。

### <a name="go-to-definitiondeclaration"></a>移至定義/宣告

在任何應用程式開發介面名稱或成員變數上按 F12 鍵，即可移至其定義。 如果定義是在.winmd 檔案中 （適用於 UWP 或 Windows 8.x 市集應用程式），則您會在物件瀏覽器中顯示類型資訊。 您也可以選擇**移至定義**或**移至宣告**由變數或類型名稱上按一下滑鼠右鍵，然後從內容功能表選擇選項。

### <a name="find-all-references"></a>尋找所有參考

在原始程式碼檔案，並將滑鼠游標的類型或方法或變數名稱上按一下滑鼠右鍵，然後選擇 **尋找所有參考**傳回檔案、 專案或方案中的每個位置清單，其中使用的型別。 **尋找所有參考**是智慧型功能，只會傳回執行個體完全相同之變數，即使在不同範圍的其他變數具有相同的名稱。

## <a name="add-and-edit-resources--msbuild"></a>新增和編輯資源 (MSBuild)

詞彙*資源*在內容中的 Visual Studio 桌面專案項目包括例如對話方塊、 圖示、 可當地語系化的字串、 啟動顯示畫面、 資料庫連接字串或您想要包含在任何任意資料可執行檔。

如需加入和編輯原生桌面 c + + 專案中的資源的詳細資訊，請參閱[使用的資源檔](../windows/working-with-resource-files.md)。

## <a name="build-compile-and-link"></a>建置 （編譯和連結）

選擇**建置** > **建置方案**功能表中的列，或輸入 Ctrl + Shift + B 以編譯及連結專案組合鍵。 若要建立可執行程式碼，Visual Studio 會使用[MSBuild](/visualstudio/msbuild/msbuild1)或 CMake 或任何建置環境您設定透過**開啟資料夾**。 MSBuild 專案中，您可以設定底下的一般建置選項**工具** > **選項** > **專案和方案**，您可以設定屬性在特定專案**專案** > **屬性**。 建置錯誤和警告會報告錯誤清單中 (Ctrl +\\，E)。 非 MSBuild 專案會使用您在 [方案總管] 中建立的 JSON 檔案設定。 無論建置的系統使用，**輸出**(Alt + 2) 視窗會顯示在建置程序的相關資訊。 如需 MSBuild 組態的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)和[Visual Studio 中建置 c + + 專案](../ide/building-cpp-projects-in-visual-studio.md)。

您也可以使用編譯器 (cl.exe) 和許多其他與組建相關的獨立工具，例如 NMAKE 和 LIB 直接從命令列。 如需詳細資訊，請參閱[命令列上的建置 C/c + + 程式碼](../build/building-on-the-command-line.md)和[C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)。

## <a name="test"></a>測試

Visual Studio 包含同時適用於原生 C++ 和 C++/CLI 的單元測試架構。 如需詳細資訊，請參閱[使用單元測試驗證程式碼](/visualstudio/test/unit-test-your-code)和[C/c + + 的 Microsoft 單元測試架構適用於 c + + 撰寫單元測試](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)

## <a name="debug"></a>偵錯

您可以藉由按下偵錯程式**F5**當您的專案組態設為偵錯。 偵錯您可以藉由按下設定中斷點時**F9**，逐步執行程式碼，藉由按下**F10**、 檢視指定的變數或暫存器的值和甚至在某些情況下，請在程式碼中進行變更後繼續偵錯，而不需要重新編譯。 如需詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。

## <a name="deploy-completed-applications"></a>部署完成的應用程式

您將 UWP 應用程式部署至客戶透過 Microsoft 市集**專案** > **存放區**功能表選項。 CRT 的部署會在背景自動處理。 如需詳細資訊，請參閱 [銷售應用程式](http://go.microsoft.com/fwlink/p/?LinkId=262280)。

當您將原生 C++ 桌面應用程式部署至另一部電腦時，您必須安裝該應用程式本身及其相依的所有程式庫檔案。 若要部署的應用程式通用的 c + + 執行階段 (UCRT) 的三種方式： 集中部署、 本機部署或靜態連結。 如需詳細資訊，請參閱[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)。

如需部署 C + + /CLI 程式，請參閱[開發人員部署手冊](/dotnet/framework/deployment/deployment-guide-for-developers)，

## <a name="related-articles"></a>相關文章

|||
|-|-|
|[Visual Studio 版本中的 Visual C++ 工具和功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|顯示各版 Visual Studio 中的可用功能。|
|[建立和管理 MSBuild 為基礎的專案](../ide/creating-and-managing-visual-cpp-projects.md)|提供 c + + MSBuild 型的專案，在 Visual Studio 和其他文章說明如何建立和管理這些連結的概觀。|
|[CMake 專案中 Visual c + +](cmake-tools-for-visual-cpp.md)。|描述如何建置 CMake 或其他非 MSBuild 專案中 Visual c + +。|
|[建置 C/C++ 程式](../build/building-c-cpp-programs.md)|說明如何建置 C++ 專案。|
|[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)|提供 C++ 應用程式的部署概觀，以及詳細說明部署的其他文章連結。|
|[Visual C++ 移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)|有關如何升級在舊版的 Visual Studio 中，所建立的 c + + 應用程式以及如何使用 Visual Studio 以外工具所建立的應用程式移轉的詳細的資訊。|
|[Visual C++](../top/visual-cpp-in-visual-studio.md)|說明 Visual Studio 中的 Visual C++ 主要功能，以及 Visual C++ 文件其餘部分的連結。|
