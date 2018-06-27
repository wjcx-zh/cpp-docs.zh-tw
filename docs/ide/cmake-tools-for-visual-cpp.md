---
title: Visual C++ 中的 CMake 專案 | Microsoft Docs
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38bcd102e94ac98aba56a4eb98b69df6d3f16111
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238561"
---
# <a name="cmake-projects-in-visual-c"></a>Visual C++ 中的 CMake 專案

本文假設您已熟悉 CMake，這是用於定義在多個平台上執行之建置程序的跨平台開放原始碼工具。

在 Visual Studio 2015 中，Visual Studio 使用者可以使用 [CMake 產生器](https://cmake.org/cmake/help/v3.9/manual/cmake-generators.7.html)來產生 MSBuild 專案檔，再由 IDE 取用這些檔案供 IntelliSense、瀏覽和編譯之用。 

從 Visual Studio 2017 開始，**適用於 CMake 的 Visual C++ 工具**元件使用 [開啟資料夾] 功能，讓 IDE 直接取用 CMake 專案檔 (例如 CMakeLists.txt) 供 IntelliSense 和瀏覽之用。 如果您使用 Visual Studio 產生器，則會產生暫存專案檔並傳遞至 msbuild.exe，但永遠不會載入供 IntelliSense 或瀏覽之用。 

**Visual Studio 2017 15.3 版**：提供對 Ninja 和 Visual Studio 產生器的支援。

**Visual Studio 2017 15.4 版**：新增對 Linux 上 CMake 的支援。 如需詳細資訊，請參閱[設定 Linux CMake 專案](../linux/cmake-linux-project.md)。

**Visual Studio 2017 15.5 版**：新增對匯入現有 CMake 快取的支援。 Visual Studio 會自動擷取自訂變數，並建立預先填入的 CMakeSettings.json 檔案。

**Visual Studio 2017 15.7 版**：新增支援以停用自動快取產生、[方案總管] 中的 [Targets View] \(目標檢視\) 和單一檔案編譯。

## <a name="installation"></a>安裝

**適用於 CMake 的 Visual C++ 工具**預設會安裝作為**使用 C++ 的桌面開發**工作負載的一部分。

![C++ 桌面工作負載中的 CMake 元件](media/cmake-install.png)
 
## <a name="ide-integration"></a>IDE 整合

當您選擇 [檔案] | [開啟] | [資料夾] 開啟包含 CMakeLists.txt 檔案的資料夾時，會發生下列情況：

- Visual Studio 會將 [CMake] 功能表項目新增至主功能表，並提供檢視和編輯 CMake 指令碼的命令。
- [方案總管] 會顯示資料夾結構和檔案。
- Visual Studio 會執行 CMake.exe，並為預設「組態」(即 x86 偵錯) 產生 CMake 快取。 CMake 命令列會連同 CMake 的其他輸出一起顯示在 [輸出] 視窗中。  **Visual Studio 2017 15.7 版和更新版本**：可以在 [工具] | [選項] | [CMake] | [一般] 對話方塊中停用自動快取產生。
- Visual Studio 會在背景開始編製原始程式檔的索引，以啟用 IntelliSense、瀏覽資訊、重構等。 Visual Studio 會在您工作時，監視編輯器和磁碟上的變更，以確保其索引與來源同步。
 
您可以開啟包含任意數目之 CMake 專案的資料夾。 Visual Studio 會偵測並設定您工作區中的所有「根」CMakeLists.txt 檔案。 您可以對工作區中的所有 CMake 專案進行 CMake 作業 (設定、建置、偵錯)，以及 C++ IntelliSense 和瀏覽。

![具有多個根檔案的 CMake 專案](media/cmake-multiple-roots.png)  

**Visual Studio 2017 15.7 版和更新版本**：您也可以檢視依目標以邏輯方式組織的專案。 從 [方案總管] 工具列的下拉式清單中選擇 [Targets View] \(目標檢視\)：

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png)

## <a name="import-an-existing-cache"></a>匯入現有的快取

當您匯入現有的 CMakeCache.txt 檔案時，Visual Studio 會自動擷取自訂變數，並根據這些變數建立預先填入的 CMakeSettings.json 檔案。 原始快取不會有任何修改，而且仍可從命令列或是透過用於產生的任何工具或 IDE 來使用。 新的 CMakeSettings.json 檔案會與專案的根 CMakeLists.txt 放在一起。 Visual Studio 會根據設定檔產生新的快取。  


**Visual Studio 2017 15.7 版和更新版本**：您可以在 [工具] | [選項] | [CMake] | [一般] 對話方塊中覆寫自動快取產生。

快取中的所有項目不會全部匯入。  產生器和編譯器位置等屬性會取代成已知適用於 IDE 的預設值。

### <a name="to-import-an-existing-cache"></a>匯入現有的快取

1. 從主功能表，選擇 [檔案] | [開啟] | [CMake]：

   ![開啟 CMake](media/cmake-file-open.png "[檔案]、[開啟]、[CMake]") 

   這會顯示 [從快取匯入 CMake 精靈]。 
   
2. 巡覽至您要匯入的 CMakeCache.txt 檔案，然後按一下 [確定]。 [從快取匯入 CMake 專案精靈] 隨即出現：

   ![匯入 CMake 快取](media/cmake-import-wizard.png "開啟 CMake 匯入快取精靈") 

   當精靈完成時，您可以在 [方案總管] 中看到新的 CMakeCache.txt 檔案，就在您專案中的根 CMakeLists.txt 檔案旁。


## <a name="building-cmake-projects"></a>建置 CMake 專案

若要建置 CMake 專案，您有下列選項：

1. 在 [偵錯] 下拉式清單中選取目標，然後按 **F5** 鍵，或按一下 [執行] (綠色三角形) 按鈕。 專案會先自動建置，如同 Visual Studio 方案一樣。
1. 以滑鼠右鍵按一下 CMakeLists.txt，然後從操作功能表選取 [建置]。 如果您的資料夾結構中有多個目標，您可以選擇全部建置或只建置一個特定目標；或
1. 從主功能表，選取 [建置] | [建置方案] (**F7** 或 **Ctrl+Shift+B**)。 確定已在 [一般] 工具列的 [啟動項目] 下拉式清單中選取 CMake 目標。

![CMake 建置功能表命令](media/cmake-build-menu.png "CMake 建置命令功能表") 

針對使用中組態選取 Visual Studio 產生器時，會使用 `-m -v:minimal` 引數叫用 MSBuild.exe。 若要在 CMakeSettings.json 檔案中自訂組建，您可以指定要透過 `buildCommandArgs` 屬性傳遞至建置系統的其他命令列引數：

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

如您所預期，建置結果會顯示在 [輸出] 視窗和 [錯誤清單] 中。
 
![CMake 建置錯誤](media/cmake-build-errors.png "CMake 建置錯誤")

在具有多個建置目標的資料夾中，您可以在 [CMake] 功能表上選擇 [建置] 項目，或選擇 [CMakeLists.txt] 操作功能表以指定要建置哪些 CMake 目標。 在 CMake 專案中按 **Ctrl+Shift+B** 會建置目前的使用中文件。

## <a name="debug-the-project"></a>偵錯專案

若要偵錯 CMake 專案，請選擇所需的組態，然後按 **F5** 鍵，或按下工具列中的 [執行] 按鈕。 如果 [執行] 按鈕顯示 [選取啟動項目]，請選取下拉式箭頭並選擇您要執行的目標。 (在 CMake 專案中，[目前文件] 選項僅適用於 .cpp 檔案。) 

![CMake 執行按鈕](media/cmake-run-button.png "CMake 執行按鈕")

如果自上次建置以來已有所變更，[執行] 或 **F5** 命令會先建置專案。

## <a name="configure-cmake-debugging-sessions"></a>設定 CMake 偵錯工作階段

[一般] 工具列的 [啟動項目] 下拉式清單中會顯示所有可執行的 CMake 目標。 若要啟動偵錯工作階段，只要選取其中一個目標並啟動偵錯工具即可。

![CMake 啟動項目下拉式清單](media/cmake-startup-item-dropdown.png "CMake 啟動項目下拉式清單")


您也可以從 [CMake] 功能表啟動偵錯工作階段。

若要自訂您專案中任何可執行 CMake 目標的偵錯工具設定，請以滑鼠右鍵按一下特定 CMakeLists.txt 檔案，然後選取 [偵錯並啟動設定]。 當您在子功能表中選取 CMake 目標時，會建立稱為 launch.vs.json 的檔案。 此檔案會預先填入您已選取之 CMake 目標的相關資訊，並可讓您指定其他參數，例如程式引數或偵錯工具類型。 若要參考 CMakeSettings.json 檔案中的任何索引鍵，請在前面加上 "Cmake"。 (launch.vs.json 中)。 下列範例顯示一個簡單的 launch.vs.json 檔案，它會提取目前所選組態之 CMakeSettings.json 檔案中的 "remoteCopySources" 索引鍵值：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
   {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

一旦您儲存 launch.vs.json 檔案，系統會使用新名稱在 [啟動項目] 下拉式清單中建立一個項目。 藉由編輯 launch.vs.json 檔案，您可以視需要為任意數目的 CMake 目標建立許多偵錯組態。

**Visual Studio 2017 15.4 版**：Launch.vs.json 支援 CMakeSettings.json (如下所示) 中宣告且適用於目前所選組態的變數。 它還包含名為 "currentDir" 的索引鍵，可設定啟動應用程式的目前目錄：


```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

當您執行應用程式時，`currentDir` 的值會類似於

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>編輯 CMakeLists.txt 檔案

若要編輯 CMakeLists.txt 檔案，請在 [方案總管] 中以滑鼠右鍵按一下該檔案，然後選擇 [開啟]。 如果您對檔案進行變更，則會顯示一個黃色狀態列，通知您 IntelliSense 即將更新，並讓您有機會取消更新作業。 如需 CMakeLists.txt 的資訊，請參閱 [CMake 文件](https://cmake.org/documentation/)。

   ![CMakeLists.txt 檔案編輯](media/cmake-cmakelists.png "CMakeLists.txt 檔案編輯")


一旦您儲存檔案，設定步驟會自動再次執行，並在 [輸出] 視窗中顯示資訊。 錯誤和警告會顯示在 [錯誤清單] 或 [輸出] 視窗中。 按兩下 [錯誤清單] 中的錯誤，即可巡覽至 CMakeLists.txt 中有問題的那一行。

   ![CMakeLists.txt 檔案錯誤](media/cmake-cmakelists-error.png "CMakeLists.txt 檔案錯誤")

## <a name="cmake_settings"></a> CMake 設定和自訂組態

根據預設，Visual Studio 提供六種預設 CMake 組態 ("x86-Debug"、"x86-Release"、"x64-Debug"、"x64-Release"、"Linux-Debug" 和 "Linux-Release")。 這些組態會定義如何叫用 CMake.exe 來為指定的專案建立 CMake 快取。 若要修改這些組態，或建立新的自訂組態，請選擇 [CMake] | [變更 CMake 設定]，然後選擇套用設定的 CMakeLists.txt 檔案。 您也可以在 [方案總管] 中，使用檔案的操作功能表來存取 [變更 CMake 設定] 命令。 此命令會在專案資料夾中建立 CMakeSettings.json 檔案。 此檔案會用來重新建立 CMake 快取檔案，例如在**清除**作業之後。 

   ![CMake 主功能表的變更設定命令](media/cmake-change-settings.png)

JSON IntelliSense 可協助您編輯 CMakeSettings.json 檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

下列範例顯示範例組態，您可以作為起點使用，在 CMakeSettings.json 中建立自己的組態：

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

1. **name**：出現在 C++ 組態下拉式清單中的名稱。 此屬性值也可作為巨集 `${name}` 使用，以指定其他屬性值。 如需範例，請參閱 CMakeSettings.json 中的 **buildRoot** 定義。
1. **generator**：對應至 **-G** 參數並指定要使用的產生器。 此屬性也可作為巨集 `${generator}` 使用，以協助指定其他屬性值。 Visual Studio 目前支援下列 CMake 產生器：

    - "Ninja"
    - "Visual Studio 14 2015"
    - "Visual Studio 14 2015 ARM"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"

由於 Ninja 是專為加快建置速度 (而不是彈性和功能) 所設計，因此預設會設定此產生器。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況，您可以指示 CMake 改為產生 Visual Studio 專案。

若要指定 Visual Studio 產生器，請從主功能表選擇 [CMake] | [變更 CMake 設定] 開啟 CMakeSettings.json。 刪除 “Ninja” 並鍵入 “V”。 這會啟用 IntelliSense，讓您選擇想要的產生器。

1. **buildRoot**：對應至 **-DCMAKE_BINARY_DIR** 參數並指定 CMake 快取的建立位置。 如果資料夾不存在，則會建立資料夾。
1. **variables**：包含成對的 CMake 變數名稱和值，會以 **-D**_name_**=**_value_ 形式傳遞至 CMake。 如果您的 CMake 專案建置指示指定直接將任何變數新增至 CMake 快取檔案，建議您改為在此新增。
1. **cmakeCommandArgs**：指定您要傳遞至 CMake.exe 的任何其他參數。
1. **configurationType**：定義所選產生器的組建組態類型。 目前支援的值為 "Debug"、"MinSizeRel"、"Release" 和 "RelWithDebInfo"。

### <a name="environment-variables"></a>環境變數

CMakeSettings.json 也支援在任何上述屬性中取用環境變數。 使用的語法是 `${env.FOO}`，可擴充環境變數 %FOO%。
您也可以存取此檔案的內建巨集：

- `${workspaceRoot}` - 提供工作區資料夾的完整路徑
- `${workspaceHash}` - 工作區位置的雜湊；適用於建立目前工作區的唯一識別碼 (例如用於資料夾路徑)
- `${projectFile}` - 根 CMakeLists.txt 檔案的完整路徑
- `${projectDir}` - 根 CMakeLists.txt 檔案資料夾的完整路徑
- `${thisFile}` - CMakeSettings.json 檔案的完整路徑
- `${name}` - 組態的名稱
- `${generator}` - 用於此組態之 CMake 產生器的名稱

### <a name="ninja-command-line-arguments"></a>Ninja 命令列引數

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
|   -n      | 試執行 (不執行命令但假裝已成功)|
|   -v       | 建置時顯示所有命令列|
|   -d MODE  | 啟用偵錯 (使用 -d list 可列出模式)|
|   -t TOOL  | 執行子工具 (使用 -t list 可列出子工具)。 終止最上層選項，並將更多旗標傳遞至工具| 
|   -w FLAG  | 調整警告 (使用 -w list 可列出警告)|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>繼承的環境 (Visual Studio 2017 15.5 版)
CMakeSettings.json 現在支援繼承的環境。 此功能可讓您 (1) 繼承預設環境，以及 (2) 建立自訂環境變數，以在執行時傳遞至 CMake.exe。

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

上述範例相當於使用 **-arch=amd64 -host_arch=amd64** 引數執行 **VS 2017 開發人員命令提示字元**。

下表顯示預設值及其命令列對應項：

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
在 CMakeSettings.json 中，您可以全域或根據 **environments** 屬性中的組態定義自訂環境變數。 下列範例會定義一個全域變數 **BuildDir**，這是 x86-Debug 和 x64-Debug 組態中會繼承的變數。 每個組態使用此變數來指定該組態的 **buildRoot** 屬性值。 另請注意每個組態如何使用 **inheritEnvironments** 屬性來指定只會套用至該組態的變數。

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

在下一個範例中，x86-Debug 組態會定義自己的 **BuildDir** 屬性值，且此值會覆寫全域 **BuildDir** 屬性所設定的值，讓 **BuildRoot** 評估為 `D:\custom-builddir\x86-Debug`。

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

## <a name="cmake-configure-step"></a>CMake 設定步驟

對 CMakeSettings.json 或 CMakeLists.txt 檔案進行重大變更時，Visual Studio 會自動重新執行 CMake 設定步驟。 如果設定步驟完成且沒有錯誤，所收集的資訊即可用於 C++ IntelliSense 和語言服務，以及建置和偵錯作業。

如有多個 CMake 專案使用相同的 CMake 組態名稱 (例如 x86-Debug)，只要選取該組態，就會設定並建置所有專案 (在其自己的組建根資料夾中)。 您可以從所有參與該 CMake 組態的 CMake 專案偵錯目標。

   ![CMake 僅建置功能表項目](media/cmake-build-only.png "CMake 僅建置功能表項目")

若要將組建和偵錯工作階段限制為工作區中的一小部分專案，請在 CMakeSettings.json 檔案中建立具有唯一名稱的新組態，並將它只套用至這些專案。 選取該組態時，只有指定的專案才會啟用 IntelliSense 以及建置和偵錯命令。

## <a name="troubleshooting-cmake-cache-errors"></a>針對 CMake 快取錯誤進行疑難排解

如果您需要 CMake 快取狀態的詳細資訊以診斷問題，請開啟 [CMake] 主功能表，或在 [方案總管] 中開啟 [CMakeLists.txt] 操作功能表，執行下列其中一個命令：

- [檢視快取] 會在編輯器中從組建根資料夾開啟 CMakeCache.txt 檔案。 (如果您清除快取，您在此對 CMakeCache.txt 所做的任何編輯都會遭到抹除。 若要在清除快取之後保存所做的變更，請參閱本文稍早的 [CMake 設定和自訂組態](#cmake_settings)。)
- [開啟快取資料夾] 會將檔案總管視窗開啟至組建根資料夾。  
- [清除快取] 會刪除組建根資料夾，讓後續 CMake 設定步驟從全新的快取開始。
- [產生快取] 會強制執行產生步驟，即使 Visual Studio 認為環境處於最新狀態也一樣。
 
**Visual Studio 2017 15.7 版和更新版本**：可以在 [工具] | [選項] | [CMake] | [一般] 對話方塊中停用自動快取產生。

## <a name="single-file-compilation"></a>單一檔案編譯

**Visual Studio 2017 15.7 版和更新版本**：若要在 CMake 專案中建置單一檔案，請以滑鼠右鍵按一下 [方案總管] 中的檔案，然後選擇 [編譯]。 您也可以使用 CMake 主功能表來建置目前已在編輯器中開啟的檔案：

![CMake 單一檔案編譯](media/cmake-single-file-compile.png)