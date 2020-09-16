---
title: 在 Visual Studio 中部署、執行和調試您的 Linux MSBuild c + + 專案
description: 描述如何從 Visual Studio 中的 MSBuild 型 Linux c + + 專案，在遠端目標上編譯、執行和偵錯工具代碼。
ms.date: 08/08/2020
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 4200e30b445f4a09fc60083db0067996c96ea953
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686700"
---
# <a name="deploy-run-and-debug-your-linux-msbuild-project"></a>部署、執行 Linux MSBuild 專案及對其進行偵錯

::: moniker range="vs-2015"
Visual Studio 2017 及更新版本支援 Linux。 若要查看這些版本的檔，請將位於目錄上方的 **版本** 下拉式清單設定為 **Visual Studio 2017** 或 **Visual Studio 2019**。
::: moniker-end

當您在 Visual Studio 中建立以 MSBuild 為基礎的 Linux c + + 專案，而且已使用 [Linux 連線管理員](connect-to-your-remote-linux-computer.md)連接到專案之後，您就可以執行和調試專案。 您可以在遠端目標上編譯、執行及偵錯程式碼。

::: moniker range="vs-2019"

**Visual Studio 2019 16.1 版**：您能夠以不同 Linux 系統為目標來進行偵錯和建置。 例如，以 IoT 案例為目標時，您可以在 x64 上交叉編譯並部署到 ARM 裝置。 如需詳細資訊，請參閱本文稍後的[針對建置與偵錯指定不同的電腦](#separate_build_debug)。

::: moniker-end

有數種方式可以與 Linux 專案互動，並對其進行偵錯。

- 使用中斷點、監看式視窗以及將滑鼠指標停留在變數上等傳統 Visual Studio 功能進行偵錯。 使用這些方法，可讓您以對其他專案類型所使用的一般方式進行偵錯。

- 在 Linux 主控台視窗中檢視目標電腦的輸出。 您也可以使用主控台將輸出傳送到目標電腦。

## <a name="debug-your-linux-project"></a>對 Linux 專案進行偵錯

1. 在 [偵錯]**** 屬性頁面中選取偵錯模式。

   ::: moniker range="vs-2019"

   GDB 用來偵錯在 Linux 上執行的應用程式。 在遠端系統 (而不是 WSL) 上進行偵錯時，GDB 可以透過兩種不同的模式執行，而您可以從專案 [偵錯]**** 屬性頁的 [偵錯模式]**** 選項中進行選取：

   ![Visual Studio 2019 Linux 主控台應用程式 [屬性頁] 對話方塊的螢幕擷取畫面，其中包含已選取 G B D 的設定屬性 > 偵錯工具已反白顯示，且已從下拉式清單中反白顯示。](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB 用來偵錯在 Linux 上執行的應用程式。 GDB 可以透過兩種不同的模式執行，而您可以從專案 [偵錯]**** 屬性頁的 [偵錯模式]**** 選項中進行選取：

   ![Visual Studio 2017 Linux 主控台應用程式 [屬性頁] 對話方塊的螢幕擷取畫面，其中包含已選取 G B D 的設定屬性 > 偵錯工具已反白顯示，且已從下拉式清單中反白顯示。](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - 在 **gdbserver** 模式中，GDB 會在本機執行，以連線到在遠端系統上的 gdbserver。

   - 在 **gdb** 模式中，Visual Studio 偵錯工具會在遠端系統上驅動 GDB。 如果本機版本的 GDB 與目的電腦上安裝的版本不相容，這是較好的選項。 這是 Linux 主控台視窗唯一支援的模式。

   > [!NOTE]
   > 若無法在 gdbserver 偵錯模式中叫用中斷電，請嘗試 gdb 模式。 必須先在遠端目標上[安裝](download-install-and-setup-the-linux-development-workload.md) gdb。

1. 在 Visual Studio 中使用標準 [偵錯]**** 工具列選取遠端目標。

   當遠端目標可供使用時，您會看到它以 [名稱] 或 [IP 位址] 列出。

   ![遠端目標](media/remote_target.png)

   如果您尚未連線到遠端目標，您將會看到使用 [Linux 連線管理員](connect-to-your-remote-linux-computer.md) 連接到遠端目標的指示。

   ![遠端架構](media/architecture.png)

1. 在某些您認定會執行之程式碼的左側裝訂邊上按一下，即可設定中斷點。

   在您設定中斷點的程式碼上會顯示紅點。

1. 按一下 **F5** (或 [偵錯] > [開始偵錯]****) 以開始偵錯。

   當您開始偵錯時，應用程式會在啟動前於遠端目標上編譯。 任何編譯錯誤都會顯示在 [錯誤清單]**** 視窗中。

   如果沒有任何錯誤，應用程式就會啟動，而偵錯工具則會在中斷點暫停。

   ![叫用中斷點](media/hit_breakpoint.png)

   現在，您可以在應用程式的目前狀態下互動、查看變數，然後按下命令鍵（例如 **F10** 或 **F11**）逐步執行程式碼。

1. 若想使用 Linux 主控台與應用程式互動，請選取 [偵錯] > [Linux 主控台]****。

   ![Linux 主控台功能表](media/consolemenu.png)

   此主控台會顯示來自目的電腦的任何主控台輸出，並取得輸入並將其傳送至目的電腦。

   ![Linux 主控台視窗](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-projects"></a> (MSBuild 專案設定其他調試選項) 

- 使用專案 [偵錯]**** 屬性頁中的 [程式引數]**** 項目，即可將命令列引數傳遞至可執行檔。
- 您可以 `DISPLAY` 使用專案的 [**調試**程式] 屬性頁中的 [**預先啟動] 命令**來匯出環境變數。 例如：`export DISPLAY=:0.0`

   ![程式引數](media/settings_programarguments.png)

- 使用 [其他偵錯工具命令]**** 項目，可以將特定偵錯工具選項傳遞至 GDB。  例如，您可能想要忽略 SIGILL (不合法指令) 訊號。  您可以將下列項目新增至 [其他偵錯工具命令]**** 項目 (如上所示)，以便使用 **handle** 命令達成此目的：

   `handle SIGILL nostop noprint`

## <a name="debug-with-attach-to-process"></a>使用 [附加至處理序] 進行偵錯

Visual Studio 專案的 [偵錯](prop-pages/debugging-linux.md) 屬性頁和 CMake 專案的 [Launch.vs.json]**** 設定，具有可讓您附加至執行中處理序的設定。 如果您需要這些設定所提供項目之外的其他控制項，您可以將名為 `Microsoft.MIEngine.Options.xml` 的檔案放在解決方案或工作區的根目錄中。 以下是一個簡單的範例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

**AttachOptionsForConnection** 具有大部分您可能需要的屬性。 上述範例示範如何指定要用來搜尋其他 .so 程式庫的位置。 子元素 **ServerOptions** 可讓您改為附加至 gdbserver 的遠端程序。 若要這樣做，您必須指定本機 gdb 用戶端 (Visual Studio 2017 中隨附的用戶端會顯示在上方) 和二進位檔的本機複本，並包含符號。 **SetupCommands** 元素可讓您直接傳遞至 gdb 命令。 您可以在 GitHub 上找到 [LaunchOptions.xsd 結構描述](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) 的所有可用選項。

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging-in-msbuild-based-linux-projects"></a><a name="separate_build_debug"></a> 在以 MSBuild 為基礎的 Linux 專案中，指定不同的電腦來建立和偵錯工具

在 Visual Studio 2019 16.1 版中，您可以針對以 MSBuild 為基礎的 Linux 專案和以遠端 Linux 電腦為目標的 CMake 專案，將遠端組建電腦與遠端偵錯程式區隔開。 例如，以 IoT 案例為目標時，您現在可以在 x64 上交叉編譯並部署到 ARM 裝置。

根據預設，遠端偵錯程式與遠端組建電腦**相同 (設定**內容  >  **一般**  >  **遠端組建電腦**) 。 若要指定新的遠端偵錯電腦，以滑鼠右鍵按一下 [方案總管]**** 中的專案，並移至 [組態屬性]**** > [偵錯]**** > [遠端偵錯電腦]****。  

![Linux 遠端偵錯電腦](media/linux-remote-debug-machine.png)

[遠端偵錯電腦]**** 的下拉式功能表會填入所有已建立的遠端連線。 若要加入新的遠端連線，請流覽至 [**工具**  >  **選項**  >  ]**跨平臺**  >  **連線管理員**，或在**快速啟動**中搜尋 "連線管理員"。 您也可以在專案的 [屬性] 頁面中指定新的遠端部署目錄 **， (設定**內容  >  **一般**  >  **遠端部署目錄**) 。

根據預設，只有處理序偵錯所需的檔案會部署到遠端偵錯電腦。 您可以使用 [方案總管]**** 設定部署到遠端偵錯電腦的原始程式檔。 當您按一下原始程式檔時，您會在方案總管的正下方看到其檔案屬性的預覽。

![Linux 可部署的檔案](media/linux-deployable-content.png)

[內容]**** 屬性會指定是否將檔案部署到遠端偵錯電腦。 您可以流覽至 [**屬性頁**]  >  **Configuration Manager** ，並取消核取所需的設定 **，以完全**停用部署。

在某些情況下，您可能需要更充分掌控專案的部署。 例如，您想要部署的某些檔案可能會在解決方案之外，或是您想要針對每個檔案或目錄自訂遠端部署目錄。 在這些情況下，將下列程式碼區塊附加至 .vcxproj 檔案，並以實際的檔案名稱取代 "example.cpp"：

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>CMake 專案

針對以遠端 Linux 電腦為目標的 CMake 專案，您可以在 launch.vs.json 中指定新的遠端偵錯電腦。 根據預設，"remoteMachineName" 的值會與 CMakeSettings.json 中，對應至您遠端組建電腦的 "remoteMachineName" 屬性同步處理。 這些屬性不再需要比對，而且 launch.vs.json 中的 "remoteMachineName" 值將會指定用於部署和偵錯的遠端電腦。

![CMake 遠端偵錯電腦](media/cmake-remote-debug-machine.png)

IntelliSense 將會建議所有已建立之遠端連線的所有清單。 您可以藉由流覽至 [**工具**  >  **選項**]  >  **跨平臺**  >  **連線管理員**，或在**快速啟動**中搜尋 "連線管理員" 來新增遠端連線。

如果您想要完整控制部署，可以將下列程式碼區塊附加到 launch.vs.json 檔案。 請記得以實際的值取代預留位置值：

```json
"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]
```

::: moniker-end

## <a name="next-steps"></a>後續步驟

- 若要在 Linux 上偵錯 ARM 裝置，請參閱此部落格文章：[Debugging an embedded ARM device in Visual Studio](https://devblogs.microsoft.com/cppblog/debugging-an-embedded-arm-device-in-visual-studio/) (在 Visual Studio 中對內嵌 ARM 裝置進行偵錯)。

## <a name="see-also"></a>另請參閱

[C++ 偵錯屬性 (Linux C++)](prop-pages/debugging-linux.md)
