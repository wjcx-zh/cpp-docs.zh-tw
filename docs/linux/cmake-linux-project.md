---
title: 在 Visual Studio 中設定 Linux CMake 專案 | Microsoft Docs
description: 如何在 Visual Studio 中設定 Linux CMake 專案
ms.custom: ''
ms.date: 07/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 0e735ece878797ffdcf89fffefa33473107ad3d5
ms.sourcegitcommit: 7098d64443ffbd4a47f30bc41753007b570b47e8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120560"
---
# <a name="configure-a-linux-cmake-project"></a>設定 Linux CMake 專案

**Visual Studio 2017 15.4 版和更新版本**<br/>
當您為 Visual Studio 安裝 Linux C++ 工作負載時，預設會選取適用於 Linux 的 CMake 支援。 您現在可以使用採用 CMake 的現有程式碼基底，而不必將它轉換成 Visual Studio 專案。 如果程式碼基底為跨平台，您可以從 Visual Studio 內將 Windows 和 Linux 鎖定為目標。

本主題假設您對 Visual Studio 中的 CMake 支援有基本認識。 如需詳細資訊，請參閱 [Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)。 如需 CMake 本身的詳細資訊，請參閱 [Build, Test and Package Your Software With CMake](https://cmake.org/) (使用 CMake 建置、測試及封裝您的軟體)。

> [!NOTE]  
> Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 針對 Microsoft 所提供的 CMake 變數，請在下列網頁下載最新的預先建置二進位檔：[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)。 

## <a name="open-a-folder"></a>開啟資料夾

若要開始使用，請從主功能表選擇 [檔案] > [開啟] > [資料夾]，或在命令列上鍵入 `devenv.exe <foldername>`。 您開啟的資料夾內應該有 CMakeLists.txt 檔案，以及您的原始程式碼。
下列範例顯示簡單的 CMakeLists.txt 檔案和 .cpp 檔案：

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

CMakeLists.txt：

```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>選擇 Linux 目標

只要您開啟資料夾，Visual Studio 就會剖析 CMakeLists.txt 檔案，並指定 **x86-Debug** 的 Windows 目標。 若要以 Linux 為目標，請將專案設定變更為 **Linux-Debug** 或 **Linux-Release**。

根據預設，Visual Studio 會選擇清單中的第一個遠端系統 (在 [工具] > [選項] > [跨平台] > [連線管理員] 下)。 如果找不到遠端連線，系統會提示您建立一個連線。

指定 Linux 目標之後，您的來源會複製到 Linux 電腦。 然後會在 Linux 電腦上執行 CMake，以產生您專案的 CMake 快取。

![在 Linux 上產生 CMake 快取](media/cmake-linux-1.png "在 Linux 上產生 CMake 快取")

**Visual Studio 2017 15.7 版和更新版本：**<br/>
為了提供遠端標頭的 IntelliSense 支援，Visual Studio 會自動將之複製到本機 Windows 電腦上的目錄。 如需詳細資訊，請參閱[適用於遠端標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

## <a name="debug-the-project"></a>偵錯專案

若要在遠端系統上偵錯您的程式碼，請設定中斷點、在專案設定旁的工具列功能表中選取 CMake 目標作為啟動項目，然後選擇工具列上的 [&#x23f5; 開始] 或按 F5。

若要自訂您程式的命令列引數，請在 [方案總管] 中以滑鼠右鍵按一下該可執行檔，然後選取 [偵錯並啟動設定]。 這會開啟或建立包含您應用程式資訊的 launch.vs.json 設定檔。 若要指定其他引數，請新增在 `args` JSON 陣列中。 如需詳細資訊，請參閱 [Visual C++ 中的「開啟資料夾」專案](../ide/non-msbuild-projects.md)。

## <a name="configure-cmake-settings-for-linux"></a>設定適用於 Linux 的 CMake 設定

若要變更預設 CMake 設定，請從主功能表選擇 [CMake] | [變更 CMake 設定] | [CMakeLists.txt]，或在**方案總管**中以滑鼠右鍵按一下 CMakeSettings.txt，然後選擇 [變更 CMake 設定]。 Visual Studio 接著會在您的資料夾中建立新的檔案 `CMakeSettings.json`，並填入 [專案設定] 功能表項目中列出的預設組態。 下列範例顯示根據上一個程式碼範例之 Linux-Debug 的預設組態：

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

`name` 值可以是您喜歡的任何值。 `remoteMachineName` 值指定以哪部遠端系統為目標 (如果有多部遠端系統)。 此欄位已啟用 IntelliSense 來協助您選取正確的系統。 `remoteCMakeListsRoot` 欄位指定專案來源將要複製到的遠端系統。 `remoteBuildRoot` 欄位是遠端系統上將產生組建輸出的位置。 該輸出也會在本機複製到 `buildRoot` 所指定的位置。 `remoteInstallRoot` 和 `installRoot` 欄位類似於 `remoteBuildRoot` 和 `buildRoot`，不同之處在於前者會在進行 CMake 安裝時套用。 `remoteCopySources` 項目會控制您的本機來源是否複製到遠端電腦。 若您有大量檔案，而且已經自行同步來源，可能會將此設為 false。 若您需要診斷錯誤，`remoteCopyOutputVerbosity` 值會控制複製步驟的詳細資訊。 `remoteCopySourcesConcurrentCopies` 項目會控制要繁衍多少處理序來進行複製。 `remoteCopySourcesMethod` 值可以是 rsync 或 sftp 其中之一。 `remoteCopySourcesExclusionList` 欄位可讓您控制會複製到遠端電腦的內容。 `rsyncCommandArgs` 值可讓您控制複製的 rsync 方法。 `remoteCopyBuildOutput` 欄位會控制遠端組建輸出是否複製到您的本機組建資料夾。

另外還有幾項選擇性設定可用來進行其他控制：

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

這些選項可讓您在建置前後及 CMake 產生之前，於遠端方塊執行命令。 這些命令可以是遠端方塊上的任何有效命令。 輸出會經由管線回到 Visual Studio。

## <a name="download-prebuilt-cmake-binaries"></a>下載預先建置的 CMake 二進位檔

您的 Linux 發行套件可能會有較舊版本的 CMake。 Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 針對 Microsoft 所提供的 CMake 變數，請在下列網頁下載最新的預先建置二進位檔：[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)。 


## <a name="see-also"></a>請參閱

[使用專案屬性](../ide/working-with-project-properties.md)<br/>
[Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)  
