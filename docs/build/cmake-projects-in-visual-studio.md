---
title: Visual Studio 中的 CMake 專案
description: 如何在 Visual Studio 中使用 CMake 來建立和建立 c + + 專案。
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

CMake 是可在多個平台上執行之定義建置程序的跨平台開放原始碼工具。 本文假設您已經熟悉 CMake。 您可以在[使用 CMake 建置、測試和封裝您的軟體](https://cmake.org/)中深入了解它。

> [!NOTE]
> CMake 在過去幾個版本中已變得越來越整合 Visual Studio。 若要查看您慣用版本 Visual Studio 的檔，請使用**版本**選取器控制項。 您可在此頁面的目錄頂端找到該檔案。

::: moniker range="vs-2019"

適用于**Windows 的 c + + CMake 工具**元件會使用 [[開啟資料夾](open-folder-projects-cpp.md)] 功能，直接取用 CMake 專案檔（例如*remote monitoring.h cmakelists.txt .Txt*），以供 IntelliSense 和流覽之用。 支援 Ninja 和 Visual Studio 產生器。 如果您使用 Visual Studio 產生器，它會產生臨時專案檔，並將它傳遞至 msbuild.exe。 不過，基於 IntelliSense 或流覽目的，永遠不會載入專案。 您也可以匯入現有的 CMake 快取。

## <a name="installation"></a>安裝

**適用于 Windows 的 c + + CMake 工具**是在**使用 c + + 進行桌面開發**和 c + + 工作負載的**Linux 開發**中安裝的一部分。 如需詳細資訊，請參閱[跨平臺 CMake 專案](../linux/cmake-linux-project.md)。

![C++ 桌面工作負載中的 CMake 元件](media/cmake-install-2019.png)

如需詳細資訊，請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 整合

當您選擇 [檔案] **> 開啟 > 資料夾**來開啟包含*remote monitoring.h cmakelists.txt*檔案的資料夾時，會發生下列情況：

- Visual Studio 會將**CMake**專案新增至 [**專案**] 功能表，以及用來查看和編輯 CMake 腳本的命令。

- [方案總管]**** 會顯示資料夾結構和檔案。

- Visual Studio 會執行 cmake，並產生預設（x64 Debug）設定的 CMake 快取檔案（*cmakecache.txt .txt*）。 CMake 命令列會連同 CMake 的其他輸出一起顯示在 [輸出]**** 視窗中。

- Visual Studio 會在背景開始編製原始程式檔的索引，以啟用 IntelliSense、瀏覽資訊、重構等。 Visual Studio 會在您工作時，監視編輯器和磁碟上的變更，以確保其索引與來源同步。

您可以開啟包含任意數目之 CMake 專案的資料夾。 Visual Studio 會偵測並設定您工作區中的所有 "root" *remote monitoring.h cmakelists.txt*檔案。 您工作區中的所有 CMake 專案都可以使用 CMake 作業（[設定]、[組建]、[偵錯工具]、c + + IntelliSense 和流覽）。

![具有多個根檔案的 CMake 專案](media/cmake-multiple-roots.png)

您也可以檢視依目標以邏輯方式組織的專案。 從 [方案總管]**** 工具列的下拉式清單中選擇 [Targets View] \(目標檢視\)****：

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png)

按一下**方案總管**頂端的 [**顯示所有**檔案] 按鈕，以查看*out/build\</config>* 資料夾中所有 CMake 產生的輸出。

Visual Studio 使用名為**CMakeSettings**的設定檔。 此檔案可讓您定義和儲存多個組建設定，並在 IDE 中方便地進行切換。 設定*是一種 Visual Studio*結構，可封裝特定組建類型專屬的設定。 這些設定可用來設定 Visual Studio 傳遞至 cmake 的預設命令列選項。 您也可以在這裡指定其他 CMake 選項，並定義任何您想要的其他變數。 所有選項都是以內部或外部變數的形式寫入至 CMake 快取。 在 Visual Studio 2019 中，[ **CMake 設定編輯器**] 提供一個方便的方式來編輯您的設定。 如需詳細資訊，請參閱[自訂 CMake 設定](customize-cmake-settings.md)。

其中一個設定`intelliSenseMode`不會傳遞至 CMake，但只能由 Visual Studio 使用。

在每個專案資料夾中使用**remote monitoring.h cmakelists.txt** ，就像在任何 CMake 專案中一樣。 您可以指定來源檔案、尋找程式庫、設定編譯器和連結器選項，以及指定其他組建系統相關資訊。

若要在偵錯工具時將引數傳遞至可執行檔，您可以使用另一個名為 [**啟動] 的**檔案。 在某些情況下，Visual Studio 會自動產生這些檔案。 您可以手動進行編輯，或甚至自行建立檔案。

> [!NOTE]
> 針對其他類型的開啟資料夾專案，會使用兩個額外的 JSON 檔案： **CppProperties**和工作 **。 vs. json**。 它們都和 CMake 專案不相關。

## <a name="open-an-existing-cache"></a>開啟現有的快取

當您開啟現有的 CMake 快取檔案（*cmakecache.txt .txt*）時，Visual Studio 不會嘗試為您管理快取和組建樹狀結構。 您的自訂或慣用工具可以完整控制 CMake 如何設定您的專案。 若要在 Visual Studio 中開啟現有的快取，請選擇 [檔案] **> 開啟 > CMake**]。 然後，流覽至現有的*cmakecache.txt*檔案。

您可以將現有的 CMake 快取加入至開啟的專案。 其做法與新增設定的方式相同。 如需詳細資訊，請參閱我們在[Visual Studio 中開啟現有](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)快取的 blog 文章。

## <a name="building-cmake-projects"></a>建置 CMake 專案

若要建置 CMake 專案，您有下列選項：

1. 在 [**一般] 工具列中，尋找**[設定] 下拉式清單。 根據預設，它可能會顯示「x64-Debug」。 選取慣用的設定並按**F5**，或按一下工具列上的 [**執行**] （綠色三角形）按鈕。 專案會先自動建置，如同 Visual Studio 方案一樣。

1. 以滑鼠右鍵按一下 [ *remote monitoring.h cmakelists.txt* ]，然後從內容功能表中選取 [**組建**]。 如果您的資料夾結構中有多個目標，您可以選擇全部建置或只建置一個特定目標。

1. 從主功能表中，選取 [**組建] > [全部建立**] （**F7**或**Ctrl + Shift + B**）。 確定已在 [一般]**** 工具列的 [啟動項目]**** 下拉式清單中選取 CMake 目標。

![CMake 組建功能表命令](media/cmake-build-menu.png "CMake build 命令功能表")

如您所預期，建置結果會顯示在 [輸出]**** 視窗和 [錯誤清單]**** 中。

![CMake 組建錯誤](media/cmake-build-errors.png "CMake 組建錯誤")

在具有多個組建目標的資料夾中，您可以指定要建立的 CMake 目標：選擇 [ **CMake** ] 功能表上的 [**組建**] 專案或 [ *remote monitoring.h cmakelists.txt* ] 內容功能表，以指定目標。 如果您在 CMake 專案中輸入**Ctrl + Shift + B** ，它會建立目前的使用中檔。

## <a name="debugging-cmake-projects"></a>偵錯 CMake 專案

若要 debug CMake 專案，請選擇慣用的設定，然後按**F5**鍵，或按工具列中的 [**執行**] 按鈕。 如果 [**執行**] 按鈕顯示 [選取啟動專案]，請選取下拉箭號。 選擇您想要執行的目標。 (在 CMake 專案中，[目前文件] 選項僅適用於 .cpp 檔案。)

![CMake 執行按鈕](media/cmake-run-button.png "CMake 執行按鈕")

如果自上次建置以來已有所變更，[執行]**** 或 **F5** 命令會先建置專案。 對*CMakeSettings*所做的變更會導致重新產生 CMake 快取。

您可以藉由設定 [**啟動]. vs. json**檔案中的屬性來自訂 CMake 的偵錯工具會話。 如需詳細資訊，請參閱[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)。

## <a name="just-my-code-for-cmake-projects"></a>CMake 專案的 Just My Code

當您使用 MSVC 編譯器為 Windows 建立時，CMake projects 支援 Just My Code 的偵錯工具。 若要變更 Just My Code 設定，請移至 [**工具** > ] [**選項** > ] [**調試** > **一般**]。

## <a name="vcpkg-integration"></a>Vcpkg 整合

如果您已安裝[vcpkg](vcpkg.md)，在 Visual Studio 中開啟的 CMake 專案會自動整合 vcpkg 工具鏈檔。 這表示不需要進行其他設定，就能將 vcpkg 與您的 CMake 專案搭配使用。 這項支援適用于您所設為目標的遠端系統上的本機 vcpkg 安裝和 vcpkg 安裝。 當您在 CMake Settings 設定中指定任何其他工具鏈時，會自動停用此行為。

## <a name="customize-configuration-feedback"></a>自訂設定意見反應

根據預設，除非發生錯誤，否則會隱藏大部分的設定訊息。 您可以在 [**工具** > ] [**選項** > ]**CMake**中啟用此功能，以查看所有訊息。

   ![設定 CMake 診斷選項](media/vs2019-cmake-configure-options.png "CMake 診斷選項")

## <a name="editing-cmakeliststxt-files"></a>編輯 CMakeLists.txt 檔案

若要編輯*remote monitoring.h cmakelists.txt .txt*檔案，請在**方案總管**中的檔案上按一下滑鼠右鍵，然後選擇 [**開啟**]。 如果您對檔案進行變更，系統會顯示黃色的狀態列，並通知您 IntelliSense 將會更新。 這可讓您有機會取消更新作業。 如需有關*remote monitoring.h cmakelists.txt*的詳細資訊，請參閱[CMake 檔](https://cmake.org/documentation/)。

   ![Remote monitoring.h cmakelists.txt .txt 檔案編輯](media/cmake-cmakelists.png "Remote monitoring.h cmakelists.txt .txt 檔案編輯")

一旦您儲存檔案，設定步驟會自動再次執行，並在 [輸出]**** 視窗中顯示資訊。 錯誤和警告會顯示在 [錯誤清單]**** 或 [輸出]**** 視窗中。 按兩下 [**錯誤清單**中的錯誤，以流覽至*remote monitoring.h cmakelists.txt*中的問題行。

   ![Remote monitoring.h cmakelists.txt .txt 檔錯誤](media/cmake-cmakelists-error.png "Remote monitoring.h cmakelists.txt .txt 檔錯誤")

## <a name="cmake-configure-step"></a>CMake 設定步驟

當您對*CMakeSettings*進行重大變更或*remote monitoring.h cmakelists.txt .txt*檔案時，Visual Studio 會自動重新執行 CMake 設定步驟。 如果設定步驟完成且沒有錯誤，則會在 c + + IntelliSense 和語言服務中提供所收集的資訊。 它也會用於組建和偵錯工具作業。

## <a name="troubleshooting-cmake-cache-errors"></a>針對 CMake 快取錯誤進行疑難排解

如果您需要 CMake 快取狀態的詳細資訊來診斷問題，請開啟 [**專案**] 主功能表或**方案總管**中的 [ *remote monitoring.h cmakelists.txt* ] 操作功能表，以執行下列其中一個命令：

- **View Cache**會從編輯器中的組建根資料夾開啟*cmakecache.txt。* （如果您清除快取，則會清除您在此處對*cmakecache.txt*所做的任何編輯。 若要在清除快取之後進行變更，請參閱[自訂 CMake 設定](customize-cmake-settings.md)）。

- [開啟快取資料夾]**** 會將檔案總管視窗開啟至組建根資料夾。

- [清除快取]**** 會刪除組建根資料夾，讓後續 CMake 設定步驟從全新的快取開始。

- [**產生**快取] 會強制執行 [產生] 步驟，即使 Visual Studio 將環境視為最新狀態也一樣。

可以在 [工具] [ **> 選項] [> CMake] > [一般**] 對話方塊中停用自動快取產生。

## <a name="run-cmake-from-the-command-line"></a>從命令列執行 CMake

如果您已從 Visual Studio 安裝程式安裝 CMake，則可以遵循下列步驟從命令列執行：

1. 執行適當的 vsdevcmd.bat (x86/x64)。 如需詳細資訊，請參閱在[命令列上建立](building-on-the-command-line.md)。

1. 切換至您的輸出資料夾。

1. 執行 CMake 以建置/設定您的應用程式。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 對 CMake 有豐富的支援，包括[跨平臺 CMake 專案](../linux/cmake-linux-project.md)。 **Visual C++ Tools For CMake**元件會使用 [**開啟資料夾**] 功能，讓 IDE 直接取用 CMake 專案檔（例如*remote monitoring.h cmakelists.txt .Txt*），以供 IntelliSense 和流覽之用。 支援 Ninja 和 Visual Studio 產生器。 如果您使用 Visual Studio 產生器，它會產生臨時專案檔，並將它傳遞至 msbuild.exe。 不過，基於 IntelliSense 或流覽目的，永遠不會載入專案。 您也可以匯入現有的 CMake 快取。

## <a name="installation"></a>安裝

**適用于 CMake 的 Visual C++ 工具**會隨著使用 c **+ + 進行桌面開發**和**c + + 的 Linux 開發**工作負載一起安裝。

![C++ 桌面工作負載中的 CMake 元件](media/cmake-install.png)

如需詳細資訊，請參閱[在 Visual Studio 中安裝 C++ Linux 工作負載](../linux/download-install-and-setup-the-linux-development-workload.md)。

## <a name="ide-integration"></a>IDE 整合

當您選擇 [檔案] **> 開啟 > 資料夾**來開啟包含*remote monitoring.h cmakelists.txt*檔案的資料夾時，會發生下列情況：

- Visual Studio 會將 [CMake]**** 功能表項目新增至主功能表，並提供檢視和編輯 CMake 指令碼的命令。

- [方案總管]**** 會顯示資料夾結構和檔案。

- Visual Studio 會執行 CMake.exe，並選擇性為預設「組態」**(即 x86 偵錯) 產生 CMake 快取。 CMake 命令列會連同 CMake 的其他輸出一起顯示在 [輸出]**** 視窗中。

- Visual Studio 會在背景開始編製原始程式檔的索引，以啟用 IntelliSense、瀏覽資訊、重構等。 Visual Studio 會在您工作時，監視編輯器和磁碟上的變更，以確保其索引與來源同步。

您可以開啟包含任意數目之 CMake 專案的資料夾。 Visual Studio 會偵測並設定您工作區中的所有 "root" *remote monitoring.h cmakelists.txt*檔案。 您工作區中的所有 CMake 專案都可以使用 CMake 作業（[設定]、[組建]、[偵錯工具]、c + + IntelliSense 和流覽）。

![具有多個根檔案的 CMake 專案](media/cmake-multiple-roots.png)

您也可以檢視依目標以邏輯方式組織的專案。 從 [方案總管]**** 工具列的下拉式清單中選擇 [Targets View] \(目標檢視\)****：

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png)

Visual Studio 使用名為*CMakeSettings*的檔案來儲存 Cmake 的環境變數或命令列選項。 *CMakeSettings*也可讓您定義和儲存多個 CMake 組建設定。 您可以在 IDE 中輕鬆切換它們。

否則，請使用*remote monitoring.h cmakelists.txt* ，如同您在任何 CMake 專案中指定來源檔案、尋找程式庫、設定編譯器和連結器選項，以及指定其他組建系統相關資訊。

如果您需要在執行偵錯工具時，將引數傳遞至可執行檔，您可以使用另一個名為 [**啟動. 與 json**] 的檔案。 在某些情況下，Visual Studio 會自動產生這些檔案。 您可以手動進行編輯，或甚至自行建立檔案。

> [!NOTE]
> 針對其他類型的開啟資料夾專案，會使用兩個額外的 JSON 檔案： **CppProperties**和工作 **。 vs. json**。 它們都和 CMake 專案不相關。

## <a name="import-an-existing-cache"></a>匯入現有的快取

當您匯入現有的*cmakecache.txt*檔案時，Visual Studio 會自動解壓縮自訂的變數，並根據這些變數建立預先填入的*CMakeSettings。* 原始快取不會以任何方式修改。 您仍然可以從命令列使用它，或使用任何用來產生它的工具或 IDE。 新的*CMakeSettings*會與專案的根*remote monitoring.h cmakelists.txt*放在一起。 Visual Studio 會根據設定檔產生新的快取。 您可以在 [工具] [ **> 選項] > CMake > [一般**] 對話方塊中，覆寫自動快取產生。

快取中的所有項目不會全部匯入。  產生器和編譯器位置等屬性會取代成已知適用於 IDE 的預設值。

### <a name="to-import-an-existing-cache"></a>匯入現有的快取

1. 從主功能表中，選擇 [檔案] **> 開啟 > CMake**：

   ![開啟 CMake](media/cmake-file-open.png "File、Open、CMake")

   此命令會從快取 wizard 開啟 [匯**入 CMake** ]。

2. 流覽至您要匯入的*cmakecache.txt .txt*檔案，然後按一下 **[確定]**。 [從快取匯入 CMake 專案精靈]**** 隨即出現：

   ![匯入 CMake 快取](media/cmake-import-wizard.png "開啟 CMake 匯入快取嚮導")

   當 wizard 完成時，您可以在專案的根*remote monitoring.h cmakelists.txt*檔案旁邊的**方案總管**中看到新的*cmakecache.txt .txt*檔案。

## <a name="building-cmake-projects"></a>建置 CMake 專案

若要建置 CMake 專案，您有下列選項：

1. 在 [**一般] 工具列中，尋找**[設定] 下拉式清單。 根據預設，它可能會顯示「Linux-Debug」或「x64-Debug」。 選取慣用的設定並按**F5**，或按一下工具列上的 [**執行**] （綠色三角形）按鈕。 專案會先自動建置，如同 Visual Studio 方案一樣。

1. 以滑鼠右鍵按一下 [ *remote monitoring.h cmakelists.txt* ]，然後從內容功能表中選取 [**組建**]。 如果您的資料夾結構中有多個目標，您可以選擇全部建置或只建置一個特定目標。

1. 從主功能表中，選取 [**組建] > [組建方案**] （**F7**或**Ctrl + Shift + B**）。 確定已在 [一般]**** 工具列的 [啟動項目]**** 下拉式清單中選取 CMake 目標。

![CMake 組建功能表命令](media/cmake-build-menu.png "CMake build 命令功能表")

您可以自訂群組建設定、環境變數、命令列引數，以及*CMakeSettings*中的其他設定。 它可讓您進行變更，而不需要修改*remote monitoring.h cmakelists.txt*檔案。 如需詳細資訊，請參閱[自訂 CMake 設定](customize-cmake-settings.md)。

如您所預期，建置結果會顯示在 [輸出]**** 視窗和 [錯誤清單]**** 中。

![CMake 組建錯誤](media/cmake-build-errors.png "CMake 組建錯誤")

在具有多個組建目標的資料夾中，您可以指定要建立的 CMake 目標：選擇 [ **CMake** ] 功能表上的 [**組建**] 專案或 [ *remote monitoring.h cmakelists.txt* ] 內容功能表，以指定目標。 如果您在 CMake 專案中輸入**Ctrl + Shift + B** ，它會建立目前的使用中檔。

## <a name="debugging-cmake-projects"></a>偵錯 CMake 專案

若要 debug CMake 專案，請選擇慣用的設定，然後按**F5**。 或者，按工具列中的 [**執行**] 按鈕。 如果 [執行]**** 按鈕顯示 [選取啟動項目]，請選取下拉式箭頭並選擇您要執行的目標。 (在 CMake 專案中，[目前文件] 選項僅適用於 .cpp 檔案。)

![CMake 執行按鈕](media/cmake-run-button.png "CMake 執行按鈕")

如果自上次建置以來已有所變更，[執行]**** 或 **F5** 命令會先建置專案。

您可以藉由設定 [**啟動]. vs. json**檔案中的屬性來自訂 CMake 的偵錯工具會話。 如需詳細資訊，請參閱[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)。

## <a name="editing-cmakeliststxt-files"></a>編輯 CMakeLists.txt 檔案

若要編輯*remote monitoring.h cmakelists.txt .txt*檔案，請在**方案總管**中的檔案上按一下滑鼠右鍵，然後選擇 [**開啟**]。 如果您對檔案進行變更，系統會顯示黃色的狀態列，並通知您 IntelliSense 將會更新。 這可讓您有機會取消更新作業。 如需有關*remote monitoring.h cmakelists.txt*的詳細資訊，請參閱[CMake 檔](https://cmake.org/documentation/)。

   ![Remote monitoring.h cmakelists.txt .txt 檔案編輯](media/cmake-cmakelists.png "Remote monitoring.h cmakelists.txt .txt 檔案編輯")

一旦您儲存檔案，設定步驟會自動再次執行，並在 [輸出]**** 視窗中顯示資訊。 錯誤和警告會顯示在 [錯誤清單]**** 或 [輸出]**** 視窗中。 按兩下 [**錯誤清單**中的錯誤，以流覽至*remote monitoring.h cmakelists.txt*中的問題行。

   ![Remote monitoring.h cmakelists.txt .txt 檔錯誤](media/cmake-cmakelists-error.png "Remote monitoring.h cmakelists.txt .txt 檔錯誤")

## <a name="cmake-configure-step"></a>CMake 設定步驟

對*CMakeSettings*進行重大變更或*remote monitoring.h cmakelists.txt .txt*檔案時，Visual Studio 會自動重新執行 CMake 設定步驟。 如果設定步驟完成且沒有錯誤，則會在 c + + IntelliSense 和語言服務中提供所收集的資訊。 它也會用於組建和偵錯工具作業。

多個 CMake 專案可能會使用相同的 CMake 設定名稱（例如，x86-Debug）。 當選取該設定時，所有這些專案都是在其專屬的組建根資料夾中進行設定和建立。 您可以從所有參與該 CMake 組態的 CMake 專案偵錯目標。

   ![CMake 僅限組建功能表項目](media/cmake-build-only.png "CMake 僅限組建功能表項目")

您可以將組建和 debug 會話限制為工作區中專案的子集。 在*CMakeSettings*中，使用唯一的名稱建立新的設定。 然後，只將設定套用至這些專案。 選取該設定時，IntelliSense 和 build 和 debug 命令僅適用于這些指定的專案。

## <a name="troubleshooting-cmake-cache-errors"></a>針對 CMake 快取錯誤進行疑難排解

如果您需要 CMake 快取狀態的詳細資訊以診斷問題，請開啟 [CMake]**** 主功能表，或在 [方案總管]**** 中開啟 [CMakeLists.txt]** 操作功能表，執行下列其中一個命令：

- **View Cache**會從編輯器中的組建根資料夾開啟*cmakecache.txt。* （如果您清除快取，則會清除您在此處對*cmakecache.txt*所做的任何編輯。 若要在清除快取之後進行變更，請參閱[自訂 CMake 設定](customize-cmake-settings.md)）。

- [開啟快取資料夾]**** 會將檔案總管視窗開啟至組建根資料夾。

- [清除快取]**** 會刪除組建根資料夾，讓後續 CMake 設定步驟從全新的快取開始。

- [**產生**快取] 會強制執行 [產生] 步驟，即使 Visual Studio 將環境視為最新狀態也一樣。

可以在 [工具] [ **> 選項] [> CMake] > [一般**] 對話方塊中停用自動快取產生。

## <a name="single-file-compilation"></a>單一檔案編譯

若要在 CMake 專案中建立單一檔案，請以滑鼠右鍵按一下**方案總管**中的檔案。 從快顯功能表中選擇 [**編譯**]。 您也可以使用主要的 [ **CMake** ] 功能表，在編輯器中建立目前開啟的檔案：

![CMake 單一檔案編譯](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>從命令列執行 CMake

如果您已從 Visual Studio 安裝程式安裝 CMake，則可以遵循下列步驟從命令列執行：

1. 執行適當的 vsdevcmd.bat (x86/x64)。 如需詳細資訊，請參閱在[命令列上建立](building-on-the-command-line.md)。

1. 切換至您的輸出資料夾。

1. 執行 CMake 以建置/設定您的應用程式。

::: moniker-end

::: moniker range="vs-2015"

在 Visual Studio 2015 中，Visual Studio 使用者可以使用 [CMake 產生器](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)來產生 MSBuild 專案檔，再由 IDE 取用這些檔案供 IntelliSense、瀏覽和編譯之用。

::: moniker-end

## <a name="see-also"></a>請參閱

[教學課程：在 Visual Studio 中建立 c + + 跨平臺專案](get-started-linux-cmake.md)\
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)\
[連接到您的遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)\
[自訂 CMake 組建設定](customize-cmake-settings.md)\
[CMakeSettings。 json 架構參考](cmakesettings-reference.md)\
[設定 CMake 的調試階段](configure-cmake-debugging-sessions.md)\
[部署、執行及偵錯工具您的 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)
