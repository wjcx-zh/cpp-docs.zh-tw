---
title: Visual Studio 中 C++ 組建系統的開啟資料夾支援
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320966"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Visual Studio 中 C++ 組建系統的開啟資料夾支援

::: moniker range="vs-2015"

"打開資料夾"功能在 Visual Studio 2017 及更高版本提供。

::: moniker-end

::: moniker range=">=vs-2017"

在 Visual Studio 2017 及之後的版本中，能利用「開啟資料夾」功能，開啟原始程式檔的資料夾，並立即開始撰寫程式碼，同時還支援 IntelliSense、瀏覽、重構、偵錯等等。 當您編輯、建立、移動或刪除檔案時，Visual Studio 會自動追蹤變更並持續更新其 IntelliSense 索引。 不會載入 .sln 或 .vcxproj 檔案；如有需要，您可以指定自訂工作，以及透過簡單的.JSON 檔案建置並啟動參數。 此功能使您能夠將任何第三方構建系統整合到 Visual Studio 中。 如需開啟資料夾的一般資訊，請參閱[在 Visual Studio 中開發程式碼而無須專案或解決方案](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)。

## <a name="cmake-and-qt"></a>CMake 與 Qt

CMake 作為C++桌面工作負載的一個元件集成到 Visual Studio IDE 中。 CMake 的工作流與本文中描述的工作流不同。 如果您使用的是"單行",請參閱[可視化工作室中的"製作"專案](cmake-projects-in-visual-studio.md)。 您還可以使用 CMake 建構 Qt 專案,也可以為 Visual Studio 2015 或 Visual Studio 2017 使用[Qt 視覺工作室擴展](https://download.qt.io/development_releases/vsaddin/)。

## <a name="other-build-systems"></a>其他產生系統

要將 Visual Studio IDE 與主選單中沒有直接支援的生成系統或編譯器工具集一起使用,請選擇 **「檔 |打開 |資料夾**或按**Ctrl = 移位+ Alt = O**。導航到包含原始程式碼檔的資料夾。 要產生專案,請設定 IntelliSense 並設定除錯參數,請新增三個 JSON 檔:

| | |
|-|-|
|CppProperties.json|指定自訂組態資訊以供瀏覽。 如有需要，請在您的根專案資料夾中建立此檔案。 (不會在 CMake 專案中使用。)|
|tasks.vs.json|指定自定義生成命令。 存取方式為透過 [方案總管]**** 的操作功能表項目 [設定工作]****。|
|launch.vs.json|指定偵錯工具的命令列引數。 存取方式為透過 [方案總管]**** 的操作功能表項目 [偵錯並啟動設定]****。|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>使用 CppProperties.json 設定代碼導覽

對於 IntelliSense 和瀏覽行為(如**轉到定義**)正常工作,Visual Studio 需要知道您正在使用的編譯器、系統標頭的位置以及如果任何其他包含檔不直接位於已打開的資料夾中(工作區資料夾),則這些檔案的位置。 要指定設定,可以從主工具列的下拉清單中選擇 **「管理設定**」:

![管理設定下拉清單](media/manage-configurations-dropdown.png)

Visual Studio 提供以下預設設定:

![預設組態](media/default-configurations.png)

例如,如果您選擇**x64-Debug**,Visual Studio 會在根項目資料夾中建立名為*CppProperties.json*的檔案:

```json
{
  "configurations": [
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
    }
  ]
}
```

此設定繼承 Visual Studio [x64 開發人員命令提示符](building-on-the-command-line.md)的環境變數。 其中一個變數是`INCLUDE`,您可以使用`${env.INCLUDE}`宏在此處引用它。 該`includePath`屬性告訴 Visual Studio 在何處查找 IntelliSense 所需的所有來源。 在這種情況下,它表示"查看 INCLUDE 環境變數指定的所有目錄,以及當前工作資料夾樹中的所有目錄。 屬性`name`是將顯示在下拉清單中的名稱,可以是任何您喜歡的名稱。 當`defines`IntelliSense 遇到條件編譯塊時,該屬性向 IntelliSense 提供提示。 該`intelliSenseMode`屬性基於編譯器類型提供一些其他提示。 MSVC、GCC 和Clang提供了多種選項。

> [!NOTE]
> 如果 Visual Studio 似乎忽略*CppProperties.json*中的設定,請嘗試向 *.gitignore*檔案添加異常,`!/CppProperties.json`如下所示: .

## <a name="default-configuration-for-mingw-w64"></a>明GW-w64的預設設定

如果添加 MinGW-W64 配置,JSON 如下所示:

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

請注意區`environments`塊 。 它定義的屬性的行為類似於環境變數,不僅在*CppProperties.json*檔案中可用,在其他配置檔*任務中*也*可用。* 配置`Mingw64``mingw_w64`繼承環境,並使用`INCLUDE`其 屬性指定的`includePath`值。 您可以根據需要向此陣組屬性添加其他路徑。

該`intelliSenseMode`屬性設置為適合 GCC 的值。 有關所有這些屬性的詳細資訊,請參閱[CppProperties 架構參考](cppproperties-schema-reference.md)。

當一切工作正常時,當您將滑鼠懸停在類型上時,您將從 GCC 標頭上看到 IntelliSense:

![海灣合作委員會感知](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>啟用感知診斷

如果您沒有看到預期中的 IntelliSense,則可以通過存**取工具** > **選項** > **文字編輯器** > **C/C++** > **進階**和將**啟用日誌記錄**設置為**true**來進行故障排除。 首先,請嘗試將**日誌記錄級別**設置為 5,**並將篩選器**設置為 8。

![診斷記錄](media/diagnostic-logging.png)

輸出透過導管到**輸出視窗**,當您選擇 「*顯示輸出從: 可視C++日誌*」時,輸出可見。 輸出包含 IntelliSense 嘗試使用的實際路徑清單。 如果路徑與*CppProperties.json*中的路徑不匹配,請嘗試關閉資料夾並刪除包含緩存流覽數據的 *.vs*子資料夾。

### <a name="define-build-tasks-with-tasksvsjson"></a>使用 tasks.vs.json 定義建置工作

您可以針對您目前在工作區中所擁有的檔案自動化建置指令碼或任何其他外部作業，方法是直接在 IDE 中以工作的形式執行它們。 您能以滑鼠右鍵按一下檔案或資料夾，並選取 [設定工作]**** 來設定新工作。

![開啟資料夾設定工作](media/configure-tasks.png)

這將在 Visual Studio 在根項目資料夾中建立的 .vs 資料夾中建立(或打開)*任務. vs.json*檔。 您可以在此檔案中定義任意工作，然後從 [方案總管]**** 操作功能表叫用它。 要繼續 GCC 範例,以下代碼段將顯示一個完整的*任務.vs.json*檔,該檔作為單個任務呼叫*g_.exe*來生成專案。 假設該專案包含一個稱為*hello.cpp*的檔。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

JSON 檔案放置在 *.vs*子資料夾中。 要檢視該資料夾,請單擊**解決方案資源管理員**頂部的 **「顯示所有檔案**」按鈕。 您可以通過右鍵單擊**解決方案資源管理器**中的根節點並選擇**生成 hello**來運行此任務。 任務完成後,您應該看到一個新檔 *,hello.exe*在**解決方案資源管理器**中。

您可以定義許多類型的任務。 下面的範例顯示了定義單工作*的工作. vs.json 檔*。 `taskLabel` 定義出現在操作功能表中的名稱。 `appliesTo` 定義可執行該命令的檔案。 該`command`屬性引用 COMSPEC 環境變數,該變數識別主控台的路徑(Windows 上的*cmd.exe)。* 您也可以參考 CppProperties.json 或 CMakeSettings.json 中宣告的環境變數。 `args` 屬性指定要叫用的命令列。 `${file}` 巨集會在 [方案總管]**** 中擷取選取的檔案。 下列範例會顯示目前所選 .cpp 檔案的檔名。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

儲存*工作後.vs.json*,您可以右鍵單擊資料夾中的任何 *.cpp*檔,從上下文選單中選擇**Echo 檔名**,並查看「輸出」視窗中顯示的檔名。

如需詳細資訊，請參閱 [Tasks.vs.json 結構描述參考](tasks-vs-json-schema-reference-cpp.md)。

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 設定偵錯參數

要自定義程式的命令列參數和調試說明,請右鍵單擊**解決方案資源管理器**中的可執行檔,然後選擇 **「調試和啟動設定**」。 這將打開現有的*啟動.vs.json*檔,或者如果不存在,它將創建一個包含一組最小啟動設置的新檔。 首先,您可以選擇要配置的調試會話類型。 對於調試 MinGw-w64 專案,我們選擇**C/C++ 啟動為明格格/西格溫 (gdb)。** 這將創建一個啟動配置,用於使用*gdb.exe,* 對預設值進行一些有根據的猜測。 這些預設值之一是`MINGW_PREFIX`。 您可以取代文字路徑(如下所示),也可以在*CppProperties.json*`MINGW_PREFIX`中定義屬性:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

要開始除錯,請在除錯下拉清單中選擇可執行檔,然後單擊綠色箭頭:

![啟動除錯器](media/launch-debugger-gdb.png)

您應該看到**初始除錯器**對話框,然後看到執行程式的外部主控台視窗。

有關詳細資訊,請參閱[啟動.vs.json 架構參考](launch-vs-schema-reference-cpp.md)。

## <a name="launching-other-executables"></a>啟動其他執行檔

您可以為電腦上的任何可執行檔定義啟動設定。 下面的範例啟動*7za*並透過將它們`args`加入 JSON 陣列來指定其他參數:

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

::: moniker-end
