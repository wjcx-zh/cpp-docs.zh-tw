---
title: Visual Studio 中 C++ 組建系統的開啟資料夾支援
ms.date: 08/20/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 78b1c00b07423e9d02f585c707156a1c843bea6f
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975977"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>Visual Studio 中 C++ 組建系統的開啟資料夾支援

::: moniker range="vs-2015"

[開啟資料夾] 功能可在 Visual Studio 2017 和更新版本中取得。

::: moniker-end

::: moniker range=">=vs-2017"

在 Visual Studio 2017 及之後的版本中，能利用「開啟資料夾」功能，開啟原始程式檔的資料夾，並立即開始撰寫程式碼，同時還支援 IntelliSense、瀏覽、重構、偵錯等等。 當您編輯、建立、移動或刪除檔案時，Visual Studio 會自動追蹤變更並持續更新其 IntelliSense 索引。 不會載入 .sln 或 .vcxproj 檔案；如有需要，您可以指定自訂工作，以及透過簡單的.JSON 檔案建置並啟動參數。 這項功能可讓您將任何協力廠商組建系統整合到 Visual Studio 中。 如需開啟資料夾的一般資訊，請參閱[在 Visual Studio 中開發程式碼而無須專案或解決方案](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)。

## <a name="cmake-and-qt"></a>CMake 和 Qt

CMake 會在 Visual Studio IDE 中整合成C++桌面工作負載的元件。 CMake 的工作流程與本文所述的工作流程並不相同。 如果您使用的是 CMake, 請參閱[在 Visual Studio 中 CMake 專案](cmake-projects-in-visual-studio.md)。 您也可以使用 CMake 來建立 Qt 專案, 也可以使用 Visual Studio 2015 或 Visual Studio 2017 的[Qt Visual Studio 延伸](https://download.qt.io/development_releases/vsaddin/)模組。

## <a name="other-build-systems"></a>其他組建系統

若要使用 Visual Studio IDE 搭配無法直接從主功能表支援的組建系統或編譯器工具組, 請選取 [檔案] **|開啟 |資料夾**, 或按**Ctrl + Shift + Alt + O**。流覽至包含原始程式碼檔案的資料夾。 若要建立專案、設定 IntelliSense 和設定調試參數, 您可以新增三個 JSON 檔案:

| | |
|-|-|
|CppProperties.json|指定自訂組態資訊以供瀏覽。 如有需要，請在您的根專案資料夾中建立此檔案。 (不會在 CMake 專案中使用。)|
|tasks.vs.json|指定自訂群組建命令。 存取方式為透過 [方案總管] 的操作功能表項目 [設定工作]。|
|launch.vs.json|指定偵錯工具的命令列引數。 存取方式為透過 [方案總管] 的操作功能表項目 [偵錯並啟動設定]。|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>使用 CppProperties 設定程式碼導覽

若要讓 IntelliSense 和流覽行為 (例如 [**移至定義**] 正常運作), Visual Studio 需要知道您所使用的編譯器、系統標頭的所在位置, 以及任何其他 include 檔案 (如果它們不是直接位於您已開啟的資料夾 (工作區資料夾)。 若要指定設定, 您可以從主工具列的下拉式清單中選擇 [**管理**設定]:

![[管理設定] 下拉式清單](media/manage-configurations-dropdown.png)

目前, Visual Studio 提供四個預設設定, 全都適用于C++ Microsoft 編譯器:

![預設組態](media/default-configurations.png)

例如, 如果您選擇 [ **x64-Debug**], Visual Studio 會在根專案資料夾中建立名為*CppProperties*的檔案, 並將其填入, 如下所示:

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

此設定會「繼承」 Visual Studio [x64 開發人員命令提示字元](building-on-the-command-line.md)的環境變數。 其中一個變數是`INCLUDE` , 您可以在這裡`${env.INCLUDE}`使用宏來參考它。 `includePath`屬性會告訴 Visual Studio 在何處尋找 IntelliSense 所需的所有來源。 在此情況下, 它會指出「查詢 INCLUDE 環境變數所指定的所有目錄, 以及目前工作資料夾樹狀結構中的所有目錄」。 `name`屬性是將出現在下拉式清單中的名稱, 而且可以是任何您喜歡的專案。 `defines`屬性會在遇到條件式編譯區塊時, 提供提示給 IntelliSense。 屬性`intelliSenseMode`會根據編譯器類型提供一些額外的提示。 有數個選項可供 MSVC、GCC 和 Clang 使用。

## <a name="example-configuration-for-gcc"></a>GCC 的範例設定

如果您使用 Microsoft C++以外的編譯器, 就必須在*CppProperties*中建立自訂設定和環境。 下列範例顯示一個完整的*CppProperties json*檔案, 其中包含在 MSYS2 安裝中使用 GCC 的單一自訂設定:

```json
{
  "configurations": [
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
          "TOOLSET_VERSION": "8.3.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
   }
}
```

請注意`environments`區塊。 它會定義行為類似環境變數的屬性, 而且不僅可在*CppProperties*檔案中使用, 還會在其他設定檔工作中 *。 vs.* json 和*啟動。與 json*。 設定會`INCLUDE`繼承環境, 並使用其屬性來指定的值`includePath`。 `mingw_w64` `Mingw64` 您可以視需要將其他路徑新增至此陣列屬性。

> [!WARNING]
> 目前已知的問題是, 在中`INCLUDE` `environments`指定的值`includePath`未正確地傳遞至屬性。 您可以藉由將完整的常值 include 路徑加入至`includePath`陣列來解決此問題。

`intelliSenseMode`屬性會設定為適用于 GCC 的值。 如需所有這些屬性的詳細資訊, 請參閱[CppProperties 架構參考](cppproperties-schema-reference.md)。

當所有專案都正常運作時, 您會在將滑鼠停留在類型上時, 看到來自 GCC 標頭的 IntelliSense:

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>啟用 IntelliSense 診斷

如果您看不到預期的 IntelliSense, 可以移至 [**工具** > ] [**選項** > ] [**文字編輯器** > ] [ >  **C/C++** **Advanced** ], 以進行疑難排解將 [**啟用記錄**] 設定為 [ **true**]。 若要開始, 請嘗試將**記錄層級**設定為 5, 並將**篩選準則記錄**到8。

![診斷記錄](media/diagnostic-logging.png)

輸出會輸送至**輸出視窗**, 並在您選擇 [*顯示輸出來源] 時顯示:視覺C++效果*記錄。 輸出中包含 IntelliSense 嘗試使用之實際 include 路徑的清單。 如果路徑不符合*CppProperties*中的路徑, 請嘗試關閉資料夾, 並刪除包含快取流覽資料的 *. vs*子資料夾。

### <a name="define-build-tasks-with-tasksvsjson"></a>使用 tasks.vs.json 定義建置工作

您可以針對您目前在工作區中所擁有的檔案自動化建置指令碼或任何其他外部作業，方法是直接在 IDE 中以工作的形式執行它們。 您能以滑鼠右鍵按一下檔案或資料夾，並選取 [設定工作] 來設定新工作。

![開啟資料夾設定工作](media/configure-tasks.png)

這會在. vs 資料夾中建立 (或開啟) 與 Visual Studio 在根專案資料夾中建立的*vs. 與 json*檔案。 您可以在此檔案中定義任意工作，然後從 [方案總管] 操作功能表叫用它。 為了繼續 GCC 範例, 下列程式碼片段顯示一個完整的工作 *. vs. json*檔案, 其具有做為單一工作, 可叫用*g + + .exe*來建立專案。 假設專案包含名為*hello .cpp*的單一檔案。

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

JSON 檔案會放在 *. vs*子資料夾中, 如果您按一下**方案總管**頂端的 [**顯示所有**檔案] 按鈕, 就會看到此檔案。 您可以用滑鼠右鍵按一下**方案總管**中的根節點, 然後選擇 [**建立 hello**], 來執行這項工作。 當工作完成時, 您應該會在**方案總管**中看到新的檔案*hello .exe* 。

您可以定義許多類型的工作。 下列範例顯示定義單一工作的工作 *. vs. json*檔案。 `taskLabel` 定義出現在操作功能表中的名稱。 `appliesTo` 定義可執行該命令的檔案。 屬性會參考 COMSPEC 環境變數, 其可識別主控台的路徑 (Windows 上的 cmd.exe)。 `command` 您也可以參考 CppProperties.json 或 CMakeSettings.json 中宣告的環境變數。 `args` 屬性指定要叫用的命令列。 `${file}` 巨集會在 [方案總管] 中擷取選取的檔案。 下列範例會顯示目前所選 .cpp 檔案的檔名。

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

儲存工作之後, 您可以在資料夾中的任何 *.cpp*檔案上按一下滑鼠右鍵, 從內容功能表中選擇 [ **Echo filename** ], 然後查看 [輸出] 視窗中顯示的檔案名。

如需詳細資訊，請參閱 [Tasks.vs.json 結構描述參考](tasks-vs-json-schema-reference-cpp.md)。

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 設定偵錯參數

若要自訂程式的命令列引數和偵錯工具指令, 請在**方案總管**中的可執行檔上按一下滑鼠右鍵, 然後選取 [ **Debug and 啟動設定**]。 這會開啟現有的*啟動檔案與 json*檔案, 如果不存在, 則會建立具有一組最小啟動設定的新檔案。 首先, 您可以選擇要設定哪種類型的 debug 會話。 針對 MinGw-w64 專案的偵錯工具, 我們選擇**CC++ /啟動 for MinGGW/Cygwin (gdb)** 。 這會建立使用*gdb*的啟動設定, 並對預設值有一些已接受的猜測。 其中一個預設值是`MINGW_PREFIX`。 您可以替代常值路徑 (如下所示), 也可以在`MINGW_PREFIX` *CppProperties*中定義屬性:

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

若要開始進行偵錯工具, 請在 [偵錯工具] 下拉式清單中選擇可執行檔, 然後按一下綠色箭號:

![啟動偵錯工具](media/launch-debugger-gdb.png)

您應該會看到正在**初始化的偵錯工具**對話方塊, 以及執行程式的外部主控台視窗。

如需詳細資訊, 請參閱[啟動. vs. json 架構參考](launch-vs-schema-reference-cpp.md)。

## <a name="launching-other-executables"></a>啟動其他可執行檔

您可以為電腦上的任何可執行檔定義啟動設定。 下列範例會啟動*7za*並指定其他引數, 方法是將它們`args`新增至 JSON 陣列:

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
