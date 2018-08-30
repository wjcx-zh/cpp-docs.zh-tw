---
title: Visual C++ 中的開啟資料夾專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4444e70ec158d7afa35c3955bbef9af4bfa12f2
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131319"
---
# <a name="open-folder-projects-in-visual-c"></a>Visual C++ 中的開啟資料夾專案

在 Visual Studio 2017 及之後的版本中，能利用「開啟資料夾」功能，開啟原始程式檔的資料夾，並立即開始撰寫程式碼，同時還支援 IntelliSense、瀏覽、重構、偵錯等等。 不會載入 .sln 或 .vcxproj 檔案；如有需要，您可以指定自訂工作，以及透過簡單的.JSON 檔案建置並啟動參數。 有了「開啟資料夾」，Visual C++ 現在不僅可以支援鬆散的檔案集合，也幾乎支援任何建置系統，包括 CMake、Ninja、QMake (適用於 Qt 專案)、gyp、SCons、Gradle、Buck、make 等。 

若要使用「開啟資料夾」，請從主功能表選取 [檔案] | [開啟] | [資料夾]，或按 *Ctrl + Shift + Alt + O*。[方案總管] 會立即顯示資料夾中的所有檔案。 您可以按一下任何檔案以開始編輯它。 Visual Studio 會在背景開始編制檔案的索引，以啟用 IntelliSense、瀏覽及重構功能。 當您編輯、建立、移動或刪除檔案時，Visual Studio 會自動追蹤變更並持續更新其 IntelliSense 索引。 
  
## <a name="cmake-projects"></a>CMake 專案
CMake 已整合到 Visual Studio IDE 作為 Visual C++ CMake 工具，這是 C++ 桌面工作負載的一個元件。 如需詳細資訊，請參閱 [Visual C++ 的 CMake 工具](cmake-tools-for-visual-cpp.md)。
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>以 Qt 架構為目標的 QMake 專案
您可以使用 Visual C++ 的 CMake 工具，設定要建置 Qt 專案的目標 Qt，也可以為 Visual Studio 2015 或 Visual Studio 2017 使用 [Qt Visual Studio 延伸模組](https://download.qt.io/development_releases/vsaddin/)。

## <a name="gyp-cons-scons-buck-etc"></a>gyp、Cons、SCons、Buck 等
您可以在 Visual C++ 中使用任何建置系統，並仍享有 Visual C++ IDE 和偵錯工具的優點。 當您開啟專案的根資料夾時，Visual C++ 會使用啟發學習法來編製原始程式檔的索引供 IntelliSense 和瀏覽之用。 您可以藉由編輯 CppProperties.json 檔案，提供您程式碼結構的相關提示。 同樣地，您也可以藉由編輯 launch.vs.json 檔案，設定您的建置程式。 

## <a name="configuring-open-folder-projects"></a>設定「開啟資料夾」專案
您可以透過三個 JSON 檔案自訂「開啟資料夾」專案：
|||
|-|-|
|CppProperties.json|指定自訂組態資訊以供瀏覽。 如有需要，請在您的根專案資料夾中建立此檔案。|
|launch.vs.json|指定命令列引數。 存取方式為透過 [方案總管] 的操作功能表項目 [偵錯並啟動設定]。|
|tasks.vs.json|指定自訂建置命令和編譯器參數。 存取方式為透過 [方案總管] 的操作功能表項目 [設定工作]。|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>使用 CppProperties.json 設定 IntelliSense
IntelliSense 和瀏覽行為部分取決於使用中組建組態，這會定義 #include 路徑、編譯器參數和其他參數。 根據預設，Visual Studio 會提供偵錯和發行組態。 針對某些專案，您可能需要建立自訂組態，讓 IntelliSense 和瀏覽功能可以完全理解您的程式碼。 若要定義新的組態，請在根資料夾中建立稱為 CppProperties.json 的檔案。 請看以下範例：

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
組態可以有下列任何屬性：

|||  
|-|-| 
|`name`|出現在 C++ 組態下拉式清單中的組態名稱|
|`includePath`|應該在 Include 路徑中指定的資料夾清單 (大多數編譯器會對應至 /I)|
|`defines`|應該定義的巨集清單 (大多數編譯器會對應至 /D)|
|`compilerSwitches`|可能會影響 IntelliSense 行為的一或多個其他參數|
|`forcedInclude`|要自動包含在每個編譯單位中的標頭 (MSVC 會對應至 /FI，clang 會對應至 -include)|
|`undefines`|要取消定義的巨集清單 (MSVC 會對應至 /U)|
|`intelliSenseMode`|要使用的 IntelliSense 引擎。 您可以指定適用於 MSVC、gcc 或 Clang 的架構特定變化：
- msvc-x86 (預設值)
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux-arm
- gccarm

#### <a name="environment-variables"></a>環境變數
CppProperties.json 支援 Include 路徑和其他屬性值的系統環境變數擴充。 語法是 `${env.FOODIR}`，可擴充環境變數 `%FOODIR%`。 此外，也支援下列系統定義的變數：

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

在 CppProperties.json 中，您可以全域或根據組態定義自訂環境變數。 下列範例示範如何宣告及使用預設和自訂環境變數。 全域 **environments** 屬性會宣告名為 **INCLUDE** 的變數，可供任何組態使用：

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
您也可以在組態中定義 **environments** 屬性，讓它只會套用至該組態，並覆寫相同名稱的任何全域變數。 在下列範例中，x64 組態會定義區域 **INCLUDE** 變數來覆寫全域值：

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\\src\\includes"
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
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\\src\\includes64"
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

所有自訂和預設環境變數也會位於 tasks.vs.json 和 launch.vs.json 中。

#### <a name="macros"></a>巨集
您可以存取 CppProperties.json 的下列內建巨集：
|||
|-|-|
|`${workspaceRoot}`| 工作區資料夾的完整路徑|
|`${projectRoot}`| CppProperties.json 所在資料夾的完整路徑|
|`${vsInstallDir}`| 執行中 VS 2017 執行個體安裝所在資料夾的完整路徑|

例如，如果您的專案具有 Include 資料夾，也包含 windows.h 及 Windows SDK 中的其他常見標頭，您可能需要使用下列 Include 檔更新您的 CppProperties.json 組態檔：

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\ucrt",
        "${env.NETFXSDKDir}\\include\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\um",
        "${env.WindowsSdkDir}include\\${env.WindowsSDKVersion}\\shared",
        "${env.VCToolsInstallDir}include"
      ]
    }
  ]
}
```

**注意：**`%WindowsSdkDir%` 和 `%VCToolsInstallDir%` 未設定為全域環境變數，因此請務必從定義這些變數的「VS 2017 開發人員命令提示字元」啟動 devenv.exe。

若要針對遺失 Include 路徑所造成的 IntelliSense 錯誤進行疑難排解，請開啟 [錯誤清單]，並將其輸出篩選至「僅限 IntelliSense」和錯誤碼 E1696：「無法開啟原始程式檔…」。 

您可以在 CppProperties.json 中建立任意數目的組態。 每個組態都會出現在組態下拉式清單中：

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
### <a name="define-tasks-with-tasksvsjson"></a>以 tasks.vs.json 定義工作
您可以針對您目前在工作區中所擁有的檔案自動化建置指令碼或任何其他外部作業，方法是直接在 IDE 中以工作的形式執行它們。 您能以滑鼠右鍵按一下檔案或資料夾，並選取 [設定工作] 來設定新工作。 

![開啟資料夾設定工作](media/open-folder-config-tasks.png)

這會在 Visual Studio 於您的根專案資料夾建立的 .vs 資料夾中，建立 (或開啟) `tasks.vs.json` 檔案。 您可以在此檔案中定義任意工作，然後從 [方案總管] 操作功能表叫用它。 下列範例會顯示定義單一工作的 tasks.vs.json 檔案。 `taskName` 定義出現在操作功能表中的名稱。 `appliesTo` 定義可執行該命令的檔案。 `command` 屬性參考 COMSPEC 環境變數，以識別主控台的路徑 (在 Windows 上為 cmd.exe)。 您也可以參考 CppProperties.json 或 CMakeSettings.json 中宣告的環境變數。 `args` 屬性指定要叫用的命令列。 `${file}` 巨集會在 [方案總管] 中擷取選取的檔案。 下列範例會顯示目前所選 .cpp 檔案的檔名。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```
您可以在儲存 tasks.vs.json 之後，以滑鼠右鍵按一下資料夾中的任何 .cpp 檔案，從操作功能表選擇 [Echo filename]，然後查看 [輸出] 視窗中顯示的檔案名稱。



#### <a name="appliesto"></a>appliesTo
您可以在 `appliesTo` 欄位中指定任何檔案或資料夾的名稱來針對它們建立工作，例如 `"appliesTo" : "hello.cpp"`。 下列檔案遮罩可作為值使用：
|||
|-|-|
|`"*"`| 工作可供工作區中的所有檔案及資料夾使用|
|`"*/"`| 工作可供工作區中的所有資料夾使用|
|`"*.cpp"`| 工作可供工作區中所有具有 .cpp 副檔名的檔案使用|
|`"/*.cpp"`| 工作可供工作區根目錄中所有具有 .cpp 副檔名的檔案使用|
|`"src/*/"`| 工作可供 "src" 資料夾的所有子資料夾使用|
|`"makefile"`| 工作可供工作區中的所有 Makefile 檔案使用|
|`"/makefile"`| 工作僅可供工作區根目錄中的 Makefile 使用|

#### <a name="output"></a>output
使用 `output` 屬性，指定當您按下 **F5** 鍵時會啟動的可執行檔。 例如: 

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>適用於 tasks.vs.json 的巨集

|||
|-|-|
|`${env.<VARIABLE>}`| 指定針對開發人員命令提示字元所設定的任何環境變數 (例如 ${env.PATH}、${env.COMSPEC} 等)。 如需詳細資訊，請參閱[適用於 Visual Studio 的開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)。|
|`${workspaceRoot}`| 工作區資料夾的完整路徑 (例如 "C:\sources\hello")|
|`${file}`| 選取用於執行此工作之檔案或資料夾的完整路徑 (例如 "C:\sources\hello\src\hello.cpp")|
|`${relativeFile}`| 檔案或資料夾的相對路徑 (例如 "src\hello.cpp")|
|`${fileBasename}`| 沒有路徑或副檔名的檔案名稱 (例如 "hello")|
|`${fileDirname}`| 不包括檔名的檔案完整路徑 (例如 "C:\sources\hello\src")|
|`${fileExtname}`| 所選取檔案的副檔名 (例如 ".cpp")|

#### <a name="custom-macros"></a>自訂巨集
若要在 tasks.vs.json 中定義自訂巨集，請在工作區塊前面新增名稱:值對。 下列範例會定義名為 `outDir` 並在 `args` 屬性中取用的巨集：

```json
{
"version": "0.2.1",
  "outDir": "${workspaceRoot}\\bin",
  "tasks": [
    {
      "taskName": "List outputs",
      "*",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": [
        "dir ${outDir}"
      ]
    }
  ]
```

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 設定偵錯參數
若要自訂您程式的命令列引數，請在 [方案總管] 中以滑鼠右鍵按一下該可執行檔，然後選取 [偵錯並啟動設定]。 這會開啟現有的 `launch.vs.json` 檔案；如果不存在任何檔案，則會建立新的檔案，並預先填入您已選取之程式的相關資訊。 

若要指定其他引數，只要在 `args` JSON 陣列中新增這些引數即可，如下列範例所示：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

當您儲存此檔案時，新的組態會出現在 [偵錯目標] 下拉式清單中，且您可以選取它以啟動偵錯工具。 您可以視需要為任何數目的可執行檔建立許多偵錯組態。 如果您現在按下 **F5** 鍵，偵錯工具會啟動並叫用任何您可能已設定的中斷點。 現在可以使用所有熟悉的偵錯工具視窗及其功能。

## <a name="see-also"></a>請參閱
[開發 Visual C++ 的 IDE 和工具](ide-and-tools-for-visual-cpp-development.md)

