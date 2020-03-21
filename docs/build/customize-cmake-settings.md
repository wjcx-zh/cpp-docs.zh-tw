---
title: 自訂 Visual Studio 中的 CMake 建置設定
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: f93997e498502e0e326edfc2b023af9808f86357
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078658"
---
# <a name="customize-cmake-build-settings"></a>自訂 CMake 建置設定

::: moniker range="vs-2019"

在 Visual Studio 2019 和更新版本中，您可以新增組態並使用 **CMake 設定編輯器**自訂其設定。 編輯器是用來手動編輯*CMakeSettings*檔案的較簡單替代方案，但如果您想要直接編輯檔案，可以按一下編輯器右上方的 [**編輯 json** ] 連結。

若要開啟編輯器，請按一下主要工具列中的 [組態] 下拉式清單，然後選擇 [管理組態]。

![CMake 組態下拉式清單](media/vs2019-cmake-manage-configurations.png)

此時您會看到**設定編輯器**，且左側會顯示已安裝的組態。

![CMake 設定編輯器](media/cmake-settings-editor.png)

Visual Studio 預設會提供一個 `x64-Debug` 設定。 您可以按一下綠色的加號來新增其他設定。 您在編輯器中看到的設定可能會根據所選取的設定而有所不同。

您在編輯器中選擇的選項會寫入名為*CMakeSettings*的檔案中。 此檔案會提供在您建置專案時會傳至 CMake 的命令列引數和環境變數。 Visual Studio 絕不會自動修改*remote monitoring.h cmakelists.txt* ;藉由使用*CMakeSettings* ，您可以透過 Visual Studio 自訂群組建，同時讓 CMake 專案檔案維持不變，讓小組中的其他人可以使用其所使用的任何工具來取用它們。

## <a name="cmake-general-settings"></a>CMake 一般設定

以下是 [一般] 標題下提供的設定：

### <a name="configuration-name"></a>組態名稱

對應於 **name** 設定。 這個名稱會出現在C++ [設定] 下拉式清單中。 您可以使用 `${name}` 巨集來撰寫其他屬性值，例如路徑。

### <a name="configuration-type"></a>組態類型

對應於 **configurationType** 設定。 定義所選產生器的組建組態類型。 目前支援的值為 "Debug"、"MinSizeRel"、"Release" 和 "RelWithDebInfo"。 它會對應到[CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)。

### <a name="toolset"></a>Toolset

對應於 **inheritedEnvironments** 設定。 定義用來建立所選設定的編譯器環境。 支援的值取決於組態的類型。 若要建立自訂環境，請選擇 [設定] 編輯器右上角的 [**編輯 JSON** ] 連結，然後直接編輯*CMakeSettings*檔案。

### <a name="cmake-toolchain-file"></a>CMake 工具鏈檔案

[CMake 工具鏈](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html)檔的路徑。 這個路徑會當做 "-DCMAKE_TOOLCHAIN_FILE = \<filepath >" 傳遞給 CMake。 工具鏈 files 指定編譯器和工具鏈公用程式的位置，以及其他目標平臺和編譯器相關資訊。 根據預設，如果未指定此設定，Visual Studio 會使用[vcpkg 工具鏈](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake)檔。

### <a name="build-root"></a>組建根

對應於 **buildRoot**。 對應至[CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)，並指定要建立 CMAKE 快取的位置。 如果指定的資料夾不存在，則會加以建立。

## <a name="command-arguments"></a>命令引數

以下是 [命令引數] 標題下提供的設定：

### <a name="cmake-command-arguments"></a>CMake 命令引數

對應於 **cmakeCommandArgs**。 指定傳遞至 CMake 的任何其他[命令列選項](https://cmake.org/cmake/help/latest/manual/cmake.1.html)。

### <a name="build-command-arguments"></a>組建命令引數

對應至**buildCommandArgs**。 指定要傳遞至基礎組建系統的其他參數。 例如，在使用 Ninja 產生器時傳遞 `-v`，會強制 Ninja 輸出命令列。

### <a name="ctest-command-arguments"></a>CTest 命令引數

對應至**ctestCommandArgs**。 指定執行測試時要傳遞至 CTest 的其他[命令列選項](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html)。

## <a name="general-settings-for-remote-builds"></a>遠端組建的一般設定

在設定像是使用遠端組建的 Linux 時，也可以使用下列設定：

### <a name="rsync-command-arguments"></a>rsync 命令引數

傳遞至[rsync](https://download.samba.org/pub/rsync/rsync.html)的其他命令列選項，這是一種快速且多功能的檔案複製工具。

## <a name="cmake-variables-and-cache"></a>CMake 變數和快取

這些設定可讓您設定 CMake 變數，並將它們儲存在*CMakeSettings*中。 它們會在組建階段傳遞至 CMake，並覆寫*remote monitoring.h cmakelists.txt*檔中的任何值。 您可以比照您使用 CMakeGUI 的相同方式來使用這個部分，以檢視所有可用於編輯的 CMake 變數清單。 按一下 [儲存並產生快取] 按鈕，以檢視所有可用於編輯的 CMake 變數清單，包括進階變數 (依據 CMakeGUI)。 您可以依變數名稱篩選清單。

對應至**變數**。 包含 CMake 變數的名稱/值組，以 **-D** *_名稱_=_值_* 傳遞至 CMake。 如果您的 CMake 專案組建指示指定將任何變數直接新增至 CMake 快取檔案，我們建議您改為在此加入。

## <a name="advanced-settings"></a>進階設定

### <a name="cmake-generator"></a>CMake 產生器

對應至**產生**器。 對應至 CMake **-G**參數，並指定要使用的[CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)產生器。 此屬性也可以在撰寫其他屬性值時用來作為巨集 `${generator}`。 Visual Studio 目前支援下列 CMake 產生器：

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
  
由於 Ninja 是針對快速組建速度而設計，而不是彈性和功能，因此會設定為預設值。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況，您可以指示 CMake 改為產生 Visual Studio 專案。

### <a name="intellisense-mode"></a>IntelliSense 模式

IntelliSense 引擎所使用的 IntelliSense 模式。 如果未選取任何模式，則 Visual Studio 會繼承自指定的工具組。  

### <a name="install-directory"></a>安裝目錄

CMake 安裝目標所在的目錄。 對應至[CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)。

### <a name="cmake-executable"></a>CMake 可執行檔

CMake 程式可執行檔的完整路徑，包括檔案名和副檔名。 它可讓您將 CMake 的自訂版本與 Visual Studio 搭配使用。 對於遠端組建，請指定遠端機器上的 CMake 位置。

在設定像是使用遠端組建的 Linux 時，也可以使用下列設定：

### <a name="remote-cmakeliststxt-root"></a>遠端 CMakeLists.txt 根目錄

遠端電腦上包含根*remote monitoring.h cmakelists.txt .txt*檔案的目錄。

### <a name="remote-install-root"></a>遠端安裝根目錄

CMake 在遠端機器上安裝目標的目錄。 對應至[CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)。

### <a name="remote-copy-sources"></a>遠端複製來源

指定是否要將來源檔案複製到遠端電腦，並讓您指定是否要使用 rsync 或 sftp。

## <a name="directly-edit-cmakesettingsjson"></a>直接編輯 CMakeSettings.json

您也可以直接編輯*CMakeSettings*來建立自訂設定。 **設定編輯器**的右上方有 [編輯 JSON] 按鈕可開啟檔案以進行編輯。

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

JSON IntelliSense 可協助您編輯*CMakeSettings json*檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

當您選擇不相容的設定時，JSON 編輯器也會通知您。

如需檔案中每個屬性的詳細資訊，請參閱 [CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 提供數種 CMake 組態，定義如何叫用 CMake.exe 來建立指定專案的 CMake 快取。 若要新增新的組態，請按一下工具列中的 [組態] 下拉式清單，然後選擇 [管理組態]：

   ![CMake 管理組態](media/cmake-manage-configurations.png)

您可以從預先定義組態的清單中選擇：

   ![CMake 預先定義組態](media/cmake-configurations.png)

第一次選取設定時，Visual Studio 會在專案的根資料夾中建立*CMakeSettings。* 此檔案會用來重新建立 CMake 快取檔案，例如在**清除**作業之後。

若要新增其他設定，請以滑鼠右鍵按一下 [ *CMakeSettings* ]，然後選擇 [**新增**設定]。

   ![CMake 新增設定](media/cmake-add-configuration.png "CMake 新增設定")

您也可以使用 **CMake 設定編輯器**來編輯檔案。 以滑鼠右鍵按一下**方案總管**中的 [ *CMakeSettings* ]，然後選擇 [**編輯 CMake 設定**]。 或者，從編輯器視窗頂端的 [組態] 下拉式清單，選取 [管理組態]。

您也可以直接編輯*CMakeSettings*來建立自訂設定。 下列範例顯示範例組態，可供您作為作業起點：

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

JSON IntelliSense 可協助您編輯*CMakeSettings json*檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

如需檔案中每個屬性的詳細資訊，請參閱 [CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)
