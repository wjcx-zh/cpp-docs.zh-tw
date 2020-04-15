---
title: 在視覺工作室中使用 Clang-Tidy
description: 如何在可視化工作室中使用Clang-Tidy進行微軟C++代碼分析。
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355154"
---
# <a name="using-clang-tidy-in-visual-studio"></a>在視覺工作室中使用 Clang-Tidy

::: moniker range="<=vs-2017"

支援 Clang-Tidy 需要 Visual Studio 2019 版本 16.4 或更高版本。 要查看此版本的文檔,請將本文的可視化工作室**版本**選擇器控制項設定為 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end

::: moniker range=">=vs-2019"

代碼分析本機支援用於 MSBuild 和 CMake 專案的[Clang-Tidy,](https://clang.llvm.org/extra/clang-tidy/)無論是使用 Clang 還是 MSVC 工具集。 Clang-Tidy 檢查可以作為背景代碼分析的一部分運行。 它們顯示為編輯器內警告(擺動),並顯示在錯誤清單中。

Clang-Tidy 支援可從 Visual Studio 2019 版本 16.4 中開始提供。 當您在可視化工作室安裝程式中選擇C++工作負載時,它會自動包括在內。

Clang-Tidy 是使用 LLVM/clang-cl 工具集時的預設分析工具,在 MSBuild 和 CMake 中都可用。 您可以使用 MSVC 工具集與標準代碼分析體驗一起運行或替換它。 如果使用 clang-cl 工具集,則 Microsoft 代碼分析不可用。

Clang-Tidy 在成功編譯後運行。 您可能需要解決原始程式碼錯誤,以獲得 Clang-Tidy 結果。

## <a name="msbuild"></a>MSBuild

您可以將 Clang-Tidy 設定為作為代碼分析的一部分運行,並在「項目屬性」視窗中的代碼**分析** > **常規**頁下生成。 配置工具的選項可以在 Clang-Tidy 子功能表下找到。

有關詳細資訊,請參閱[如何:為 C/C++專案設定代碼分析屬性](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)。

## <a name="cmake"></a>CMake

在"製作"專案中,可以在`CMakeSettings.json`中配置 Clang-Tidy 檢查。 打開後,按一下「完成項目設置編輯器」右上角的「編輯 JSON」。。 識別以下鍵:

- `enableMicrosoftCodeAnalysis`: 開啟微軟碼分析
- `enableClangTidyCodeAnalysis`: 開啟 Clang-Tidy 分析
- `clangTidyChecks`:Clang-Tidy 設定,指定為逗號分隔清單,即要啟用或禁用的檢查

如果未指定兩個"啟用"選項,Visual Studio 將選擇與所使用的平臺工具集匹配的分析工具。

## <a name="warning-display"></a>警告顯示

Clang-Tidy 執行會導致錯誤列表中顯示的警告,並且作為編輯器中的代碼相關部分下方的擺動。 使用錯誤清單中的「類別」列對 Clang-Tidy 警告進行排序和組織。 您可以通過切換"禁用代碼分析擺動"設置在 **"工具** > **選項**」下配置編輯器內警告。

## <a name="clang-tidy-configuration"></a>Clang-Tidy 設定

您可以通過**Clang-Tidy 檢查**選項設定在 Visual Studio 中執行的支票。 此輸入提供給工具的 **--檢查**參數。 任何進一步的配置都可以包含在自定義*`.clang-tidy`* 檔中。 有關詳細資訊,請參閱[有關 LLVM.org 的 Clang-Tidy 文件](https://clang.llvm.org/extra/clang-tidy/)。

## <a name="see-also"></a>另請參閱

- [Clang/LLVM 支援 MS 建設專案](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Clang/LLVM 支援 CMake 專案](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
