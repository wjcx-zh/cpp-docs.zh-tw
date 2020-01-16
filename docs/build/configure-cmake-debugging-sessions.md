---
title: 在 Visual Studio 中設定 CMake 偵錯工作階段
description: 描述如何使用 Visual Studio 來設定 CMake 偵錯工具設定
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 5e627f02b5245baede6e92268cedfc43957f3abc
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031333"
---
# <a name="configure-cmake-debugging-sessions"></a>設定 CMake 偵錯工作階段

::: moniker range="vs-2015"

Visual Studio 2017 和更新版本提供原生 CMake 支援。

::: moniker-end

::: moniker range=">=vs-2017"

[一般] 工具列的 [啟動項目] 下拉式清單中會顯示所有可執行的 CMake 目標。 若要啟動偵錯工作階段，只要選取其中一個目標並啟動偵錯工具即可。

![CMake 啟始專案下拉式清單](media/cmake-startup-item-dropdown.png "CMake 啟始專案下拉式清單")

您也可以從方案總管啟動 debug 會話。 首先，切換至 [**方案總管**] 視窗中的 [ **CMake 目標**]。

![CMake 目標視圖按鈕](media/cmake-targets-view.png  "CMake 目標 View 功能表項目")

然後，在任何可執行檔上按一下滑鼠右鍵，然後選取 [ **debug** ] 或 [ **Debug and 啟動設定**]。 [ **Debug** ] 會根據您的使用中設定，自動開始對選取的目標進行偵錯工具。 [**偵錯工具和啟動設定**] 會開啟 [*啟動檔案與 json*檔案]，並為選取的目標加入新的 [debug] 設定。

## <a name="customize-debugger-settings"></a>自訂偵錯工具設定

您可以在名為 [*啟動. vs. json*] 的檔案中，自訂專案中任何可執行 CMake 目標的偵錯工具設定。 此檔案有三個進入點：

- 從主功能表選取 [ **debug] > debug And 啟動 $ {activeDebugTarget}** 的 [設定]，以編輯作用中 debug 目標的特定 Debug 設定。 如果您未選取作用中的目標，這個選項將會呈現灰色。

- 流覽至方案總管中的 [**目標] View** 。 然後，以滑鼠右鍵按一下 [debug] 目標，然後選取 [ **debug And 啟動設定**]，以編輯所選目標特定的偵錯工具設定。

- 以滑鼠右鍵按一下根 Remote monitoring.h cmakelists.txt，然後選取 [ **Debug And 啟動設定**] 以開啟 [**選取偵錯工具**] 對話方塊。 此對話方塊可讓您新增任何 debug 設定，但您必須手動指定要透過 `projectTarget` 屬性叫用的 CMake 目標。

若要參考*CMakeSettings json*檔案中的任何索引鍵，請在其前面加上*啟動. 與 json*中的 `cmake.`。 下列範例顯示簡單的*啟動檔案與 json*檔案，該檔案會針對目前選取的設定，提取*CMakeSettings*中 `remoteCopySources` 機碼的值：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

當您儲存*與 json*檔案時，Visual Studio 會在 [**啟動專案**] 下拉式清單中建立新名稱的專案。 您可以編輯*啟動檔案與 json*檔案，為任何數目的 CMake 目標建立多個偵錯工具設定。

## <a name="launchvsjson-reference"></a>啟動. 與 json 參考

有許多*啟動和 json*屬性可支援您的所有偵錯工具案例。 下列屬性通用於所有的調試設定，包括遠端和本機：

- `projectTarget`：指定建立專案時要叫用的 CMake 目標。 Visual Studio 會自動此屬性。如果您*從*debug > 中輸入 [activeDebugTarget}] 或 [**目標] 視圖** **的 debug 和啟動設定**。

- `program`：遠端系統上程式可執行檔的完整路徑。 您可以在這裡使用宏 `${debugInfo.fullTargetPath}`。

- `args`：傳遞給程式以進行 debug 的命令列引數。

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>適用于遠端 Linux 專案的啟動與 json 參考

下列屬性是**遠端 debug**設定特有的。 您也可以[執行自訂 gdb 命令](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)，將命令直接傳送至基礎偵錯工具，並[啟用 MIEngine 記錄](https://github.com/microsoft/MIEngine/wiki/Logging)來查看傳送給 gdb 的命令、要傳回哪些輸出 gdb，以及每個命令所需的時間長度。

- `cwd`：在遠端電腦上尋找相依性和其他檔案的目前工作目錄。 您可以使用宏 `${debugInfo.defaultWorkingDirectory}`。 除非在*remote monitoring.h cmakelists.txt*中覆寫，否則預設值為遠端工作區根目錄。 此屬性僅用於遠端設定;`currentDir` 可用來為本機專案設定啟動應用程式的目前目錄。

- `environment`：使用此語法新增至程式環境的其他環境變數：

```json
  "environment": [
      {
        "name": "ENV1",
        "value": "envvalue1"
      },
      {
        "name": "ENV2",
        "value": "envvalue2"
      }
    ]
```

- `pipeArgs`：傳遞至管道程式以設定連接的命令列引數。 管道程式是用來轉送 Visual Studio 與 gdb 之間的標準輸入/輸出。 命令 `${debuggerCommand}` 會在遠端系統上啟動 gdb，而且可以修改為：

  - 匯出 Linux 系統上的環境變數顯示值。 在下列範例中，這個值是 `:1`。

  ```json
  "pipeArgs": [
      "/s",
      "${debugInfo.remoteMachineId}",
      "/p",
      "${debugInfo.parentProcessId}",
      "/c",
      "export DISPLAY=:1;${debuggerCommand}",
      "--tty=${debugInfo.tty}"
    ],
  ```

  - 在執行 gdb 之前先執行腳本。 請確定已在您的腳本上設定執行許可權。

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`：布林值，指定是否要在啟動進程時立即中斷。 預設為 false。

- `visualizerFile`：要在對這個進程進行偵錯工具時使用的[natvis](/visualstudio/debugger/create-custom-views-of-native-objects)檔案。 此選項與 gdb 整齊的列印不相容。 當您設定此屬性時，也請設定 `showDisplayString`。

- `showDisplayString`：在指定 `visualizerFile` 時啟用顯示字串的布林值。 將此選項設定為 `true` 可能會在進行調試過程時導致效能變慢。

- `setupCommands`：要執行的一或多個 gdb 命令，以設定基礎偵錯工具。

- `externalConsole`：布林值，指定是否為偵錯工具啟動主控台。

- `miDebuggerPath`： gdb 的完整路徑。 若未指定，Visual Studio 會先針對偵錯工具搜尋路徑。

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`：裝載 gdb 和程式來進行 debug 的遠端 Linux 系統。

::: moniker-end

::: moniker range="vs-2019"

下列屬性可用來將您的**遠端組建系統**與**遠端偵錯程式系統**分開。 如需詳細資訊，請參閱[指定不同的機器來建立和偵錯工具](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects)。

- `remoteMachineName`：裝載 gdb 和程式來進行 debug 的遠端 Linux 系統。 此專案不需要符合*CMakeSettings*中指定之組建所使用的遠端 Linux 系統。 按**Ctrl + 空格鍵**，即可查看儲存在[連接管理員](../linux/connect-to-your-remote-linux-computer.md)中的所有遠端連線的清單。

- `disableDeploy`：指出是否停用組建/調試區分隔。 啟用時，此功能可讓您在兩部不同的電腦上進行組建和 debug。

- `deployDirectory`：遠端偵錯程式的目錄（由 `remoteMachineName`所指定），可執行檔將會複製到該電腦上。

- `deploy`：先進部署設定的陣列。 當您想要更細微地控制部署程式時，您只需要設定這些設定。 根據預設，只有處理序偵錯所需的檔案會部署到遠端偵錯電腦。

  - `sourceMachine`：將從中複製檔案或目錄的電腦。 按**Ctrl + 空格鍵**，即可查看儲存在連接管理員中的所有遠端連線的清單。

  - `targetMachine`：將複製檔案或目錄的目的電腦。 按**Ctrl + 空格鍵**，即可查看儲存在連接管理員中的所有遠端連線的清單。

  - `sourcePath`： `sourceMachine`上的檔案或目錄位置。

  - `targetPath`： `targetMachine`上的檔案或目錄位置。

  - `deploymentType`：部署類型的描述。 支援 `LocalRemote` 和 `RemoteRemote`。 `LocalRemote` 表示從本機檔案系統複製到啟動中 `remoteMachineName` 所指定的遠端系統。*與 json*。 `RemoteRemote` 表示從*CMakeSettings*中指定的遠端組建系統複製到*啟動*時所指定的不同遠端系統。

  - `executable`：指出部署的檔案是否為可執行檔。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>附加至遠端進程

您可以將 `processId` 設定為要附加偵錯工具的處理序識別碼，以附加至在 Linux 系統上執行的進程。 如需詳細資訊，請參閱[使用 GDB 進行附加至進程的疑難排解](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>使用 gdbserver 在 Linux 上進行調試

Visual Studio 2019 16.5 Preview 1 或更新版本支援使用 gdbserver 進行 CMake 專案的遠端偵錯。 如需詳細資訊，請參閱[使用 gdbserver 來對 Linux CMake 專案進行調試](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)程式。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>請參閱

[Visual Studio\ 中的 CMake 專案](cmake-projects-in-visual-studio.md)
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)\
[連接到您的遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)\
[自訂 CMake 組建設定](customize-cmake-settings.md)\
[設定 CMake 的調試階段](configure-cmake-debugging-sessions.md)\
[部署、執行及偵錯工具您的 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)

::: moniker-end
