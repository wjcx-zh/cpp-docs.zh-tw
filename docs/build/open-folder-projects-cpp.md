---
title: Visual Studio 中 C++ 組建系統的開啟資料夾支援
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9d9f59817a499f4d529363c88adc57154268c0bc
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039582"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Visual Studio 中 C++ 組建系統的開啟資料夾支援

::: moniker range="vs-2015"

[開啟資料夾] 功能可在 Visual Studio 2017 和更新版本中使用。

::: moniker-end

::: moniker range=">=vs-2017"

在 Visual Studio 2017 及之後的版本中，能利用「開啟資料夾」功能，開啟原始程式檔的資料夾，並立即開始撰寫程式碼，同時還支援 IntelliSense、瀏覽、重構、偵錯等等。 當您編輯、建立、移動或刪除檔案時，Visual Studio 會自動追蹤變更並持續更新其 IntelliSense 索引。 不會載入 .sln 或 .vcxproj 檔案；如有需要，您可以指定自訂工作，以及透過簡單的.JSON 檔案建置並啟動參數。 這項功能可讓您將任何協力廠商組建系統整合到 Visual Studio 中。 如需開啟資料夾的一般資訊，請參閱[在 Visual Studio 中開發程式碼而無須專案或解決方案](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)。

## <a name="cmake-and-qt"></a>CMake 和 Qt

CMake 整合在 Visual Studio IDE 中，作為 c + + 桌面工作負載的元件。 CMake 的工作流程與本文所述的工作流程不相同。 如果您使用的是 CMake，請參閱 [Visual Studio 中的 CMake 專案](cmake-projects-in-visual-studio.md)。 您也可以使用 CMake 來建立 Qt 專案，也可以使用 Visual Studio 2015 或 Visual Studio 2017 的 [Qt Visual Studio 延伸](https://download.qt.io/development_releases/vsaddin/) 模組。

## <a name="other-build-systems"></a>其他組建系統

若要搭配使用 Visual Studio IDE 與主功能表中不直接支援的組建系統或編譯器工具組，請選取 [檔案] **|開啟 |資料夾** 或按 **Ctrl + Shift + Alt + O**。流覽至包含您原始程式碼檔的資料夾。 若要建立專案、設定 IntelliSense 和設定調試參數，您可以新增三個 JSON 檔案：

| 檔案 | 描述 |
|-|-|
|CppProperties.json|指定自訂組態資訊以供瀏覽。 如有需要，請在您的根專案資料夾中建立此檔案。 (不會在 CMake 專案中使用。)|
|tasks.vs.json|指定自訂群組建命令。 存取方式為透過 [方案總管]**** 的操作功能表項目 [設定工作]****。|
|launch.vs.json|指定偵錯工具的命令列引數。 存取方式為透過 [方案總管]**** 的操作功能表項目 [偵錯並啟動設定]****。|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>使用 CppProperties.js來設定程式碼導覽

為了讓 IntelliSense 和流覽行為（例如 [ **移至定義** ] 正常運作），Visual Studio 需要知道您所使用的編譯器、系統標頭是什麼，以及任何其他包含檔案的位置，如果它們不是直接放在您 (工作區資料夾) 開啟的資料夾中。 若要指定設定，您可以從主要工具列的下拉式清單中選擇 [ **管理** 設定]：

![管理設定下拉式清單](media/manage-configurations-dropdown.png)

Visual Studio 提供下列預設設定：

![預設組態](media/default-configurations.png)

例如，如果您選擇 **x64-Debug**，Visual Studio 會在根專案資料夾中建立一個名為 *CppProperties.js的* 檔案：

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

此設定會繼承 Visual Studio [x64 開發人員命令提示字元](building-on-the-command-line.md)的環境變數。 其中一個變數是 `INCLUDE` ，您可以在這裡使用宏來參考它 `${env.INCLUDE}` 。 `includePath`屬性會告訴 Visual Studio 要在哪裡尋找 IntelliSense 所需的所有來源。 在此情況下，它會顯示「查詢 INCLUDE 環境變數所指定的所有目錄，以及目前工作資料夾樹狀目錄中的所有目錄」。 `name`屬性是將出現在下拉式清單中的名稱，而且可以是您喜歡的任何名稱。 `defines`屬性會在遇到條件式編譯區塊時，提供 IntelliSense 的提示。 `intelliSenseMode`屬性會根據編譯器類型提供一些額外的提示。 MSVC、GCC 和 Clang 有數個選項可供使用。

> [!NOTE]
> 如果 Visual Studio 似乎忽略 *CppProperties.js*中的設定，請嘗試將例外狀況新增至 *.gitignore* 檔案，如下所示： `!/CppProperties.json` 。

## <a name="default-configuration-for-mingw-w64"></a>MinGW-w64 的預設設定

如果您新增 MinGW W64 設定，JSON 會如下所示：

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

請注意 `environments` 區塊。 它會定義行為類似環境變數的屬性，而且不僅能在 *CppProperties.js* 檔案中使用，也可在其他設定檔中 *task.vs.js* 和 *launch.vs.js*。 `Mingw64`設定會繼承 `mingw_w64` 環境，並使用其 `INCLUDE` 屬性來指定的值 `includePath` 。 您可以視需要將其他路徑新增至此陣列屬性。

`intelliSenseMode`屬性會設定為適用于 GCC 的值。 如需所有這些屬性的詳細資訊，請參閱 [cppproperties.json 架構參考](cppproperties-schema-reference.md)。

當一切正常運作時，當您將滑鼠停留在類型上時，就會看到來自 GCC 標頭的 IntelliSense：

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>啟用 IntelliSense 診斷

如果您看不到預期的 IntelliSense，您可以移至 [**工具**  >  **選項**  >  **文字編輯器**：  >  **C/c + +**  >  **Advanced** ] 和 [設定**啟用記錄**至 **`true`** ] 來進行疑難排解。 若要開始使用，請嘗試將 **記錄層級** 設定為5，並將 **篩選準則記錄** 到8。

![診斷記錄](media/diagnostic-logging.png)

輸出會以管道傳送至 **輸出視窗** ，當您選擇 [*顯示輸出來源： Visual C++ 記錄*] 時，就會顯示輸出。 輸出中會包含 IntelliSense 嘗試使用的實際包含路徑清單，還有其他專案。 如果路徑不符合*CppProperties.js*中的路徑，請嘗試關閉資料夾並刪除包含快取流覽資料的 vs 子資料夾 *。*

### <a name="define-build-tasks-with-tasksvsjson"></a>使用 tasks.vs.json 定義建置工作

您可以針對您目前在工作區中所擁有的檔案自動化建置指令碼或任何其他外部作業，方法是直接在 IDE 中以工作的形式執行它們。 您能以滑鼠右鍵按一下檔案或資料夾，並選取 [設定工作]**** 來設定新工作。

![開啟資料夾設定工作](media/configure-tasks.png)

這會建立 (或開啟) vs 資料夾中 Visual Studio 在您的根專案資料夾中建立的檔案 *tasks.vs.js* 。 您可以在此檔案中定義任意工作，然後從 [方案總管]**** 操作功能表叫用它。 為了繼續 GCC 範例，下列程式碼片段會以單一工作（叫用*g + + .exe*來建立專案）顯示完整的檔案*tasks.vs.js* 。 假設專案包含名為 *hello .cpp*的單一檔案。

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

JSON 檔案會放在 *vs* 子資料夾中。 若要查看該資料夾，請按一下**方案總管**頂端的 [**顯示所有**檔案] 按鈕。 您可以用滑鼠右鍵按一下 **方案總管** 中的根節點，然後選擇 [ **建立 hello**]，來執行這項工作。 當工作完成時，您應該會看到新的檔案， *hello.exe* 在 **方案總管**中。

您可以定義許多種類的工作。 下列範例顯示定義單一工作的檔案 *tasks.vs.js* 。 `taskLabel` 定義出現在操作功能表中的名稱。 `appliesTo` 定義可執行該命令的檔案。 `command`屬性會參考 COMSPEC 環境變數，以識別主控台 (*cmd.exe*在 Windows) 上的路徑。 您也可以參考 CppProperties.json 或 CMakeSettings.json 中宣告的環境變數。 `args` 屬性指定要叫用的命令列。 `${file}` 巨集會在 [方案總管]**** 中擷取選取的檔案。 下列範例會顯示目前所選 .cpp 檔案的檔名。

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

將 *tasks.vs.js*儲存之後，您可以用滑鼠右鍵按一下資料夾中的任何 *.cpp* 檔案，從內容功能表中選擇 [ **Echo filename** ]，然後查看 [輸出] 視窗中顯示的檔案名。

如需詳細資訊，請參閱 [Tasks.vs.json 結構描述參考](tasks-vs-json-schema-reference-cpp.md)。

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 設定偵錯參數

若要自訂您程式的命令列引數和偵錯工具，請在 **方案總管** 中的可執行檔上按一下滑鼠右鍵，然後選取 [ **Debug 和啟動設定**]。 這會開啟檔案上現有的 *launch.vs.js* ，或者，如果不存在，則會建立具有一組基本啟動設定的新檔案。 首先，您可以選擇想要設定的 debug 會話類型。 針對 MinGw w64 專案的偵錯工具，我們選擇 **C/c + + 啟動 For MinGw/Cygwin (gdb) **。 這會建立使用 *gdb.exe* 的啟動設定，並對預設值有一些相關的猜測。 其中一個預設值為 `MINGW_PREFIX` 。 您可以使用常值路徑來取代 (如下所示) 或您可以 `MINGW_PREFIX` 在 *CppProperties.js*中定義屬性：

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

若要啟動偵錯工具，請選擇 [偵錯工具] 下拉式清單中的可執行檔，然後按一下綠色箭號：

![啟動偵錯工具](media/launch-debugger-gdb.png)

您應該會看到 [ **正在初始化調試** 程式] 對話方塊，以及正在執行程式的外部主控台視窗。

如需詳細資訊，請參閱 [ 架構參考上的launch.vs.js](launch-vs-schema-reference-cpp.md)。

## <a name="launching-other-executables"></a>啟動其他可執行檔

您可以定義電腦上任何可執行檔的啟動設定。 下列範例會啟動 *7za* ，並指定其他引數，方法是將它們新增至 `args` JSON 陣列：

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
