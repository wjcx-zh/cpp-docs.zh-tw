---
title: 在 Visual Studio 中建立 C++ 跨平台專案
description: 如何在以 Linux 和 Windows 為目標的 Visual Studio C++中，設定、編譯和偵測開放原始碼 CMake 專案。
author: mikeblome
ms.topic: tutorial
ms.date: 11/08/2019
ms.openlocfilehash: 269c9e88133a492f66df7c7f81ab35424aff125d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303249"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教學課程： C++在 Visual Studio 中建立跨平臺專案

Visual Studio C 和 C++ 開發不再僅限於 Windows。 本教學課程說明如何在 Windows 和C++ Linux 上使用跨平臺開發的 Visual Studio。 它是以 CMake 為基礎，因此您不需要建立或產生 Visual Studio 專案。 當您開啟包含 Remote monitoring.h cmakelists.txt 檔案的資料夾時，Visual Studio 會自動設定 IntelliSense 和組建設定。 您可以在 Windows 本機快速開始編輯、建立和偵錯工具代碼。 然後，切換您的設定，以在 Linux 上執行相同的動作，全都從 Visual Studio 內。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 從 GitHub 複製開放原始碼 CMake 專案
> * 在 Visual Studio 中開啟專案
> * 在 Windows 上建置和偵錯可執行檔目標
> * 新增 Linux 電腦的連線
> * 在 Linux 上建置和偵錯同一目標

## <a name="prerequisites"></a>先決條件

* 設定 Visual Studio 執行跨平台 C++ 開發
  * 首先，[安裝 Visual Studio](https://visualstudio.microsoft.com/vs/)並選擇使用 **C++工作負載**進行的 **C++桌面開發**和 Linux 開發。 這種最小安裝僅限 3 GB。 視您的下載速度而定，安裝應該不會超過10分鐘。

* 設定 Linux 電腦執行跨平台 C++ 開發
  * Visual Studio 不需要任何特定的 Linux 發行版本。 OS 可以在實體電腦、VM 或雲端中執行。 您也可以使用適用于 Linux 的 Windows 子系統（WSL）。 不過，在本教學課程中，需要圖形化環境。 WSL 不建議用於此處，因為它主要是用來進行命令列作業。
  * Visual Studio 需要 Linux 電腦上的下列工具： C++編譯器、gdb、ssh、rsync 和 zip。 在以 Debian 為基礎的系統上，您可以使用此命令來安裝這些相依性：

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync zip
    ```

  * Visual Studio 在已啟用伺服器模式的 Linux 電腦上需要最新版本的 CMake （至少3.8）。 Microsoft 會產生 CMake 的通用組建，您可以安裝在任何的 Linux 發行版本。 建議您使用此組建，以確保您擁有最新的功能。 您可以在 GitHub 的 [Microsoft CMake 存放庫分支](https://github.com/Microsoft/CMake/releases)中取得 CMake 二進位檔。 移至該頁面，並下載符合 Linux 電腦上系統架構的版本，然後將它標示為可執行檔：

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * 您會看到執行指令碼的選項 `-–help`。 建議您使用 [`–prefix`] 選項指定 [在 **/usr/local**路徑中安裝]，因為這是 Visual Studio 尋找 CMake 的預設位置。 下列範例示範 Linux-x86_64 指令碼。 如果您使用不同的目標平臺，請視需要加以變更。

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```

* 安裝在 Windows 電腦上的 Git For Windows。
* GitHub 帳戶。

## <a name="clone-an-open-source-cmake-project-from-github"></a>從 GitHub 複製開放原始碼 CMake 專案

本教學課程使用 GitHub 上的專案符號物理 SDK。 它提供許多應用程式的碰撞偵測和物理模擬。 SDK 包含可編譯和執行的範例可執行程式，而不需要撰寫額外的程式碼。 本教學課程不會修改任何原始程式碼或組建腳本。 若要開始，請在已安裝 Visual Studio 的電腦上，從 GitHub 複製*之 bullet3*存放庫。

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. 在 Visual Studio 主功能表上，選擇 [檔案 **> 開啟 > CMake**]。 流覽至您剛才下載之之 bullet3 存放庫根目錄中的 Remote monitoring.h cmakelists.txt。

    ![Visual Studio 的 [檔案] > [開啟] > [CMake] 功能表](media/cmake-open-cmake.png)

    一旦您開啟資料夾，您的資料夾結構就會顯示在**方案總管**中。

    ![Visual Studio [方案總管] 資料夾檢視](media/cmake-bullet3-solution-explorer.png)

    此檢視會顯示磁碟的確切內容，而不是邏輯或篩選過的檢視。 根據預設，不會顯示隱藏的檔案。

1. 選擇 [**顯示所有**檔案] 按鈕，以查看資料夾中的所有檔案。

    ![Visual Studio [方案總管] 的 [顯示所有檔案] 按鈕](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切換至目標檢視

當您開啟使用 CMake 的資料夾時，Visual Studio 會自動產生 CMake 快取。 這項作業可能需要一些時間，視您的專案大小而定。

1. 在 [輸出視窗] 中，選取 [顯示輸出來源]，然後選擇 [CMake] 監視快取產生程序的狀態。 作業完成時會顯示「目標資訊擷取完成」。

   ![顯示 CMake 輸出的 Visual Studio [輸出] 視窗](media/cmake-bullet3-output-window.png)

   在此作業完成之後，會設定 IntelliSense。 您可以建立專案，並對應用程式進行 debug。 Visual Studio 現在會根據 Remote monitoring.h cmakelists.txt 檔案中指定的目標，顯示解決方案的邏輯觀點。

1. 使用 [方案總管] 的 [解決方案與資料夾] 按鈕切換至 CMake 目標檢視。

   ![顯示 CMake 目標檢視之 [方案總管] 的 [解決方案與資料夾] 按鈕](media/cmake-bullet3-show-targets.png)

   以下是 Bullet SDK 的檢視外觀：

   ![[方案總管] CMake 目標檢視](media/cmake-bullet3-targets-view.png)

   目標檢視提供此來源基底的更直觀檢視。 您會看到有些目標是程式庫，有些則是可執行檔。

1. 展開 CMake 目標檢視中的節點，查看其原始程式碼檔案，無論這些檔案是否可能位於磁碟上。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>新增明確的 Windows x64 偵錯組態

Visual Studio 會建立 Windows 的預設**x64-Debug**設定。 組態是 Visual Studio 了解將為 CMake 使用何種平台目標的方法。 預設組態不會呈現在磁碟上。 當您明確地新增設定時，Visual Studio 會建立名為*CMakeSettings*的檔案。 它會針對您指定的所有設定填入設定。

1. 新增設定。 開啟工具列中**的 [設定**] 下拉式選單，然後選取 [**管理**設定]。

   ![管理組態下拉式清單](media/cmake-bullet3-manage-configurations.png)

   [ [CMake 設定編輯器](customize-cmake-settings.md)] 隨即開啟。 選取編輯器左側的綠色加號，以加入新的設定。 [**將設定新增至 CMakeSettings** ] 對話方塊隨即出現。

   ![[將組態新增至 CMakeSettings] 對話方塊](media/cmake-bullet3-add-configuration-x64-debug.png)

   這個對話方塊會顯示 Visual Studio 隨附的所有設定，以及您所建立的任何自訂設定。 如果您想要繼續使用**x64-Debug**設定，這應該是您新增的第一個設定。 選取 [ **x64-Debug**]，然後選擇 [**選取**] 按鈕。 Visual Studio 會建立具有**x64-Debug**設定的 CMakeSettings json 檔案，並將它儲存到磁片。 您可以直接在 CMakeSettings.json 中變更 name 參數，使用您喜歡的任何組態名稱。

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>在 Windows 上設定中斷點、組建和執行

在此步驟中，我們會偵錯示範 Bullet Physics 程式庫的範例程式。
  
1. 在 [方案總管] 中，選取並展開 AppBasicExampleGui。

1. 開啟檔案 `BasicExample.cpp`。

1. 設定當您在執行中的應用程式中按一下時所叫用的中斷點。 Click 事件是在 helper 類別內的方法中處理。 若要快速獲得此結果：

   1. 選取結構 `BasicExample` 衍生的 `CommonRigidBodyBase`。 大約是第30行。

   1. 按一下滑鼠右鍵選擇 [移至定義]。 現在您是在 CommonRigidBodyBase 標頭中。

   1. 在您來源上方的瀏覽器視圖中，您應該會看到您在 `CommonRigidBodyBase`中。 您可以在右邊選取要檢查的成員。 開啟下拉式選單，然後選取 [`mouseButtonCallback`]，以移至標頭中該函式的定義。

      ![Visual Studio 成員清單工具列](media/cmake-bullet3-member-list-toolbar.png)

1. 將中斷點放在此函式的第一行。 當您在應用程式視窗中按下滑鼠按鍵時，就會叫用它（在 Visual Studio 偵錯工具底下執行）。

1. 若要啟動應用程式，請選取工具列中的 [啟動] 下拉式選單。 這是具有綠色播放圖示的人，表示「選取啟動專案」。 在下拉式選單中，選取 [AppBasicExampleGui]。 可執行檔的名稱現在會顯示在 [啟動] 按鈕上：

   ![選取啟動項目的 Visual Studio 工具列啟動下拉式清單](media/cmake-bullet3-launch-button.png)

1. 選擇 [啟動] 按鈕，以建立應用程式和必要的相依性，然後使用附加的 Visual Studio 偵錯工具啟動它。 一會兒後，正在執行的應用程式即會出現：

   ![Visual Studio 偵錯 Windows 應用程式](media/cmake-bullet3-launched.png)

1. 將滑鼠移至應用程式視窗中，然後按一下按鈕觸發中斷點。 中斷點會將 Visual Studio 帶回前景，而編輯器會顯示執行暫停的那一行。 您可以檢查應用程式變數、物件、執行緒和記憶體，或以互動方式逐步執行程式碼。 選擇 [**繼續**] 讓應用程式繼續執行，然後正常結束。 或者，使用 [停止] 按鈕，在 Visual Studio 中停止執行。

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>新增 Linux 組態並連線到遠端電腦

1. 新增 Linux 設定。 以滑鼠右鍵按一下 [方案總管] 檢視中的 CMakeSettings.json 檔案，然後選取 [新增組態]。 您會看到和以前一樣的 [新增組態至 CMakeSettings] 對話方塊。 選取 [ **Linux-** 在此時間進行 Debug]，然後儲存 CMakeSettings 檔案（ctrl + s）。

1. 在 [設定] 下拉式選單中選取 [ **Linux-Debug** ]。

   ![啟動具有 [X64 偵錯] 與 [Linux 偵錯] 選項的組態下拉式清單](media/cmake-bullet3-linux-configuration-item.png)

   如果這是您第一次連線到 Linux 系統，則會出現 [**連接到遠端系統**] 對話方塊。

   ![Visual Studio [連線到遠端系統] 對話方塊](media/cmake-bullet3-connection-manager.png)

   如果您已新增遠端連線，您可以流覽至 [工具] [ **> 選項] [> 跨平臺 > 連線管理員**] 來開啟此視窗。

1. 提供[連接資訊給您的 Linux 電腦](/cpp/linux/connect-to-your-remote-linux-computer)，然後選擇 [連線 **]** 。 Visual Studio 會將該機器新增至 CMakeSettings，做為**Linux-Debug**的預設連接。 它也會從您的遠端電腦拉出標頭，讓您取得[該遠端連線特定的 IntelliSense](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense)。 接下來，Visual Studio 將您的檔案傳送至遠端電腦，並在遠端系統上產生 CMake 快取。 這些步驟可能需要一些時間，視您的網路速度和遠端電腦的能力而定。 當 [CMake 輸出] 視窗中出現「目標資訊解壓縮完成」訊息時，您會知道它已完成。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>在 Linux 上設定中斷點、組建和執行

因為它是桌面應用程式，所以您必須提供一些額外的設定資訊給 debug 設定。

1. 在 [CMake 目標] 視圖中，以滑鼠右鍵按一下 [AppBasicExampleGui]，然後選擇 [**偵錯工具和啟動設定**]，開啟位於隱藏的 **. vs**子資料夾中的 [啟動檔案]。 這對開發環境而言是本機檔案。 如果您想要簽入它並與小組儲存在一起，您可以將它移到專案的根目錄中。 在此檔案中，已新增 AppBasicExampleGui 的設定。 這些預設設定適用于大部分的情況，但在這裡則不會。 因為它是桌面應用程式，所以您需要提供一些額外的資訊來啟動程式，以便您可以在 Linux 電腦上看到它。

1. 若要在您的 Linux 電腦上找出環境變數 `DISPLAY` 的值，請執行此命令：

   ```cmd
   echo $DISPLAY
   ```

   在 AppBasicExampleGui 的設定中，有一個參數陣列 "pipeArgs"。 它包含一行： "$ {debuggerCommand}"。 這是在遠端電腦上啟動 gdb 的命令。 Visual Studio 必須先將顯示匯出到此內容，然後該命令才會執行。 例如，如果顯示的值是 `:1`，請修改該行，如下所示：

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. 啟動和偵錯工具。 開啟工具列上的 [**選取啟動專案**] 下拉式選單，然後選擇 [ **AppBasicExampleGui**]。 接下來，選擇工具列中的綠色播放圖示，或按**F5**鍵。 應用程式及其相依性建置於遠端 Linux 電腦上，然後使用附加的 Visual Studio 偵錯工具啟動。 在您的遠端 Linux 電腦上，您應該會看到應用程式視窗。

1. 將滑鼠移至應用程式視窗，然後按一下按鈕。 到達中斷點。 程式執行會暫停，Visual Studio 回到前景，您就會看到您的中斷點。 您也應該會在 Visual Studio 中看到 Linux 主控台視窗。 此視窗會提供遠端 Linux 機器的輸出，也可以接受 `stdin`的輸入。 就像任何 Visual Studio 視窗一樣，您可以將它停駐在您偏好的位置。 其位置會保存在未來的會話中。

   ![Visual Studio Linux 主控台視窗](media/cmake-bullet3-linux-console.png)

1. 您可以檢查應用程式變數、物件、執行緒、記憶體，並使用 Visual Studio 以互動方式逐一檢查程式碼。 但這次是在遠端 Linux 電腦上執行，而不是在您的本機 Windows 環境中進行。 您可以選擇 [**繼續**] 讓應用程式正常地繼續和結束，或者您也可以選擇 [停止] 按鈕，就像使用本機執行一樣。

1. 查看 [呼叫堆疊] 視窗，並檢視 `x11OpenGLWindow` 呼叫，因為 Visual Studio 是在 Linux 上啟動應用程式。

   ![顯示 Linux 呼叫堆疊的 [呼叫堆疊] 視窗](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>您已了解到

在本教學課程中，您已直接從 GitHub 複製程式碼基底。 您在 Windows 上建立、執行和調試它，而不需要修改。 然後您使用相同的程式碼基底，並進行次要設定變更，以在遠端 Linux 電腦上建立、執行和偵錯工具。

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
