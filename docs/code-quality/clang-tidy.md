---
title: 在 Visual Studio 中使用 Clang 整齊
description: 如何在 Visual Studio 中使用 Clang 整齊的 Microsoft c + + 程式碼分析。
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
ms.openlocfilehash: 30378ab0713d5e00e704f778646b9d60856f2234
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842464"
---
# <a name="using-clang-tidy-in-visual-studio"></a>在 Visual Studio 中使用 Clang 整齊

::: moniker range="<=vs-2017"

Clang 的支援需要 Visual Studio 2019 16.4 版或更新版本。 若要查看此版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end

::: moniker range=">=vs-2019"

針對 MSBuild 和 CMake 專案，程式碼分析原本就支援 [Clang](https://clang.llvm.org/extra/clang-tidy/) ，不論是使用 CLANG 或 MSVC 工具組。 Clang 整齊的檢查可以作為背景程式碼分析的一部分來執行。 它們會顯示為編輯器中的警告 (波浪線) ，並顯示在錯誤清單中。

從 Visual Studio 2019 16.4 版開始提供 Clang 整齊的支援。 當您在 Visual Studio 安裝程式中選擇 c + + 工作負載時，它就會自動包含在內。

使用 LLVM/Clang-cl 工具組時，Clang-整齊是預設的分析工具，可在 MSBuild 和 CMake 中使用。 您可以在使用 MSVC 工具組同時執行，或取代標準的程式碼分析體驗時進行設定。 如果您使用 clang-cl 工具組，則無法使用 Microsoft 程式碼分析。

在成功編譯之後，會執行 Clang 整齊。 您可能需要解決原始程式碼錯誤，才能取得 Clang 整齊的結果。

## <a name="msbuild"></a>MSBuild

您可以在專案屬性視窗的 [程式**代碼分析**  >  **一般**] 頁面中，將 Clang 設定為同時以程式碼分析和組建的一部分來執行。 您可以在 [Clang] 子功能表下找到設定工具的選項。

如需詳細資訊，請參閱 [如何：為 C/c + + 專案設定程式碼分析屬性](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)。

## <a name="cmake"></a>CMake

在 CMake 專案中，您可以在中設定 Clang 整齊的檢查 `CMakeSettings.json` 。 開啟後，選取 CMake 專案設定編輯器右上角的 [編輯 JSON]。 可辨識下列金鑰：

- `enableMicrosoftCodeAnalysis`：啟用 Microsoft 程式碼分析
- `enableClangTidyCodeAnalysis`：啟用 Clang 整齊分析
- `clangTidyChecks`： Clang 整齊的設定，指定為以逗號分隔的清單，也就是要啟用或停用的檢查

如果未指定任何 "enable" 選項，Visual Studio 將會選取符合所使用平臺工具組的分析工具。

## <a name="warning-display"></a>警告顯示

Clang 整齊執行會在錯誤清單中顯示警告，並在程式碼的相關區段底下顯示為編輯器中的波浪線。 您可以使用 [錯誤清單] 中的 [類別] 資料行來排序和組織 Clang 整齊的警告。 您可以切換 [**工具**選項] 下的 [停用程式碼分析波浪線] 設定，以設定編輯器中的警告  >  ** **。

## <a name="clang-tidy-configuration"></a>Clang-整齊設定

您可以透過 [ **clang] 檢查** 選項，設定在 Visual Studio 內執行 clang 整齊的檢查。 此輸入會提供給 **`--checks`** 工具的引數。 任何進一步的設定都可以包含在自訂檔案中 *`.clang-tidy`* 。 如需詳細資訊，請參閱 [LLVM.org 上的 Clang 整齊檔](https://clang.llvm.org/extra/clang-tidy/)。

## <a name="see-also"></a>另請參閱

- [MSBuild 專案的 Clang/LLVM 支援](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [CMake 專案的 Clang/LLVM 支援](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
