---
title: CppProperties.json 結構描述參考
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: 06029157b4b3826bc9c34a4434ab390f3eaa5a44
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975927"
---
# <a name="cpppropertiesjson-schema-reference"></a>CppProperties.json 結構描述參考

未使用 CMake 的開啟資料夾專案可以將 IntelliSense 的專案設定設定儲存在*CppProperties 的 json*檔案中。 (CMake 專案會使用 [CMakeSettings.json](customize-cmake-settings.md) 檔案。)組態由成對的名稱和數值組成，並定義 #include 路徑、編譯器參數及其他參數。 如需如何在開啟資料夾專案中加入設定的詳細資訊, 請參閱[開啟資料夾專案C++ ](open-folder-projects-cpp.md) 。

## <a name="configuration-properties"></a>組態屬性

組態可以有下列任何屬性：

|||
|-|-|
|`inheritEnvironments`| 指定套用到此設定的環境。|
|`name`|將出現在 [ C++設定] 下拉式清單中的設定名稱|
|`includePath`|應在 include 路徑中指定的資料夾清單 (以逗號分隔) (大多數編譯器的對應至/I)|
|`defines`|應定義的巨集清單 (對應到大多數編譯器的 /D)|
|`compilerSwitches`|可能會影響 IntelliSense 行為的一或多個其他參數|
|`forcedInclude`|要自動包含在每個編譯單位中的標頭 (MSVC 會對應至 /FI，clang 會對應至 -include)|
|`undefines`|要使其成為未定義的巨集清單 (MSVC 會對應至 /U)|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 您可以為 MSVC、gcc 或 Clang 指定其中一個預先定義的架構特定變體。|
|`environments`|使用者定義的變數集, 其行為類似于命令提示字元中的環境變數, 並使用 $ {env.<VARIABLE>} 來存取 向宏.|

### <a name="intellisensemode-values"></a>intelliSenseMode 值

當您開始輸入時, 程式碼編輯器會顯示可用的選項:

![開啟資料夾 IntelliSense](media/open-folder-intellisense-mode.png "開啟資料夾 IntelliSense")

以下是支援的值:

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
- linux-gcc-arm

注意:`msvc-x86` 和 `msvc-x64` 值僅適用於舊版。 請改用`windows-msvc-*` variant。

## <a name="pre-defined-environments"></a>預先定義的環境

Visual Studio 為 Microsoft C++提供下列預先定義的環境, 其對應至相對應的開發人員命令提示字元。 當您繼承其中一個環境時, 您可以使用全域屬性`env`搭配此宏語法來參考任何環境變數: $ {env。\<變數 >}。

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

|變數名稱|說明|
|-----------|-----------------|
|linux_x86|從遠端鎖定 x86 Linux|
|linux_x64|從遠端鎖定 x64 Linux|
|linux_arm|從遠端鎖定 ARM Linux|

## <a name="user_defined_environments"></a>使用者定義環境

您可以選擇性地使用`environments`屬性, 在*CppProperties*中定義全域或每個設定的變數集。 這些變數的行為就像是開啟資料夾專案內容中的環境變數, 而且可以使用 $ {env 來存取\< 。來自工作的變數 >} 語法, 在這裡定義之後, 與*json*和*啟動. 與 json*的比較。 不過, 它們不一定會在任何 Visual Studio 在內部使用的命令提示字元中, 設定為實際的環境變數。

當您使用環境時, 您必須在`inheritsEnvironments`屬性中指定它, 即使環境已定義為相同設定的一部分`environment` ; 屬性也會指定環境的名稱。 下列範例顯示在 MSYS2 安裝中啟用適用于 GCC 的 IntelliSense 的範例設定。 請注意, 設定會定義和繼承`mingw_64`環境, 以及`includePath`屬性如何存取`INCLUDE`變數。

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

當您在設定內定義**環境**屬性時, 它會覆寫相同名稱的任何全域變數。

## <a name="built-in-macros"></a>內建宏

您可以在*CppProperties*中存取下列內建宏:

|||
|-|-|
|`${workspaceRoot}`| 工作區資料夾的完整路徑|
|`${projectRoot}`| 放置*CppProperties*之資料夾的完整路徑|
|`${env.vsInstallDir}`| 已安裝 Visual Studio 實例之資料夾的完整路徑|

### <a name="example"></a>範例

如果您的專案具有 include 資料夾, 而且也包含來自 Windows SDK 的*windows .h*和其他常見標頭, 您可能會想要使用下列專案來更新*CppProperties*的設定檔:

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

如果您看不到預期的 IntelliSense, 可以移至 [**工具** > ] [**選項** > ] [**文字編輯器** > ] [ >  **C/C++** **Advanced** ], 以進行疑難排解將 [**啟用記錄**] 設定為 [ **true**]。 若要開始, 請嘗試將**記錄層級**設定為 5, 並將**篩選準則記錄**到8。

![診斷記錄](media/diagnostic-logging.png)

輸出會輸送至**輸出視窗**, 並在您選擇 [ **顯示輸出來源] 時顯示:視覺C++效果**記錄。 輸出中包含 IntelliSense 嘗試使用之實際 include 路徑的清單。 如果路徑不符合*CppProperties*中的路徑, 請嘗試關閉資料夾, 並刪除包含快取流覽資料的 *. vs*子資料夾。

若要針對遺失 Include 路徑所造成的 IntelliSense 錯誤進行疑難排解，請開啟 [錯誤清單]，並將其輸出篩選至「僅限 IntelliSense」和錯誤碼 E1696：「無法開啟原始程式檔…」。
