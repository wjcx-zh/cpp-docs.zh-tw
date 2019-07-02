---
title: Visual Studio 的 CMake 專案中的 clang/LLVM 支援
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++
ms.openlocfilehash: 6773d9cdb076ef305ba635306f3bc9c6575d2203
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67517103"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Visual Studio 的 CMake 專案中的 clang/LLVM 支援

::: moniker range="<=vs-2017"

使用 Visual Studio 2019 clang 支援。

::: moniker-end

::: moniker range="vs-2019"

您可以使用 Clang 使用 Visual Studio 來編輯和偵錯C++CMake 專案的目標 Windows 或 Linux。

**Windows**：Visual Studio 2019 版本 16.1 包含編輯、 建置和使用 Clang/LLVM 以 Windows 為目標的 CMake 專案中進行偵錯的支援。 

**Linux**：沒有特殊的 Visual Studio 支援 Linux CMake 專案，則需要。 Instalovat Clang 使用您的散發套件的套件管理員，即可 CMakeLists.txt 檔案中新增適當的命令。

## <a name="install"></a>安裝

如需在 Visual Studio 中的最佳 IDE 支援，我們建議使用最新的 Clang 編譯器 tools for Windows。 如果您還沒有這些，您可以安裝它們開啟 Visual Studio 安裝程式，然後選擇**Windows 的 Clang 編譯器**下方**使用的桌面開發C++** 選用元件。

![Clang 元件安裝](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>建立新的組態

若要將新的 Clang 組態新增至 CMake 專案中：

1. 以滑鼠右鍵按一下中 CMakeLists.txt**方案總管 中**，然後選擇**專案的 CMake 設定**。

1. 底下**組態**，按下**加入組態**按鈕：

   ![新增組態](media/cmake-add-config-icon.png)

1. 選擇所需的 Clang 設定 （請注意，區隔的 Clang 組態會提供適用於 Windows 和 Linux），然後按**選取**:

   ![CMake Clang 組態](media/cmake-clang-configuration.png)

1. 要修改此組態，請使用**CMake 設定編輯器**。 如需詳細資訊，請參閱 <<c0> [ 來自訂 CMake 建置 Visual Studio 中的設定](customize-cmake-settings.md)。

## <a name="modify-an-existing-configuration-to-use-clang"></a>修改現有的組態使用 Clang

若要修改現有的組態，以使用 Clang，請遵循下列步驟：

1. 以滑鼠右鍵按一下中 CMakeLists.txt**方案總管 中**，然後選擇**專案的 CMake 設定**。

1. 底下**一般**選取**工具組**下拉式清單中選擇所需的 Clang 工具組：

   ![CMake Clang 工具組](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>自訂的 Clang 位置

根據預設，Visual Studio 會尋找 Clang 在兩個地方：

- (Windows)Clang/LLVM 隨附於 Visual Studio 安裝程式在內部已安裝的複本。
- （Windows 和 Linux）PATH 環境變數中。

您可以指定另一個位置，藉由設定**CMAKE_C_COMPILER**並**CMAKE_CXX_COMPILER**中的 CMake 變數**CMake 設定**:

![CMake Clang 工具組](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 的相容性模式

針對 Windows 設定，預設的 CMake 叫用中的 Clang [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式和標準程式庫的 Microsoft 實作的連結。 根據預設， **clang cl.exe**位於`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`。

 您可以修改這些值**CMake 設定**下方**CMake 變數和快取**。 按一下 **顯示變數的進階**。 向下捲動找到**CMAKE_CXX_COMPILER**，然後按一下**瀏覽**按鈕，以指定不同的編譯器的路徑。

## <a name="edit-build-and-debug"></a>編輯、 建置和偵錯

您已將 Clang 組態設定之後，您可以建置和偵錯專案。 Visual Studio 會偵測您使用 Clang 編譯器，並提供 IntelliSense、 反白顯示，瀏覽，以及其他編輯功能。 中會顯示錯誤和警告**輸出視窗**。

偵錯時，您可以使用中斷點、 記憶體和資料視覺效果和其他大部分的偵錯功能。 某些編譯器有相依性功能，例如編輯後繼續不適用 Clang 組態。

![CMake Clang 偵錯](media/clang-debug-visualize.png)

::: moniker-end
