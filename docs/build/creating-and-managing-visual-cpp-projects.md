---
title: Visual Studio 專案 - C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: d6bfefdaa3dfc67f861cf116718f89c0e9766e47
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624470"
---
# <a name="visual-studio-projects---c"></a>Visual Studio 專案 - C++

*Visual Studio 專案*是以 MSBuild 建置系統為基礎的專案。 MSBuild 是 Visual Studio 的原生組建系統，通常是用於 Windows 特定程式的最佳組建系統。 MSBuild 會與 Visual Studio 緊密整合，但您也可以從命令列使用它。 針對跨平臺專案或使用開放原始碼程式庫的專案，我們建議在 Visual Studio 2017 和更新版本的 Visual Studio 中使用[CMake 專案](cmake-projects-in-visual-studio.md)。 如需從舊版 Visual Studio 升級 MSBuild 專案的詳細資訊，請參閱[Microsoft C++移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)。

## <a name="create-a-project"></a>建立專案

::: moniker range="vs-2019"

您可以藉由選擇 [檔案] > [新增] > [專案]，並將 [語言] 設為 C++，來建立 C++ 專案。 在結果清單中您會看到專案範本清單，而您可以藉由設定 [平台] 或 [專案類型] 並在搜尋方塊中輸入關鍵字，來篩選該清單。 

   ![Visual Studio 2019 專案範本](../build/media/vs2019-choose-console-app.png "Visual Studio 2019 [新增專案] 對話方塊")

::: moniker-end

::: moniker range="vs-2017"

您可以藉由選擇 [檔案] > [新增] > [專案]，並在左窗格中選擇 [Visual C++]，來建立 C++ 專案。 在中間窗格中，您會看到專案範本清單：

   ![專案範本](../overview/media/vs2017-new-project.png "Visual Studio 2017 [新增專案] 對話方塊")

::: moniker-end

如需隨附於 Visual Studio 的所有預設專案範本的詳細資訊，請參閱 [Visual Studio 中的 C++ 專案範本](reference/visual-cpp-project-types.md)。 您可以建立您自己的專案範本。 如需詳細資訊，請參閱[如何：建立專案範本](/visualstudio/ide/how-to-create-project-templates)。

專案建立後，將會顯示在 [方案總管](/visualstudio/ide/solutions-and-projects-in-visual-studio) 視窗中：

   ![底下提供說明，包括方案總管](media/mathlibrary-solution-explorer-153.png)

當您建立新的專案時，也會建立方案檔 (.sln)。 您可以在 [方案總管] 中以滑鼠右鍵按一下其他專案，將該專案新增至方案。 方案檔可在您有多個相關的專案時用來協調組建相依性，但其功能大概就是如此。 所有編譯器選項都會在專案層級設定。

## <a name="add-items"></a>新增項目

在 [方案總管] 中以滑鼠右鍵按一下專案，然後選擇 [新增] > [新增] 或 [新增] > [現有的]，將原始程式碼檔案、圖示或任何其他項目新增至您的專案。

## <a name="add-third-party-libraries"></a>新增第三方程式庫

若要新增第三方程式庫，請使用 [vcpkg](vcpkg.md) 套件管理員。 執行 Visual Studio 整合步驟，以設定您從任何 Visual Studio 專案參考該程式庫時的路徑。 

## <a name="set-compiler-options-and-other-build-properties"></a>設定編譯器選項和其他組建屬性

若要設定專案的組建設定，請在 [方案總管] 中以滑鼠右鍵按一下專案，然後選擇 [屬性]。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](working-with-project-properties.md)。

## <a name="compile-and-run"></a>編譯和執行

若要編譯和執行新的專案，請按 **F5**，或按一下主要工具列上具有綠色箭頭的*偵錯下拉式清單*。 您可以在*組態下拉式清單*中選擇是否要執行*偵錯*或*發行*組建 (或其他自訂組態)。

新的專案編譯無誤。 當您新增自己的程式碼時，有時可能會導入錯誤或觸發警告。 錯誤會使組建無法完成；警告則否。 當您建置專案時，所有錯誤和警告會都出現在 [輸出] 視窗和錯誤清單中。 

   ![輸出視窗和錯誤清單](../overview/media/vs2017-output-error-list.png)

在錯誤清單中，您可以對醒目標示的錯誤按 **F1**，以移至其文件主題。

## <a name="in-this-section"></a>本章節內容

[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](working-with-project-properties.md)<br/>
如何使用屬性頁和屬性工作表來指定專案設定。

[在建置階段參考程式庫和元件](adding-references-in-visual-cpp-projects.md)<br/>
如何在專案中包含程式庫、Dll、COM 和 .NET 元件。
 
[組織專案輸出檔案](how-to-organize-project-output-files-for-builds.md)<br/>
如何自訂在建置流程中建立的可執行檔所在的位置。

[自訂建置步驟和建置事件](understanding-custom-build-steps-and-build-events.md)<br/>
如何將任何任意命令新增至建置程序的指定點。

[從現有程式碼建立專案](how-to-create-a-cpp-project-from-existing-code.md)<br/>
如何從來源檔案的鬆散式集合建立新的 Visual Studio 專案。

## <a name="see-also"></a>請參閱

[專案和建置系統](projects-and-build-systems-cpp.md)<br>
[Microsoft C++移植和升級指南](../porting/visual-cpp-porting-and-upgrading-guide.md)
