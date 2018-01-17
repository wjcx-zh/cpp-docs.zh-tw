---
title: "在 Visual c + + 中開啟資料夾專案 |Microsoft 文件"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 721dd39cf8cda6277eb129f259b7ede2d9f0da28
ms.sourcegitcommit: ef2a263e193410782c6dfe47d00764263439537c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="open-folder-projects-in-visual-c"></a>在 Visual c + + 中開啟專案資料夾
Visual Studio 2017 導入了 「 開啟資料夾 」 功能，可讓您開啟來源檔案的資料夾並立即開始撰寫程式碼以支援 IntelliSense、 瀏覽、 重構、 偵錯等等。 會不載入任何.sln 或.vcxproj 檔案;如有需要您可以指定自訂工作，以及建置並啟動參數，透過簡單的.json 檔案。 由開啟的資料夾，Visual c + + 現在可以支援不僅鬆散集合的檔案，而且也幾乎任何建置系統，包括 CMake、 忍者一樣，QMake （適用於 Qt 專案），又試過 gyp、 SCons、 Gradle、 Buck、 請等等。 

若要使用開啟的資料夾，請從主功能表選取*檔案 |開啟 |資料夾*或按*Ctrl + Shift + Alt + O*。方案總管 中立即顯示所有檔案的資料夾中。 您可以按一下任何檔案來開始編輯。 在背景中，Visual Studio 會啟動編製索引的檔案啟用 IntelliSense、 導覽和重構的功能。 當您編輯、 建立、 移動或刪除檔案時，Visual Studio 會自動追蹤變更，並持續更新其 IntelliSense 的索引。 
  
## <a name="cmake-projects"></a>CMake 專案
CMake 已 Visual c + +、 c + + 桌面工作負載的元件，Visual Studio IDE 中整合 CMake 的工具。 如需詳細資訊，請參閱 [Visual C++ 的 CMake 工具](cmake-tools-for-visual-cpp.md)。
 
## <a name="qmake-projects-that-target-the-qt-framework"></a>QMake Qt framework 為目標的專案
您可以使用 CMake 工具 Visual c + + 為目標 Qt 建置 Qt 專案，或您可以使用 Qt Visual Studio 擴充功能。 附註： 自年 8 月 2017年[Qt Visual Studio 擴充功能支援 Visual Studio 2017](https://download.qt.io/development_releases/vsaddin/)可做為測試版。

## <a name="gyp-cons-scons-buck-etc"></a>又試過 gyp，Cons、 SCons、 Buck 等等
您可以在 Visual c + + 中使用任何建置系統，且仍有 Visual c + + 的 IDE 和偵錯工具的優點。 當您開啟專案的根資料夾時，Visual c + + 會使用啟發式來索引為 IntelliSense 和瀏覽的來源檔案。 您可以藉由編輯 CppProperties.json 檔案提供有關您的程式碼結構的提示。 類似的方式，您可以藉由編輯 launch.vs.json 檔案設定建置程式。 

## <a name="configuring-open-folder-projects"></a>設定專案開啟資料夾
您可以透過三個 JSON 檔案中自訂開啟資料夾專案：
|||
|-|-|
|CppProperties.json|指定瀏覽的自訂組態的資訊。 如有需要根專案資料夾中建立此檔案中。|
|launch.vs.json|指定命令列引數。 透過存取**方案總管 中**操作功能表項目**偵錯和啟動設定**。|
|tasks.vs.json|指定自訂建置命令和編譯器參數。 透過存取**方案總管 中**操作功能表項目**設定工作**。|

### <a name="configure-intellisense-with-cpppropertiesjson"></a>設定 IntelliSense 與 CppProperties.json
IntelliSense 和瀏覽的行為部分取決於作用中的組建組態，它會定義 #include 路徑、 編譯器參數和其他參數。 根據預設，Visual Studio 會提供偵錯和發行組態。 針對某些專案，您可能需要讓 IntelliSense 和瀏覽功能，可完全了解您的程式碼建立自訂組態。 若要定義新的組態，建立稱為 CppProperties.json 根資料夾中的檔案。 請看以下範例：

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
組態可能會有任何下列屬性：

|||  
|-|-| 
|`name`|c + + 的組態下拉式清單中顯示的組態名稱|
|`includePath`|應指定 include 路徑 （對應至 /I 大多數的編譯器） 中的資料夾清單|
|`defines`|定義 （適用於大多數的編譯器有對應到 /D） 的巨集，應該是清單。|
|`compilerSwitches`|一或多個會影響 IntelliSense 行為的其他參數|
|`forcedInclude`|會自動加到每個編譯單位中的標頭 （對應到 /FI MSVC 或-包括 clang）|
|`undefines`|是未定義 （對應至如 MSVC /U） 巨集清單|
|`intelliSenseMode`|使用 IntelliSense 引擎。 您可以指定架構特定變體 MSVC、 gcc 或 Clang:
- msvc x86 （預設值）
- msvc-x64
- msvc-arm
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- Linux-x64
- Linux-x86
- Linux arm
- gccarm

#### <a name="environment-variables"></a>環境變數
CppProperties.json 支援系統環境變數擴充為包含路徑和其他屬性值。 語法是`${env.FOODIR}`展開環境變數`%FOODIR%`。 也支援下列系統定義的變數：

|變數名稱|描述|  
|-----------|-----------------|
|vsdev|預設的 Visual Studio 環境|
|msvc_x86|適用於 x86 使用 x86 編譯工具|
|msvc_arm|使用 x86 arm 編譯工具|
|msvc_arm64|使用 x86 ARM64 針對編譯工具|
|msvc_x86_x64|使用 x86 AMD64 針對編譯工具|
|msvc_x64_x64|使用 64 位元工具針對 AMD64 編譯|
|msvc_arm_x64|為 ARM 使用 64 位元工具進行編譯|
|msvc_arm64_x64|使用 64 位元工具針對 ARM64 編譯|

安裝 Linux 工作負載時，就有一個下列環境可供從遠端目標 Linux 和 WSL:

|變數名稱|描述|  
|-----------|-----------------|
|linux_x86|目標 x86 Linux 遠端|
|linux_x64|目標 x64 Linux 遠端|
|linux_arm|從遠端目標 ARM Linux|

您可以定義自訂的環境變數中 CppProperties.json 是全域或每個組態。 下列範例會示範如何預設和自訂的環境變數可宣告及使用。 全域**環境**屬性會宣告名為的變數**INCLUDE** ，可以由任何設定：

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
您也可以定義**環境**屬性設定，讓它只適用於該組態，並覆寫相同名稱的任何全域變數內。 在下列範例中，x64 組態會定義本機**INCLUDE**會覆寫全域值的變數：

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

所有自訂和預設環境變數也可以在 tasks.vs.json 和 launch.vs.json。

#### <a name="macros"></a>巨集
您可以存取內 CppProperties.json 下列內建的巨集：
|||
|-|-|
|`${workspaceRoot}`| 工作區資料夾的完整路徑|
|`${projectRoot}`| CppProperties.json 所在資料夾的完整路徑|
|`${vsInstallDir}`| VS 2017 執行個體安裝所在的資料夾完整路徑|

例如，如果您的專案已加入資料夾，而且也包含 windows.h 和 Windows SDK 中的其他常見標頭，您可能想要更新這些組態檔包含您 CppProperties.json:

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

**注意：** `%WindowsSdkDir%`和`%VCToolsInstallDir%`未設定全域環境變數，請確定啟動 devenv.exe 的 「 開發人員命令提示字元之下 VS 2017 」 定義這些變數。

若要疑難排解 IntelliSense 遺失所造成的錯誤 include 路徑，開啟**錯誤清單**並篩選輸出，以 「 僅 IntelliSense 」，以及錯誤碼 E1696 「 無法開啟原始程式檔 … 」。 

您可以在 CppProperties.json 建立任意數目的設定。 每個會出現在下拉式清單中：

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
### <a name="define-tasks-with-tasksvsjson"></a>定義與 tasks.vs.json 工作
您可以自動化建置指令碼或其他外部操作您的目前工作區中執行它們做為直接在 IDE 中的工作檔案。 您可以設定新的工作檔案或資料夾上按一下滑鼠右鍵，然後選取**設定工作**。 

![開啟資料夾設定工作](media/open-folder-config-tasks.png)

這會建立 （或開啟） `tasks.vs.json` .vs 資料夾會在根專案資料夾中建立 Visual Studio 中的檔案。 您可以定義此檔案中的任何任意的工作，然後再叫用它從**方案總管 中**操作功能表。 下列範例會示範 tasks.vs.json 檔案，以定義單一工作。 `taskName`在內容功能表中會定義顯示的名稱。 `appliesTo`定義哪些檔案可執行命令。 `command`屬性參考到 COMSPEC 環境變數，可用來識別主控台 (在 Windows 上的 cmd.exe) 的路徑。 您也可以參考環境變數中 CppProperties.json 或 CMakeSettings.json 宣告。 `args`屬性會指定要叫用的命令列。 `${file}`巨集擷取選取的檔案中**方案總管 中**。 下列範例會顯示目前選取的.cpp 檔案的檔案名稱。

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
您可以在儲存之後 tasks.vs.json，以滑鼠右鍵按一下資料夾中的任何.cpp 檔案、 選擇**回應檔名**從內容功能表中，並請參閱 [輸出] 視窗中顯示的檔案名稱。



#### <a name="appliesto"></a>appliesTo
您可以建立的任何檔案或資料夾的工作，藉由指定其名稱中的`appliesTo`欄位，例如`"appliesTo" : "hello.cpp"`。 當做值，就可以使用下列的檔案遮罩：
|||
|-|-|
|`"*"`| 工作可以使用所有檔案和工作區中的資料夾|
|`"*/"`| 工作可以使用工作區中的所有資料夾|
|`"*.cpp"`| 工作可以使用與副檔名.cpp 工作區中的所有檔案|
|`"/*.cpp"`| 工作可以使用與副檔名.cpp 工作區的根目錄中的所有檔案|
|`"src/*/"`| 工作可以使用 「 來源 」 資料夾的所有子資料夾|
|`"makefile"`| 工作可以使用工作區中的所有 makefile 檔案|
|`"/makefile"`| 工作是僅適用於在工作區的根目錄 makefile|

#### <a name="output"></a>output
使用`output`屬性來指定當您按下將會啟動可執行檔**F5**。 例如: 

```json
      "output": "${workspaceRoot}\\bin\\hellomake.exe" 
```

#### <a name="macros-for-tasksvsjson"></a>Tasks.vs.json 巨集

|||
|-|-|
|`${env.<VARIABLE>}`| 指定任何環境變數 （例如，${env。PATH} ${env.COMSPEC} 等等)，設定為開發人員命令提示字元。 如需詳細資訊，請參閱[Visual Studio 的開發人員命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)。|
|`${workspaceRoot}`| 工作區資料夾 (例如，"C:\sources\hello") 的完整路徑|
|`${file}`| 檔案或資料夾，選取要執行這項工作 (例如，"C:\sources\hello\src\hello.cpp 」) 針對完整的路徑|
|`${relativeFile}`| 相對路徑的檔案或資料夾 (例如，"src\hello.cpp")|
|`${fileBasename}`| 不含路徑或副檔名 (例如，"hello") 檔案的名稱|
|`${fileDirname}`| 完整檔案路徑，但不包括檔名 (例如，"C:\sources\hello\src")|
|`${fileExtname}`| 選取的檔案 (例如，".cpp") 的延伸模組|

#### <a name="custom-macros"></a>自訂巨集
若要定義自訂的巨集 tasks.vs.json 中，新增的名稱： 值配對工作區塊之前。 下列範例會定義名為巨集`outDir`的消耗了多少`args`屬性：

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
若要自訂您的程式命令列引數，以滑鼠右鍵按一下中的可執行檔**方案總管 中**選取**偵錯和啟動設定**。 這會開啟一個現有`launch.vs.json`檔案，或如果沒有，就會建立新的檔案，預先填入您所選取的計畫的相關資訊。 

若要指定其他引數，只將其加入`args`JSON 陣列，如下列範例所示：

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

當您儲存此檔案時，新的組態會顯示在偵錯目標下拉式清單中，您可以選取它，以便開始偵錯工具。 您可以建立許多偵錯組態，各代表任何數目的可執行檔。 如果您按下**F5**現在，偵錯工具會啟動，來叫用已設定任何中斷點。 熟悉的偵錯工具的所有視窗和其功能現在會是可用項目。

## <a name="see-also"></a>請參閱
[開發 Visual C++ 的 IDE 和工具](ide-and-tools-for-visual-cpp-development.md)

