---
title: Visual Studio 中的 CMake 專案
description: 如何在可視化工作室中使用"CMake"創建和構建C++專案。
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329165"
---
# <a name="cmake-projects-in-visual-studio"></a>Visual Studio 中的 CMake 專案

CMake 是可在多個平台上執行之定義建置程序的跨平台開放原始碼工具。 本文假定您熟悉 CMake。 您可以在[使用 CMake 建置、測試和封裝您的軟體](https://cmake.org/)中深入了解它。

> [!NOTE]
> 在過去幾個版本中,CMake 與 Visual Studio 的整合性越來越大。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

用於 Windows 元件**的 C++ CMake 工具**使用[「打開資料夾」](open-folder-projects-cpp.md)功能直接用於用於 IntelliSense 和瀏覽目的的「CMakeLists.txt」專案檔(如*CMakelists.txt)。* 支援 Ninja 和 Visual Studio 產生器。 如果使用 Visual Studio 生成器,它將生成一個臨時專案檔並將其傳遞給 msbuild.exe。 但是,該項目永遠不會載入用於 IntelliSense 或流覽目的。 您還可以導入現有的 CMake 緩存。

## <a name="installation"></a>安裝

**C++ Windows 的 CMake 工具**是桌面開發中的一部分 **,具有 C++工作負載 C++** 和**Linux 開發**。 有關詳細資訊,請參閱[跨平臺"造單專案](../linux/cmake-linux-project.md)"。

![C++ 桌面工作負載中的 CMake 元件](media/cmake-install-2019.png)

如需詳細資訊，請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 整合

當您選擇 **「打開>資料夾>打開**包含*CMakelists.txt*檔案的資料夾時,會發生以下情況:

- Visual Studio 將 **「CMake」** 專案新增到 **「專案」** 選單中,並帶有用於查看和編輯 CMake 文稿的命令。

- [方案總管]**** 會顯示資料夾結構和檔案。

- Visual Studio 執行 cmake.exe 並生成預設 (x64 除錯) 設定的 CMake 快取檔案 (*CMakeCache.txt*)。 CMake 命令列會連同 CMake 的其他輸出一起顯示在 [輸出]**** 視窗中。

- Visual Studio 會在背景開始編製原始程式檔的索引，以啟用 IntelliSense、瀏覽資訊、重構等。 Visual Studio 會在您工作時，監視編輯器和磁碟上的變更，以確保其索引與來源同步。

您可以開啟包含任意數目之 CMake 專案的資料夾。 Visual Studio 檢測並配置工作區中的所有"根 *"CMakelists.txt*檔。 CMake 操作(配置、生成、除錯)、C++ IntelliSense 和瀏覽都可用於工作區中的所有 CMake 專案。

![具有多個根檔案的 CMake 專案](media/cmake-multiple-roots.png)

您也可以檢視依目標以邏輯方式組織的專案。 從 [方案總管]**** 工具列的下拉式清單中選擇 [Targets View] \(目標檢視\)****：

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png)

單擊**解決方案資源管理員**頂部的 **「顯示所有檔案**」按鈕,查看*出/生成/\<配置>* 資料夾中的所有 CMake 生成的輸出。

可視化工作室使用名為 **「CMakeSettings.json」的**配置檔。 此檔允許您定義和存儲多個生成配置,並在 IDE 中方便地在它們之間進行切換。 *配置*是可視化工作室構造,用於封裝特定於給定生成類型的設置。 這些設置用於設定 Visual Studio 傳遞給 cmake.exe 的預設命令列選項。 您還可以在此處指定其他 CMake 選項,並定義您喜歡的任何其他變數。 所有選項都作為內部變數或外部變數寫入 CMake 快取。 在 Visual Studio 2019 中 **,CMake 設置編輯器**提供了一種編輯設置的便捷方式。 有關詳細資訊,請參閱[自訂"自訂造拍"設定](customize-cmake-settings.md)。

一個設置`intelliSenseMode`不會傳遞到「單行」,但僅由 Visual Studio 使用。

在每個項目資料夾中使用**CMakelists.txt**檔,就像在任何 CMake 專案中一樣。 您可以指定源檔、尋找庫、設定編譯器和連結器選項以及指定其他生成系統相關資訊。

要在調試時將參數傳遞給可執行檔,可以使用另一個稱為**launch.vs.json**的檔。 在某些情況下,Visual Studio 會自動生成這些檔。 您可以手動編輯它們,甚至可以自己創建檔。

> [!NOTE]
> 對其他類型的開啟資料夾專案,使用另外兩個 JSON 檔 **:CppProperties.json**與**工作.vs.json**。 它們都和 CMake 專案不相關。

## <a name="open-an-existing-cache"></a>開啟現有快取

當您打開現有的 CMake 快取檔案 (*CMakeCache.txt*) 時,Visual Studio 不會嘗試管理緩存並為您建構樹。 您的自定義或首選工具可以完全控制 CMake 如何配置專案。 要在可視化工作室中打開現有緩存,請選擇 **"檔>打開>"製作**"。 然後,導航到現有的*CMakeCache.txt*檔。

您可以將現有的 CMake 快取到打開的專案。 它所做的方式與添加新配置的方式相同。 有關詳細資訊,請參閱我們在 Visual Studio[中打開現有緩存的](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)部落格文章。

## <a name="building-cmake-projects"></a>建置 CMake 專案

若要建置 CMake 專案，您有下列選項：

1. 在「一般」工具列中,尋找 **「設定」** 下拉清單。 默認情況下,它可能顯示「x64 調試」。 選擇首選設定並按**F5**,或按一下工具列上的**執行**(綠色三角形)」。 專案會先自動建置，如同 Visual Studio 方案一樣。

1. 右鍵按下*CMakelists.txt,* 然後從上下文選單中選擇 **「生成**」 。。 如果您的資料夾結構中有多個目標，您可以選擇全部建置或只建置一個特定目標。

1. 從主選單中,選擇 **「生成>全部構建****(F7**或**Ctrl_Shift_B**)。 確定已在 [一般]**** 工具列的 [啟動項目]**** 下拉式清單中選取 CMake 目標。

![CMake 產生選單指令](media/cmake-build-menu.png "CMake 產生指令選單")

如您所預期，建置結果會顯示在 [輸出]**** 視窗和 [錯誤清單]**** 中。

![CMake 產生錯誤](media/cmake-build-errors.png "CMake 產生錯誤")

在具有多個生成目標的資料夾中,可以指定要構建的 CMake 目標:在 **「CMake」** 選單或*CMakelists.txt*上下文選單中選擇**生成**項以指定目標。 如果在 CMake 專案中輸入**Ctrl_Shift_B,** 它將生成當前活動文檔。

## <a name="debugging-cmake-projects"></a>偵錯 CMake 專案

要除錯 CMake 專案,請選擇首選設定並按**F5**,或按工具列中的 **「執行」** 按鈕。 如果 **「運行」** 按鈕顯示「選擇啟動專案」,請選擇下拉箭頭。 選擇要運行的目標。 (在 CMake 專案中，[目前文件] 選項僅適用於 .cpp 檔案。)

![CMake 執行按鈕](media/cmake-run-button.png "CMake 執行按鈕")

如果自上次建置以來已有所變更，[執行]**** 或 **F5** 命令會先建置專案。 對 *「CMakeSettings.json」的*更改會導致重新生成 CMake 緩存。

您可以透過在**啟動.vs.json**檔中設定屬性來自定義 CMake 除錯工作階段。 如需詳細資訊，請參閱[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)。

## <a name="just-my-code-for-cmake-projects"></a>只為我的代碼為 CMake 專案

當您使用 MSVC 編譯器為 Windows 生成時,CMake 專案支援僅使用「我的代碼」調試。 要變更「僅我的代碼」設定,請轉到**工具** > **選項** > **除錯** > **一般**。

## <a name="vcpkg-integration"></a>Vcpkg 整合

如果您安裝了[vcpkg,](vcpkg.md)在 Visual Studio 中打開的 CMake 專案會自動整合 vcpkg 工具鏈檔。 這意味著無需額外配置即可將 vcpkg 用於您的 CMake 專案。 此支援適用於您定位的遠端系統上的本地 vcpkg 安裝和 vcpkg 安裝。 當您在"CMake 設置"配置中指定任何其他工具鏈時,將自動禁用此行為。

## <a name="customize-configuration-feedback"></a>自訂設定回饋

預設情況下,除非出現錯誤,否則將禁止大多數配置消息。 通過在**工具** > **選項** > **CMake**中啟用此功能,可以查看所有消息。

   ![設定 CMake 診斷選項](media/vs2019-cmake-configure-options.png "CMake 診斷選項")

## <a name="editing-cmakeliststxt-files"></a>編輯 CMakeLists.txt 檔案

要編輯*CMakelists.txt*檔案,請右鍵單擊**解決方案資源管理員**中的檔案並選擇 **「打開**」。 如果對文件進行更改,將顯示一個黃色狀態列,並通知您 IntelliSense 將更新。 它為您提供了取消更新操作的機會。 有關*CMakelists.txt*的資訊,請參考[CMake 文件](https://cmake.org/documentation/)。

   ![CMakelists.txt 檔案編輯](media/cmake-cmakelists.png "CMakelists.txt 檔案編輯")

一旦您儲存檔案，設定步驟會自動再次執行，並在 [輸出]**** 視窗中顯示資訊。 錯誤和警告會顯示在 [錯誤清單]**** 或 [輸出]**** 視窗中。 按兩下**錯誤清單中**的錯誤,以導航到*CMakelist.txt*中的違規行。

   ![CMakelists.txt 檔案錯誤](media/cmake-cmakelists-error.png "CMakelists.txt 檔案錯誤")

## <a name="cmake-configure-step"></a>CMake 設定步驟

當您對*CMakeSettings.json*或*CMakelists.txt*檔進行重大更改時,Visual Studio 會自動重新運行「CMake 設定」步驟。 如果配置步驟完成且沒有錯誤,則收集的資訊可在 C++ IntelliSense 和語言服務中提供。 它還用於生成和調試操作。

## <a name="troubleshooting-cmake-cache-errors"></a>針對 CMake 快取錯誤進行疑難排解

如果您需要有關 CMake 快取狀態的詳細資訊來診斷問題,在**解決方案資源管理員**中開啟**專案**主選單或*CMakelists.txt*上下文選單以執行以下指令之一:

- **檢視快取**從編輯器中的生成根資料夾中開啟*CMakeCache.txt*檔案。 (如果您清理快取,您在此處對*CMakeCache.txt*進行的任何編輯都會被擦除。 要進行在清理緩存後仍然存在的變更,請參閱自訂[CMake 設定](customize-cmake-settings.md)。

- [開啟快取資料夾]**** 會將檔案總管視窗開啟至組建根資料夾。

- [清除快取]**** 會刪除組建根資料夾，讓後續 CMake 設定步驟從全新的快取開始。

- 即使 Visual Studio 認為環境是最新的,**生成緩存**也會強制生成步驟運行。

可以在 **「工具>選項>常規**對話框中禁用自動快取生成>一般對話框。

## <a name="run-cmake-from-the-command-line"></a>從命令列執行 CMake

如果您已從 Visual Studio 安裝程式安裝 CMake，則可以遵循下列步驟從命令列執行：

1. 執行適當的 vsdevcmd.bat (x86/x64)。 有關詳細資訊,請參閱[在命令列上建構](building-on-the-command-line.md)。

1. 切換至您的輸出資料夾。

1. 執行 CMake 以建置/設定您的應用程式。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 對 CMake 有豐富的支援,包括[跨平臺的 CMake 專案](../linux/cmake-linux-project.md)。 用於**CMake 元件的可視化 C++工具**使用 **「打開資料夾」** 功能,使 IDE 能夠直接使用 CMake 專案檔(如*CMakelists.txt),* 用於智慧感知和瀏覽。 支援 Ninja 和 Visual Studio 產生器。 如果使用 Visual Studio 生成器,它將生成一個臨時專案檔並將其傳遞給 msbuild.exe。 但是,該項目永遠不會載入用於 IntelliSense 或流覽目的。 您還可以導入現有的 CMake 緩存。

## <a name="installation"></a>安裝

**以 CMake 的視覺化C++工具**作為桌面開發的一部分安裝 **,具有C++工作負載C++** 和**Linux 開發**。

![C++ 桌面工作負載中的 CMake 元件](media/cmake-install.png)

如需詳細資訊，請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 整合

當您選擇 **「打開>資料夾>打開**包含*CMakelists.txt*檔案的資料夾時,會發生以下情況:

- Visual Studio 會將 [CMake]**** 功能表項目新增至主功能表，並提供檢視和編輯 CMake 指令碼的命令。

- [方案總管]**** 會顯示資料夾結構和檔案。

- Visual Studio 會執行 CMake.exe，並選擇性為預設「組態」**(即 x86 偵錯) 產生 CMake 快取。 CMake 命令列會連同 CMake 的其他輸出一起顯示在 [輸出]**** 視窗中。

- Visual Studio 會在背景開始編製原始程式檔的索引，以啟用 IntelliSense、瀏覽資訊、重構等。 Visual Studio 會在您工作時，監視編輯器和磁碟上的變更，以確保其索引與來源同步。

您可以開啟包含任意數目之 CMake 專案的資料夾。 Visual Studio 檢測並配置工作區中的所有"根 *"CMakelists.txt*檔。 CMake 操作(配置、生成、除錯)、C++ IntelliSense 和瀏覽都可用於工作區中的所有 CMake 專案。

![具有多個根檔案的 CMake 專案](media/cmake-multiple-roots.png)

您也可以檢視依目標以邏輯方式組織的專案。 從 [方案總管]**** 工具列的下拉式清單中選擇 [Targets View] \(目標檢視\)****：

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png)

Visual Studio 使用名為*CMakeSettings.json*的檔案來儲存 Cmake.exe 的環境變數或命令列選項。 *CMakeSettings.json*還使您能夠定義和存儲多個 CMake 生成配置。 您可以在 IDE 中方便地在它們之間進行切換。

否則,使用*CMakelists.txt,* 就像在任何 CMake 專案中一樣,指定源檔、尋找庫、設定編譯器和連結器選項以及指定其他與生成系統相關的資訊。

如果需要在調試時將參數傳遞給可執行檔,則可以使用另一個稱為 **"啟動.vs.json"** 的檔。 在某些情況下,Visual Studio 會自動生成這些檔。 您可以手動編輯它們,甚至可以自己創建檔。

> [!NOTE]
> 對其他類型的開啟資料夾專案,使用另外兩個 JSON 檔 **:CppProperties.json**與**工作.vs.json**。 它們都和 CMake 專案不相關。

## <a name="import-an-existing-cache"></a>匯入現有的快取

匯入現有*CMakeCache.txt*檔時,Visual Studio 會自動提取自定義變數,並根據這些變數創建預填充的*CMakeSettings.json*檔。 原始緩存不會以任何方式修改。 它仍然可以從命令行使用,也可以與用於生成它的任何工具或IDE一起使用。 新的*CMakeSettings.json*檔與專案的根*CdMakelists.txt*放在一起。 Visual Studio 會根據設定檔產生新的快取。 您可以在 **「工具>選項>常規對話框中**覆蓋自動快取產生>一般對話框。

快取中的所有項目不會全部匯入。  產生器和編譯器位置等屬性會取代成已知適用於 IDE 的預設值。

### <a name="to-import-an-existing-cache"></a>匯入現有的快取

1. 從主選單中選擇 **「檔案>打開>」::**

   ![開啟 CMake](media/cmake-file-open.png "檔案, 開啟, 製作")

   此命令將啟動 **「從快取導入 CMake」** 精靈。

2. 導航到要導入的*CMakeCache.txt*檔,然後單擊 **"確定**"。 [從快取匯入 CMake 專案精靈]**** 隨即出現：

   ![匯入 CMake 快取](media/cmake-import-wizard.png "開啟 CMake 匯入快取精靈")

   嚮導完成後,您可以在**解決方案資源管理員**中看到專案中根*CMakelists.txt*檔旁邊的新的*CMakeCache.txt*檔。

## <a name="building-cmake-projects"></a>建置 CMake 專案

若要建置 CMake 專案，您有下列選項：

1. 在「一般」工具列中,尋找 **「設定」** 下拉清單。 默認情況下,它可能顯示"Linux 調試"或"x64 調試"。 選擇首選設定並按**F5**,或按一下工具列上的**執行**(綠色三角形)」。 專案會先自動建置，如同 Visual Studio 方案一樣。

1. 右鍵按下 *「CMakelists.txt」* 並從上下文選單中選擇 **「生成**」 。。 如果您的資料夾結構中有多個目標，您可以選擇全部建置或只建置一個特定目標。

1. 從主選單中,選擇 **「構建>構建解決方案****(F7**或**Ctrl_Shift_B**)。 確定已在 [一般]**** 工具列的 [啟動項目]**** 下拉式清單中選取 CMake 目標。

![CMake 產生選單指令](media/cmake-build-menu.png "CMake 產生指令選單")

您可以在*CMakeSettings.json*檔中自定義生成配置、環境變數、命令列參數和其他設置。 它允許您在不修改*CMakelists.txt*檔案的情況下進行更改。 有關詳細資訊,請參閱[自訂"自訂造拍"設定](customize-cmake-settings.md)。

如您所預期，建置結果會顯示在 [輸出]**** 視窗和 [錯誤清單]**** 中。

![CMake 產生錯誤](media/cmake-build-errors.png "CMake 產生錯誤")

在具有多個生成目標的資料夾中,可以指定要構建的 CMake 目標:在 **「CMake」** 選單或*CMakelists.txt*上下文選單中選擇**生成**項以指定目標。 如果在 CMake 專案中輸入**Ctrl_Shift_B,** 它將生成當前活動文檔。

## <a name="debugging-cmake-projects"></a>偵錯 CMake 專案

要除錯 CMake 專案,請選擇首選設定,然後按**F5**。 或者,按工具列中的 **「運行」** 按鈕。 如果 [執行]**** 按鈕顯示 [選取啟動項目]，請選取下拉式箭頭並選擇您要執行的目標。 (在 CMake 專案中，[目前文件] 選項僅適用於 .cpp 檔案。)

![CMake 執行按鈕](media/cmake-run-button.png "CMake 執行按鈕")

如果自上次建置以來已有所變更，[執行]**** 或 **F5** 命令會先建置專案。

您可以透過在**啟動.vs.json**檔中設定屬性來自定義 CMake 除錯工作階段。 如需詳細資訊，請參閱[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)。

## <a name="editing-cmakeliststxt-files"></a>編輯 CMakeLists.txt 檔案

要編輯*CMakelists.txt*檔案,請右鍵單擊**解決方案資源管理員**中的檔案並選擇 **「打開**」。 如果對文件進行更改,將顯示一個黃色狀態列,並通知您 IntelliSense 將更新。 它為您提供了取消更新操作的機會。 有關*CMakelists.txt*的資訊,請參考[CMake 文件](https://cmake.org/documentation/)。

   ![CMakelists.txt 檔案編輯](media/cmake-cmakelists.png "CMakelists.txt 檔案編輯")

一旦您儲存檔案，設定步驟會自動再次執行，並在 [輸出]**** 視窗中顯示資訊。 錯誤和警告會顯示在 [錯誤清單]**** 或 [輸出]**** 視窗中。 按兩下**錯誤清單中**的錯誤,以導航到*CMakelist.txt*中的違規行。

   ![CMakelists.txt 檔案錯誤](media/cmake-cmakelists-error.png "CMakelists.txt 檔案錯誤")

## <a name="cmake-configure-step"></a>CMake 設定步驟

當對*CMakeSettings.json*或*CMakelists.txt*檔進行重大更改時,Visual Studio 會自動重新運行「CMake 配置」步驟。 如果配置步驟完成且沒有錯誤,則收集的資訊可在 C++ IntelliSense 和語言服務中提供。 它還用於生成和調試操作。

多個 CMake 專案可能使用相同的 CMake 設定名稱(例如,x86-Debug)。 選擇配置時,將配置和生成所有這些配置(在自己的生成根資料夾中)。 您可以從所有參與該 CMake 組態的 CMake 專案偵錯目標。

   ![只有製作「僅產生」選單項目](media/cmake-build-only.png "只有製作「僅產生」選單項目")

您可以將生成和調試會話限制為工作區中專案的子集。 在*CMakeSettings.json*檔中建立具有唯一名稱的新配置。 然後,僅將配置應用於這些專案。 選擇該配置後,IntelliSense 和生成和調試命令僅適用於這些指定的專案。

## <a name="troubleshooting-cmake-cache-errors"></a>針對 CMake 快取錯誤進行疑難排解

如果您需要 CMake 快取狀態的詳細資訊以診斷問題，請開啟 [CMake]**** 主功能表，或在 [方案總管]**** 中開啟 [CMakeLists.txt]** 操作功能表，執行下列其中一個命令：

- **檢視快取**從編輯器中的生成根資料夾中開啟*CMakeCache.txt*檔案。 (如果您清理快取,您在此處對*CMakeCache.txt*進行的任何編輯都會被擦除。 要進行在清理緩存後仍然存在的變更,請參閱自訂[CMake 設定](customize-cmake-settings.md)。

- [開啟快取資料夾]**** 會將檔案總管視窗開啟至組建根資料夾。

- [清除快取]**** 會刪除組建根資料夾，讓後續 CMake 設定步驟從全新的快取開始。

- 即使 Visual Studio 認為環境是最新的,**生成緩存**也會強制生成步驟運行。

可以在 **「工具>選項>常規**對話框中禁用自動快取生成>一般對話框。

## <a name="single-file-compilation"></a>單一檔案編譯

要在 CMake 專案中生成單個檔,請右鍵單擊**解決方案資源管理器**中的檔。 從彈出式功能表中選擇 **「編譯**」。 您還可以使用主**CMake**選單在編輯器中產生目前開啟的檔案:

![CMake 單一檔案編譯](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>從命令列執行 CMake

如果您已從 Visual Studio 安裝程式安裝 CMake，則可以遵循下列步驟從命令列執行：

1. 執行適當的 vsdevcmd.bat (x86/x64)。 有關詳細資訊,請參閱[在命令列上建構](building-on-the-command-line.md)。

1. 切換至您的輸出資料夾。

1. 執行 CMake 以建置/設定您的應用程式。

::: moniker-end

::: moniker range="vs-2015"

在 Visual Studio 2015 中，Visual Studio 使用者可以使用 [CMake 產生器](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)來產生 MSBuild 專案檔，再由 IDE 取用這些檔案供 IntelliSense、瀏覽和編譯之用。

::: moniker-end

## <a name="see-also"></a>另請參閱

[教程:在可視化工作室創建C++跨平台專案](get-started-linux-cmake.md)\
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)\
[連接到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)\
[自訂「製作」構建設定](customize-cmake-settings.md)\
[CMakeSettings.json 架構引用](cmakesettings-reference.md)\
[設定「製作」除錯工作階段](configure-cmake-debugging-sessions.md)\
[部署、執行及除錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)
