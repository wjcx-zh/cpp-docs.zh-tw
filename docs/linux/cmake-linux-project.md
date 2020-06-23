---
title: 在 Visual Studio 中建立及設定 Linux CMake 專案
description: 如何在 Visual Studio 中建立、設定、編輯和編譯 Linux CMake 專案
ms.date: 06/22/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 2149b102c452149070d59c9645ce34a5977a6057
ms.sourcegitcommit: f9344b09a734e8b05a7494415991a22b7aec5ae8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85269724"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>建立及設定 Linux CMake 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="before-you-begin"></a>開始之前

首先，請確認您已安裝 [使用 C++ 進行 Linux 開發]**** 工作負載，其中包括 CMake 元件。 請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

在 Linux 系統上，確定已安裝下列項目：

- gcc
- gdb
- rsync
- zip
- ninja-組建

::: moniker-end

::: moniker range="vs-2019"

CMake 專案的 Linux 支援需要目的電腦擁有最新版本的 CMake。 散發者的預設封裝管理員所提供的版本通常不夠新，無法支援 Visual Studio 所需的所有功能。 Visual Studio 2019 會偵測 Linux 系統上是否已安裝最新版的 CMake。 如果找不到，Visual Studio 會在編輯器窗格的頂端顯示資訊列。 它提供從安裝 CMake 的 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 。

Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 在 Visual Studio 2019 中，建議使用 3.14 或更新版本。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 如需 Microsoft 提供的 CMake 變異，請下載最新的預建二進位檔，網址為 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 。

二進位檔會安裝在中 `~/.vs/cmake` 。 部署二進位檔之後，您的專案會自動重新產生。 如果 `cmakeExecutable` *CMakeSettings.json*的欄位所指定的 CMake 無效（它不存在或不是不支援的版本），而且有預先建立的二進位檔存在，Visual Studio 會忽略 `cmakeExecutable` 並使用預先建立的二進位檔。

:::moniker-end

::: moniker range="vs-2019"

## <a name="create-a-new-linux-cmake-project"></a>建立新的 Linux CMake 專案

若要在 Visual Studio 2019 中設定新的 Linux CMake 專案：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]****，或按 **Ctrl+Shift+N**。
1. 將 [語言]**** 設定為 [C++]****，並搜尋 "CMake"。 然後選擇 [下一步]  。 輸入**名稱**和**位置**，然後選擇 [建立]****。

Visual Studio 會建立最小的*CMakeLists.txt*檔案，其中只包含可執行檔的名稱和所需的最小 CMake 版本。 不過，您可以依需要手動編輯此檔案；Visual Studio 將永遠不會覆寫您的變更。 您可以在此檔案中指定 CMake 命令列引數和環境變數。 以滑鼠右鍵按一下**方案總管**中的根*CMakeLists.txt*檔案，然後選擇 [**專案的 CMake 設定**]。 若要指定用於偵錯的選項，以滑鼠右鍵按一下專案節點，然後選擇 [偵錯並啟動設定]****。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>開啟 CMake 專案資料夾

當您開啟包含現有 CMake 專案的資料夾時，Visual Studio 會使用 CMake 快取中的變數來自動設定 IntelliSense 和組建。 本機設定和調試設定會儲存在 JSON 檔案中。 您可以選擇性地與使用 Visual Studio 的其他人共用這些檔案。

Visual Studio 不會修改*CMakeLists.txt*檔案。 它是單獨的，讓其他使用相同專案的人可以繼續使用現有的工具。 當您將編輯儲存到*CMakeLists.txt*或在某些情況下*CMakeSettings.js*時，Visual Studio 會重新產生快取。 但是，如果您使用**現有**的快取設定，則 Visual Studio 不會修改快取。

如需有關 Visual Studio 中 CMake 支援的一般資訊，請參閱 [Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)。 請先閱讀該文，再於此處繼續。

若要開始使用，**請**從主功能表選擇 [檔案] [  >  **開啟**  >  **資料夾**]，或在 [ `devenv.exe <foldername>` [開發人員命令提示](../build/building-on-the-command-line.md)字元] 視窗中輸入。 您開啟的資料夾中應該有一個*CMakeLists.txt*檔案，以及您的原始程式碼。

下列範例顯示簡單的*CMakeLists.txt*檔案和 .cpp 檔案：

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

## <a name="choose-a-linux-target"></a>選擇 Linux 目標

一旦您開啟資料夾，Visual Studio 會剖析*CMakeLists.txt*檔案，並指定**x86-Debug**的 Windows 目標。 若要以遠端 Linux 系統為目標，請將專案設定變更為 **Linux-Debug** 或 **Linux-Release**。 (請參閱下方的[設定適用於 Linux 的 CMake 設定](#configure_cmake_linux))。

::: moniker-end

::: moniker range="vs-2019"

若要以適用于 Linux 的 Windows 子系統為目標，請在主要工具列的 [設定] 下拉式清單中按一下 [**管理**設定]。 然後按 [**新增**設定] 按鈕，然後選擇 [ **WSL-Debug** ] 或 [ **WSL-發行**] （如果使用 GCC）。 如果使用 Clang/LLVM 工具組，請使用 Clang 變體。

**Visual Studio 2019 16.1 版**以 WSL 為目標時，不需要複製來源或標頭。 這是因為 Linux 上的編譯器可以直接存取 Windows 檔案系統中的來源檔案。 （在 Windows 10 1903 版和更新版本中，Windows 應用程式同樣可以直接存取 Linux 標頭檔。 Visual Studio 還不會利用這項功能）。

::: moniker-end

::: moniker range=">=vs-2017"

Visual Studio 會選擇 [**工具**] [選項] 底下的 [  >  **Options**  >  遠端目標的**跨平臺**  >  **連接管理員**] 清單中的第一個遠端系統。 如果找不到任何遠端連線，系統會提示您建立一個。 如需詳細資訊，請參閱[連線到您的遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)。

如果指定遠端 Linux 目標，您的來源會複製到遠端系統。

選取目標之後，CMake 會自動在 Linux 系統上執行，以便為您的專案產生 CMake 快取。

![在 Linux 上產生 CMake 快取](media/cmake-linux-1.png "在 Linux 上產生 CMake 快取")

### <a name="intellisense"></a>Intellisense

為了提供遠端 Linux 系統標頭的 IntelliSense 支援，Visual Studio 會自動從 Linux 電腦，將其複製到本機 Windows 電腦上的目錄。 如需詳細資訊，請參閱[適用於遠端標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

### <a name="locale"></a>Locale

如需詳細資訊，請參閱[Linux 目標地區設定](configure-a-linux-project.md#locale)。

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a> 為 CMake 專案偵錯

若要在指定的目標系統上，對您的程式碼進行偵錯工具，請設定中斷點。 在專案設定旁邊的工具列功能表中，選取 [CMake] 目標作為 [啟動] 專案。 然後選擇工具列上的 [ **&#x23f5; 開始**]，或按**F5**。

若要自訂程式的命令列引數，請按**方案總管**頂端的 [**切換目標**] 按鈕，然後選擇 [**目標] View**。 接著，以滑鼠右鍵按一下目標，然後選取 [偵錯並啟動設定]****。 此命令會開啟或建立包含程式相關資訊的設定檔案*launch.vs.js* 。 若要指定原始程式檔的位置，請將**sourceFileMap**屬性新增至檔案，如下列範例所示：

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

若要指定其他引數，請新增在 `args` JSON 陣列中。 如需詳細資訊，請參閱 [Open Folder projects for C++](../build/open-folder-projects-cpp.md) (適用於 C++ 的開啟資料夾專案) 及 [Configure CMake debugging sessions](../build/configure-cmake-debugging-sessions.md) (設定 CMake 偵錯工作階段)。

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a>設定 Linux 的 CMake 設定

CMake Linux 專案中的檔案*CMakeSettings.js*可以指定 [[自訂 CMake 設定](../build/customize-cmake-settings.md)] 中所列的所有屬性，再加上控制遠端 Linux 電腦上之組建設定的其他屬性。

::: moniker-end

::: moniker range="vs-2019"

若要變更 Visual Studio 2019 中的預設 CMake 設定，請從主要工具列開啟 [**設定] 下拉式**清單，然後選擇 [**管理**設定]。

![CMake 管理設定](../build/media/vs2019-cmake-manage-configurations.png "CMake 組態下拉式清單")

此命令會顯示 [ **CMake 設定編輯器**]，您可以用來編輯根專案資料夾中檔案的*CMakeSettings.js* 。 您也可以直接在編輯器中按一下 [編輯 JSON]**** 按鈕，開啟該檔案。 如需詳細資訊，請參閱[自訂 CMake 設定](../build/customize-cmake-settings.md)。

Visual Studio 2019 16.1 版和更新版本中的預設 Linux 偵錯組態如下所示：

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```

::: moniker-end

::: moniker range="vs-2017"

若要變更 Visual Studio 2017 中的預設 CMake 設定，請從主功能表選擇 [ **CMake**] [  >  **變更 CMake 設定**] [  >  **CMakeLists.txt** ]。 或者，以滑鼠右鍵按一下**方案總管**中的*CMakeSettings.txt* ，然後選擇 [**變更 CMake 設定**]。 Visual Studio 接著會在根專案資料夾中的檔案上建立新的*CMakeSettings.js* 。 您可以使用 **CMake 設定**編輯器來開啟檔案，或直接修改檔案。 如需詳細資訊，請參閱[自訂 CMake 設定](../build/customize-cmake-settings.md)。

下列範例會根據先前的程式碼範例，顯示 Visual Studio 2017 (和 Visual Studio 2019 16.0 版) 中 Linux-Debug 的預設組態：

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range=">=vs-2017"

如需有關這些設定的詳細資訊，請參閱 [CMakeSettings.json 參考](../build/cmakesettings-reference.md)。

## <a name="optional-settings"></a>選擇性設定

您可以使用下列選擇性設定來取得更多控制：

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

這些選項可讓您在建置前和建置後，以及在 CMake 產生前於 Linux 系統上執行命令。 其值可以是遠端系統上任何有效的命令。 輸出會經由管道輸送回 Visual Studio。

## <a name="see-also"></a>另請參閱

[使用專案屬性](../build/working-with-project-properties.md)<br/>
[Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)<br/>
[連線到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)<br/>
[自訂 CMake 設定](../build/customize-cmake-settings.md)<br/>
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)<br/>
[部署、執行和偵錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
