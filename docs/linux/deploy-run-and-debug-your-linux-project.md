---
title: 在 Visual Studio 中部署及執行您的 C++ Linux 專案以及針對其進行偵錯
description: 描述如何在 Visual Studio 中，從 Linux C++ 專案中在遠端目標上進行程式碼編譯、執行和偵錯。
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 70770385bde859d47532b130463a1cc54e32a570
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042759"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>部署、執行和偵錯 Linux 專案

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

在 Visual Studio 中建立 Linux C++ 專案並使用 [Linux 連線管理員](connect-to-your-remote-linux-computer.md)連線至專案後，即可執行與偵錯專案。 您可以在遠端目標上編譯、執行及偵錯程式碼。

::: moniker range="vs-2019"

**Visual Studio 2019 16.1 版**：您能夠以不同 Linux 系統為目標來進行偵錯和建置。 例如，以 IoT 案例為目標時，您可以在 x64 上交叉編譯並部署到 ARM 裝置。 如需詳細資訊，請參閱本文稍後的[針對建置與偵錯指定不同的電腦](#separate_build_debug)。

::: moniker-end

有數種方式可以與 Linux 專案互動，並對其進行偵錯。

- 使用中斷點、監看式視窗以及將滑鼠指標停留在變數上等傳統 Visual Studio 功能進行偵錯。 使用這些方法，可讓您以對其他專案類型所使用的一般方式進行偵錯。

- 在 Linux 主控台視窗中檢視目標電腦的輸出。 您也可以使用主控台將輸出傳送到目標電腦。

## <a name="debug-your-linux-project"></a>對 Linux 專案進行偵錯

1. 在 [偵錯]  屬性頁面中選取偵錯模式。
   
   ::: moniker range="vs-2019"

   GDB 用來偵錯在 Linux 上執行的應用程式。 在遠端系統 (而不是 WSL) 上進行偵錯時，GDB 可以透過兩種不同的模式執行，而您可以從專案 [偵錯]  屬性頁的 [偵錯模式]  選項中進行選取：

   ![GDB 選項](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB 用來偵錯在 Linux 上執行的應用程式。 GDB 可以透過兩種不同的模式執行，而您可以從專案 [偵錯]  屬性頁的 [偵錯模式]  選項中進行選取：

   ![GDB 選項](media/vs2017-debugger-settings.png)

   ::: moniker-end


   - 在 **gdbserver** 模式中，GDB 會在本機執行，以連線到在遠端系統上的 gdbserver。  請注意，這是 Linux 主控台視窗唯一支援的模式。

   - 在 **gdb** 模式中，Visual Studio 偵錯工具會在遠端系統上驅動 GDB。 若本機版本的 GDB 和目標電腦上安裝的版本不相容，此為較佳的選項。 |

   > [!NOTE]
   > 若無法在 gdbserver 偵錯模式中叫用中斷電，請嘗試 gdb 模式。 必須先在遠端目標上[安裝](download-install-and-setup-the-linux-development-workload.md) gdb。

1. 在 Visual Studio 中使用標準 [偵錯]  工具列選取遠端目標。

   當遠端目標可用時，該目標會以名稱或 IP 位址的形式列出。

   ![遠端目標](media/remote_target.png)

   若尚未連線至遠端目標，您會看到使用 [Linux 連線管理員](connect-to-your-remote-linux-computer.md) 以連線到遠端目標的指示。

   ![遠端架構](media/architecture.png)

1. 在某些您認定會執行之程式碼的左側裝訂邊上按一下，即可設定中斷點。

   在您設定中斷點的程式碼上會顯示紅點。

1. 按一下 **F5** (或 [偵錯] > [開始偵錯]  ) 以開始偵錯。

   當您開始偵錯時，應用程式會在啟動前於遠端目標上編譯。 任何編譯錯誤都會顯示在 [錯誤清單]  視窗中。

   如果沒有任何錯誤，應用程式就會啟動，而偵錯工具則會在中斷點暫停。

   ![叫用中斷點](media/hit_breakpoint.png)

   您現在可以和目前狀態下的應用程式互動、檢視變數，以及按 **F10** 或 **F11** 等命令鍵逐步完成程式碼。

1. 若想使用 Linux 主控台與應用程式互動，請選取 [偵錯] > [Linux 主控台]  。

   ![Linux 主控台功能表](media/consolemenu.png)

   此主控台將會顯示來自目標電腦的任何主控台輸出，以及接受輸入，並將其傳送至目標電腦。

   ![Linux 主控台視窗](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>設定其他偵錯選項 (MSBuild 型專案)

- 使用專案 [偵錯]  屬性頁中的 [程式引數]  項目，即可將命令列引數傳遞至可執行檔。

   ![程式引數](media/settings_programarguments.png)

- 使用 [其他偵錯工具命令]  項目，可以將特定偵錯工具選項傳遞至 GDB。  例如，您可能想要忽略 SIGILL (不合法指令) 訊號。  您可以將下列項目新增至 [其他偵錯工具命令]  項目 (如上所示)，以便使用 **handle** 命令達成此目的：

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>設定其他偵錯選項 (CMake 專案)

您可以在 launch.vs.json 檔案中，為 CMake 專案指定其他命令列引數。 如需詳細資訊，請參閱[為 CMake 專案偵錯](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>使用 [附加至處理序] 進行偵錯

Visual Studio 專案的 [偵錯](prop-pages/debugging-linux.md) 屬性頁和 CMake 專案的 [Launch.vs.json]  設定，具有可讓您附加至執行中處理序的設定。 如果您需要這些設定所提供項目之外的其他控制項，您可以將名為 `Microsoft.MIEngine.Options.xml` 的檔案放在解決方案或工作區的根目錄中。 以下是一個簡單的範例：

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

**AttachOptionsForConnection** 具有大部分您可能需要的屬性。 上述範例示範如何指定要用來搜尋其他 .so 程式庫的位置。 子元素 **ServerOptions** 可讓您改為附加至 gdbserver 的遠端程序。 若要這樣做，您需要使用符號指定本機 gdb 用戶端 (隨附於 Visual Studio 2017 的用戶端，如上所示) 和二進位檔的本機複本。 **SetupCommands** 元素可讓您直接傳遞至 gdb 命令。 您可以在 GitHub 上找到 [LaunchOptions.xsd 結構描述](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) 的所有可用選項。

::: moniker range="vs-2019"

## <a name="separate_build_debug"></a> 針對建置與偵錯指定不同的電腦

在 Visual Studio 2019 16.1 版中，您可以將您的遠端組建電腦與遠端偵錯電腦分開，以便用於 MSBuild 型 Linux 專案和以遠端 Linux 電腦為目標的 CMake 專案。 例如，以 IoT 案例為目標時，您現在可以在 x64 上交叉編譯並部署到 ARM 裝置。

### <a name="msbuild-based-projects"></a>MSBuild 型專案

根據預設，遠端偵錯電腦與遠端組建電腦 ([組態屬性]   > [一般]   > [遠端組建電腦]  ) 相同。 若要指定新的遠端偵錯電腦，以滑鼠右鍵按一下 [方案總管]  中的專案，並移至 [組態屬性]   > [偵錯]   > [遠端偵錯電腦]  。  

![Linux 遠端偵錯電腦](media/linux-remote-debug-machine.png)

[遠端偵錯電腦]  的下拉式功能表會填入所有已建立的遠端連線。 若要新增遠端連線，請瀏覽至 [工具]   > [選項]   > [跨平台]   > [連線管理員]  ，或在 [快速啟動]  中搜尋「連線管理員」。 您也可以在專案的 [屬性頁] 中指定新的遠端部署目錄 ([組態屬性]   > [一般]   > [遠端部署目錄]  )。

根據預設，只有處理序偵錯所需的檔案會部署到遠端偵錯電腦。 您可以使用 [方案總管]  設定部署到遠端偵錯電腦的原始程式檔。 當您按一下原始程式檔時，您會看到 [方案總管] 正下方的 [檔案內容] 預覽。

![Linux 可部署的檔案](media/linux-deployable-content.png)

[內容]  屬性會指定是否將檔案部署到遠端偵錯電腦。 若要完全停用部署，請瀏覽至 [屬性頁]   > [組態管理員]  ，然後針對所需的組態，取消核取 [部署]  。

在某些情況下，您可能需要更充分掌控您的專案部署。 例如，您想要部署的某些檔案可能是您的解決方案之外，或您想要針對每個檔案或目錄自訂您的遠端部署目錄。 在這些情況下，將下列程式碼區塊附加至 .vcxproj 檔案，並以實際的檔案名稱取代 "example.cpp"：

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

IntelliSense 將會建議所有已建立之遠端連線的所有清單。 若要新增遠端連線，請瀏覽至 [工具]   > [選項]   > [跨平台]   > [連線管理員]  ，或在 [快速啟動]  中搜尋「連線管理員」。

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

- 若要偵錯 Linux 上的 ARM 裝置，請參閱此部落格文章：[在 Visual Studio 中偵錯內嵌 ARM 裝置](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/)。

## <a name="see-also"></a>另請參閱

[C++ 偵錯屬性 (Linux C++)](prop-pages/debugging-linux.md)
