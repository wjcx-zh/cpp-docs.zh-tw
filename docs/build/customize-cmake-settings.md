---
title: 自訂 Visual Studio 中的 CMake 建置設定
ms.date: 05/16/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: a00b18f163758be0238a05c4d2af3195014d79b0
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042546"
---
# <a name="customize-cmake-build-settings"></a>自訂 CMake 建置設定

::: moniker range="vs-2019"

在 Visual Studio 2019 和更新版本中，您可以新增組態並使用 **CMake 設定編輯器**自訂其設定。 編輯器可作為手動編輯 CMakeSettings.json 檔案的簡單替代工具，但如果您想要直接編輯檔案，您可以按一下編輯器右上方的 [編輯 JSON]  連結。 

若要開啟編輯器，請按一下主要工具列中的 [組態]  下拉式清單，然後選擇 [管理組態]  。

![CMake 組態下拉式清單](media/vs2019-cmake-manage-configurations.png)

此時您會看到**設定編輯器**，且左側會顯示已安裝的組態。 

![CMake 設定編輯器](media/cmake-settings-editor.png)

Visual Studio 依預設會提供兩個設定：`x64-Debug` 和 `x86-Debug`。 您可以按一下綠色加號以新增其他組態。您在編輯器中看到的設定可能會依據選取的組態而有所不同。

您在編輯器中選擇的選項會寫入至名為 CMakeSettings.json 的檔案。 此檔案會提供在您建置專案時會傳至 CMake 的命令列引數和環境變數。 Visual Studio 不會自動修改 CMakeLists.txt；藉由使用 CMakeSettings.json，您可以透過 Visual Studio 自訂組建，同時將 CMake 專案檔保持為原狀，讓小組的其他成員可以使用他們選擇的任何工具加以取用。

## <a name="cmake-general-settings"></a>CMake 一般設定

以下是 [一般]  標題下提供的設定：

### <a name="configuration-name"></a>組態名稱

對應於 **name** 設定。 這是出現在 C++ 組態下拉式清單中的名稱。 您可以使用 `${name}` 巨集來撰寫其他屬性值，例如路徑。


### <a name="configuration-type"></a>組態類型

對應於 **configurationType** 設定。 定義所選產生器的組建組態類型。 目前支援的值為 "Debug"、"MinSizeRel"、"Release" 和 "RelWithDebInfo"。

### <a name="toolset"></a>Toolset

對應於 **inheritedEnvironments** 設定。 定義將用來建置所選組態的編譯器環境。 支援的值取決於組態的類型。 若要建立自訂環境，請按一下「設定」編輯器右上角中的 [編輯 JSON]  連結，並直接編輯 CMakeSettings.json 檔案。

### <a name="cmake-toolchain-file"></a>CMake 工具鏈檔案

CMake 工具鏈檔案的路徑。 將會傳至 CMake 作為 "-DCMAKE_TOOLCHAIN_FILE = \<filepath>"。

### <a name="build-root"></a>組建根

對應於 **buildRoot**。 對應至 **-DCMAKE_BINARY_DIR** 參數，並指定 CMake 快取的建立位置。 如果資料夾不存在，則會建立資料夾。

## <a name="command-arguments"></a>命令引數

以下是 [命令引數]  標題下提供的設定：

### <a name="cmake-command-arguments"></a>CMake 命令引數

對應於 **cmakeCommandArgs**。 指定要傳至 CMake.exe 的任何其他參數。

### <a name="build-command-arguments"></a>組建命令引數

對應於 **buildCommandArgs**：指定要傳至基礎建置系統的其他參數。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。


### <a name="ctest-command-arguments"></a>CTest 命令引數

對應於 **ctestCommandArgs**：指定在執行測試時要傳至 CTest 的其他參數。

## <a name="general-settings-for-remote-builds"></a>遠端組建的一般設定

在設定像是使用遠端組建的 Linux 時，也可以使用下列設定：

### <a name="rsync-command-arguments"></a>rsync 命令引數

提供要傳至 rsync 的任何命令引數。 

## <a name="cmake-variables-and-cache"></a>CMake 變數和快取

這些設定可讓您設定 CMake 變數，並將其儲存在 CMakeSettings.json 中。 這些變數會在建置期間傳至 CMake，並且將覆寫 CMakeLists.txt 檔案中可能包含的任何值。 您可以比照您使用 CMakeGUI 的相同方式來使用這個部分，以檢視所有可用於編輯的 CMake 變數清單。 按一下 [儲存並產生快取]  按鈕，以檢視所有可用於編輯的 CMake 變數清單，包括進階變數 (依據 CMakeGUI)。 您可以依變數名稱篩選清單。 

對應於 **variables**：包含成對的 CMake 變數名稱和值，會以 **-D** *_name_=_value_* 形式傳至 CMake。 如果您的 CMake 專案建置指示指定直接將任何變數新增至 CMake 快取檔案，建議您改為在此新增。

## <a name="advanced-settings"></a>進階設定

### <a name="cmake-generator"></a>CMake 產生器

對應於 **generator**：對應至 CMake **-G** 參數，並指定要使用的產生器。 此屬性也可以在撰寫其他屬性值時用來作為巨集 `${generator}`。 Visual Studio 目前支援下列 CMake 產生器：

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
  
  由於 Ninja 是專為加快建置速度 (而不是彈性和功能) 所設計，因此預設會設定此產生器。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況，您可以指示 CMake 改為產生 Visual Studio 專案。

### <a name="intellisense-mode"></a>IntelliSense 模式

若要使用精確的 IntelliSense，請為您的專案將此項目設為適當的值。

### <a name="install-directory"></a>安裝目錄

CMake 將其建置的目標安裝所在的目錄。

### <a name="cmake-executable"></a>CMake 可執行檔

通往 CMake 可執行檔的完整路徑，包括檔案名稱和副檔名。 對於遠端組建，請指定遠端機器上的 CMake 位置。

在設定像是使用遠端組建的 Linux 時，也可以使用下列設定：

### <a name="remote-cmakeliststxt-root"></a>遠端 CMakeLists.txt 根目錄

遠端電腦上包含根 CMakeLists.txt 檔案的目錄。

### <a name="remote-install-root"></a>遠端安裝根目錄

CMake 在遠端機器上安裝目標的目錄。

### <a name="remote-copy-sources"></a>遠端複製來源

指定是否要將來源檔案複製到遠端機器，並且可讓您指定要使用 rsync 還是 sftp。 

## <a name="directly-edit-cmakesettingsjson"></a>直接編輯 CMakeSettings.json

您也可以直接編輯 `CMakeSettings.json` 以建立自訂組態。 **設定編輯器**的右上方有 [編輯 JSON]  按鈕可開啟檔案以進行編輯。 

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

JSON IntelliSense 會協助您編輯 `CMakeSettings.json` 檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

JSON 編輯器也會在您選擇了不相容的設定時通知您。

如需檔案中每個屬性的詳細資訊，請參閱 [CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 提供數種 CMake 組態，定義如何叫用 CMake.exe 來建立指定專案的 CMake 快取。 若要新增新的組態，請按一下工具列中的 [組態] 下拉式清單，然後選擇 [管理組態]  ：

   ![CMake 管理組態](media/cmake-manage-configurations.png)

您可以從預先定義組態的清單中選擇：

   ![CMake 預先定義組態](media/cmake-configurations.png)

當您第一次選取組態時，Visual Studio 會在您專案的根資料夾中建立一個 `CMakeSettings.json` 檔案。 此檔案會用來重新建立 CMake 快取檔案，例如在**清除**作業之後。 

若要新增額外的組態，請以滑鼠右鍵按一下 `CMakeSettings.json`，然後選擇 [新增組態]  。 

   ![CMake 新增組態](media/cmake-add-configuration.png "CMake 新增組態")

您也可以使用 **CMake 設定編輯器**來編輯檔案。 請以滑鼠右鍵在 [方案總管]  中按一下 `CMakeSettings.json`，然後選擇 [編輯 CMake 設定]  。 或者，從編輯器視窗頂端的 [組態] 下拉式清單，選取 [管理組態]  。 

您也可以直接編輯 `CMakeSettings.json` 以建立自訂組態。下列範例顯示範例組態，可供您作為作業起點：

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

JSON IntelliSense 會協助您編輯 `CMakeSettings.json` 檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

如需檔案中每個屬性的詳細資訊，請參閱 [CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)<br/>
