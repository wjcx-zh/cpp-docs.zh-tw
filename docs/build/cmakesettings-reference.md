---
title: CMakeSettings.json 結構描述參考
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: f9c864b66df86165090b7d6d6fc9c4fc51d65a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328886"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 結構描述參考

::: moniker range="vs-2015"

2017 年及以後的 Visual Studio 支援 CMake 專案。

::: moniker-end

::: moniker range=">=vs-2017"

**CMakeSettings.json**檔包含 Visual Studio 用於 IntelliSense 的資訊,並建構它傳遞給 cmake.exe 的指令列參數,用於指定的*設定*和編譯器*環境*。 設定指定在特定平台與產生類型的屬性,例如,`x86-Debug`或`Linux-Release`。 每個配置指定一個環境,該環境封裝有關編譯器工具集的資訊,例如 MSVC、GCC 或 Clang。 CMake 使用命令列參數重新生成專案的根*CMakeCache.txt*檔案和其他專案檔。 可以在*CMakelists.txt*檔中重寫這些值。

您可以在 IDE 中添加或刪除配置,然後直接在 JSON 檔中編輯這些配置,或使用**CMake 設定編輯器**(Visual Studio 2019 及更高版本)。 您可以在 IDE 中的設定之間輕鬆切換以生成各種專案檔。 有關詳細資訊,請參閱[在可視化工作室中自訂「自訂單行」產生設定](customize-cmake-settings.md)。

## <a name="configurations"></a>組態

該`configurations`陣列包含 CMake 專案的所有配置。 有關預先定義設定的詳細資訊,請參考[CMake 預先定義的設定參考](cmake-predefined-configuration-reference.md)。 可以向檔案添加任意數量的預定義或自定義配置。

`configuration` 有這些屬性：

- `addressSanitizerEnabled`:如果使用`true`位址消毒器編譯程式(在 Windows 上進行實驗)。 在 Linux 上,使用 -fno-omit 幀指標和編譯器優化級別 -O 或 -Oo 編譯以獲得最佳結果。
- `addressSanitizerRuntimeFlags`:通過ASAN_OPTIONS環境變數傳遞給位址薩尼策器的運行時標誌。 格式:標誌1=值:標誌2=值2。
- `buildCommandArgs`：指定在 --build -- 之後傳遞到 CMake 的原生組建參數。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。 如需有關 Ninja 命令的詳細資訊，請參閱 [Ninja 命令列引數](#ninja)。
- `buildRoot`：指定目錄，CMake 會在此產生所選產生器的組建指令碼。  映射到 **-DCMAKE_BINARY_DIR**交換機並指定將在何處創建*CMakeCache.txt。* 如果資料夾不存在，則會建立資料夾。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `cacheGenerationCommand`:指定命令列工具和參數,例如*gencache.bat 除錯*以生成緩存。 當使用者顯式請求重新生成時,該命令從指定環境中的 shell 運行,或者修改 CMakelists.txt 或 CMakeSettings.json 檔。
- `cacheRoot`：指定 CMake 快取的路徑。 此目錄應包含現有的*CMakeCache.txt*檔。
- `clangTidyChecks`:逗號分隔的警告清單,將傳遞給clang-tidy;通配符是允許的,並且"-" 首碼將刪除檢查。
- `cmakeCommandArgs`:指定在調用生成專案檔時傳遞給 CMake 的其他命令列選項。
- `cmakeToolchain`：指定工具鏈檔案。 這會使用 -DCMAKE_TOOLCHAIN_FILE 傳遞給 CMake。
- `codeAnalysisRuleset`：指定執行程式碼分析時要使用的規則集。 這可以是完整的路徑，或是 Visual Studio 安裝之規則集檔案的檔案名稱。
- `configurationType`：針對所選產生器指定組建類型組態。 可能是下列其中之一：

  - 偵錯
  - 版本
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`：指定執行測試時，會傳遞到 CTest 的其他命令列選項。
- `description`：此組態的描述會出現在功能表中。
- `enableClangTidyCodeAnalysis`:使用 Clang-Tidy 進行代碼分析。
- `enableMicrosoftCodeAnalysis`:使用微軟代碼分析工具進行代碼分析。
- `generator`：指定要用於此組態的 CMake 產生器。 可能是下列其中之一：
  
  **僅限視覺工作室 2019:**
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

由於 Ninja 是專為加快建置速度 (而不是彈性和功能) 所設計，因此預設會設定此產生器。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況,您可以指示 CMake 改為生成 Visual Studio 專案。

要在 Visual Studio 2017 中指定 Visual Studio 生成器,請選擇**CMake |更改"製作設置"** 刪除"忍者"併鍵入"V"。 這會啟用 IntelliSense，讓您選擇想要的產生器。

要在 Visual Studio 2019 中指定 Visual Studio 生成器,請右鍵單擊**解決方案資源管理器**中的*CMakelists.txt*>檔,然後為專案 **「顯示進階設定**>**」"製作生成器**「選擇 **」CMake 設定」。。**

當使用中的組態指定 Visual Studio 產生器時，根據預設，會使用 `-m -v:minimal` 引數叫用 MSBuild.exe。 要自訂產生,請在*CMakeSettings.json*檔中指定`buildCommandArgs`要透過 屬性傳遞給產生系統的其他[MSBuild 命令列參數](../build/reference/msbuild-visual-cpp-overview.md):

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot`：指定目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `inheritEnvironments`：指定此組態依賴的一或多個編譯器環境。 可以是任何自訂的環境，或預先定義的環境之一。 如需詳細資訊，請參閱[環境](#environments)。
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

- `name`：命名組態。  有關預先定義設定的詳細資訊,請參考[CMake 預先定義的設定參考](cmake-predefined-configuration-reference.md)。
- `wslPath`:Linux Windows 子系統實例的啟動器的路徑。

### <a name="additional-settings-for-cmake-linux-projects"></a>CMake Linux 專案的其他設定

- `remoteMachineName`：指定裝載 CMake、組建和偵錯工具之遠端 Linux 電腦的名稱。 使用連線管理員新增新的 Linux 電腦。 支援的巨集包括 `${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`：指定從來源到遠端電腦的複製作業詳細資訊層級。 可能為「正常」、「詳細資訊」或「診斷」其中之一。
- `remoteCopySourcesConcurrentCopies`:指定源與遠端電腦同步期間使用的併發副本數(僅限 sftp)。
- `remoteCopySourcesMethod`：指定將檔案複製到遠端電腦的方法。 可能為 "rsync" 或 "sftp"。
- `remoteCMakeListsRoot`：指定遠端電腦上包含 CMake 專案的目錄。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteBuildRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的組建指令碼。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteInstallRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}` 和 `${env.VARIABLE}`，其中 `VARIABLE` 是已在系統、使用者或工作階段層級定義的環境變數。
- `remoteCopySources`:`boolean`指定 Visual Studio 是否應將源檔案複製到遠端電腦。 預設值是 true。 如果自行管理檔案同步處理，請設定為 false。
- `remoteCopyBuildOutput`:`boolean`指定是否從遠端系統複製生成輸出。
- `remoteCopyAdditionalIncludeDirectories`:其他包括從遠端計算機複製的目錄,以支援 IntelliSense。 格式為"/路徑1;/path2..."。
- `remoteCopyExcludeDirectories`:包括不從遠端計算機複製的目錄。 格式為"/路徑1;/path2..."。
- `remoteCopyUseCompilerDefaults`:指定是否使用編譯器的預設值定義,並包含 IntelliSense 的路徑。 僅當使用的編譯器不支援 gcc 樣式參數時,才應為 false。
- `rsyncCommandArgs`：指定一組傳遞給 rsync 的額外命令列選項。
- `remoteCopySourcesExclusionList``array`指定複製來源檔時要排除的路徑清單的:路徑可以是檔/目錄的名稱,也可以是相對於副本根目錄的路徑。 萬用字元 \\\"*\\\" 和 \\\"?\\\" 可以用於 Glob 模式比對。
- `cmakeExecutable`：指定 CMake 程式可執行檔的完整路徑，包括檔案名稱與副檔名。
- `remotePreGenerateCommand`:指定在執行 CMake 以解析*CMakelists.txt*檔之前執行的命令。
- `remotePrebuildCommand`：指定建置之前必須對遠端電腦執行的命令。
- `remotePostbuildCommand`：指定建置之後必須對遠端電腦執行的命令。
- `variables`：包含成對的 CMake 變數名稱和值，會以 **-D** *_name_=_value_* 形式傳遞至 CMake。 如果您的 CMake 專案產生說明指定將任何變數直接添加到*CMakeCache.txt*檔中,建議您在此處添加這些變數。 下列範例會顯示如何指定 14.14.26428 MSVC 工具組的成對名稱和數值：

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

請注意,如果不定義`"type"`, 則默認情況下將`"STRING"`假定 類型。

- `remoteCopyOptimizations`:Visual **Studio 2019 版本 16.5 或更高版本**用於控制源複製到遠端目標的屬性。 默認情況下啟用優化。 包含 `remoteCopyUseOptimizations`、`rsyncSingleDirectoryCommandArgs` 與 `remoteCopySourcesMaxSmallChange`。

## <a name="environments"></a><a name="environments"></a>環境

*環境*封裝了在 Visual Studio 用於調用 cmake.exe 的過程中設置的環境變數。 對於 MSVC 專案,變數是在特定平台的[開發人員命令提示符](building-on-the-command-line.md)中設置的變數。 `msvc_x64_x64`例如,環境與使用 **-arch_amd64 -host_arch_amd64**參數運行**VS 2017 的開發人員命令提示**符或 VS **2019 的開發人員命令提示符**相同。 您可以使用`env.{<variable_name>}`*CMakeSettings.json*中的語法來引用各個環境變數,例如建構資料夾的路徑。  提供以下預先定義環境:

- linux_arm:遠端定位 ARM Linux。
- linux_x64:遠端定位 x64 Linux。
- linux_x86:遠端定位x86 Linux。
- msvc_arm:使用 MSVC 編譯器定位 ARM Windows。
- msvc_arm_x64:使用 64 位 MSVC 編譯器定位 ARM Windows。
- msvc_arm64:使用 MSVC 編譯器定位 ARM64 Windows。
- msvc_arm64_x64:使用 64 位 MSVC 編譯器定位 ARM64 Windows。
- msvc_x64:使用 MSVC 編譯器定位 x64 Windows。
- msvc_x64_x64:使用 64 位 MSVC 編譯器定位 x64 Windows。
- msvc_x86:使用 MSVC 編譯器定位 x86 Windows。
- msvc_x86_x64:使用 64 位 MSVC 編譯器定位 x86 Windows。

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>從 CMakelists.txt 存取環境變數

從 CMakelists.txt 檔中,語法 參考所有`$ENV{variable_name}`環境變數 。 要檢視環境的可用變數,開啟此指令提示符並鍵入`SET`。 環境變數中的一些資訊也可通過 CMake 系統內省變數獲得,但您可能會發現使用環境變數更方便。 例如,MSVC 編譯器版本或 Windows SDK 版本通過環境變數輕鬆檢索。

### <a name="custom-environment-variables"></a>自訂環境變數

在`CMakeSettings.json`中,可以全域定義自定義環境變數,也可以在數位中定義`environments`每個配置。 自定義環境是一種方便的方式來分組一組屬性,可用於代替預定義的環境,或擴展或修改預定義環境。 `environments` 陣列中的每個項目都包含：

- `namespace`：命名環境，以便從表單 `namespace.variable` 中的組態參考其變數。 預設環境物件被呼叫`env`,並且填滿某些系統環境變數,包括`%USERPROFILE%`。
- `environment`：唯一識別此變數群組。 稍後在 `inheritEnvironments` 項目中允許繼承該群組。
- `groupPriority`:在計算這些變數時指定這些變數的優先順序的整數。 先評估數值較高的項目。
- `inheritEnvironments`:指定此組繼承的環境集的值陣列。 此功能可讓您繼承預設環境，以及建立自訂環境變數，以在執行時傳遞至 CMake.exe。

**Visual Studio 2019 版本 16.4 及更高版本:** 除錯目標會使用您在*CMakeSettings.json*中指定的環境自動啟動。 您可以在啟動中覆蓋或新增以每個目標或每個工作的環境變數[。](launch-vs-schema-reference-cpp.md) [tasks.vs.json](tasks-vs-json-schema-reference-cpp.md)

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
      // Since this configuration doesn't modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="macros"></a>巨集

以下巨集可用於*CMakeSettings.json*:

- `${workspaceRoot}`• 工作區資料夾的完整路徑
- `${workspaceHash}` - 工作區位置的雜湊；適用於建立目前工作區的唯一識別碼 (例如用於資料夾路徑)
- `${projectFile}` - 根 CMakeLists.txt 檔案的完整路徑
- `${projectDir}` - 根 CMakeLists.txt 檔案資料夾的完整路徑
- `${thisFile}` – `CMakeSettings.json` 檔案的完整路徑
- `${name}` - 組態的名稱
- `${generator}` - 用於此組態之 CMake 產生器的名稱

在將宏設置.exe 命令行傳遞給 cmake.exe 命令行之前,將展開對*CMakeSettings.json*中宏和環境變數的所有引用。

## <a name="ninja-command-line-arguments"></a><a name="ninja"></a> Ninja 命令列引數

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
