---
title: 在 Visual Studio 中設定 Linux CMake 專案
description: 如何在 Visual Studio 中設定 Linux CMake 設定
ms.date: 08/08/2020
ms.openlocfilehash: d39423b803b66d6bdf55cc67d488e74ccb682323
ms.sourcegitcommit: 2034f8e744a8b36cff8b15e9a5cfe684afebadfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "88048186"
---
# <a name="configure-a-linux-cmake-project-in-visual-studio"></a>在 Visual Studio 中設定 Linux CMake 專案

::: moniker range="vs-2015"
Visual Studio 2017 及更新版本支援 Linux。 若要查看這些版本的檔，請將位於目錄上方的**版本**下拉式清單設定為**Visual Studio 2017**或**Visual Studio 2019**。
::: moniker-end

::: moniker range=">=vs-2017"
本主題說明如何將 Linux 設定新增至 CMake 專案，其目標為遠端 Linux 系統或適用于 Linux 的 Windows 子系統 (WSL) 。 它會繼續[在 Visual Studio 中建立 Linux CMake 專案](cmake-linux-project.md)一開始的系列。 如果您是使用 MSBuild，請參閱[在 Visual Studio 中設定 Linux MSBuild 專案](configure-a-linux-project.md)。

## <a name="add-a-linux-configuration"></a>新增 Linux 設定

設定可以用來將不同的平臺設為目標， (Windows、WSL，以及具有相同原始程式碼的遠端系統) 。 設定也可用來設定您的編譯器、傳遞環境變數，以及自訂 CMake 的叫用方式。 檔案*上的CMakeSettings.js*會指定 [[自訂 CMake 設定](../build/customize-cmake-settings.md)] 中所列的部分或所有屬性，再加上控制遠端 Linux 電腦上之組建設定的其他屬性。
::: moniker-end

::: moniker range="vs-2017"
若要變更 Visual Studio 2017 中的預設 CMake 設定，請從主功能表選擇 [ **CMake**] [  >  **變更 CMake 設定**] [  >  **CMakeLists.txt** ]。 或者，以滑鼠右鍵按一下**方案總管**中的*CMakeLists.txt* ，然後選擇 [**變更 CMake 設定**]。 Visual Studio 接著會在根專案資料夾中的檔案上建立新的*CMakeSettings.js* 。 若要進行變更，請開啟檔案並直接加以修改。 如需詳細資訊，請參閱[自訂 CMake 設定](../build/customize-cmake-settings.md)。

在 Visual Studio 2017 (和 Visual Studio 2019 版本 16.0) 中，Linux 的預設設定為 [Debug]，如下所示：

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

::: moniker range="vs-2019"
若要變更 Visual Studio 2019 中的預設 CMake 設定，請從主要工具列開啟 [**設定] 下拉式**清單，然後選擇 [**管理**設定]。

![CMake 管理設定](../build/media/vs2019-cmake-manage-configurations.png "CMake 組態下拉式清單")

此命令會開啟 [ **CMake 設定編輯器**]，您可以用來編輯根專案資料夾中檔案的*CMakeSettings.js* 。 您也可以按一下編輯器中的 [**編輯 json** ] 按鈕，以 JSON 編輯器開啟檔案。 如需詳細資訊，請參閱[自訂 CMake 設定](../build/customize-cmake-settings.md)。

Visual Studio 2019 16.1 版和更新版本中的預設 Linux-Debug 設定如下所示：

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

在 Visual Studio 2019 16.6 或更新版本中，Ninja 是以遠端系統或 WSL 為目標之設定的預設產生器。 如需詳細資訊，請參閱[c + + 小組 Blog](https://devblogs.microsoft.com/cppblog/linux-development-with-visual-studio-first-class-support-for-gdbserver-improved-build-times-with-ninja-and-updates-to-the-connection-manager/)的這篇文章。

::: moniker-end
::: moniker range=">=vs-2017"
如需有關這些設定的詳細資訊，請參閱 [CMakeSettings.json 參考](../build/cmakesettings-reference.md)。

當您執行組建時：
- 如果您的目標是遠端系統，Visual Studio 會選擇 [**工具**] [選項] 底下的 [遠端目標] 下的 [ > **Options** > 依**平臺** > **連線管理員**] 清單中的第一個遠端系統。
- 如果找不到任何遠端連線，系統會提示您建立一個。 如需詳細資訊，請參閱[連線到您的遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)。

## <a name="choose-a-linux-target"></a>選擇 Linux 目標

當您開啟 CMake 專案資料夾時，Visual Studio 會剖析*CMakeLists.txt*檔案，並指定**x86-Debug**的 Windows 目標。 若要將目標設為遠端 Linux 系統，您必須將專案設定變更為**Linux-Debug**或**linux 版本**。

如果指定遠端 Linux 目標，您的來源會複製到遠端系統。

選取目標後，CMake 會自動在 Linux 系統上執行，以產生您專案的 CMake 快取：

![在 Linux 上產生 CMake 快取](media/cmake-linux-1.png "在 Linux 上產生 CMake 快取")

::: moniker-end
::: moniker range="vs-2019"

### <a name="target-windows-subsystem-for-linux"></a>適用于 Linux 的 Windows 子系統目標

如果您的目標是適用于 Linux 的 Windows 子系統 (WSL) ，則不需要新增遠端連線。

若要以 WSL 為目標，請在主要工具列的 [設定] 下拉式清單中選取 [**管理**設定]。 然後按 [**新增**設定] 按鈕，然後選擇 [ **WSL-Debug** ] 或 [ **WSL-發行**] （如果使用 GCC）。 如果使用 Clang/LLVM 工具組，請使用 Clang 變體。

**Visual Studio 2019 16.1 版**當您以 WSL 為目標時，Visual Studio 不需要複製原始程式檔並維護兩個組建樹狀目錄的同步複本，因為 Linux 上的編譯器可直接存取裝載的 Windows 檔案系統中的來源檔案。
::: moniker-end
::: moniker range=">=vs-2017"

### <a name="intellisense"></a>IntelliSense

必須能夠存取 c + + 原始程式檔所參考的 c + + 標頭，才能正確地使用 c Visual Studio 會自動使用從 Linux 到 Windows 的 CMake 專案所參考的標頭，以提供完全失真的 IntelliSense 體驗。 如需詳細資訊，請參閱[適用於遠端標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

### <a name="locale-setting"></a>地區設定

Visual Studio 語言設定不會傳播到 Linux 目標，因為 Visual Studio 不會管理或設定已安裝的套件。 顯示在 [輸出] 視窗中的訊息，例如組建錯誤，會使用 Linux 目標的語言和地區設定來顯示。 您必須針對所需的地區設定，設定您的 Linux 目標。

## <a name="additional-settings"></a>其他設定

使用下列設定在建立之前和之後，以及在 CMake 產生之前，于 Linux 系統上執行命令。 其值可以是遠端系統上任何有效的命令。 輸出會經由管道輸送回 Visual Studio。

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

## <a name="next-steps"></a>後續步驟

[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)

## <a name="see-also"></a>另請參閱

[使用專案屬性](../build/working-with-project-properties.md)<br/>
[自訂 CMake 設定](../build/customize-cmake-settings.md)<br/>
[CMake 預先定義組態參考](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
