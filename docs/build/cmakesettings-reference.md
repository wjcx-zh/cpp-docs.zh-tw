---
title: CMakeSettings.json 結構描述參考
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 0dcd05833af005807d874d71e8f6a07d4e738e8c
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042598"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 結構描述參考

**cmakesettings.json**` 檔案包含的資訊會指定 Visual Studio 應該如何與 CMake 互動，為指定的平台建置專案。 此檔案會儲存環境變數或 cmake.exe 環境引數等資訊。 您可以直接編輯或使用 **CMake 設定編輯器** (Visual Studio 2019 及更新版本)。 如需有關編輯器的詳細資訊，請參閱[在 Visual Studio 中自訂 CMake 建置設定](customize-cmake-settings.md)。

## <a name="environments"></a>環境

`environments` 陣列包含 `object` 類型的 `items` 清單，用於定義「環境」編譯器工具組。 環境可用來將一組變數套用至 `configuration`。 `environments` 陣列中的每個項目都包含：

- `namespace`：命名環境，以便從表單 `namespace.variable` 中的組態參考其變數。 預設的環境物件稱為 `env`，以特定的系統環境變數填入，包括 `%USERPROFILE%`。
- `environment`：唯一識別此變數群組。 稍後在 `inheritEnvironments` 項目中允許繼承該群組。
- `groupPriority`：整數，在評估這些變數時指定其優先順序。 先評估數值較高的項目。
- `inheritEnvironments`：值陣列，指定此群組繼承的環境組。 此功能可讓您繼承預設環境，以及建立自訂環境變數，以在執行時傳遞至 CMake.exe。

   ```json
   "inheritEnvironments": [ "msvc_x64_x64" ]
   ```

   上述範例相當於使用 **-arch=amd64 -host_arch=amd64** 引數執行 **VS 2017 開發人員命令提示字元**或 **VS 2019 開發人員命令提示字元**。 可以使用任何自訂的環境，或這些預先定義的環境：
 
  - linux_arm：從遠端鎖定 ARM Linux。
  - linux_x64：從遠端鎖定 x64 Linux。
  - linux_x86：從遠端鎖定 x86 Linux。
  - msvc_arm：鎖定含 MSVC 編譯器的 ARM Windows。
  - msvc_arm_x64：鎖定含 64 位元 MSVC 編譯器的 ARM Windows。
  - msvc_arm64：鎖定含 MSVC 編譯器的 ARM64 Windows。
  - msvc_arm64_x64：鎖定含 64 位元 MSVC 編譯器的 ARM64 Windows。
  - msvc_x64：鎖定含 MSVC 編譯器的 x64 Windows。
  - msvc_x64_x64：鎖定含 64 位元 MSVC 編譯器的 x64 Windows。
  - msvc_x86：鎖定含 MSVC 編譯器的 x86 Windows。
  - msvc_x86_x64：鎖定含 64 位元 MSVC 編譯器的 x86 Windows。

## <a name="configurations"></a>組態

`configurations` 陣列的組成物件，代表套用至相同資料夾中 CMakeLists.txt 檔案的 CMake 組態。 您可以使用這些物件來定義多個組建組態，並可在 IDE 中輕鬆切換它們。 

`configuration` 有這些屬性：
- `name`：命名組態。
- `description`：此組態的描述會出現在功能表中。
- `generator`：指定要用於此組態的 CMake 產生器。 可能是下列其中之一：
  
  **僅限 Visual Studio 2019：**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 及更新版本：**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix Makefiles
  - Ninja

由於 Ninja 是專為加快建置速度 (而不是彈性和功能) 所設計，因此預設會設定此產生器。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況，您可以指示 CMake 改為產生 Visual Studio 專案。

若要在 Visual Studio 2017 中指定 Visual Studio 產生器，請選擇 [CMake | 變更 CMake 設定]  ，從主功能表開啟 `CMakeSettings.json`。 刪除 “Ninja” 並鍵入 “V”。 這會啟用 IntelliSense，讓您選擇想要的產生器。

若要在 Visual Studio 2019 中指定 Visual Studio 產生器，請以滑鼠右鍵按一下 [方案總管]  中的 CMakeLists.txt 檔案，然後選擇 [專案的 CMake 設定]   > [顯示進階設定]   > [CMake 產生器]  。

當使用中的組態指定 Visual Studio 產生器時，根據預設，會使用 `-m -v:minimal` 引數叫用 MSBuild.exe。 若要自訂組建，在 `CMakeSettings.json` 檔案內部，您可以指定將額外的 [MSBuild 命令列引數](../build/reference/msbuild-visual-cpp-overview.md)透過 `buildCommandArgs` 屬性傳遞至組建系統：

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`：針對所選產生器指定組建類型組態。 可能是下列其中之一：
 
  - 偵錯
  - 版本
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`：指定此組態依賴的一或多個編譯器環境。 可以是任何自訂的環境，或預先定義的環境之一。
- `buildRoot`：指定目錄，CMake 會在此產生所選產生器的組建指令碼。  對應至 **-DCMAKE_BINARY_DIR** 參數並指定 CMake 快取的建立位置。 如果資料夾不存在，則會加以建立。支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `installRoot`：指定目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `cmakeCommandArgs`：指定為產生快取而叫用時，會傳遞到 CMake 的其他命令列選項。
- `cmakeToolchain`：指定工具鏈檔案。 這會使用 -DCMAKE_TOOLCHAIN_FILE 傳遞給 CMake。
- `buildCommandArgs`：指定在 --build -- 之後傳遞到 CMake 的原生組建參數。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。 如需有關 Ninja 命令的詳細資訊，請參閱 [Ninja 命令列引數](#ninja)。
- `ctestCommandArgs`：指定執行測試時，會傳遞到 CTest 的其他命令列選項。
- `codeAnalysisRuleset`：指定執行程式碼分析時要使用的規則集。 這可以是完整的路徑，或是 Visual Studio 安裝之規則集檔案的檔案名稱。
- `intelliSenseMode`：指定計算 Intellisense 資訊時所使用的模式。 可能是下列其中之一：
 
  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `cacheRoot`：指定 CMake 快取的路徑。 此目錄應包含現有 CMakeCache.txt 檔案。

### <a name="additional-settings-for-cmake-linux-projects"></a>CMake Linux 專案的額外設定。 

- `remoteMachineName`：指定裝載 CMake、組建和偵錯工具之遠端 Linux 電腦的名稱。 使用連線管理員新增新的 Linux 電腦。 支援的巨集包括 `${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`：指定從來源到遠端電腦的複製作業詳細資訊層級。 可能為「正常」、「詳細資訊」或「診斷」其中之一。
- `remoteCopySourcesConcurrentCopies`： 指定並行複製到遠端電腦 (僅 sftp) 來源的同步處理期間所使用的數目。
- `remoteCopySourcesMethod`：指定將檔案複製到遠端電腦的方法。 可能為 "rsync" 或 "sftp"。
- `remoteCMakeListsRoot`：指定遠端電腦上包含 CMake 專案的目錄。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteBuildRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的組建指令碼。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteInstallRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}` 和 `${env.VARIABLE}`，其中 `VARIABLE` 是已在系統、使用者或工作階段層級定義的環境變數。
- `remoteCopySources`：`boolean`，指定 Visual Studio 是否應該將來源檔案複製到遠端電腦。 預設值為 true。 如果自行管理檔案同步處理，請設定為 false。
- `remoteCopyBuildOutput`：`boolean`，指定是否要從遠端系統複製組建輸出。
- `rsyncCommandArgs`：指定一組傳遞給 rsync 的額外命令列選項。
- `remoteCopySourcesExclusionList`：`array`指定複製來源檔案時要排除的路徑清單：路徑可以是檔案/目錄名稱，或複本根目錄的相對路徑。 萬用字元 \\\"*\\\" 和 \\\"?\\\" 可以用於 Glob 模式比對。
- `cmakeExecutable`：指定 CMake 程式可執行檔的完整路徑，包括檔案名稱與副檔名。
- `remotePreGenerateCommand`：指定執行 CMake 以剖析 CMakeLists.txt 之前必須執行的命令。
- `remotePrebuildCommand`：指定建置之前必須對遠端電腦執行的命令。
- `remotePostbuildCommand`：指定建置之後必須對遠端電腦執行的命令。
- `variables`：包含成對的 CMake 變數名稱和值，會以 **-D** *_name_=_value_* 形式傳遞至 CMake。 如果您的 CMake 專案建置指示指定直接將任何變數新增至 CMake 快取檔案，建議您改為在此新增。 下列範例會顯示如何指定 14.14.26428 MSVC 工具組的成對名稱和數值：

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

請注意，如果您未定義 `"type"`，預設值會假設為 "STRING" 類型。

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
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
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

## <a name="ninja"></a> Ninja 命令列引數

如果未指定目標，則會建置「預設」目標。

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
|   -t TOOL  | 執行子工具 (使用 -t list 可列出子工具)。 終止最上層選項；並將更多旗標傳遞至工具|
|   -w FLAG  | 調整警告 (使用 -w list 可列出警告)|




