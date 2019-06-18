---
title: Visual Studio 中 C++ 組建系統的開啟資料夾支援
ms.date: 03/21/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 8856a5b1782c75c5a59dfdc93a8203627059ea12
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042716"
---
# <a name="open-folder-projects-for-c"></a>C++ 的開啟資料夾專案

在 Visual Studio 2017 及之後的版本中，能利用「開啟資料夾」功能，開啟原始程式檔的資料夾，並立即開始撰寫程式碼，同時還支援 IntelliSense、瀏覽、重構、偵錯等等。 不會載入 .sln 或 .vcxproj 檔案；如有需要，您可以指定自訂工作，以及透過簡單的.JSON 檔案建置並啟動參數。 如需開啟資料夾的一般資訊，請參閱[在 Visual Studio 中開發程式碼而無須專案或解決方案](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions)。

CMake 整合 Visual Studio IDE 中的元件為C++桌面工作負載。 如需詳細資訊，請參閱 [Visual Studio 中的 CMake 專案](cmake-projects-in-visual-studio.md)。 針對任何其他的組建系統，您可以使用開啟資料夾功能。 開啟資料夾可有效地將程式碼編輯器、偵錯工具和分析器從組建系統和編譯器工具組分離。 您可以搭配幾乎任何組建系統來使用 C++ 程式碼編輯器及其豐富的 IntelliSense 功能、程式碼分析器及 Visual Studio 偵錯工具，包括 CMake、Ninja、QMake (適用於 Qt 專案)、gyp、SCons、Gradle、Buck、make 等。 它甚至可和沒有組建系統的單一檔案或鬆散檔案集合搭配運作。

若要使用「開啟資料夾」，請從主功能表選取 [檔案] | [開啟] | [資料夾]  ，或按 **Ctrl + Shift + Alt + O**。[方案總管] 會立即顯示資料夾中的所有檔案。 您可以按一下任何檔案以開始編輯它。 Visual Studio 會在背景開始編制檔案的索引，以啟用 IntelliSense、瀏覽及重構功能。 當您編輯、建立、移動或刪除檔案時，Visual Studio 會自動追蹤變更並持續更新其 IntelliSense 索引。 

## <a name="qmake-projects-that-target-the-qt-framework"></a>以 Qt 架構為目標的 QMake 專案

您可以使用 CMake 建置 Qt 專案，或者您可以使用[Qt Visual Studio 擴充功能](https://download.qt.io/development_releases/vsaddin/)Visual Studio 2015 或 Visual Studio 2017。

## <a name="gyp-cons-scons-buck-etc"></a>gyp、Cons、SCons、Buck 等

您可以在 Visual Studio 中使用任何組建系統，並仍享有 C++ IDE 和偵錯工具的優點。 當您開啟專案的根資料夾時，C++ 程式碼編輯器會使用啟發學習法來編製來源檔案的索引供 IntelliSense 和瀏覽使用。 您可以藉由編輯 CppProperties.json 檔案，提供您程式碼結構的相關提示。 同樣地，您也可以藉由編輯 launch.vs.json 檔案來設定和叫用您的建置程式。

## <a name="configuring-open-folder-projects"></a>設定「開啟資料夾」專案

您可以透過三個 JSON 檔案自訂「開啟資料夾」專案：

| | |
|-|-|
|CppProperties.json|指定自訂組態資訊以供瀏覽。 如有需要，請在您的根專案資料夾中建立此檔案。 (不會在 CMake 專案中使用。)|
|tasks.vs.json|指定自訂建置命令和編譯器參數。 存取方式為透過 [方案總管]  的操作功能表項目 [設定工作]  。|
|launch.vs.json|指定偵錯工具的命令列引數。 存取方式為透過 [方案總管]  的操作功能表項目 [偵錯並啟動設定]  。|

### <a name="configure-intellisense-and-browsing-hints-with-cpppropertiesjson"></a>使用 CppProperties.json 設定 IntelliSense 並瀏覽提示

IntelliSense 和瀏覽行為部分取決於使用中組建組態，這會定義 #include 路徑、編譯器參數和其他參數。 根據預設，Visual Studio 會提供偵錯和發行組態。 CMake 專案使用 CMakeSettings.json 檔案及 CMakeLists.txt 檔案來進行此操作。 針對其他類型的開啟資料夾專案，您可能需要建立自訂組態，讓 IntelliSense 和瀏覽功能可以完全理解您的程式碼。 若要定義新的組態，請在根資料夾中建立稱為 CppProperties.json 的檔案。 請看以下範例：

```json
{
  "configurations": [
    {
      "name": "Windows x64",
      "includePath": [ "include" ],
      "defines": [ "_DEBUG" ],
      "compilerSwitches": "/std:c++17",
      "intelliSenseMode": "windows-msvc-x64",
      "forcedInclude": [ "pch.h" ],
      "undefines": []
    }
  ]
}
```
如需詳細資訊，請參閱 [CppProperties 結構描述參考](cppproperties-schema-reference.md)。

### <a name="define-build-tasks-with-tasksvsjson"></a>使用 tasks.vs.json 定義建置工作

您可以針對您目前在工作區中所擁有的檔案自動化建置指令碼或任何其他外部作業，方法是直接在 IDE 中以工作的形式執行它們。 您能以滑鼠右鍵按一下檔案或資料夾，並選取 [設定工作]  來設定新工作。

![開啟資料夾設定工作](media/open-folder-config-tasks.png)

這會建立 （或開啟） **tasks.vs.json** .vs 資料夾下的 Visual Studio 會建立在專案根資料夾中的檔案。 您可以在此檔案中定義任意工作，然後從 [方案總管]  操作功能表叫用它。 下列範例會顯示定義單一工作的 tasks.vs.json 檔案。 `taskName` 定義出現在操作功能表中的名稱。 `appliesTo` 定義可執行該命令的檔案。 `command` 屬性參考 COMSPEC 環境變數，以識別主控台的路徑 (在 Windows 上為 cmd.exe)。 您也可以參考 CppProperties.json 或 CMakeSettings.json 中宣告的環境變數。 `args` 屬性指定要叫用的命令列。 `${file}` 巨集會在 [方案總管]  中擷取選取的檔案。 下列範例會顯示目前所選 .cpp 檔案的檔名。

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

您可以在儲存 tasks.vs.json 之後，以滑鼠右鍵按一下資料夾中的任何 .cpp 檔案，從操作功能表選擇 [Echo filename]  ，然後查看 [輸出] 視窗中顯示的檔案名稱。

如需詳細資訊，請參閱 [Tasks.vs.json 結構描述參考](tasks-vs-json-schema-reference-cpp.md)。

### <a name="configure-debugging-parameters-with-launchvsjson"></a>使用 launch.vs.json 設定偵錯參數

若要自訂您程式的命令列引數，請在 [方案總管]  中以滑鼠右鍵按一下該可執行檔，然後選取 [偵錯並啟動設定]  。 這會開啟的現有**launch.vs.json**檔案，或如果不存在，它會建立新的檔案，預先填入您所選取的計畫的相關資訊。

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
