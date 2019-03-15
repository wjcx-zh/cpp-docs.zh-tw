---
title: 在 Visual Studio 中建立 c + + 跨平台專案
description: 本教學課程會示範如何設定、 編譯和偵錯在 Linux 和 Windows 為目標的 Visual Studio 中的 c + + 開放原始碼 CMake 專案。
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: deb2c91d6d09d8945e5eb57a7ac742c5b1705e83
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824724"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 c + + 跨平台專案 

Visual Studio C 和 c + + 開發不僅限於 Windows 再。 本教學課程會示範如何使用 c + + 的 Visual Studio 跨平台開發根據 CMake，而不需要建立或產生的 Visual Studio 專案。 當您開啟包含 CMakeLists.txt 檔案的資料夾時，Visual Studio 設定 IntelliSense 和組建自動。 您可以快速地被編輯、 建置和偵錯您的程式碼，Windows，在本機，然後您這麼做在 Linux 上，從 Visual Studio 內的組態。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 複製 GitHub 的開放原始碼 CMake 專案
> * 在 Visual Studio 中開啟專案 
> * 建置和偵錯在 Windows 上的可執行檔目標
> * 新增連線至 Linux 機器
> * 建置和偵錯在 Linux 上的相同目標

## <a name="prerequisites"></a>必要條件

- 跨平台 c + + 開發設定 Visual Studio
    - 首先您必須擁有[安裝 Visual Studio](https://visualstudio.microsoft.com/vs/)。 接下來，請確認您有**使用 c + + 的桌面開發**並**使用 c + + 工作負載的 Linux 開發**安裝。 此最小安裝只有 3 GB，根據您的下載速度安裝應該不需要超過 10 分鐘。
- 設定跨平台 c + + 開發的 Linux 機器
    - Visual Studio 並不需要任何特定 Linux 的配送。 Linux (WSL) 時，OS 可以實體機器，VM、 雲端，或 Windows 子系統上執行。 不過，本教學課程的圖形化的環境是必要的資訊;因此 WSL 也不建議，因為它主要供命令列作業。
    - Visual Studio 需要在 Linux 機器的工具包括：C + + 編譯器、 GDB，ssh，和 zip。 在 Debian 型系統上，您可以安裝這些相依性，如下所示。
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Visual Studio 需要 Linux 機器有具有伺服器模式啟用 (至少 3.8) CMake 的最新版本。 Microsoft 會產生 CMake，您可以在任何 Linux 散發版本上安裝的通用組建。 我們建議使用此組建以確保您擁有最新的功能。 您可以取得的 CMake 二進位檔[Microsoft CMake 存放庫的分支](https://github.com/Microsoft/CMake/releases)GitHub 上。 移至該頁面，並下載符合您系統架構，在您的 Linux 機器，然後將它標示為可執行檔的版本：
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - 您可以看到執行具有指令碼之選項的`-–help`。 我們建議您改用`–prefix`選項來指定在安裝 **/usr/local**路徑，因為這是 Visual Studio 的 CMake 的尋找位置的預設位置。 下列範例會顯示 Linux-x86_64 指令碼。 視需要變更，如果您使用不同的目標平台。 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Git for Windows 電腦上安裝 windows。
- GitHub 帳戶。

## <a name="clone-an-open-source-cmake-project-from-github"></a>複製 GitHub 的開放原始碼 CMake 專案

本教學課程會使用項目符號物理 SDK 在 GitHub 上，其會提供各種不同的應用程式中的碰撞偵測及物理模擬。 它包含的編譯和執行而不需要撰寫額外程式碼範例可執行程式。 本教學課程不會修改任何原始程式碼，或建置指令碼。 若要開始，複製 bullet3 存放庫從 GitHub 在電腦上的必須安裝 Visual Studio。 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. 從 Visual Studio 主功能表中，選擇**檔案 > 開啟 > CMake**並瀏覽至您剛才下載的 bullet3 存放庫的根目錄中 CMakeLists.txt 檔案。

    ![Visual Studio 功能表中的檔案 > 開啟 > CMake](media/cmake-open-cmake.png)

    當您開啟資料夾時，會顯示在您的資料夾結構**方案總管 中**。

    ![Visual Studio 方案總管資料夾檢視](media/cmake-bullet3-solution-explorer.png)

    此檢視會顯示您到底什麼是磁碟上，不是邏輯或已篩選檢視。 根據預設，不會顯示隱藏的檔案。 

2. 按下**顯示所有檔案**按鈕以查看資料夾中的所有檔案。

    ![Visual Studio 方案總管顯示所有檔案 按鈕](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切換至目標檢視

當您開啟使用 CMake 的資料夾時，Visual Studio 會自動產生 CMake 快取。 這項作業可能需要一些時間，視您的專案大小而定。 

1. 在 **輸出視窗**，選取**顯示輸出來源**，然後選擇  **CMake**來監視快取產生程序的狀態。 作業完成時，它會說 「 目標資訊擷取完成 」。

    ![Visual Studio 輸出視窗會顯示從 CMake 的輸出](media/cmake-bullet3-output-window.png)

    這項作業完成之後，IntelliSense 設定，系統可以建置專案，而您可以偵錯應用程式。 Visual Studio 現在可以提供根據 CMakeLists 檔案中指定的目標方案的邏輯檢視。 

2. 使用**解決方案與資料夾**按鈕**方案總管 中**切換至 CMake 目標檢視。

    ![解決方案與資料夾的按鈕，在方案總管 中，顯示 CMake 目標檢視](media/cmake-bullet3-show-targets.png)

    以下是哪些該檢視看起來像項目符號的 SDK:

    ![方案總管 CMake 目標檢視](media/cmake-bullet3-targets-view.png)

    目標檢視會提供更直覺的這個來源基底中檢視。 您可以看到某些目標屬於程式庫，有些則是可執行檔。 

3. 不論這些檔案可能位於磁碟上，請展開以查看其原始程式碼檔案，CMake 目標檢視中的節點。

## <a name="set-a-breakpoint-build-and-run"></a>設定中斷點、 建置和執行

在此步驟中，我們將示範項目符號物理程式庫範例程式偵錯。
  
1. 在 [**方案總管] 中**、 選取 AppBasicExampleGui 並將其展開。 
1. 開啟檔案`BasicExample.cpp`。 
1. 設定當您按一下 執行的應用程式時將會被叫用的中斷點。 內的 helper 類別的方法被處理 click 事件。 若要快速取得那里：

    1. 選取  `CommonRigidBodyBase` ，該結構`BasicExample`衍生自第 30 行周圍。
    1. 以滑鼠右鍵按一下，然後選擇 **移至定義**。 現在您已經 CommonRigidBodyBase.h 標頭中。 
    1. 在上方，您的來源瀏覽器檢視您應該會看到您處於`CommonRigidBodyBase`。 到右方時，您可以選取要檢查的成員。 按一下下拉箭號，然後選取`mouseButtonCallback`即可移至該函式標頭中定義。

        ![Visual Studio 成員清單工具列](media/cmake-bullet3-member-list-toolbar.png)

1. 此函式中的第一行上放置中斷點。 當您按一下應用程式在 Visual Studio 偵錯工具啟動時的視窗內的滑鼠按鈕時，這將會叫用。

1. 若要啟動應用程式，選取 啟動播放圖示，指出工具列中的 選取啟動項目 的下拉式清單。 在下拉式清單選取 AppBasicExampleGui.exe。 可執行檔的名稱現在會顯示在 [啟動] 按鈕：

    ![Visual Studio 工具列啟動下拉式清單選取啟動項目](media/cmake-bullet3-launch-button.png)

5.  按下 [啟動] 按鈕，來建置應用程式和必要的相依性，然後將它附加 Visual Studio 偵錯工具中啟動。 幾分鐘之後執行的應用程式就會出現：

    ![Visual Studio 偵錯 Windows 應用程式](media/cmake-bullet3-launched.png)

6. 將滑鼠移至 [應用程式] 視窗中，然後按一下按鈕觸發中斷點。 這會回到前景的 Visual Studio 編輯器顯示一行已暫停執行。 您可以檢查應用程式變數、 物件、 執行緒和記憶體。 您可以以互動方式逐步執行程式碼。 您可以按一下**繼續**讓應用程式繼續與正常的結束時間或停止使用 [停止] 按鈕的 Visual Studio 內執行。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>新增明確的 Windows x64 偵錯組態

到目前為止，您已使用預設值**x64 偵錯**Windows 設定。 組態可讓您為 Visual Studio 如何了解何種平台將會使用 CMake 的目標。 預設組態不代表磁碟上。 當您明確地新增了組態時，Visual Studio 會建立名為了適用於 CMakeSettings.json 中會填入與您指定的所有組態設定的檔案。 

1. 按一下 加入新的組態設定工具列的下拉式清單，然後選取**管理組態...**

    ![管理組態 下拉式清單](media/cmake-bullet3-manage-configurations.png)

    **新增組態發生 CMakeSettings**對話方塊隨即出現。

    ![將設定新增至發生 CMakeSettings 對話方塊](media/cmake-bullet3-add-configuration-x64-debug.png)

    此對話方塊會顯示隨附於 Visual Studio 中的所有設定，以及您可能會建立任何自訂設定。 如果您想要繼續使用預設值**x64 偵錯**應該是您所新增的第一個的組態。 藉由新增該組態，您可以來回切換之間 Windows 和 Linux 設定。 選取  **x64 偵錯**然後按一下**選取**。 這會建立的組態的 CMakeSettings.json 檔案**x64 偵錯**和切換 Visual Studio 來使用該組態，而不是預設值。 您會看到 [組態] 下拉式清單不會再顯示 「 （預設） 」 名稱的一部分。 您可以使用任何您想要您的組態變更直接在 CMakeSettings.json 中的 name 參數的名稱。

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>新增 Linux 設定並連接到遠端電腦

1. 現在新增 Linux 設定。 中的 CMakeSettings.json 檔案上按一下滑鼠右鍵**方案總管**檢視，然後選取**加入組態**。 您會看到與之前的發生 CMakeSettings 對話方塊相同加入組態。 選取  **Linux-debug**這次，然後儲存的 CMakeSettings.json 檔案。 
2. 現在，選取**Linux-debug**組態下拉式清單中。

    ![啟動組態 X64 偵錯與 Linux 偵錯選項的下拉式清單](media/cmake-bullet3-linux-configuration-item.png)

    如果這是您要連接到 Linux 系統，第一次**連線到遠端系統**對話方塊隨即出現。

    ![Visual Studio 連線到遠端系統對話方塊](media/cmake-bullet3-connection-manager.png)

    如果您已新增的遠端連線您還可以開啟此視窗，瀏覽至**工具 > 選項 > 跨平台 > 連接管理員**。
 
3. 提供您的 Linux 機器的連線資訊，然後按**Connect**。 Visual Studio 會將該機器對於 CMakeSettings.json 做為您預設值**Linux-debug**。 它也將會提取您的遠端電腦中的標頭，以便取得 IntelliSense 特有該機器使用時。 現在 Visual Studio 會將您的檔案傳送至遠端電腦，然後產生 CMake 快取，以及在完成 Visual Studio 將會設定為使用該遠端 Linux 電腦使用相同的來源基底。 這些步驟可能需要一些時間，取決於您的網路速度和遠端機器的電源。 您會知道這項作業在 CMake 的 [輸出] 視窗中出現訊息 「 目標資訊擷取完成 」 時所完成。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>設定中斷點、 建置及執行在 Linux 上

因為這是桌面應用程式時，您需要提供偵錯組態的一些其他組態資訊。 

1. 在 CMake 目標檢視中，以滑鼠右鍵按一下 AppBasicExampleGui，然後選擇**偵錯並啟動設定**以開啟 launch.vs.json 檔案中的隱藏 **.vs**子資料夾。 這個檔案是本機開發環境。 您可以將它移到您的專案的根目錄如果您想要與您的小組中，並將它儲存檢查。 此檔案中 AppBasicExampleGui 已新增的組態。 這些預設設定適用於大部分的情況下，但因為這是桌面應用程式，您需要提供一些額外的資訊，以啟動程式的方式可以看到我們的 Linux 機器上。 
2. 您需要知道的環境變數值`DISPLAY`您 Linux 電腦上，執行下列命令可取得它。

    ```cmd
    echo $DISPLAY
    ```

    AppBasicExampleGui 的組態中沒有參數陣列 」 pipeArgs"。 在這裡是"${debuggerCommand}"。 這是啟動遠端電腦上的 gdb 命令。 Visual Studio 必須匯出到此內容中顯示該命令執行之前。 比方說，如果您的顯示值： 1，那一行修改，如下所示：

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. 現在，若要啟動並偵錯我們的應用程式，選擇**選取啟動項目**工具列的下拉式清單，然後選擇 AppBasicExampleGui。 現在按下該按鈕，或叫用**F5**。 這會建置應用程式，然後在遠端 Linux 電腦上的其相依性啟動它附加 Visual Studio 偵錯工具。 在遠端 Linux 機器，您應該會看到應用程式視窗會出現。

4. 將滑鼠移至 [應用程式] 視窗中，按一下按鈕，並會叫用中斷點。 程式執行暫停，Visual Studio 會回到移至前景，，而且您會在您的中斷點。 您也應該查看 Linux 主控台視窗會出現在 Visual Studio。 此視窗會提供從遠端 Linux 機器中，輸出，它也可以接受輸入`stdin`。 任何 Visual Studio 視窗中，它可以停駐，您想要查看它和其位置就會保存在未來的工作階段。

    ![Visual Studio Linux 主控台視窗](media/cmake-bullet3-linux-console.png)

5. 您可以透過互動方式使用 Visual Studio 程式碼來檢查應用程式變數、 物件、 執行緒、 記憶體和步驟。 但這次進行所有遠端 Linux 電腦上而不您的本機 Windows 環境。 您可以按一下**繼續**，讓應用程式繼續執行，並結束正常的或者，您可以按 [停止] 按鈕，就如同使用本機執行一樣。

6. 查看呼叫堆疊 視窗，並檢視呼叫`x11OpenGLWindow`因為 Visual Studio 啟動 Linux 上的應用程式。

    ![呼叫堆疊 視窗中顯示 Linux 呼叫堆疊](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>您中學到什麼 

在本教學課程中，您已看到直接從 GitHub 複製和建置、 執行，以及偵錯，作為，不需修改基礎 Windows 程式碼。 這是程式碼基底，以小幅度設定變更、 已建置、 執行和偵錯在遠端 Linux 電腦上。 

## <a name="next-steps"></a>後續步驟

深入了解設定和偵錯 Visual Studio 中的 CMake 專案：

> [!div class="nextstepaction"]
> [Visual Studio 中的 CMake 專案](cmake-projects-in-visual-studio.md)<br/><br/>
> [設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/><br/>
> [連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [自訂 CMake 建置設定](customize-cmake-settings.md)<br/><br/>
> [設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/><br/>
> [部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [預先定義的 CMake 組態參考](cmake-predefined-configuration-reference.md)
> 
