---
title: CppProperties.json 結構描述參考
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual Studio
ms.openlocfilehash: 8432b72deaef99ee20147505030cbc8a9a270869
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344409"
---
# <a name="cpppropertiesjson-schema-reference"></a>CppProperties.json 結構描述參考

開啟不使用 CMake 的資料夾專案可將專案組態設定儲存在 `CppProperties.json` 檔案中。 (CMake 專案會使用 [CMakeSettings.json](customize-cmake-settings.md) 檔案。)Visual Studio IDE 會針對 IntelliSense 及程式碼導覽使用 `CppProperties.json`。 組態由成對的名稱和數值組成，並定義 #include 路徑、編譯器參數及其他參數。 


## <a name="default-configurations"></a>預設組態

Visual Studio 提供 x86 及 x64 偵錯及版本的預先定義組態。 根據預設，您的專案會在 `CppProperties.json` 中擁有 x86-Debug 組態。 若要加入新的組態，以滑鼠右鍵按一下`CppProperties.json`檔案中**方案總管**，然後選擇**加入組態**:

![開啟資料夾-加入新的組態](media/open-folder-add-config.png "開啟資料夾新增新的組態")

預設組態如下所示：

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
針對擁有一組可允許值的屬性，程式碼編輯器會在您開始鍵入時顯示可用選項：

![開啟資料夾 IntelliSense](media/open-folder-intellisense-mode.png "開啟資料夾 IntelliSense")



## <a name="configuration-properties"></a>組態屬性

組態可以有下列任何屬性：

|||
|-|-|
|`name`|出現在 C++ 組態下拉式清單中的組態名稱|
|`includePath`|應在 Include 路徑中指定的資料夾清單 (對應到大多數編譯器的 /I)|
|`defines`|應定義的巨集清單 (對應到大多數編譯器的 /D)|
|`compilerSwitches`|可能會影響 IntelliSense 行為的一或多個其他參數|
|`forcedInclude`|要自動包含在每個編譯單位中的標頭 (MSVC 會對應至 /FI，clang 會對應至 -include)|
|`undefines`|要使其成為未定義的巨集清單 (MSVC 會對應至 /U)|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 您可以指定特定架構的變體 MSVC、 gcc，或 Clang:<br/><br/>- windows-msvc-x86 (default)<br/>- windows-msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

注意:`msvc-x86` 和 `msvc-x64` 值僅適用於舊版。 使用`windows-msvc-*`變體改。

## <a name="custom-configurations"></a>自訂組態


您可以在 `CppProperties.json` 中自訂任何預設組態，或是建立新的組態。 每個組態都會出現在組態下拉式清單中：

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```

## <a name="system-environment-variables"></a>系統環境變數 

 `CppProperties.json` 支援系統環境變數擴充，包含路徑及其他屬性值。 語法是 `${env.FOODIR}`，可擴充環境變數 `%FOODIR%`。 此外，也支援下列系統定義的變數：

|變數名稱|描述|
|-----------|-----------------|
|vsdev|預設 Visual Studio 環境|
|msvc_x86|使用 x86 工具對 x86 進行編譯|
|msvc_arm|使用 x86 工具對 ARM 進行編譯|
|msvc_arm64|使用 x86 工具對 ARM64 進行編譯|
|msvc_x86_x64|使用 x86 工具對 AMD64 進行編譯|
|msvc_x64_x64|使用 64 位元工具對 AMD64 進行編譯|
|msvc_arm_x64|使用 64 位元工具對 ARM 進行編譯|
|msvc_arm64_x64|使用 64 位元工具對 ARM64 進行編譯|

安裝 Linux 工作負載之後，即可使用下列環境從遠端鎖定 Linux 和 WSL：

|變數名稱|描述|
|-----------|-----------------|
|linux_x86|從遠端鎖定 x86 Linux|
|linux_x64|從遠端鎖定 x64 Linux|
|linux_arm|從遠端鎖定 ARM Linux|

## <a name="custom-environment-variables"></a>自訂環境變數

您可以在 `CppProperties.json` 中，全域或根據組態定義自訂環境變數。 下列範例示範如何宣告及使用預設和自訂環境變數。 全域 **environments** 屬性會宣告名為 **INCLUDE** 的變數，可供任何組態使用：

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>每個組態的環境變數

您也可以定義**環境**在組態內的屬性。 它只適用於該組態，並會覆寫相同名稱的任何全域變數。 在下列範例中，x64 組態會定義區域 **INCLUDE** 變數來覆寫全域值：

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\src\includes64"
        }
      ],

      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

所有自訂和預設環境變數也都能在 `tasks.vs.json` 和 `launch.vs.json` 中取得。

#### <a name="build-in-macros"></a>內建巨集

您可以存取下列位於 `CppProperties.json` 內部的內建巨集：

|||
|-|-|
|`${workspaceRoot}`| 工作區資料夾的完整路徑|
|`${projectRoot}`| 指向放置 `CppProperties.json` 資料夾的完整路徑|
|`${vsInstallDir}`| 執行中的 Visual Studio 執行個體安裝所在資料夾的完整路徑|

例如，如果您的專案已加入資料夾，而且也包含 windows.h 和其他常見的標頭，從 Windows SDK，您可能想要更新您`CppProperties.json`以下列的組態檔包含：

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

若要針對遺失 Include 路徑所造成的 IntelliSense 錯誤進行疑難排解，請開啟 [錯誤清單]  ，並將其輸出篩選至「僅限 IntelliSense」和錯誤碼 E1696：「無法開啟原始程式檔…」。
