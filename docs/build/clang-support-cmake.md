---
title: Visual Studio CMake 專案中的 Clang/LLVM 支援
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 4e912c905dd7d0f742768da4c7a2acb968b4ca8e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218278"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Visual Studio CMake 專案中的 Clang/LLVM 支援

::: moniker range="<=vs-2017"

Visual Studio 2019 提供 Clang 支援。

::: moniker-end

::: moniker range="vs-2019"

您可以使用 Visual Studio 搭配 Clang 來編輯和調試C++以 Windows 或 Linux 為目標的 CMake 專案。

**Windows**：Visual Studio 2019 16.1 版包含在以 Windows 為目標的 CMake 專案中, 對 Clang/LLVM 進行編輯、建立和偵錯工具的支援。 

**Linux**：針對 Linux CMake 專案, 不需要任何特殊的 Visual Studio 支援。 您可以使用散發版本的套件管理員安裝 Clang, 並在 Remote monitoring.h cmakelists.txt 檔案中新增適當的命令。

## <a name="install"></a>安裝

如需 Visual Studio 中的最佳 IDE 支援, 我們建議使用適用于 Windows 的最新 Clang 編譯器工具。 如果您還沒有這些專案, 您可以開啟 Visual Studio 安裝程式, 然後在 [**桌面開發C++**  ] 下選擇 [ **C++** 使用選用元件的 Clang 編譯器] 來安裝它們。 使用自訂 Clang 安裝時, 請核取 [  **C++ Clang-cl for 適用于 v142 build tools** ] 元件。

![Clang 元件安裝](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>建立新的設定

若要將新的 Clang 設定加入至 CMake 專案:

1. 以滑鼠右鍵按一下**方案總管**中的 [remote monitoring.h cmakelists.txt], 然後選擇 [**專案的 CMake 設定**]。

1. 在[設定] 下, 按 [**新增**設定] 按鈕:

   ![新增設定](media/cmake-add-config-icon.png)

1. 選擇所需的 Clang 設定 (請注意, 系統會針對 Windows 和 Linux 提供個別的 Clang 設定), 然後按下 [**選取**]:

   ![CMake Clang 設定](media/cmake-clang-configuration.png)

1. 若要對此設定進行修改, 請使用 [ **CMake 設定編輯器**]。 如需詳細資訊, 請參閱[在 Visual Studio 中自訂 CMake 組建設定](customize-cmake-settings.md)。

## <a name="modify-an-existing-configuration-to-use-clang"></a>修改現有設定以使用 Clang

若要修改現有設定以使用 Clang, 請遵循下列步驟:

1. 以滑鼠右鍵按一下**方案總管**中的 [remote monitoring.h cmakelists.txt], 然後選擇 [**專案的 CMake 設定**]。

1. 在 **[一般**] 底下選取 [**工具**組] 下拉式清單, 然後選擇所需的 Clang 工具組

   ![CMake Clang 工具組](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>自訂 Clang 位置

根據預設, Visual Studio 會在兩個位置中尋找 Clang:

- 時段Visual Studio 安裝程式隨附之 Clang/LLVM 的內部安裝複本。
- (Windows 和 Linux)PATH 環境變數。

您可以在 [ **CMAKE 設定**] 中設定**CMAKE_C_COMPILER**和**CMAKE_CXX_COMPILER** CMAKE 變數, 以指定另一個位置:

![CMake Clang 工具組](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 相容性模式

對於 Windows 設定, CMake 預設會在[Clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式中叫用 Clang, 並使用標準程式庫的 Microsoft 實作為連結。 根據預設, **clang-cl**位於`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`。

 您可以在 [ **CMake 變數和**快取] 底下的 [ **CMake 設定**] 中修改這些值。 按一下 [**顯示先進的變數**]。 向下滾動以尋找 [ **CMAKE_CXX_COMPILER**], 然後按一下 [**流覽]** 按鈕以指定不同的編譯器路徑。

## <a name="edit-build-and-debug"></a>編輯、組建和 debug

設定 Clang 設定之後, 您可以建立並對專案進行 debug。 Visual Studio 偵測到您使用 Clang 編譯器, 並提供 IntelliSense、醒目提示、導覽和其他編輯功能。 錯誤和警告會顯示在**輸出視窗**中。

在調試時, 您可以使用中斷點、記憶體和資料視覺效果, 以及大部分其他的調試功能。 某些與編譯器相關的功能 (例如 [編輯後繼續]) 不適用於 Clang 設定。

![CMake Clang 的調試](media/clang-debug-visualize.png)

::: moniker-end
