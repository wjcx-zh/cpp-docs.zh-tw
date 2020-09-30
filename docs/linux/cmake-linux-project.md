---
title: 在 Visual Studio 中建立 CMake Linux 專案
description: 如何在 Visual Studio 中建立 Linux CMake 專案
ms.date: 08/06/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 5753dbb37c11686becb3e141261284b68468a3bc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507955"
---
# <a name="create-a-cmake-linux-project-in-visual-studio"></a>在 Visual Studio 中建立 CMake Linux 專案

::: moniker range="vs-2015"
Visual Studio 2017 及更新版本支援 Linux。 若要查看這些版本的檔，請將位於目錄上方的 **版本** 下拉式清單設定為 **Visual Studio 2017** 或 **Visual Studio 2019**。
::: moniker-end

::: moniker range=">=vs-2017"

建議您針對跨平臺的專案使用 CMake，或將其設為開放原始碼。 您可以使用 CMake 專案，在 Windows、Windows 子系統 Linux 版 (WSL) 和遠端系統上建立和調試相同的原始程式碼。

## <a name="before-you-begin"></a>開始之前

首先，請確定您已安裝 Visual Studio 的 Linux 工作負載，包括 CMake 元件。 這就是在 Visual Studio 安裝程式中 **使用 c + +** 工作負載的 Linux 開發工作負載。 如果您不確定是否已安裝，請參閱 [在 Visual Studio 中安裝 c + + Linux 工作負載](download-install-and-setup-the-linux-development-workload.md) 。

此外，請確定已在遠端電腦上安裝下列各項：

- gcc
- gdb
- rsync
- zip
- ninja-組建 (Visual Studio 2019 或更新版本) 
::: moniker-end

::: moniker range="vs-2017"
Visual Studio 中的 CMake 支援需要 CMake 3.8 中引進的伺服器模式支援。 若為 Microsoft 提供的 CMake 變體，請下載最新的預建二進位檔 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 。

二進位檔會安裝在中 `~/.vs/cmake` 。 部署二進位檔之後，您的專案會自動重新產生。 如果CMakeSettings.js中的欄位所指定的 CMake `cmakeExecutable` 無效 (它不存在或不是支援的版本) ，且預建的二進位檔存在，Visual Studio 會忽略*CMakeSettings.json* `cmakeExecutable` 並使用預建的二進位檔。

Visual Studio 2017 無法從頭開始建立 CMake 專案，但是您可以開啟包含現有 CMake 專案的資料夾，如下一節所述。
::: moniker-end

::: moniker range=">=vs-2019"
您可以使用 Visual Studio 2019 在遠端 Linux 系統或 WSL 上建立和偵錯工具，而 CMake 將會在該系統上叫用。 目的電腦上應該安裝 Cmake 3.14 版或更新版本。

請確定目的電腦具有最新版本的 CMake。 通常，散發套件的預設封裝管理員所提供的版本，並不夠新，無法支援 Visual Studio 所需的所有功能。 Visual Studio 2019 會偵測 Linux 系統上是否已安裝最新版的 CMake。 如果找不到，Visual Studio 會在編輯器窗格的頂端顯示資訊列。 它提供從為您安裝 CMake [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 。

使用 Visual Studio 2019，您可以從頭開始建立 CMake 專案，或開啟現有的 CMake 專案。 若要建立新的 CMake 專案，請遵循下列指示。 如果您已經有 CMake 專案，請直接跳到 [開啟 CMake 專案資料夾](#open-a-cmake-project-folder) 。

## <a name="create-a-new-linux-cmake-project"></a>建立新的 Linux CMake 專案

若要在 Visual Studio 2019 中設定新的 Linux CMake 專案：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]****，或按 **Ctrl+Shift+N**。
1. 將 [語言]**** 設定為 [C++]****，並搜尋 "CMake"。 然後選擇 [下一步]  。 輸入**名稱**和**位置**，然後選擇 [建立]****。

或者，您可以在 Visual Studio 2019 中開啟自己的 CMake 專案。 下一節將說明如何。

Visual Studio 會建立最小的 *CMakeLists.txt* 檔案，其中只包含可執行檔的名稱以及所需的最小 CMake 版本。 不過，您可以依需要手動編輯此檔案；Visual Studio 將永遠不會覆寫您的變更。

若要協助您瞭解、編輯及撰寫 Visual Studio 2019 中的 CMake 腳本，請參閱下列資源：

- [Visual Studio 中 CMake 的編輯器內檔](https://devblogs.microsoft.com/cppblog/in-editor-documentation-for-cmake-in-visual-studio/)
- [CMake 腳本的程式碼導覽](https://devblogs.microsoft.com/cppblog/code-navigation-for-cmake-scripts/)
- [輕鬆地新增、移除和重新命名 CMake 專案中的檔案和目標](https://devblogs.microsoft.com/cppblog/easily-add-remove-and-rename-files-and-targets-in-cmake-projects/)
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>開啟 CMake 專案資料夾

當您開啟包含現有 CMake 專案的資料夾時，Visual Studio 會使用 CMake 快取中的變數來自動設定 IntelliSense 和組建。 本機設定和調試設定會儲存在 JSON 檔案中。 您可以選擇性地與使用 Visual Studio 的其他人共用這些檔案。

Visual Studio 不會修改 *CMakeLists.txt* 的檔案。 這可讓其他正在使用相同專案的人繼續使用其現有的工具。 當您將編輯儲存至 *CMakeLists.txt*（或在某些情況下）來 *CMakeSettings.js*時，Visual Studio 會重新產生快取。 如果您是使用 **現有** 的快取設定，則 Visual Studio 不會修改快取。

如需有關 Visual Studio 中 CMake 支援的一般資訊，請參閱 [Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。 在這裡繼續進行之前，請先閱讀。

若要開始使用，**請**  >  從主功能表選擇 [檔案**開啟**  >  **資料夾**]，或 `devenv.exe <foldername>` 在[開發人員命令提示](../build/building-on-the-command-line.md)字元視窗中輸入。 您開啟的資料夾中應該有 *CMakeLists.txt* 檔案，以及您的原始程式碼。

下列範例顯示簡單的 *CMakeLists.txt* 檔案和 .cpp 檔案：

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt*：

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="next-steps"></a>後續步驟

[設定 Linux CMake 專案](cmake-linux-configure.md)

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)<br/>
::: moniker-end
