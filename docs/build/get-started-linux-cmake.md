---
title: 在 Visual Studio 中建立 C++ 跨平台專案
description: 本教學課程會示範如何在以 Linux 和 Windows 為目標的 Visual Studio 中，設定、編譯和偵錯 C++ 開放原始碼 CMake 專案。
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: deb2c91d6d09d8945e5eb57a7ac742c5b1705e83
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196296"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 C++ 跨平台專案 

Visual Studio C 和 C++ 開發不再僅限於 Windows。 本教學課程會示範如何使用 Visual Studio 以 CMake 為基礎執行 C++ 跨平台開發，但不必建立或產生 Visual Studio 專案。 當您開啟包含 CMakeLists.txt 檔案的資料夾時，Visual Studio 會設定 IntelliSense 並自動建置設定。 您可以在 Windows 本機快速編輯、建置和偵錯程式碼，然後切換組態到 Linux 以進行相同的作業，這全都在 Visual Studio 內完成。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 從 GitHub 複製開放原始碼 CMake 專案
> * 在 Visual Studio 中開啟專案 
> * 在 Windows 上建置和偵錯可執行檔目標
> * 新增 Linux 電腦的連線
> * 在 Linux 上建置和偵錯同一目標

## <a name="prerequisites"></a>必要條件

- 設定 Visual Studio 執行跨平台 C++ 開發
    - 首先，您必須[安裝 Visual Studio](https://visualstudio.microsoft.com/vs/)。 接下來，確認已安裝**使用 C++ 的桌面開發**和**使用 C++ 的 Linux 程式開發工作負載**。 此最小安裝只有 3 GB，視您的下載速度而定，安裝不應該超過 10 分鐘。
- 設定 Linux 電腦執行跨平台 C++ 開發
    - Visual Studio 不需要任何特定的 Linux 發行版本。 此作業系統可在實體機器、VM、雲端或適用於 Linux 的 Windows 子系統 (WSL) 執行。 不過，本教學課程需要有圖形化的環境，所以不建議 WSL，因為它主要是針對命令列作業。
    - Visual Studio 在 Linux 電腦需要的工具包括：C++ 編譯器、GDB、SSH 和 ZIP。 在 Debian 型的系統上，您可以安裝這些相依性，如下所示。
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Visual Studio 需要 Linux 電腦具有啓用伺服器模式的最新版 CMake (至少 3.8)。 Microsoft 會產生 CMake 的通用組建，您可以安裝在任何的 Linux 發行版本。 建議您使用此組建，以確保您擁有最新的功能。 您可以在 GitHub 的 [Microsoft CMake 存放庫分支](https://github.com/Microsoft/CMake/releases)中取得 CMake 二進位檔。 請前往該頁面，將符合您系統架構的版本下載至 Linux 電腦，然後將它標記為可執行檔：
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - 您會看到執行指令碼的選項 `-–help`。 建議您使用 `–prefix` 選項指定安裝在 **/usr/local** 路徑，因為這是 Visual Studio 尋找 CMake 的預設位置。 下列範例示範 Linux-x86_64 指令碼。 如果您使用不同的目標平台，請視需要變更。 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- 安裝在 Windows 電腦上的 Git For Windows。
- GitHub 帳戶。

## <a name="clone-an-open-source-cmake-project-from-github"></a>從 GitHub 複製開放原始碼 CMake 專案

本教學課程使用 GitHub 上的 Bullet Physics SDK，它會提供各種不同應用程式的碰撞偵測及物理模擬。 它包含可編譯和執行的範例可執行程式，不必撰寫額外程式碼。 本教學課程不會修改任何原始程式碼或組建指令碼。 若要開始，請將 GitHub 之 bullet3 存放庫複製到已安裝 Visual Studio 的電腦上。 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. 從 Visual Studio 的主功能表中，選擇 [檔案] > [開啟] > [CMake]，然後巡覽至剛下載之 bullet3 存放庫根目錄中的 CMakeLists.txt 檔案。

    ![Visual Studio 的 [檔案] > [開啟] > [CMake] 功能表](media/cmake-open-cmake.png)

    一旦您開啟資料夾，[方案總管] 會隨即顯示您的資料夾結構。

    ![Visual Studio [方案總管] 資料夾檢視](media/cmake-bullet3-solution-explorer.png)

    此檢視會顯示磁碟的確切內容，而不是邏輯或篩選過的檢視。 根據預設，不會顯示隱藏的檔案。 

2. 按下 [顯示所有檔案] 按鈕以查看資料夾中的所有檔案。

    ![Visual Studio [方案總管] 的 [顯示所有檔案] 按鈕](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切換至目標檢視

當您開啟使用 CMake 的資料夾時，Visual Studio 會自動產生 CMake 快取。 這項作業可能需要一些時間，視您的專案大小而定。 

1. 在 [輸出視窗] 中，選取 [顯示輸出來源]，然後選擇 [CMake] 監視快取產生程序的狀態。 作業完成時會顯示「目標資訊擷取完成」。

    ![顯示 CMake 輸出的 Visual Studio [輸出] 視窗](media/cmake-bullet3-output-window.png)

    此作業完成後，IntelliSense 即已設定，系統可以建置專案，而您可以偵錯應用程式。 Visual Studio 現在可以根據 CMakeLists 檔案中指定的目標，提供解決方案的邏輯檢視。 

2. 使用 [方案總管] 的 [解決方案與資料夾] 按鈕切換至 CMake 目標檢視。

    ![顯示 CMake 目標檢視之 [方案總管] 的 [解決方案與資料夾] 按鈕](media/cmake-bullet3-show-targets.png)

    以下是 Bullet SDK 的檢視外觀：

    ![[方案總管] CMake 目標檢視](media/cmake-bullet3-targets-view.png)

    目標檢視提供此來源基底的更直觀檢視。 您會看到有些目標是程式庫，有些則是可執行檔。 

3. 展開 CMake 目標檢視中的節點，查看其原始程式碼檔案，無論這些檔案是否可能位於磁碟上。

## <a name="set-a-breakpoint-build-and-run"></a>設定中斷點、建置並執行

在此步驟中，我們會偵錯示範 Bullet Physics 程式庫的範例程式。
  
1. 在 [方案總管] 中，選取並展開 AppBasicExampleGui。 
1. 開啟檔案 `BasicExample.cpp`。 
1. 設定當您按一下執行中應用程式時即會叫用的中斷點。 Click 事件是在 helper 類別內的方法中處理。 若要快速獲得此結果：

    1. 請選取 `CommonRigidBodyBase`，其結構 `BasicExample` 衍生自第 30 行附近。
    1. 按一下滑鼠右鍵選擇 [移至定義]。 您現在位於 CommonRigidBodyBase.h 標頭中。 
    1. 在上方的瀏覽器檢視中，您應該會看到自己的來源，您位在 `CommonRigidBodyBase`。 您可以在右邊選取要檢查的成員。 按一下下拉式清單，然後選取 `mouseButtonCallback` 移至標頭中該函式的定義。

        ![Visual Studio 成員清單工具列](media/cmake-bullet3-member-list-toolbar.png)

1. 將中斷點放在此函式的第一行。 在 Visual Studio 偵錯工具下啟動應用程式時，只要在應用程式視窗內按一下滑鼠按鈕，即會叫用此中斷點。

1. 若要啟動應用程式，請在工具列中選取播放圖示指出「選取啟動項目」的啟動下拉式清單。 在下拉式清單中選取 AppBasicExampleGui.exe。 可執行檔的名稱現在會顯示在 [啟動] 按鈕上：

    ![選取啟動項目的 Visual Studio 工具列啟動下拉式清單](media/cmake-bullet3-launch-button.png)

5.  按下 [啟動] 按鈕來建置應用程式和必要的相依性，然後使用附加的 Visual Studio 偵錯工具啟動它。 一會兒後，正在執行的應用程式即會出現：

    ![Visual Studio 偵錯 Windows 應用程式](media/cmake-bullet3-launched.png)

6. 將滑鼠移至應用程式視窗中，然後按一下按鈕觸發中斷點。 這會回到 Visual Studio 前景，編輯器顯示暫停執行的那一行。 您可以檢查應用程式變數、物件、執行緒和記憶體。 您可以互動方式逐步執行程式碼。 您可以按一下 [繼續] 讓應用程式繼續及正常結束，或使用 [停止] 按鈕在 Visual Studio 內停止執行。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>新增明確的 Windows x64 偵錯組態

到目前為止，您一直在使用預設的 Windows **x64 偵錯**組態。 組態是 Visual Studio 了解將為 CMake 使用何種平台目標的方法。 預設組態不會呈現在磁碟上。 當您明確新增組態時，Visual Studio 會建立稱為 CMakeSettings.json 的檔案，填入您指定的所有組態設定。 

1. 按一下工具列的 [組態] 下拉式清單，然後選取 [管理組態]，以新增新組態。

    ![管理組態下拉式清單](media/cmake-bullet3-manage-configurations.png)

    [將組態新增至 CMakeSettings] 對話方塊隨即出現。

    ![[將組態新增至 CMakeSettings] 對話方塊](media/cmake-bullet3-add-configuration-x64-debug.png)

    此對話方塊會顯示所有隨附於 Visual Studio 的組態，以及您可能建立的任何自訂組態。 如果您想要繼續使用預設的 **x64 偵錯**組態，這應該是您新增的第一個組態。 藉由新增該組態，您可以在 Windows 和 Linux 組態之間來回切換。 選取 [x64 偵錯]，然後按一下 [選取]。 這會建立具有 **x64 偵錯**組態的 CMakeSettings.json 檔案，並切換 Visual Studio 以使用該組態，而不是使用預設組態。 您會看到 [組態] 下拉式清單的名稱中不再顯示「(預設)」。 您可以直接在 CMakeSettings.json 中變更 name 參數，使用您喜歡的任何組態名稱。

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>新增 Linux 組態並連線到遠端電腦

1. 現在新增 Linux 組態。 以滑鼠右鍵按一下 [方案總管] 檢視中的 CMakeSettings.json 檔案，然後選取 [新增組態]。 您會看到和以前一樣的 [新增組態至 CMakeSettings] 對話方塊。 這次選取 [Linux 偵錯]，然後儲存 CMakeSettings.json 檔案。 
2. 現在，在 [組態] 下拉式清單中選取 [Linux 偵錯]。

    ![啟動具有 [X64 偵錯] 與 [Linux 偵錯] 選項的組態下拉式清單](media/cmake-bullet3-linux-configuration-item.png)

    如果這是您第一次連線到 Linux 系統，就會出現 [連線到遠端系統] 對話方塊。

    ![Visual Studio [連線到遠端系統] 對話方塊](media/cmake-bullet3-connection-manager.png)

    如已新增遠端連線，您可以巡覽至 [工具] > [選項] > [跨平台] > [連線管理員] 來開啟此視窗。
 
3. 提供您的 Linux 電腦連線資訊，然後按一下 [連線]。 Visual Studio 會將該電腦新增為 CMakeSettings.json，作為您的 [Linux 偵錯] 預設。 它也會下拉您遠端電腦的標頭，以便取得使用該電腦時的特定 IntelliSense。 現在 Visual Studio 會將您的檔案傳送至遠端電腦，然後在那裡產生 CMake 快取；完成後，Visual Studio 會設定為在該遠端 Linux 電腦使用相同的來源基底。 這些步驟需要一些時間，時間長短取決於網路速度和遠端電腦的功率。 當 CMake 的輸出視窗中顯示「目標資訊擷取完成」訊息時，您就知道這項作業已完成。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>在 Linux 上設定中斷點、建置並執行

因為這是桌面應用程式，所以您需要向偵錯組態提供一些額外的組態資訊。 

1. 在 CMake 目標檢視中，以滑鼠右鍵按一下 AppBasicExampleGui，然後選擇 [偵錯並啟動設定] 開啟 launch.vs.json 檔案，它位在隱藏的 **.vs** 子資料夾中。 這對開發環境而言是本機檔案。 如果您想要簽入它並與小組儲存在一起，您可以將它移到專案的根目錄中。 在此檔案中已針對 AppBasicExampleGui 新增組態。 這些預設設定適用於大部分的情況，但因為這是桌面應用程式，您還需要提供一些額外資訊，才能以您在我們的 Linux 電腦上看到的方式來啟動程式。 
2. 您需要知道您 Linux 電腦上的環境變數 `DISPLAY` 值，請執行此命令取得它。

    ```cmd
    echo $DISPLAY
    ```

    AppBasicExampleGui 組態有參數陣列 "pipeArgs"。 其中有一行 "${debuggerCommand}"。 這是在遠端電腦上啟動 gdb 的命令。 Visual Studio 需要先將顯示結果匯出到此內容，再執行命令。 例如，如果您的顯示值為 1，請如下所示修改該行：

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. 現在，為啟動並偵錯我們的應用程式，請選擇工具列的 [選取啟動項目] 下拉式清單，然後選擇 AppBasicExampleGui。 現在按下該按鈕，或叫用 **F5**。 這會在遠端 Linux 電腦上建置應用程式及其相依性，然後使用附加的 Visual Studio 偵錯工具啟動它。 在您的遠端 Linux 電腦上，您應該會看到應用程式視窗。

4. 將滑鼠移至應用程式視窗中，按一下按鈕即會叫用中斷點。 程式暫停執行，Visual Studio 會回到前景，而您會位於您的中斷點。 您也應該會在 Visual Studio 中看到 Linux 主控台視窗。 此視窗會提供遠端 Linux 電腦的輸出，它也可以接受 `stdin` 的輸入。 如同任何 Visual Studio 視窗，它可以停駐在您指定的任何位置供查看，且位置將保存在未來的工作階段中。

    ![Visual Studio Linux 主控台視窗](media/cmake-bullet3-linux-console.png)

5. 您可以檢查應用程式變數、物件、執行緒、記憶體，並使用 Visual Studio 以互動方式逐一檢查程式碼。 但這次您要在遠端 Linux 電腦上完成所有作業，而不是在本機 Windows 環境。 您可以按一下 [繼續] 讓應用程式繼續及正常結束，或按 [停止] 按鈕，就像在本機執行時一樣。

6. 查看 [呼叫堆疊] 視窗，並檢視 `x11OpenGLWindow` 呼叫，因為 Visual Studio 是在 Linux 上啟動應用程式。

    ![顯示 Linux 呼叫堆疊的 [呼叫堆疊] 視窗](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>您已了解到 

在本教學課程中，您看到了直接從 GitHub 複製的程式碼基底，且在 Windows 上建置、執行及偵錯而不做任何修改。 這個小幅變更組態的程式碼基底，是在遠端 Linux 電腦上建置、執行和偵錯。 

## <a name="next-steps"></a>後續步驟

在 Visual Studio 中深入了解設定和偵錯 CMake 專案：

> [!div class="nextstepaction"]
> [CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/><br/>
> [設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/><br/>
> [連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [自訂 CMake 建置設定](customize-cmake-settings.md)<br/><br/>
> [設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/><br/>
> [部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)
> 
