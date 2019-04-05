---
title: Visual Studio 專案-c + +
ms.date: 12/12/2018
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: b4772b9bd625a542a18039386fefe42840ab65b1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038034"
---
# <a name="visual-studio-projects---c"></a>Visual Studio 專案-c + +

A *Visual Studio 專案*是專案為基礎的 MSBuild 建置系統。 MSBuild 是 Visual Studio 的原生組建系統，並通常是最佳的建置系統，才能使用 UWP 應用程式，以及使用 MFC 或 ATL 程式庫、 COM 元件，以及其他 Windows 特定程式的桌面應用程式。 MSBuild 會與 Visual Studio 中，以緊密整合，但您也可以使用它從命令列。 

## <a name="create-a-project"></a>建立專案

您可以選擇，以建立 c + + 專案**檔案&#124;新增&#124;專案**，然後在左窗格中選擇 Visual c + +。 在中間窗格中，您會看到一份專案範本： 

   ![專案範本](../overview/media/vs2017-new-project.png "Visual Studio 2017 [新增專案] 對話方塊")

如需包含在 Visual Studio 中的所有預設專案範本的詳細資訊，請參閱[Visual Studio 中的 c + + 專案範本](reference/visual-cpp-project-types.md)。 您可以建立您自己的專案範本。 如需詳細資訊，請參閱[如何：建立專案範本](/visualstudio/ide/how-to-create-project-templates)。

您建立專案之後，它會出現在[方案總管 中](/visualstudio/ide/solutions-and-projects-in-visual-studio)視窗：

   ![底下提供說明，包括方案總管](media/mathlibrary-solution-explorer-153.png)

當您建立新的專案時，也會建立方案檔 (.sln)。 您可以將其他專案加入方案中上按一下滑鼠右鍵**方案總管 中**。 方案檔用來協調組建相依性，當您有多個相關的專案，但不會執行更多。 在專案層級為所有的編譯器選項。

## <a name="add-items"></a>新增項目

將原始程式碼檔案、 圖示或任何其他項目加入至專案中的專案上按一下滑鼠右鍵**方案總管**，然後選擇**新增 > 新增**或是**新增 > 現有**。

## <a name="add-third-party-libraries"></a>新增協力廠商程式庫

若要新增協力廠商程式庫，請使用[vcpkg](vcpkg.md)封裝管理員。 執行 Visual Studio 整合的步驟來設定該程式庫的路徑，當您從任何 Visual Studio 專案參考它。 

## <a name="set-compiler-options-and-other-build-properties"></a>設定編譯器選項和其他組建屬性

若要設定專案的組建設定，以滑鼠右鍵按一下專案中**方案總管**，然後選擇**屬性**。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](working-with-project-properties.md)。

## <a name="compile-and-run"></a>編譯並執行

若要編譯和執行新的專案，請按**F5**或按*偵錯 下拉式清單*主要工具列上的綠色箭頭。 *組態下拉式清單*，您可以選擇是否要執行*偵錯*或是*版本*組建 （或其他自訂的設定）。

新的專案編譯無誤。 當加入您自己的程式碼，可能偶爾會導入錯誤，或觸發警告。 錯誤會導致組建無法完成;警告則否。 所有錯誤和警告會都出現在 [輸出] 視窗和錯誤清單中建置專案時。 

   ![輸出視窗和錯誤清單](../overview/media/vs2017-output-error-list.png)

在 錯誤清單中，您可以按下**F1**上醒目標示的錯誤，以移至其文件主題。

## <a name="in-this-section"></a>本節內容

[設定 c + + 編譯器和建置在 Visual Studio 中的屬性](working-with-project-properties.md)<br/>
如何使用屬性頁和屬性工作表來指定專案設定。

[參考程式庫和建置階段的元件](adding-references-in-visual-cpp-projects.md)<br/>
如何在專案中包含程式庫、 Dll、 COM 和.NET 元件。
 
[組織專案輸出檔案](how-to-organize-project-output-files-for-builds.md)<br/>
如何自訂建置流程中建立可執行檔的位置。

[自訂建置步驟和建置事件](understanding-custom-build-steps-and-build-events.md)<br/>
如何將任何任意的命令加入至建置程序，在指定的點。

[從現有程式碼建立專案](how-to-create-a-cpp-project-from-existing-code.md)<br/>
如何從原始程式檔的鬆散式集合建立新的 Visual Studio 專案。

## <a name="see-also"></a>另請參閱

[專案和組建系統](projects-and-build-systems-cpp.md)<br>
