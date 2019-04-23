---
title: Visual Studio 中的 CMake 專案
ms.date: 03/27/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 22a8ecc34e6413c32628381241d45d3d76b39ecc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030429"
---
# <a name="cmake-projects-in-visual-studio"></a>Visual Studio 中的 CMake 專案

CMake 是可在多個平台上執行之定義建置程序的跨平台開放原始碼工具。 本文假設您已熟悉 CMake。 您可以在[使用 CMake 建置、測試和封裝您的軟體](https://cmake.org/)中深入了解它。

在 Visual Studio 2015 中，Visual Studio 使用者可以使用 [CMake 產生器](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)來產生 MSBuild 專案檔，再由 IDE 取用這些檔案供 IntelliSense、瀏覽和編譯之用。

Visual Studio 2017 引入豐富的 CMake 支援，包括[跨平台的 CMake 專案](../linux/cmake-linux-project.md)。 **適用於 CMake 的 Visual C++ 工具**元件使用 [開啟資料夾] 功能，讓 IDE 直接取用 CMake 專案檔 (例如 CMakeLists.txt) 供 IntelliSense 和瀏覽之用。 支援 Ninja 和 Visual Studio 產生器。 如果您使用 Visual Studio 產生器，則會產生暫存專案檔並傳遞至 msbuild.exe，但永遠不會載入供 IntelliSense 或瀏覽之用。 您可以匯入現有 CMake 快取;Visual Studio 會自動擷取自訂的變數，並建立預先填入**CMakeSettings.json**檔案。 

## <a name="installation"></a>安裝

**適用於 CMake 的 Visual C++ 工具**預設安裝為**使用 C++ 的桌面開發**工作負載及**使用 C++ 的 Linux 程式開發**工作負載的一部分。

![C++ 桌面工作負載中的 CMake 元件](media/cmake-install.png)

如需詳細資訊，請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 整合

當您選擇 [檔案] | [開啟] | [資料夾] 開啟包含 CMakeLists.txt 檔案的資料夾時，會發生下列情況：

- Visual Studio 會將 [CMake] 功能表項目新增至主功能表，並提供檢視和編輯 CMake 指令碼的命令。

- [方案總管] 會顯示資料夾結構和檔案。

- Visual Studio 會執行 CMake.exe，並選擇性為預設「組態」(即 x86 偵錯) 產生 CMake 快取。 CMake 命令列會連同 CMake 的其他輸出一起顯示在 [輸出] 視窗中。

- Visual Studio 會在背景開始編製原始程式檔的索引，以啟用 IntelliSense、瀏覽資訊、重構等。 Visual Studio 會在您工作時，監視編輯器和磁碟上的變更，以確保其索引與來源同步。

您可以開啟包含任意數目之 CMake 專案的資料夾。 Visual Studio 會偵測並設定您工作區中的所有「根」CMakeLists.txt 檔案。 您可以對工作區中的所有 CMake 專案進行 CMake 作業 (設定、建置、偵錯)，以及 C++ IntelliSense 和瀏覽。

![具有多個根檔案的 CMake 專案](media/cmake-multiple-roots.png)

您也可以檢視依目標以邏輯方式組織的專案。 從 [方案總管] 工具列的下拉式清單中選擇 [Targets View] \(目標檢視\)：

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png)

Visual Studio 會使用名為的檔案**CMakeSettings.json**來儲存環境變數或命令列選項 Cmake.exe。 **CMakeSettings.json**也可讓您定義及儲存多個 CMake 組建組態，以及輕鬆切換其在 IDE 中。 

否則，請使用**CMakeLists.txt**就像您會在任何指定原始程式檔，尋找程式庫、 設定編譯器和連結器選項，並指定其他組建系統的 CMake 專案中的相關資訊。

如果您需要傳遞引數的可執行檔，在偵錯時，您可以使用另一個檔名**launch.vs.json**。 在某些情況下，Visual Studio 會自動產生這些檔案，您可以手動編輯它們。 您也可以自行建立檔案。

> [!NOTE]
> 至於其他類型的開啟資料夾 」 專案中，會使用兩個其他的 JSON 檔案：**CppProperties.json**並**tasks.vs.json**。 它們都和 CMake 專案不相關。

## <a name="import-an-existing-cache"></a>匯入現有的快取

當您匯入現有的 CMakeCache.txt 檔案時，Visual Studio 會自動擷取自訂變數，並根據這些變數建立預先填入的 **CMakeSettings.json** 檔案。 原始快取不會有任何修改，而且仍可從命令列或是透過用於產生的任何工具或 IDE 來使用。 新**CMakeSettings.json**檔案放置在一起的專案根 CMakeLists.txt。 Visual Studio 會根據設定檔產生新的快取。 您可以覆寫 [工具] | [選項] | [CMake] | [一般] 對話方塊中的自動快取產生。

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

1. 在一般的工具列中，尋找**組態**下拉式清單中; 它可能預設顯示 [Linux-偵錯] 或 [x64 偵錯]。 選取所需的設定，然後按**F5**，或按一下**執行**工具列上的 （綠色三角形） 按鈕。 專案會先自動建置，如同 Visual Studio 方案一樣。

1. 以滑鼠右鍵按一下 CMakeLists.txt，然後從操作功能表選取 [建置]。 如果您的資料夾結構中有多個目標，您可以選擇全部建置或只建置一個特定目標。

1. 從主功能表，選取 [建置] | [建置方案] (**F7** 或 **Ctrl+Shift+B**)。 確定已在 [一般] 工具列的 [啟動項目] 下拉式清單中選取 CMake 目標。

![CMake 建置功能表命令](media/cmake-build-menu.png "CMake 建置命令功能表")

您可以自訂組建組態、 環境變數、 命令列引數，以及其他設定，而不需要修改 CMakeLists.txt 檔案使用**CMakeSettings.json**檔案。 如需詳細資訊，請參閱[自訂 CMake 設定](customize-cmake-settings.md)。

如您所預期，建置結果會顯示在 [輸出] 視窗和 [錯誤清單] 中。

![CMake 建置錯誤](media/cmake-build-errors.png "CMake 建置錯誤")

在具有多個建置目標的資料夾中，您可以在 [CMake] 功能表上選擇 [建置] 項目，或選擇 [CMakeLists.txt] 操作功能表以指定要建置哪些 CMake 目標。 在 CMake 專案中按 **Ctrl+Shift+B** 會建置目前的使用中文件。

## <a name="debugging-cmake-projects"></a>偵錯 CMake 專案

若要偵錯 CMake 專案，請選擇所需的組態，然後按 **F5** 鍵，或按下工具列中的 [執行] 按鈕。 如果 [執行] 按鈕顯示 [選取啟動項目]，請選取下拉式箭頭並選擇您要執行的目標。 (在 CMake 專案中，[目前文件] 選項僅適用於 .cpp 檔案。)

![CMake 執行按鈕](media/cmake-run-button.png "CMake 執行按鈕")

如果自上次建置以來已有所變更，[執行] 或 **F5** 命令會先建置專案。

您可以自訂偵錯工作階段中設定屬性 CMake **launch.vs.json**檔案。 如需詳細資訊，請參閱[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)。


## <a name="editing-cmakeliststxt-files"></a>編輯 CMakeLists.txt 檔案

若要編輯 CMakeLists.txt 檔案，請在 [方案總管] 中以滑鼠右鍵按一下該檔案，然後選擇 [開啟]。 如果您對檔案進行變更，則會顯示一個黃色狀態列，通知您 IntelliSense 即將更新，並讓您有機會取消更新作業。 如需 CMakeLists.txt 的資訊，請參閱 [CMake 文件](https://cmake.org/documentation/)。

   ![CMakeLists.txt 檔案編輯](media/cmake-cmakelists.png "CMakeLists.txt 檔案編輯")

一旦您儲存檔案，設定步驟會自動再次執行，並在 [輸出] 視窗中顯示資訊。 錯誤和警告會顯示在 [錯誤清單] 或 [輸出] 視窗中。 按兩下 [錯誤清單] 中的錯誤，即可巡覽至 CMakeLists.txt 中有問題的那一行。

   ![CMakeLists.txt 檔案錯誤](media/cmake-cmakelists-error.png "CMakeLists.txt 檔案錯誤")


## <a name="cmake-configure-step"></a>CMake 設定步驟

重大變更對時**CMakeSettings.json**或 CMakeLists.txt 檔案，Visual Studio 會自動傳回 CMake 設定步驟。 如果設定步驟完成且沒有錯誤，所收集的資訊即可用於 C++ IntelliSense 和語言服務，以及建置和偵錯作業。

如有多個 CMake 專案使用相同的 CMake 組態名稱 (例如 x86-Debug)，只要選取該組態，就會設定並建置所有專案 (在其自己的組建根資料夾中)。 您可以從所有參與該 CMake 組態的 CMake 專案偵錯目標。

   ![CMake 僅建置功能表項目](media/cmake-build-only.png "CMake 僅建置功能表項目")

若要限制建置及偵錯工作階段的工作區中專案的子集，建立新的組態中的唯一名稱**CMakeSettings.json**檔案，並將它套用至僅限這些專案。 選取該組態時，只有指定的專案才會啟用 IntelliSense 以及建置和偵錯命令。

## <a name="troubleshooting-cmake-cache-errors"></a>針對 CMake 快取錯誤進行疑難排解

如果您需要 CMake 快取狀態的詳細資訊以診斷問題，請開啟 [CMake] 主功能表，或在 [方案總管] 中開啟 [CMakeLists.txt] 操作功能表，執行下列其中一個命令：

- [檢視快取] 會在編輯器中從組建根資料夾開啟 CMakeCache.txt 檔案。 (如果您清除快取，您在此對 CMakeCache.txt 所做的任何編輯都會遭到抹除。 若要保存已清除的快取之後的變更，請參閱[來自訂 CMake 設定](customize-cmake-settings.md)。)

- [開啟快取資料夾] 會將檔案總管視窗開啟至組建根資料夾。

- [清除快取] 會刪除組建根資料夾，讓後續 CMake 設定步驟從全新的快取開始。

- [產生快取] 會強制執行產生步驟，即使 Visual Studio 認為環境處於最新狀態也一樣。

您可以停用 [工具] | [選項] | [CMake] | [一般] 對話方塊中的自動快取產生。

## <a name="single-file-compilation"></a>單一檔案編譯

若要在 CMake 專案中建置單一檔案，請以滑鼠右鍵按一下 [方案總管] 中的檔案，然後選擇 [編譯]。 您也可以使用 CMake 主功能表來建置目前已在編輯器中開啟的檔案：

![CMake 單一檔案編譯](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>從命令列執行 CMake

如果您已從 Visual Studio 安裝程式安裝 CMake，則可以遵循下列步驟從命令列執行：

1. 執行適當的 vsdevcmd.bat (x86/x64)。 如需詳細資訊，請參閱[在命令列上建置](building-on-the-command-line.md)。

1. 切換至您的輸出資料夾。

1. 執行 CMake 以建置/設定您的應用程式。
  
## <a name="see-also"></a>另請參閱

[教學課程：在 Visual Studio 中建立 C++ 跨平台專案](get-started-linux-cmake.md)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[自訂 CMake 建置設定](customize-cmake-settings.md)<br/>
[CMakeSettings.json 參考](cmakesettings-reference.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)<br/>
