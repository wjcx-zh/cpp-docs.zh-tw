---
title: 視覺化工作室 CMake 專案中的 Clang/LLVM 支援
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323185"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>視覺化工作室 CMake 專案中的 Clang/LLVM 支援

::: moniker range="<=vs-2017"

Clang 支援可在 Visual Studio 2019 中提供。

::: moniker-end

::: moniker range="vs-2019"

您可以將 Visual Studio 與 Clang 一起編輯和調試C++面向 Windows 或 Linux 的 CMake 專案。

**Windows**: Visual Studio 2019 版本 16.1 包括在面向 Windows 的 CMake 專案中使用 Clang/LLVM 進行編輯、構建和調試的支援。

**Linux**:對於 Linux CMake 專案,不需要特殊的視覺工作室支援。 您可以使用發行版的包管理器安裝 Clang,並在 CMakelists.txt 檔中添加相應的命令。

## <a name="install"></a>安裝

為了在 Visual Studio 中獲得最佳 IDE 支援,我們建議使用 Windows 的最新 Clang 編譯器工具。 如果還沒有這些,則可以通過打開 Visual Studio 安裝程式和選擇桌面開發下的 Windows **C++ Clang 編譯器**來安裝它們 **,C++** 可選元件。 使用自訂 Clang 安裝時,請檢查**C++ Clang-cl 中的 v142 生成工具**元件。

![Clang 元件安裝](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>建立新設定

要加入 CMake 專案加入新的 Clang 設定,:

1. 右鍵按下**解決方案資源管理員**中的 CMakelists.txt,然後選擇**項目的「CMake」設定**。

1. 在 **「設定」** 下,按 **「新增設定**」按鈕:

   ![新增設定](media/cmake-add-config-icon.png)

1. 選擇所需的 Clang 設定(請注意,為 Windows 與 Linux 提供單獨的 Clang 設定),然後按 **「選擇**」 :

   ![CMake Clang 設定](media/cmake-clang-configuration.png)

1. 要修改此設定,請使用 **「CMake 設定編輯器**」 。。 有關詳細資訊,請參閱[在可視化工作室中自定義 CMake 產生設定](customize-cmake-settings.md)。

## <a name="modify-an-existing-configuration-to-use-clang"></a>變更現有設定以使用 Clang

要修改現有設定以使用 Clang,請按照以下步驟操作:

1. 右鍵按下**解決方案資源管理員**中的 CMakelists.txt,然後選擇**項目的「CMake」設定**。

1. 在 **「一般」** 選擇 **「工具集**下拉」並選擇所需的 Clang 工具集:

   ![CMake Clang 工具集](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>自訂 Clang 位置

預設情況下,Visual Studio 在兩個位置查找 Clang:

- (視窗)視覺工作室安裝程式附帶的 Clang/LLVM 的內部安裝副本。
- (視窗和Linux)PATH 環境變數。

您可以透過在 **「製作設定**」中設定**CMAKE_C_COMPILER**和**CMAKE_CXX_COMPILER** CMake 變數來指定其他位置:

![CMake Clang 工具集](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 相容性模式

對於 Windows 配置,CMake 預設情況下以[clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)模式調用 Clang,並與標準庫的 Microsoft 實現連結。 默認情況下 **,clang-cl.exe**位於`C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`中。

您可以在 **「CMake」變數和快取**下的 **「CMake 設定」** 中修改這些值。 按下 **「顯示進階變數**」 。 向下滾動以查找**CMAKE_CXX_COMPILER**,然後按**下 「流覽」** 按鈕以指定其他編譯器路徑。

## <a name="edit-build-and-debug"></a>編輯、產生及除錯

設置 Clang 配置後,可以生成和調試專案。 Visual Studio 檢測到您正在使用 Clang 編譯器,並提供 IntelliSense、突出顯示、導航和其他編輯功能。 錯誤與警告顯示在**輸出視窗中**。

調試時,可以使用斷點、記憶體和數據可視化以及大多數其他調試功能。 某些與編譯器相關的功能(如"編輯"和"繼續")不適用於 Clang 配置。

![CMake Clang 除錯](media/clang-debug-visualize.png)

::: moniker-end
