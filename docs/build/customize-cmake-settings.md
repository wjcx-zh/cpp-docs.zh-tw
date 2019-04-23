---
title: 自訂 Visual Studio 中的 CMake 建置設定
ms.date: 03/05/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 1bdf4ef3e20b055b6fa3d5449a880ddb7aab44a0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037519"
---
# <a name="customize-cmake-build-settings"></a>自訂 CMake 建置設定

Visual Studio 提供數種 CMake 組態，定義如何叫用 CMake.exe 來建立指定專案的 CMake 快取。 若要新增新的組態，請按一下工具列中的 [組態] 下拉式清單，然後選擇 [管理組態]：

   ![CMake 管理組態](media/cmake-manage-configurations.png)

您可以從預先定義組態的清單中選擇：

   ![CMake 預先定義組態](media/cmake-configurations.png)

當您第一次選取組態時，Visual Studio 會在您專案的根資料夾中建立一個 `CMakeSettings.json` 檔案。 此檔案會用來重新建立 CMake 快取檔案，例如在**清除**作業之後。 

若要新增額外的組態，請以滑鼠右鍵按一下 `CMakeSettings.json`，然後選擇 [新增組態]。 

   ![CMake 新增組態](media/cmake-add-configuration.png "CMake 新增組態")

JSON IntelliSense 會協助您編輯 `CMakeSettings.json` 檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

您也可以使用 **CMake 設定編輯器**來編輯檔案。 請以滑鼠右鍵在 [方案總管] 中按一下 `CMakeSettings.json`，然後選擇 [編輯 CMake 設定]。 或者，從編輯器視窗頂端的 [組態] 下拉式清單，選取 [管理組態]。 

您也可以直接編輯 `CMakeSettings.json` 來建立自訂組態。下列範例顯示範例組態，可讓您用來作為起點：

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

- **name**：出現在 C++ 組態下拉式清單中的名稱。 `${name}` 巨集可讓您在撰寫其他屬性值 (例如路徑) 時使用此值。 如需範例，請參閱 `CMakeSettings.json` 中的 **buildRoot** 定義。

- **generator**：對應至 CMake **-G** 變更切換並指定要使用的產生器。 此屬性也可以在撰寫其他屬性值時用來作為巨集 `${generator}`。 Visual Studio 目前支援下列 CMake 產生器：

  - "Ninja"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 ARM"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 15 2017 Win64"

  由於 Ninja 是專為加快建置速度 (而不是彈性和功能) 所設計，因此預設會設定此產生器。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況，您可以指示 CMake 改為產生 Visual Studio 專案。

  若要指定 Visual Studio 產生器，請選擇 [CMake | 變更 CMake 設定]，從主功能表開啟 `CMakeSettings.json`。 刪除 “Ninja” 並鍵入 “V”。 這會啟用 IntelliSense，讓您選擇想要的產生器。

  當使用中的組態指定 Visual Studio 產生器時，根據預設，會使用 `-m -v:minimal` 引數叫用 MSBuild.exe。 若要自訂組建，在 `CMakeSettings.json` 檔案內部，您可以指定將額外的 [MSBuild 命令列引數](../build/reference/msbuild-visual-cpp-overview.md)透過 `buildCommandArgs` 屬性傳遞至組建系統：
    
    ```json
    "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
    ```

- **buildRoot**：對應至 **-DCMAKE_BINARY_DIR** 參數並指定 CMake 快取的建立位置。 如果資料夾不存在，則會建立資料夾。

- **variables**：包含成對的 CMake 變數名稱和值，會以 **-D** *_name_=_value_* 形式傳遞至 CMake。 如果您的 CMake 專案建置指示指定直接將任何變數新增至 CMake 快取檔案，建議您改為在此新增。 下列範例會顯示如何指定 14.14.26428 MSVC 工具組的成對名稱和數值：

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    }
  ]
```

- **cmakeCommandArgs**：指定您要傳遞至 CMake.exe 的任何其他參數。

- **configurationType**：定義所選產生器的組建組態類型。 目前支援的值為 "Debug"、"MinSizeRel"、"Release" 和 "RelWithDebInfo"。

- **ctestCommandArgs**：指定在執行測試時要傳遞到 CTest 的額外參數。

- **buildCommandArgs**：指定要傳遞到基礎建置系統的額外參數。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。

額外設定也適用於 CMake Linux 專案。 請參閱[設定 CMake Linux 專案](../linux/cmake-linux-project.md)。

## <a name="environment-variables"></a>環境變數

 `CMakeSettings.json` 也支援在任何上述提及的內容中取用環境變數。 使用的語法是 `${env.FOO}`，可擴充環境變數 %FOO%。
您也可以存取此檔案的內建巨集：

- `${workspaceRoot}` - 提供工作區資料夾的完整路徑
- `${workspaceHash}` - 工作區位置的雜湊；適用於建立目前工作區的唯一識別碼 (例如用於資料夾路徑)
- `${projectFile}` - 根 CMakeLists.txt 檔案的完整路徑
- `${projectDir}` - 根 CMakeLists.txt 檔案資料夾的完整路徑
- `${thisFile}` – `CMakeSettings.json` 檔案的完整路徑
- `${name}` - 組態的名稱
- `${generator}` - 用於此組態之 CMake 產生器的名稱

## <a name="ninja-command-line-arguments"></a>Ninja 命令列引數

如果未指定目標，則會建置「預設」目標 (請參閱手冊)。

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|選項|描述|
|--------------|------------|
| --version  | 列印 Ninja 版本 ("1.7.1")|
|   -C DIR   | 變更為 DIR 再執行其他任何動作|
|   -f FILE  | 指定輸入組建檔案 (預設值=build.ninja)|
|   -j N     | 以平行方式執行 N 個作業 (預設值=14，衍生自可用的 CPU 數目)|
|   -k N     | 繼續進行直到 N 個作業失敗 (預設值=1)|
|   -l N     | 如果平均負載大於 N，不要啟動新的作業|
|   -n       | 試執行 (不執行命令但假裝已成功)|
|   -v       | 建置時顯示所有命令列|
|   -d MODE  | 啟用偵錯 (使用 -d list 可列出模式)|
|   -t TOOL  | 執行子工具 (使用 -t list 可列出子工具)。 結束最上層的選項;進一步將旗標傳遞至工具|
|   -w FLAG  | 調整警告 (使用 -w list 可列出警告)|

## <a name="inherited-environments"></a>繼承環境

 `CMakeSettings.json` 支援繼承的環境。 此功能可讓您 (1) 繼承預設環境，以及 (2) 建立自訂環境變數，以在執行時傳遞至 CMake.exe。

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

上述範例相當於使用 **-arch=amd64 -host_arch=amd64** 引數執行 **VS 2017 開發人員命令提示字元**。

下表顯示預設值：

|內容名稱|描述|
|-----------|-----------------|
|vsdev|預設 Visual Studio 環境|
|msvc_x86|使用 x86 工具對 x86 進行編譯|
|msvc_arm| 使用 x86 工具對 ARM 進行編譯|
|msvc_arm64|使用 x86 工具對 ARM64 進行編譯|
|msvc_x86_x64|使用 x86 工具對 AMD64 進行編譯|
|msvc_x64_x64|使用 64 位元工具對 AMD64 進行編譯|
|msvc_arm_x64|使用 64 位元工具對 ARM 進行編譯|
|msvc_arm64_x64|使用 64 位元工具對 ARM64 進行編譯|

### <a name="custom-environment-variables"></a>自訂環境變數

在 `CMakeSettings.json` 中，您可以全域或根據 **environments** 屬性中的組態來定義自訂環境變數。 下列範例會定義一個全域變數 **BuildDir**，這是 x86-Debug 和 x64-Debug 組態中會繼承的變數。 每個組態使用此變數來指定該組態的 **buildRoot** 屬性值。 另請注意每個組態如何使用 **inheritEnvironments** 屬性來指定只會套用至該組態的變數。

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

在下一個範例中，x86-Debug 組態會針對 **BuildDir** 屬性定義其自身的值。 此值會覆寫全域 **BuildDir** 屬性設定的值，使 **BuildRoot** 的評估結果為 `D:\custom-builddir\x86-Debug`。

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir",
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="see-also"></a>另請參閱

[CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)<br/>
