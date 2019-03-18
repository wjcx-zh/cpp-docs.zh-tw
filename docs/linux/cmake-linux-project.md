---
title: 在 Visual Studio 中設定 Linux CMake 專案
description: 如何在 Visual Studio 中設定 Linux CMake 專案
ms.date: 11/01/2018
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: f2186c14fbe2eb1273fceb4a378b359564eae327
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750594"
---
# <a name="configure-a-linux-cmake-project"></a>設定 Linux CMake 專案

當您開啟包含 CMake 專案的資料夾時，Visual Studio 會使用 CMake 產生的中繼資料來設定 IntelliSense 並自動建置。 本機組態和偵錯設定會儲存在 JSON 檔案中，可選擇性地與其他使用 Visual Studio 的人員共用。 

Visual Studio 不會修改 CMakeLists.txt 檔案或原始 CMake 快取，因此可讓其他正在使用相同專案之人員繼續使用任何他們已正在使用的工具。  

## <a name="before-you-begin"></a>開始之前

首先，請確認您已安裝 [使用 C++ 進行 Linux 開發] 工作負載，其中包括 CMake 元件。 請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。 

Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 如需 Microsoft 提供的 CMake 種類，請在 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 下載最新的預先建置二進位檔案。

本主題假設您已閱讀[適用於 Visual Studio 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)。 

> [!NOTE]
> Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 針對 Microsoft 所提供的 CMake 變數，請在下列網頁下載最新的預先建置二進位檔：[https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases)。 在 Visual Studio 2019 中，預先建置的二進位檔案可自動部署 (請參閱[下載預先建置的 CMake 二進位檔案](#download-prebuilt-cmake-binaries))。

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

根據預設，Visual Studio 會選擇清單中的第一個遠端系統 (在 [工具] > [選項] > [跨平台] > [連線管理員] 下)。 如果找不到遠端連線，系統會提示您建立一個連線。 如需詳細資訊，請參閱[連線到您的遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)。

指定 Linux 目標之後，您的來源會複製到 Linux 電腦。 然後會在 Linux 電腦上執行 CMake，以產生您專案的 CMake 快取。

![在 Linux 上產生 CMake 快取](media/cmake-linux-1.png "在 Linux 上產生 CMake 快取")

**Visual Studio 2017 15.7 版和更新版本：**<br/>
為了提供遠端標頭的 IntelliSense 支援，Visual Studio 會自動從 Linux 電腦，將其複製到本機 Windows 電腦上的目錄。 如需詳細資訊，請參閱[適用於遠端標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

## <a name="debug-the-project"></a>偵錯專案

若要在遠端系統上偵錯您的程式碼，請設定中斷點、在專案設定旁的工具列功能表中選取 CMake 目標作為啟動項目，然後選擇工具列上的 [&#x23f5; 開始] 或按 F5。

若要自訂您程式的命令列引數，請在 [方案總管] 中以滑鼠右鍵按一下該可執行檔，然後選取 [偵錯並啟動設定]。 這會開啟或建立包含您應用程式資訊的 launch.vs.json 設定檔。 若要指定其他引數，請新增在 `args` JSON 陣列中。 如需詳細資訊，請參閱[在 Visual C++ 中開啟資料夾專案](../ide/non-msbuild-projects.md)及[設定 CMake 偵錯工作階段](../ide/configure-cmake-debugging-sessions.md)。

## <a name="configure-cmake-settings-for-linux"></a>設定適用於 Linux 的 CMake 設定

CMake Linux 專案中的 CMakeSettings.json 檔案可指定所有在[自訂 CMake 設定](../ide/customize-cmake-settings.md)中所列出的屬性，加上控制遠端 Linux 電腦上建置設定的額外屬性。 若要變更預設 CMake 設定，請從主功能表選擇 [CMake] | [變更 CMake 設定] | [CMakeLists.txt]，或在**方案總管**中以滑鼠右鍵按一下 CMakeSettings.txt，然後選擇 [變更 CMake 設定]。 Visual Studio 接著會在您的根專案資料夾中建立新 `CMakeSettings.json` 檔案。 您可以使用 **CMake 設定**編輯器來開啟檔案，或直接修改檔案。 

下列範例顯示根據上一個程式碼範例之 Linux-Debug 的預設組態：

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
下表摘要說明設定：

|設定|說明|
|-----------|-----------------|
|`name`|此值可以是您喜歡的任何值。|
|`remoteMachineName`|指定要瞄準哪一個遠端系統 (若您有一個以上的系統)。 此欄位已啟用 IntelliSense 來協助您選取正確的系統。|
|`remoteCMakeListsRoot`|指定要將專案來源複製到遠端系統上的何處。|
|`remoteBuildRoot`|指定要在您遠端系統上的何處產生建置輸出。 該輸出也會在本機複製到 `buildRoot` 所指定的位置。|
|`remoteInstallRoot` 和 `installRoot`| 與 `remoteBuildRoot` 和 `buildRoot` 相似，但不同的是它們只會在進行 CMake 安裝時套用。|
|`remoteCopySources`|指定是否要將您的本機來源複製到遠端電腦。 若您有許多檔案且您已經自行同步來源，您可以將此設為 False。|
|`remoteCopyOutputVerbosity`| 指定複製步驟的詳細資訊 (若您需要診斷錯誤)。|
|`remoteCopySourcesConcurrentCopies`| 指定要繁衍多少處理序來進行複製。|
|`remoteCopySourcesMethod`| 可以是 `rsync` 或 `sftp`。|
|`remoteCopySourcesExclusionList`| 指定您不想要複製到遠端電腦的檔案。|
|`rsyncCommandArgs`|控制複製的 rsync 方法。|
|`remoteCopyBuildOutput`| 控制是否要將遠端建置輸出複製到您的本機建置資料夾。|

您可以使用這些選擇性設定來取得更多控制：

```json
{
      "remotePreBuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostBuildCommand": "",
}
```

這些選項可讓您在建置前和建置後，以及在 CMake 產生前於遠端系統上執行命令。 其值可以是遠端系統上任何有效的命令。 輸出會經由管道輸送回 Visual Studio。

## <a name="download-prebuilt-cmake-binaries"></a>下載預先建置的 CMake 二進位檔

您的 Linux 發行套件可能會有較舊版本的 CMake。 Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 如需 Microsoft 提供的 CMake 種類，請在 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 下載最新的預先建置二進位檔案。

**Visual Studio 2019**<br/>
若在遠端電腦上找不到有效的 CMake，將會出現資訊列並提供選項以自動部署預先建置的 CMake 二進位檔案。 二進位檔案將安裝到 `~/.vs/cmake`。 部署二進位檔案之後，您的專案將自動重新產生。 請注意，若 `CMakeSettings.json` 中之 `cmakeExecutable` 指定的 CMake 無效 (不存在或它是不支援的版本) 且預先建置的二進位檔案存在，Visual Studio 將會忽略 `cmakeExecutable` 並使用預先建置的二進位檔案。

## <a name="see-also"></a>另請參閱

[使用專案屬性](../ide/working-with-project-properties.md)<br/>
[Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)<br/>
[連線到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)<br/>
[自訂 CMake 設定](../ide/customize-cmake-settings.md)<br/>
[設定 CMake 偵錯工作階段](../ide/configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](../ide/cmake-predefined-configuration-reference.md)<br/>
