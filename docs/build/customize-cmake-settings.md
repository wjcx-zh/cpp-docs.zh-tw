---
title: 自訂 Visual Studio 中的 CMake 建置設定
ms.date: 04/25/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 20ed066f71a5c8c3acb00ef5923fa5c9f16ac229
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877129"
---
# <a name="customize-cmake-build-settings"></a>自訂 CMake 建置設定

::: moniker range="vs-2019"

在 Visual Studio 2019 和更新版本，您可以新增組態，並使用自訂他們的設定**CMake 設定編輯器**。 編輯器是簡單的替代方案，以手動方式編輯的 CMakeSettings.json 檔案，但如果您想要直接編輯檔案，您可以按一下**編輯 JSON**右上方的編輯器中的連結。 

若要開啟編輯器時，按一下**組態**主要工具列的下拉式清單，然後選擇**管理組態**。

![CMake 組態下拉式清單](media/vs2019-cmake-manage-configurations.png)

現在您會看到**設定編輯器**與左側的已安裝的設定。 

![CMake 設定編輯器](media/cmake-settings-editor.png)

Visual Studio 預設會提供兩個設定：`x64-Debug`和`x86-Debug`。 您可以按一下綠色的加號來新增其他組態。您會看到在編輯器中的設定可能會依據選取組態而有所不同。

您選擇在編輯器中的選項，會寫入名為 CMakeSettings.json 的檔案。 此檔案會提供命令列引數和建置專案時，會傳遞至 CMake 的環境變數。 Visual Studio 不會修改 CMakeLists.txt 自動;使用 CMakeSettings.json 中，您可以自訂透過 Visual Studio 建置時，讓小組的其他人可以使用取用任何他們所使用的工具離開 CMake 專案檔不變。

## <a name="cmake-general-settings"></a>CMake 一般設定

下列設定是位於**一般**標題：

### <a name="configuration-name"></a>組態名稱

對應至**名稱**設定。 這是名稱出現在C++組態下拉式清單。 您可以使用`${name}`撰寫其他的屬性值，例如路徑的巨集。


### <a name="configuration-type"></a>組態類型

對應至**configurationType**設定。 定義所選產生器的組建組態類型。 目前支援的值為 "Debug"、"MinSizeRel"、"Release" 和 "RelWithDebInfo"。

### <a name="toolset"></a>Toolset

對應至**inheritedEnvironments**設定。 定義將用來建置所選的組態的編譯器環境。 支援的值取決於組態的類型。 若要建立的自訂環境，請按一下**編輯 JSON**設定編輯器的右上角中的連結，並直接編輯的 CMakeSettings.json 檔案。

### <a name="cmake-toolchain-file"></a>CMake 工具鏈檔案

CMake 工具鏈檔案路徑。 將傳遞至 CMake 為"-DCMAKE_TOOLCHAIN_FILE =\<檔案路徑 > 」。

### <a name="build-root"></a>建立根

對應至**buildRoot**。 對應至 **-DCMAKE_BINARY_DIR**切換，並指定要建立 CMake 快取。 如果資料夾不存在，則會建立資料夾。

## <a name="command-arguments"></a>命令引數

下列設定是位於**命令引數**標題：

### <a name="cmake-command-arguments"></a>CMake 命令列引數

對應至**cmakeCommandArgs**。 指定您想要傳遞給 CMake.exe 任何其他參數。

### <a name="build-command-arguments"></a>建置命令列引數

對應至**buildCommandArgs**： 指定其他參數傳遞至基礎建置系統。 例如，在使用 Ninja 產生器時傳遞 -v 會強制 Ninja 輸出命令列。


### <a name="ctest-command-arguments"></a>CTest 命令列引數

對應至**ctestCommandArgs**： 指定要執行測試時，傳遞到 CTest 的其他參數。

## <a name="general-settings-for-remote-builds"></a>遠端組建的一般設定

設定，例如 Linux 使用遠端組建，也會提供下列設定：

### <a name="rsync-command-arguments"></a>rsync 命令列引數

提供要傳遞給 rsync 的任何命令引數。 

## <a name="cmake-variables-and-cache"></a>CMake 變數和快取

這些設定可讓您設定 CMake 變數，並將它們儲存在 CMakeSettings.json 中。 它們將會傳遞至 CMake 建置階段，而且會覆寫任何值可能是 CMakeLists.txt 檔案中。 您可以使用本節中的相同方式，您可能會使用 CMakeGUI 以檢視可用於編輯所有 CMake 變數清單。 按一下 **儲存並產生快取**包括進階的變數 （每個 CMakeGUI) 按鈕來檢視所有可用於編輯的 CMake 變數清單。 您可以依變數名稱篩選清單。 

對應至**變數**： 包含的 CMake 變數取得傳遞做為名稱 / 值組 **-D** *_名稱_= _值_* 至 CMake。 如果您的 CMake 專案建置指示指定直接將任何變數新增至 CMake 快取檔案，建議您改為在此新增。

## <a name="advanced-settings"></a>進階設定

### <a name="cmake-generator"></a>CMake 產生器

對應至**產生器**： 對應至 CMake **password-G**切換，並指定要使用產生器。 此屬性也可以在撰寫其他屬性值時用來作為巨集 `${generator}`。 Visual Studio 目前支援下列 CMake 產生器：

  - "Ninja"
  - 「 Unix Makefile"
  - 「 Visual Studio 16 2019年 」
  - 「 Visual Studio 16 2019 Win64"
  - - "Visual Studio 16 2019 ARM"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
  由於 Ninja 是專為加快建置速度 (而不是彈性和功能) 所設計，因此預設會設定此產生器。 不過，有些 CMake 專案可能無法使用 Ninja 正確地建置。 如果發生這種情況，您可以指示 CMake 改為產生 Visual Studio 專案。

### <a name="intellisense-mode"></a>IntelliSense 模式

為精確的 IntelliSense，請將此設定為適當的值，為您的專案中。

### <a name="install-directory"></a>安裝目錄

CMake 會安裝它所建置的目標目錄。

### <a name="cmake-executable"></a>CMake 可執行檔

CMake 可執行檔，包括檔名和副檔名的完整路徑。 遠端組建，請在遠端電腦上指定 CMake 位置。

設定，例如 Linux 使用遠端組建，也會提供下列設定：

### <a name="remote-cmakeliststxt-root"></a>遠端 CMakeLists.txt 根目錄

包含根 CMakeLists.txt 檔案的遠端電腦上的目錄。

### <a name="remote-install-root"></a>遠端安裝根

CMake 會安裝目標的遠端電腦上的目錄。

### <a name="remote-copy-sources"></a>遠端複製來源

指定是否要將原始程式檔複製到遠端電腦，並可讓您指定是否要使用 全部 rsync 或 sftp 傳送。 

## <a name="directly-edit-cmakesettingsjson"></a>直接編輯 CMakeSettings.json

您也可以直接編輯`CMakeSettings.json`來建立自訂組態。 **設定編輯器**已**編輯 JSON**開啟檔案進行編輯的右上角的按鈕。 

下列範例顯示範例組態中，您可以使用做為起點：

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

JSON IntelliSense 可協助您編輯`CMakeSettings.json`檔案：

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

JSON 編輯器也會通知您當您選擇不相容的設定。

如需每個檔案中的屬性的詳細資訊，請參閱[CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 提供數個定義 CMake.exe 如何叫用來建立指定的專案的 CMake 快取的 CMake 組態。 若要新增新的組態，請按一下工具列中的 [組態] 下拉式清單，然後選擇 [管理組態]：

   ![CMake 管理組態](media/cmake-manage-configurations.png)

您可以從預先定義組態的清單中選擇：

   ![CMake 預先定義組態](media/cmake-configurations.png)

當您第一次選取組態時，Visual Studio 會在您專案的根資料夾中建立一個 `CMakeSettings.json` 檔案。 此檔案會用來重新建立 CMake 快取檔案，例如在**清除**作業之後。 

若要新增額外的組態，請以滑鼠右鍵按一下 `CMakeSettings.json`，然後選擇 [新增組態]。 

   ![CMake 新增組態](media/cmake-add-configuration.png "CMake 新增組態")

您也可以使用 **CMake 設定編輯器**來編輯檔案。 請以滑鼠右鍵在 [方案總管] 中按一下 `CMakeSettings.json`，然後選擇 [編輯 CMake 設定]。 或者，從編輯器視窗頂端的 [組態] 下拉式清單，選取 [管理組態]。 

您也可以直接編輯`CMakeSettings.json`來建立自訂組態的下列範例會顯示範例組態中，您可以使用做為起點：

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

如需每個檔案中的屬性的詳細資訊，請參閱[CMakeSettings.json 結構描述參考](cmakesettings-reference.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)<br/>
