---
title: CppProperties.json 結構描述參考
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.openlocfilehash: fd655de3313dd95eb3fcefaeba21e703d32e860a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824895"
---
# <a name="cpppropertiesjson-schema-reference"></a>CppProperties.json 結構描述參考

開啟資料夾 」 專案，請勿使用 CMake 可以儲存在專案組態設定`CppProperties.json`檔案。 (CMake 專案使用[CMakeSettings.json](customize-cmake-settings.md)檔案。)Visual Studio IDE 使用`CppProperties.json`進行 IntelliSense 和程式碼瀏覽。 設定名稱/值組所組成，並定義 #include 路徑、 編譯器參數，與其他參數。 


## <a name="default-configurations"></a>預設組態

Visual Studio 會提供預先定義的組態的 x86 和 x64 偵錯和發行。 根據預設，您的專案會有 x86 偵錯組態`CppProperties.json`。 若要加入新的組態，以滑鼠右鍵按一下`CppProperties.json`檔案中**方案總管 中**，然後選擇**加入組態**:

![開啟資料夾加入組態](media/open-folder-add-config.png "開啟資料夾新增新的組態")

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
有一組允許的值的屬性，程式碼編輯器會顯示可用的選項，當您開始輸入：

![開啟資料夾 IntelliSense](media/open-folder-intellisense-mode.png "開啟資料夾的 IntelliSense")



## <a name="configuration-properties"></a>組態屬性

組態可以有下列任何屬性：

|||
|-|-|
|`name`|會出現在 c + + 組態下拉式清單中的組態名稱|
|`includePath`|應指定 include 路徑 （適用於大多數的編譯器有對應至 /I） 中的資料夾清單|
|`defines`|應該定義 （對應至 /D 適用於大多數的編譯器） 的巨集清單|
|`compilerSwitches`|一或多個可能影響 IntelliSense 行為的其他參數|
|`forcedInclude`|若要自動包含在每個編譯單位的標頭 （對應到 /FI MSVC 或-包含 clang）|
|`undefines`|為未定義 （對應至 /U 代表 MSVC） 的巨集清單|
|`intelliSenseMode`|若要使用 IntelliSense 引擎。 您可以指定適用於 MSVC、gcc 或 Clang 的架構特定變化：<br/><br/>- msvc-x86 (預設值)<br/>- msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>- windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>- Linux-arm<br/>- gccarm|

## <a name="custom-configurations"></a>自訂設定


您可以自訂任何在預設 configuations `CppProperties.json`，或建立新的組態。 每個組態都會出現在組態下拉式清單中：

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

 `CppProperties.json` 支援系統環境變數擴充的包含路徑和其他屬性值。 語法是 `${env.FOODIR}`，可擴充環境變數 `%FOODIR%`。 此外，也支援下列系統定義的變數：

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

您可以定義自訂的環境變數中`CppProperties.json`是全域或每個組態。 下列範例示範如何宣告及使用預設和自訂環境變數。 全域 **environments** 屬性會宣告名為 **INCLUDE** 的變數，可供任何組態使用：

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
      "intelliSenseMode": "msvc-x86"
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
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>每個組態的環境變數

您也可以在組態中定義 **environments** 屬性，讓它只會套用至該組態，並覆寫相同名稱的任何全域變數。 在下列範例中，x64 組態會定義區域 **INCLUDE** 變數來覆寫全域值：

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
      "intelliSenseMode": "msvc-x86"
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
      "intelliSenseMode": "msvc-x64"
    }
  ]
}
```

所有自訂和預設的環境變數中也會有`tasks.vs.json`和`launch.vs.json`。

#### <a name="build-in-macros"></a>內建巨集

您可以存取下列的內建巨集內`CppProperties.json`:

|||
|-|-|
|`${workspaceRoot}`| 工作區資料夾的完整路徑|
|`${projectRoot}`| 資料夾的完整路徑位置`CppProperties.json`放置|
|`${vsInstallDir}`| 執行中 VS 2017 執行個體安裝所在資料夾的完整路徑|

例如，如果您的專案已加入資料夾，而且也包含 windows.h 和其他常見的標頭，從 Windows SDK，您可能想要更新您`CppProperties.json`這些組態檔包含：

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
> `%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 未設定為全域環境變數，因此請務必從定義這些變數的「VS 2017 開發人員命令提示字元」啟動 devenv.exe。

## <a name="troubleshoot-intellisense-errors"></a>針對 IntelliSense 錯誤進行疑難排解

若要針對遺失 Include 路徑所造成的 IntelliSense 錯誤進行疑難排解，請開啟 [錯誤清單]，並將其輸出篩選至「僅限 IntelliSense」和錯誤碼 E1696：「無法開啟原始程式檔…」。



