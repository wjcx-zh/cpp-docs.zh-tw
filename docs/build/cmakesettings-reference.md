---
title: CMakeSettings.json 結構描述參考
ms.date: 10/31/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 6f8301c07f87feee80191f5db14fea5b16f02863
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624418"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 結構描述參考

::: moniker range="vs-2015"

Visual Studio 2017 和更新版本支援 CMake 專案。

::: moniker-end

::: moniker range=">=vs-2017"

**CMakeSettings**會包含 Visual Studio 用於 IntelliSense 的資訊，以及用來*針對指定的*設定和編譯器*環境*，建立傳遞至 cmake 的命令列引數。 設定會指定適用于特定平臺和組建類型的屬性，例如 `x86-Debug` 或 `Linux-Release`。 每個設定都會指定一個環境，其中封裝了編譯器工具組的相關資訊，例如 MSVC、GCC 或 Clang。 CMake 會使用命令列引數來重新產生專案的根*cmakecache.txt .txt*檔案和其他專案檔案。 這些值可以在*remote monitoring.h cmakelists.txt 的 .txt*檔案中覆寫。 

您可以在 IDE 中新增或移除設定，然後直接在 JSON 檔案中編輯它們，或使用 [ **CMake 設定編輯器**] （Visual Studio 2019 和更新版本）。 您可以在 IDE 中輕鬆地切換設定，以產生各種專案檔案。 如需詳細資訊，請參閱[在 Visual Studio 中自訂 CMake 組建設定](customize-cmake-settings.md)。

## <a name="configurations"></a>組態

`configurations` 陣列包含 CMake 專案的所有設定。 如需預先定義設定的詳細資訊，請參閱[CMake 預先](cmake-predefined-configuration-reference.md)定義的設定參考。 您可以將任何數目的預先定義或自訂設定新增至檔案。 

`configuration` 有這些屬性：

- `addressSDanitizerEnabled`：如果 `true` 使用 Address Sanitizer （實驗性在 Windows 上）來編譯器。 在 Linux 上，請使用-fno-rtti-省略框架指標和編譯器優化層級-Os 或-Oo 進行編譯，以獲得最佳結果。
- `addressSanitizerRuntimeFlags`：透過 ASAN_OPTIONS 環境變數傳遞至 AddressSanitizer 的執行時間旗標。 格式：-1 = 值：標誌 2 = value2。
- `buildCommandArgs`：指定在 --build -- 之後傳遞到 CMake 的原生組建參數。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。 如需有關 Ninja 命令的詳細資訊，請參閱 [Ninja 命令列引數](#ninja)。
- `buildRoot`：指定目錄，CMake 會在此產生所選產生器的組建指令碼。  對應至 **-DCMAKE_BINARY_DIR** 參數並指定 CMake 快取的建立位置。 如果資料夾不存在，則會建立資料夾。 支援的宏包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`和 `${env.VARIABLE}`。
- `cacheGenerationCommand`：指定命令列工具和引數，例如*gencache* ，以產生快取。 當使用者明確要求重新產生，或修改 Remote monitoring.h cmakelists.txt 或 CMakeSettings 檔案時，會從指定環境中的 shell 執行命令。
- `cacheRoot`：指定 CMake 快取的路徑。 此目錄應包含現有 CMakeCache.txt 檔案。
- `clangTidyChecks`：以逗號分隔的 warnigns 清單，將會傳遞給 clang-整齊;允許使用萬用字元，而 '-' 前置詞將會移除檢查。
- `cmakeCommandArgs`：指定為產生快取而叫用時，會傳遞到 CMake 的其他命令列選項。
- `cmakeToolchain`：指定工具鏈檔案。 這會使用 -DCMAKE_TOOLCHAIN_FILE 傳遞給 CMake。
- `codeAnalysisRuleset`：指定執行程式碼分析時要使用的規則集。 這可以是完整的路徑，或是 Visual Studio 安裝之規則集檔案的檔案名稱。
- `configurationType`：針對所選產生器指定組建類型組態。 可能是下列其中之一：

  - 偵錯
  - 版本
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`：指定執行測試時，會傳遞到 CTest 的其他命令列選項。
- `description`：此組態的描述會出現在功能表中。
- `enableClangTidyCodeAnalysis`：使用 Clang-整齊進行程式碼分析。
- `enableMicrosoftCodeAnalysis`：使用 Microsoft 程式碼分析工具進行程式碼分析。
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

若要在 Visual Studio 2017 中指定 Visual Studio 產生器，請從主功能表中選擇 [CMake] 來開啟。 **變更 CMake 設定**。 刪除 “Ninja” 並鍵入 “V”。 這會啟用 IntelliSense，讓您選擇想要的產生器。

若要在 Visual Studio 2019 中指定 Visual Studio 產生器，請以滑鼠右鍵按一下**方案總管**中的*remote monitoring.h cmakelists.txt* ，然後選擇 [**專案] 的 [CMake 設定**] > [ **Show Advanced settings** ] > **CMake產生器。**

當使用中的組態指定 Visual Studio 產生器時，根據預設，會使用 `-m -v:minimal` 引數叫用 MSBuild.exe。 若要在*CMakeSettings*中自訂群組建，您可以透過 `buildCommandArgs` 屬性來指定要傳遞至組建系統的其他[MSBuild 命令列引數](../build/reference/msbuild-visual-cpp-overview.md)：

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`：針對所選產生器指定組建類型組態。 可能是下列其中之一：

  - 偵錯
  - 版本
  - MinSizeRel
  - RelWithDebInfo
 
- `buildRoot`：指定目錄，CMake 會在此產生所選產生器的組建指令碼。  對應至 **-DCMAKE_BINARY_DIR**參數，並指定將建立*cmakecache.txt*的位置。 如果資料夾不存在，則會加以建立。支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `installRoot`：指定目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `cmakeCommandArgs`：指定在叫用以產生專案檔時，傳遞至 CMake 的其他命令列選項。
- `cmakeToolchain`：指定工具鏈檔案。 這會使用 -DCMAKE_TOOLCHAIN_FILE 傳遞給 CMake。
- `buildCommandArgs`：指定在 --build -- 之後傳遞到 CMake 的原生組建參數。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。 如需有關 Ninja 命令的詳細資訊，請參閱 [Ninja 命令列引數](#ninja)。
- `ctestCommandArgs`：指定執行測試時，會傳遞到 CTest 的其他命令列選項。
- `codeAnalysisRuleset`：指定執行程式碼分析時要使用的規則集。 這可以是完整的路徑，或是 Visual Studio 安裝之規則集檔案的檔案名稱。
- `inheritEnvironments`：指定此組態依賴的一或多個編譯器環境。 可以是任何自訂的環境，或預先定義的環境之一。 如需詳細資訊，請參閱[環境](#environments)。
- `installRoot`：指定目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
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

- `cacheRoot`：指定 CMake 快取的路徑。 此目錄應包含現有的*cmakecache.txt*檔案。
- `name`：命名組態。  如需預先定義設定的詳細資訊，請參閱[CMake 預先](cmake-predefined-configuration-reference.md)定義的設定參考。
- `wslPath`：適用于 Linux 的 Windows 子系統實例的啟動器路徑。

### <a name="additional-settings-for-cmake-linux-projects"></a>CMake Linux 專案的額外設定。 

- `remoteMachineName`：指定裝載 CMake、組建和偵錯工具之遠端 Linux 電腦的名稱。 使用連線管理員新增新的 Linux 電腦。 支援的巨集包括 `${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`：指定從來源到遠端電腦的複製作業詳細資訊層級。 可能為「正常」、「詳細資訊」或「診斷」其中之一。
- `remoteCopySourcesConcurrentCopies`：指定將來源同步處理到遠端電腦（僅限 sftp）期間，所使用的並行副本數目。
- `remoteCopySourcesMethod`：指定將檔案複製到遠端電腦的方法。 可能為 "rsync" 或 "sftp"。
- `remoteCMakeListsRoot`：指定遠端電腦上包含 CMake 專案的目錄。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteBuildRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的組建指令碼。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteInstallRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}` 和 `${env.VARIABLE}`，其中 `VARIABLE` 是已在系統、使用者或工作階段層級定義的環境變數。
- `remoteCopySources`：指定 Visual Studio 是否應該將來源檔案複製到遠端電腦的 `boolean`。 預設值為 true。 如果自行管理檔案同步處理，請設定為 false。
- `remoteCopyBuildOutput`：指定是否要從遠端系統複製組建輸出的 `boolean`。
- `rsyncCommandArgs`：指定一組傳遞給 rsync 的額外命令列選項。
- `remoteCopySourcesExclusionList`：指定複製來源檔案時要排除的路徑清單的 `array`：路徑可以是檔案/目錄的名稱，或是複製之根目錄的相對路徑。 萬用字元 \\\"*\\\" 和 \\\"?\\\" 可以用於 Glob 模式比對。
- `cmakeExecutable`：指定 CMake 程式可執行檔的完整路徑，包括檔案名稱與副檔名。
- `remotePreGenerateCommand`：指定執行 CMake 以剖析*remote monitoring.h cmakelists.txt .txt*檔案之前，要執行的命令。
- `remotePrebuildCommand`：指定建置之前必須對遠端電腦執行的命令。
- `remotePostbuildCommand`：指定建置之後必須對遠端電腦執行的命令。
- `variables`：包含成對的 CMake 變數名稱和值，會以 **-D** *_name_=_value_* 形式傳遞至 CMake。 如果您的 CMake 專案組建指示指定將任何變數直接新增至*cmakecache.txt* ，建議您改為在此加入。 下列範例會顯示如何指定 14.14.26428 MSVC 工具組的成對名稱和數值：

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

請注意，如果您未定義 `"type"`，預設會假設 `"STRING"` 類型。

## <a name="environments"></a>環境

*環境*會封裝 Visual Studio 用來叫用 cmake 的進程中所設定的環境變數。 若為 MSVC 專案，變數就是在特定平臺的[開發人員命令提示](building-on-the-command-line.md)字元中設定的變數。 例如，`msvc_x64_x64` 環境與針對**vs 2017 執行開發人員命令提示字元**，或使用 **---a-i-host_arch = amd64**引數**執行 vs 2019 的開發人員命令提示字元**相同。 您可以使用*CMakeSettings*中的 `env.{<variable_name>}` 語法來參考個別的環境變數，例如，用來建立資料夾的路徑。  提供下列預先定義的環境：

- linux_arm：從遠端鎖定 ARM Linux。
- linux_x64：從遠端鎖定 x64 Linux。
- linux_x86：從遠端鎖定 x86 Linux。
- msvc_arm：以 MSVC 編譯器作為 ARM 視窗的目標。
- msvc_arm_x64：以64位 MSVC 編譯器作為 ARM Windows 的目標。
- msvc_arm64：具有 MSVC 編譯器的目標 ARM64 視窗。
- msvc_arm64_x64：使用64位 MSVC 編譯器的 ARM64 Windows 目標。
- msvc_x64：使用 MSVC 編譯器以 x64 視窗為目標。
- msvc_x64_x64：以具有64位 MSVC 編譯器的 x64 Windows 為目標。
- msvc_x86：以 MSVC 編譯器為 x86 視窗設定目標。
- msvc_x86_x64：以64位 MSVC 編譯器為 x86 視窗設定目標。

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>從 Remote monitoring.h cmakelists.txt 存取環境變數

從 Remote monitoring.h cmakelists.txt 的檔案中，所有環境變數都是由語法 `$ENV{variable_name}`所參考。 若要查看環境的可用變數，請開啟對應的命令提示字元，然後輸入 `SET`。 環境變數中的某些資訊也可以透過 CMake 系統自我檢查變數取得，但您可能會發現使用環境變數會比較方便。 例如，您可以輕鬆地透過環境變數來抓取 MSVC 編譯器版本或 Windows SDK 版本。

### <a name="custom-environment-variables"></a>自訂環境變數

在 `CMakeSettings.json`中，您可以在全域或 `environments` 陣列中的每個設定定義自訂環境變數。 自訂環境是一種方便的方式，可將一組可用來取代預先定義環境的屬性，或擴充或修改預先定義的環境。 `environments` 陣列中的每個項目都包含：

- `namespace`：命名環境，以便從表單 `namespace.variable` 中的組態參考其變數。 預設的環境物件稱為 `env`，並會填入特定的系統內容變數，包括 `%USERPROFILE%`。
- `environment`：唯一識別此變數群組。 稍後在 `inheritEnvironments` 項目中允許繼承該群組。
- `groupPriority`：整數，指定這些變數在評估時的優先順序。 先評估數值較高的項目。
- `inheritEnvironments`：值的陣列，指定此群組所繼承的環境集合。 此功能可讓您繼承預設環境，以及建立自訂環境變數，以在執行時傳遞至 CMake.exe。

下列範例會定義一個全域變數 **BuildDir**，這是 x86-Debug 和 x64-Debug 組態中會繼承的變數。 每個組態使用此變數來指定該組態的 **buildRoot** 屬性值。 另請注意每個組態如何使用 **inheritEnvironments** 屬性來指定只會套用至該組態的變數。

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

## <a name="macros"></a>巨集

下列宏可以在*CMakeSettings*中使用：

- `${workspaceRoot}` –工作區資料夾的完整路徑
- `${workspaceHash}` - 工作區位置的雜湊；適用於建立目前工作區的唯一識別碼 (例如用於資料夾路徑)
- `${projectFile}` - 根 CMakeLists.txt 檔案的完整路徑
- `${projectDir}` - 根 CMakeLists.txt 檔案資料夾的完整路徑
- `${thisFile}` – `CMakeSettings.json` 檔案的完整路徑
- `${name}` - 組態的名稱
- `${generator}` - 用於此組態之 CMake 產生器的名稱

在傳遞至 cmake 命令列之前，會展開*CMakeSettings*中宏和環境變數的所有參考。

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

::: moniker-end
