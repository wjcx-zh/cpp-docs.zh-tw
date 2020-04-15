---
title: CppProperties.json 參考
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328723"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json 參考

不使用 CMake 的「打開資料夾」專案可以在*CppProperties.json*檔案中儲存 IntelliSense 的專案設定設定。 (CMake 專案使用["CMakeSettings.json"](customize-cmake-settings.md)檔案。配置由名稱/值對組成,並定義#include路徑、編譯器開關和其他參數。 有關如何在打開資料夾專案中添加配置的詳細資訊,請參閱[打開資料夾專案C++。](open-folder-projects-cpp.md) 以下各節總結了各種設置。 有關架構的完整說明,請導航到*CppProperties_schema.json*,當*CppProperties.json*處於打開時,其完整路徑位於代碼編輯器的頂部。

## <a name="configuration-properties"></a>設定屬性

組態可以有下列任何屬性：

|||
|-|-|
|`inheritEnvironments`| 指定適用於此配置的環境。|
|`name`|在 C++設定下拉清單中顯示的設定名稱|
|`includePath`|在包含路徑中指定的資料夾的逗號分隔清單(對於大多數編譯器映射到 /I)|
|`defines`|應定義的巨集清單 (對應到大多數編譯器的 /D)|
|`compilerSwitches`|可能會影響 IntelliSense 行為的一或多個其他參數|
|`forcedInclude`|要自動包含在每個編譯單位中的標頭 (MSVC 會對應至 /FI，clang 會對應至 -include)|
|`undefines`|要使其成為未定義的巨集清單 (MSVC 會對應至 /U)|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 您可以為 MSVC、gcc 或 Clang 指定預先定義的體系結構特定變體之一。|
|`environments`|使用者定義的變數集,它們在命令提示符中類似於環境變數,並且使用 $_env 進行訪問。\<變數>] 宏。|

### <a name="intellisensemode-values"></a>內泰利感知模式值

開始鍵入時,程式碼編輯器顯示可用選項:

![開啟資料夾智慧感知](media/open-folder-intellisense-mode.png "開啟資料夾智慧感知")

這些是支援的值:

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
- linux-gcc 臂

注意:`msvc-x86`值`msvc-x64`和 僅出於遺留原因受支援。 改用`windows-msvc-*`變體。

## <a name="pre-defined-environments"></a>預先定義環境

Visual Studio 為 Microsoft 提供了以下預先定義環境C++這些環境映射到相應的開發人員命令提示。 繼承這些環境之一時,可以通過使用此宏語法的全域屬性`env`來引用任何環境變數:$_env。\<可變>]。

|變數名稱|描述|
|-----------|-----------------|
|vsdev|預設 Visual Studio 環境|
|msvc_x86|使用 x86 工具對 x86 進行編譯|
|msvc_x64|使用 64 位元工具對 AMD64 進行編譯|
|msvc_arm|使用 x86 工具對 ARM 進行編譯|
|msvc_arm64|使用 x86 工具對 ARM64 進行編譯|
|msvc_x86_x64|使用 x86 工具對 AMD64 進行編譯|
|msvc_arm_x64|使用 64 位元工具對 ARM 進行編譯|
|msvc_arm64_x64|使用 64 位元工具對 ARM64 進行編譯|

安裝 Linux 工作負載之後，即可使用下列環境從遠端鎖定 Linux 和 WSL：

|變數名稱|描述|
|-----------|-----------------|
|linux_x86|從遠端鎖定 x86 Linux|
|linux_x64|從遠端鎖定 x64 Linux|
|linux_arm|從遠端鎖定 ARM Linux|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>使用者定義的環境

您可以選擇使用`environments`屬性 在*CppProperties.json*中定義全域或每個配置中的變數集。 這些變數在打開資料夾專案的上下文中類似於環境變數,可以使用 $_env 進行訪問。\<變數>]語法從*任務.vs.json*和*啟動.vs.json*定義他們在這裡。 但是,在 Visual Studio 內部使用的任何命令提示中,它們不一定設置為實際環境變數。

**Visual Studio 2019 版本 16.4 及更高版本:***在 CppProperties.json*中定義的特定於設定的變數由除錯目標與工作自動選取,而無需設定`inheritEnvironments`。 除錯目標使用您在*CppProperties.json*中指定的環境自動啟動。

**Visual Studio 2019 版本 16.3 及更早版本:** 使用環境時,即使環境定義為同一配置的一部分,`inheritsEnvironments`也必須在 屬性中指定它;屬性`environment`指定環境的名稱。 下面的範例顯示了用於在 MSYS2 安裝中為 GCC 啟用 IntelliSense 的範例配置。 請注意配置如何定義和繼承`mingw_64`環境,`includePath`以及 屬性`INCLUDE`如何存取變數。

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

在配置中定義**環境**屬性時,它將覆蓋任何同名的全域變數。

## <a name="built-in-macros"></a>內建宏

您可以存*取 CppProperties.json*中的以下內建巨集:

|||
|-|-|
|`${workspaceRoot}`| 工作區資料夾的完整路徑|
|`${projectRoot}`| 放置*CppProperties.json*的資料夾的完整路徑|
|`${env.vsInstallDir}`| 安裝 Visual Studio 執行的實體的資料夾的完整路徑|

### <a name="example"></a>範例

如果專案具有包含資料夾,並且還包括 Windows SDK 中的*windows.h*和其他常見標頭,則可能需要更新*您的 CppProperties.json*設定檔,其中包括:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 未設定為全域環境變數，因此請務必從定義這些變數的「開發人員命令提示字元」啟動 devenv.exe。 (在 Windows 的 [開始] 功能表中輸入「開發人員」)。

## <a name="troubleshoot-intellisense-errors"></a>針對 IntelliSense 錯誤進行疑難排解

如果您沒有看到預期中的 IntelliSense,則可以通過存**取工具** > **選項** > **文字編輯器** > **C/C++** > **進階**和將**啟用日誌記錄**設置為**true**來進行故障排除。 首先,請嘗試將**日誌記錄級別**設置為 5,**並將篩選器**設置為 8。

![診斷記錄](media/diagnostic-logging.png)

輸出透過導管到**輸出視窗**,當您選擇 **「顯示輸出從:可視C++日誌**」時,輸出可見。 輸出包含 IntelliSense 嘗試使用的實際路徑清單。 如果路徑與*CppProperties.json*中的路徑不匹配,請嘗試關閉資料夾並刪除包含緩存流覽數據的 *.vs*子資料夾。

若要針對遺失 Include 路徑所造成的 IntelliSense 錯誤進行疑難排解，請開啟 [錯誤清單]****，並將其輸出篩選至「僅限 IntelliSense」和錯誤碼 E1696：「無法開啟原始程式檔…」。
