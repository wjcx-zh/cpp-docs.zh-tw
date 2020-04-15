---
title: 自訂 Visual Studio 中的 CMake 建置設定
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328684"
---
# <a name="customize-cmake-build-settings"></a>自訂 CMake 建置設定

::: moniker range="vs-2019"

在 Visual Studio 2019 和更新版本中，您可以新增組態並使用 **CMake 設定編輯器**自訂其設定。 編輯器旨在手動編輯*CMakeSettings.json*檔,但如果您希望直接編輯檔,則可以按下編輯器右上角的 **「編輯 JSON」** 連結。

若要開啟編輯器，請按一下主要工具列中的 [組態]**** 下拉式清單，然後選擇 [管理組態]****。

![CMake 組態下拉式清單](media/vs2019-cmake-manage-configurations.png)

此時您會看到**設定編輯器**，且左側會顯示已安裝的組態。

![CMake 設定編輯器](media/cmake-settings-editor.png)

默認情況下,可視化工作室`x64-Debug`提供一個配置。 您可以通過單擊綠色加號來添加其他配置。 您在編輯器中看到的設定可能因選擇哪種配置而異。

您在編輯器中選擇的選項將寫入名為*CMakeSettings.json*的檔。 此檔案會提供在您建置專案時會傳至 CMake 的命令列引數和環境變數。 視覺化工作室從不自動修改 *"單行清單";* 例如,它從未自動修改"選擇清單"。"?"通過使用*CMakeSettings.json,* 您可以透過 Visual Studio 自訂生成,同時保留 CMake 專案檔不變,以便團隊中的其他人可以使用他們使用的任何工具使用它們。

## <a name="cmake-general-settings"></a>CMake 一般設定

以下是 [一般]**** 標題下提供的設定：

### <a name="configuration-name"></a>組態名稱

對應於 **name** 設定。 此名稱將顯示在C++配置下拉清單中。 您可以使用 `${name}` 巨集來撰寫其他屬性值，例如路徑。

### <a name="configuration-type"></a>組態類型

對應於 **configurationType** 設定。 定義所選產生器的組建組態類型。 目前支援的值為 "Debug"、"MinSizeRel"、"Release" 和 "RelWithDebInfo"。 它映射到[CMAKE_BUILD_TYPE。](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)

### <a name="toolset"></a>Toolset

對應於 **inheritedEnvironments** 設定。 定義用於生成所選配置的編譯器環境。 支援的值取決於組態的類型。 要建立自定義環境,請選擇"設定"編輯器右上角的 **"編輯 JSON"** 連結,然後直接編輯*CMakeSettings.json*檔。

### <a name="cmake-toolchain-file"></a>CMake 工具鏈檔案

CMake[工具鏈文件的](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html)路徑。 此路徑以"-DCMAKE_TOOLCHAIN_FILE\<= 檔案路徑>"傳遞給 CMake。 工具鏈檔指定編譯器和工具鏈實用程式的位置,以及其他目標平臺和編譯器相關資訊。 預設情況下,如果未指定此設定,Visual Studio 將使用[vcpkg 工具鍊檔案](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake)。

### <a name="build-root"></a>組建根

對應於 **buildRoot**。 映射到[CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html),並指定在何處創建 CMake 快取。 如果指定的資料夾不存在,則創建該資料夾。

## <a name="command-arguments"></a>命令引數

以下是 [命令引數]**** 標題下提供的設定：

### <a name="cmake-command-arguments"></a>CMake 命令引數

對應於 **cmakeCommandArgs**。 指定傳遞給 CMake.exe 的任何其他[指令列選項](https://cmake.org/cmake/help/latest/manual/cmake.1.html)。

### <a name="build-command-arguments"></a>組建命令引數

對應於**建立 CommandArgs**。 指定要傳遞到基礎生成系統的其他交換機。 例如,使用忍者`-v`生成器時傳遞強制忍者輸出命令行。

### <a name="ctest-command-arguments"></a>CTest 命令引數

對應於**ctestCommandArgs**。 指定執行測試時要傳遞給 CTest 的其他[指令列選項](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html)。

## <a name="general-settings-for-remote-builds"></a>遠端組建的一般設定

在設定像是使用遠端組建的 Linux 時，也可以使用下列設定：

### <a name="rsync-command-arguments"></a>rsync 命令引數

其他命令列選項傳遞給[rsync,](https://download.samba.org/pub/rsync/rsync.html)一個快速和通用的檔案複製工具。

## <a name="cmake-variables-and-cache"></a>CMake 變數和快取

這些設置使您能夠設置 CMake 變數並將其保存在*CMakeSettings.json*中。 它們在生成時傳遞到 CMake,並重寫*CMakelists.txt*檔中的任何值。 您可以比照您使用 CMakeGUI 的相同方式來使用這個部分，以檢視所有可用於編輯的 CMake 變數清單。 按一下 [儲存並產生快取]**** 按鈕，以檢視所有可用於編輯的 CMake 變數清單，包括進階變數 (依據 CMakeGUI)。 您可以按變數名稱篩選清單。

對應於**變數**。 包含作為 **-D** *_名稱_=值*傳遞給 CMake 的 CMake 變數的名稱值對。 如果您的 CMake 專案產生說明指定將任何變數直接添加到 CMake 快取檔中,我們建議您在此處添加這些變數。

## <a name="advanced-settings"></a>進階設定

### <a name="cmake-generator"></a>CMake 產生器

對應於**產生器**。 映射到 CMake **-G**開關,並指定要使用的[CMake 產生器](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)。 此屬性也可以在撰寫其他屬性值時用來作為巨集 `${generator}`。 Visual Studio 目前支援下列 CMake 產生器：

- "Ninja"
- "Unix Makefiles"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
由於忍者專為快速構建速度而設計,而不是靈活性和功能,因此將其設置為預設值。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況,您可以指示 CMake 改為生成可視化工作室專案。

### <a name="intellisense-mode"></a>IntelliSense 模式

IntelliSense 引擎使用的"感知"模式。 如果未選擇任何模式,則 Visual Studio 將從指定的工具集中繼承。  

### <a name="install-directory"></a>安裝目錄

CMake 安裝目標的目錄。 映射到[CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)。

### <a name="cmake-executable"></a>CMake 可執行檔

CMake 程式可執行的完整路徑,包括檔名和擴展名。 它允許您使用自定義版本的 CMake 與可視化工作室。 對於遠端組建，請指定遠端機器上的 CMake 位置。

在設定像是使用遠端組建的 Linux 時，也可以使用下列設定：

### <a name="remote-cmakeliststxt-root"></a>遠端 CMakeLists.txt 根目錄

包含根*CMakelists.txt*檔案的遠端電腦上的目錄。

### <a name="remote-install-root"></a>遠端安裝根目錄

CMake 在遠端機器上安裝目標的目錄。 映射到[CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)。

### <a name="remote-copy-sources"></a>遠端複製來源

指定是將源檔案複製到遠端電腦,並允許您指定是使用 rsync 還是 sftp。

## <a name="directly-edit-cmakesettingsjson"></a>直接編輯 CMakeSettings.json

您還可以直接編輯*CMakeSettings.json*以建立自訂配置。 **設定編輯器**的右上方有 [編輯 JSON]**** 按鈕可開啟檔案以進行編輯。

下列範例顯示範例組態，可供您作為作業起點：

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

JSON IntelliSense 可説明您編輯*CMakeSettings.json*檔:

   ![CMake JSON 感知](media/cmake-json-intellisense.png "CMake JSON 感知")

當您選擇不相容的設置時,JSON 編輯器也會通知您。

如需檔案中每個屬性的詳細資訊，請參閱 [CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 提供數種 CMake 組態，定義如何叫用 CMake.exe 來建立指定專案的 CMake 快取。 若要新增新的組態，請按一下工具列中的 [組態] 下拉式清單，然後選擇 [管理組態]****：

   ![CMake 管理組態](media/cmake-manage-configurations.png)

您可以從預先定義組態的清單中選擇：

   ![CMake 預先定義組態](media/cmake-configurations.png)

首次選擇配置時,Visual Studio 會在專案的根資料夾中創建一個*CMakeSettings.json*檔。 此檔案會用來重新建立 CMake 快取檔案，例如在**清除**作業之後。

要添加其他配置,請右鍵按下 *「CMakeSettings.json」,* 然後選擇「**添加設定**」。

   ![CMake 新增設定](media/cmake-add-configuration.png "CMake 新增設定")

您也可以使用 **CMake 設定編輯器**來編輯檔案。 右鍵按一下**解決方案資源管理程式**中的 *「CMakeSettings.json」,* 然後選擇 **「編輯點擊設定**」 。 或者，從編輯器視窗頂端的 [組態] 下拉式清單，選取 [管理組態]****。

您還可以直接編輯*CMakeSettings.json*以建立自訂配置。 下列範例顯示範例組態，可供您作為作業起點：

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

JSON IntelliSense 可説明您編輯*CMakeSettings.json*檔:

   ![CMake JSON 感知](media/cmake-json-intellisense.png "CMake JSON 感知")

如需檔案中每個屬性的詳細資訊，請參閱 [CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)
