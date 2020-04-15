---
title: 在 Visual Studio 中建立 C++ 跨平台專案
description: 如何在 Visual Studio 中設置、編譯和調試面向 Linux 和 Windows 的C++開源 CMake 專案。
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328749"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>教程:在可視化工作室創建C++跨平台專案

Visual Studio C 和 C++ 開發不再僅限於 Windows。 本教程演示如何使用 Visual Studio 在 Windows 和 Linux 上C++跨平台開發。 它基於 CMake,因此您不必創建或生成 Visual Studio 專案。 當您打開包含 CMakelists.txt 檔的資料夾時,Visual Studio 會自動設定 IntelliSense 並生成設定。 您可以在 Windows 上快速開始編輯、構建和除錯程式碼。 然後,切換配置,在 Linux 上執行相同的操作,所有這些都來自 Visual Studio 中。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 從 GitHub 複製開放原始碼 CMake 專案
> * 在 Visual Studio 中開啟專案
> * 在 Windows 上建置和偵錯可執行檔目標
> * 新增 Linux 電腦的連線
> * 在 Linux 上建置和偵錯同一目標

## <a name="prerequisites"></a>Prerequisites

* 設定 Visual Studio 執行跨平台 C++ 開發
  * 首先,[安裝 Visual Studio,](https://visualstudio.microsoft.com/vs/)選擇**具有 C++工作負載的 C++** 和**Linux 開發。** 此最小安裝僅為 3 GB。 根據您的下載速度,安裝時間不應超過 10 分鐘。

* 設定 Linux 電腦執行跨平台 C++ 開發
  * Visual Studio 不需要任何特定的 Linux 發行版本。 操作系統可以在物理電腦、VM 或雲中運行。 您也可以將 Windows 子系統用於 Linux (WSL)。 但是,對於本教程,需要圖形環境。 此處不建議使用 WSL,因為它主要用於命令列操作。
  * Visual Studio 需要在 Linux 電腦上使用這些工具:C++編譯器、gdb、ssh、rsync、忍者和 zip。 在基於 Debian 的系統上,您可以使用此指令安裝以下相依項:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio 要求在 Linux 電腦上啟用伺服器模式(至少 3.8)的最新版本的 CMake。 Microsoft 會產生 CMake 的通用組建，您可以安裝在任何的 Linux 發行版本。 我們建議您使用此版本來確保您具有最新的功能。 您可以在 GitHub 的 [Microsoft CMake 存放庫分支](https://github.com/Microsoft/CMake/releases)中取得 CMake 二進位檔。 跳到此頁面並下載與 Linux 電腦上的系統架構結構符合的版本,然後將其標記為可執行檔:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * 您會看到執行指令碼的選項 `-–help`。 我們建議您使用`–prefix`選項指定在 **/usr**路徑中的安裝,因為 **/usr/bin**是 Visual Studio 尋找 CMake 的預設位置。 下列範例示範 Linux-x86_64 指令碼。 如果您使用的是其他目標平臺,則根據需要進行更改。

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* 安裝在 Windows 電腦上的 Git For Windows。
* GitHub 帳戶。

## <a name="clone-an-open-source-cmake-project-from-github"></a>從 GitHub 複製開放原始碼 CMake 專案

本教學在 GitHub 上使用項目符號物理 SDK。 它為許多應用提供碰撞檢測和物理類比。 SDK 包括無需編寫其他代碼即可編譯和運行的範例可執行程式。 本教程不修改任何原始碼或生成腳本。 要開始,請從安裝了 Visual Studio 的電腦上的 GitHub 克隆*專案符號3*儲存庫。

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. 在視覺化工作室主選單上,選擇**檔案>打開>製作**。 導覽到您剛剛下載的 cmakelists.txt 的 cmakelists.txt 檔。

    ![Visual Studio 的 [檔案] > [開啟] > [CMake] 功能表](media/cmake-open-cmake.png)

    一旦打開資料夾,您的資料夾結構就會在**解決方案資源管理器**中可見。

    ![Visual Studio [方案總管] 資料夾檢視](media/cmake-bullet3-solution-explorer.png)

    此檢視會顯示磁碟的確切內容，而不是邏輯或篩選過的檢視。 根據預設，不會顯示隱藏的檔案。

1. 選擇「**顯示所有檔案**」 按鈕以檢視資料夾中的所有檔案。

    ![Visual Studio [方案總管] 的 [顯示所有檔案] 按鈕](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>切換至目標檢視

當您開啟使用 CMake 的資料夾時，Visual Studio 會自動產生 CMake 快取。 這項作業可能需要一些時間，視您的專案大小而定。

1. 在 [輸出視窗]**** 中，選取 [顯示輸出來源]****，然後選擇 [CMake]**** 監視快取產生程序的狀態。 作業完成時會顯示「目標資訊擷取完成」。

   ![顯示 CMake 輸出的 Visual Studio [輸出] 視窗](media/cmake-bullet3-output-window.png)

   此操作完成後,將配置 IntelliSense。 您可以生成專案並調試應用程式。 Visual Studio 現在根據 CMakelists 檔中指定的目標顯示解決方案的邏輯檢視。

1. 使用 [方案總管]**** 的 [解決方案與資料夾]**** 按鈕切換至 CMake 目標檢視。

   ![顯示 CMake 目標檢視之 [方案總管] 的 [解決方案與資料夾] 按鈕](media/cmake-bullet3-show-targets.png)

   以下是 Bullet SDK 的檢視外觀：

   ![[方案總管] CMake 目標檢視](media/cmake-bullet3-targets-view.png)

   目標檢視提供此來源基底的更直觀檢視。 您會看到有些目標是程式庫，有些則是可執行檔。

1. 展開 CMake 目標檢視中的節點，查看其原始程式碼檔案，無論這些檔案是否可能位於磁碟上。

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>新增明確的 Windows x64 偵錯組態

Visual Studio 為 Windows 創建預設**x64 調試**配置。 組態是 Visual Studio 了解將為 CMake 使用何種平台目標的方法。 預設組態不會呈現在磁碟上。 當您顯式添加配置時,Visual Studio 將建立一個名為 *「CMakeSettings.json」* 的檔。 它填充了您指定的所有配置的設置。

1. 添加新配置。 開啟工具列中的 **「設定**」下拉清單,然後選擇 **「管理設定**」 。

   ![管理組態下拉式清單](media/cmake-bullet3-manage-configurations.png)

   將打開[「製作設置編輯器](customize-cmake-settings.md)」 。 選擇編輯器左側的綠色加號以添加新配置。 將顯示 **「 設定」 設定為「設定」 對話框**。

   ![[將組態新增至 CMakeSettings] 對話方塊](media/cmake-bullet3-add-configuration-x64-debug.png)

   此對話框顯示 Visual Studio 中包含的所有配置,以及您創建的任何自訂配置。 如果要繼續使用**x64 調試**配置,則應是添加的第一個配置。 選擇**x64-除錯**,然後選擇 **「選擇**」按鈕。 Visual Studio 創建具有**x64 除錯**配置的 CMakeSettings.json 檔,並將其保存到磁碟。 您可以直接在 CMakeSettings.json 中變更 name 參數，使用您喜歡的任何組態名稱。

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>設定斷點、產生並在 Windows 上執行

在此步驟中，我們會偵錯示範 Bullet Physics 程式庫的範例程式。
  
1. 在 [方案總管]**** 中，選取並展開 AppBasicExampleGui。

1. 開啟檔案 `BasicExample.cpp`。

1. 設置在正在運行的應用程式中按一下時命中的斷點。 Click 事件是在 helper 類別內的方法中處理。 若要快速獲得此結果：

   1. 選擇`CommonRigidBodyBase`結構派生自該`BasicExample`結構 。 在30號線附近

   1. 按一下滑鼠右鍵選擇 [移至定義]****。 現在,您位於"共同剛性博基礎.h"的標頭中。

   1. 在來源上方的瀏覽器檢視中,您應該看到您位於中`CommonRigidBodyBase`。 您可以在右邊選取要檢查的成員。 開啟下拉清單並選擇`mouseButtonCallback`轉到標頭中該函數的定義。

      ![Visual Studio 成員清單工具列](media/cmake-bullet3-member-list-toolbar.png)

1. 將中斷點放在此函式的第一行。 當您按一下應用程式視窗中的滑鼠按鈕時,在 Visual Studio 調試器下運行時,它會被命中。

1. 要啟動應用程式,請在工具列中選擇啟動下拉清單。 它是一個綠色播放圖示,顯示"選擇啟動專案"。 在下拉清單中,選擇 AppBasicExampleGui.exe。 可執行檔的名稱現在會顯示在 [啟動] 按鈕上：

   ![選取啟動項目的 Visual Studio 工具列啟動下拉式清單](media/cmake-bullet3-launch-button.png)

1. 選擇啟動按鈕以生成應用程式和必要的依賴項,然後在附加 Visual Studio 調試器後啟動它。 一會兒後，正在執行的應用程式即會出現：

   ![Visual Studio 偵錯 Windows 應用程式](media/cmake-bullet3-launched.png)

1. 將滑鼠移至應用程式視窗中，然後按一下按鈕觸發中斷點。 斷點將 Visual Studio 帶回前臺,編輯器顯示暫停執行的行。 您可以檢查應用程式變數、對象、線程和記憶體,也可以以交互方式單步執行代碼。 選擇 **"繼續**"以讓應用程式繼續,然後正常退出。 或者,通過使用停止按鈕停止 Visual Studio 中的執行。

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>新增 Linux 組態並連線到遠端電腦

1. 添加 Linux 配置。 以滑鼠右鍵按一下 [方案總管]**** 檢視中的 CMakeSettings.json 檔案，然後選取 [新增組態]****。 您會看到和以前一樣的 [新增組態至 CMakeSettings] 對話方塊。 選擇**Linux除錯**這一次,然後保存CMakeSettings.json檔(ctrl +s)。

1. 在設定下拉清單中選擇**Linux 除錯**。

   ![啟動具有 [X64 偵錯] 與 [Linux 偵錯] 選項的組態下拉式清單](media/cmake-bullet3-linux-configuration-item.png)

   如果這是您第一次連接到 Linux 系統,則會出現 **『連接到遠端系統』** 對話方塊。

   ![Visual Studio [連線到遠端系統] 對話方塊](media/cmake-bullet3-connection-manager.png)

   如果已添加遠端連接,則可以通過導航到**工具>選項>跨平臺>連接管理器**來打開此視窗。

1. 向[Linux 電腦提供連接資訊](/cpp/linux/connect-to-your-remote-linux-computer),然後選擇 **「連接**」。。 Visual Studio 將該電腦添加為 CMakeSettings.json 作為**Linux 調試的**默認連接。 它還從遠端電腦下拉頭,因此您將獲得[特定於該遠端連接的 IntelliSense。](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense) 接下來,Visual Studio 會將檔案發送到遠端電腦,並在遠端系統上生成 CMake 快取。 這些步驟可能需要一些時間,具體取決於網路速度和遠端計算機的電源。 當「目標資訊提取完成」消息出現在 CMake 輸出視窗中時,您會知道它已完成。

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>設定斷點、建構與 Linux 執行

因為它是桌面應用程式,因此您需要向調試配置提供一些其他配置資訊。

1. 在"CMake 目標"檢視中,右鍵單擊 AppBasicExampleGui 並選擇 **「調試和啟動設定」** 以打開隱藏 **.vs**子資料夾中的啟動.vs.json 檔。 這對開發環境而言是本機檔案。 如果您想要簽入它並與小組儲存在一起，您可以將它移到專案的根目錄中。 在此檔中,已為 AppBasicExampleGui 添加了配置。 在大多數情況下,這些預設設置工作,但此處不工作。 因為它是桌面應用程式,您需要提供一些附加資訊來啟動程式,以便您可以在 Linux 電腦上看到它。

1. 要尋找 Linux 電腦上的環境變數`DISPLAY`的值,請執行以下指令:

   ```cmd
   echo $DISPLAY
   ```

   在 AppBasicExampleGui 的配置中,有一個參數陣列「pipeArgs」。。 它包含一行:"$[調試器命令]"。 它是在遠端電腦上啟動 gdb 的命令。 可視化工作室必須在該命令運行之前將顯示器匯出到此上下文中。 例如,如果顯示的值為`:1`,請修改該行,如下所示:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. 啟動和調試應用程式。 在工具列中開啟 **「選擇啟動項目**」下拉清單,然後選擇**AppBasicExampleGui**。 接下來,選擇工具列中的綠色播放圖示,或按**F5**。 應用程式及其依賴項構建在遠端 Linux 電腦上,然後隨附加 Visual Studio 調試器一起啟動。 在您的遠端 Linux 電腦上，您應該會看到應用程式視窗。

1. 將滑鼠移到應用程式視窗中,然後按一下按鈕。 斷點被命中。 程式執行暫停,Visual Studio 回到前臺,您將看到斷點。 您也應該會在 Visual Studio 中看到 Linux 主控台視窗。 該視窗提供來自遠端 Linux 計算機的輸出,並且它`stdin`還可以接受的輸入。 與任何 Visual Studio 視窗一樣,您可以將其停靠在您喜歡查看的位置。 它的立場在未來的屆會中保持不變。

   ![Visual Studio Linux 主控台視窗](media/cmake-bullet3-linux-console.png)

1. 您可以檢查應用程式變數、物件、執行緒、記憶體，並使用 Visual Studio 以互動方式逐一檢查程式碼。 但是這一次,你所做的都是在遠端 Linux 電腦上,而不是本地的 Windows 環境中。 您可以選擇 **「繼續**」以讓應用程式正常恢復和退出,也可以選擇停止按鈕,就像本地執行一樣。

1. 查看 [呼叫堆疊] 視窗，並檢視 `x11OpenGLWindow` 呼叫，因為 Visual Studio 是在 Linux 上啟動應用程式。

   ![顯示 Linux 呼叫堆疊的 [呼叫堆疊] 視窗](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>您已了解到

在本教學中,您直接從 GitHub 複製了一個程式庫。 您無需修改即可在 Windows 上生成、運行和調試它。 然後,使用相同的代碼庫(具有次要的配置更改)在遠端 Linux 電腦上生成、運行和調試。

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
