---
title: 在 Visual Studio 中設定 CMake 偵錯工作階段
description: 描述如何使用 Visual Studio 來設定 CMake 偵錯工具設定。
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328821"
---
# <a name="configure-cmake-debugging-sessions"></a>設定 CMake 偵錯工作階段

::: moniker range="vs-2015"

Visual Studio 2017 和更新版本提供原生 CMake 支援。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end

::: moniker range=">=vs-2017"

[一般]**** 工具列的 [啟動項目]**** 下拉式清單中會顯示所有可執行的 CMake 目標。 選取其中一個來啟動偵錯工具，並啟動偵錯工具。

![CMake 啟始專案下拉式清單](media/cmake-startup-item-dropdown.png "CMake 啟始專案下拉式清單")

您也可以從方案總管啟動 debug 會話。 首先，切換至 [**方案總管**] 視窗中的 [ **CMake 目標**]。

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png  "CMake 目標 View 功能表項目")

然後，以滑鼠右鍵按一下可執行檔，然後選取 [ **Debug**]。 此命令會根據您的使用中設定，自動開始對選取的目標進行偵錯工具。

## <a name="customize-debugger-settings"></a>自訂偵錯工具設定

您可以針對專案中任何可執行檔 CMake 目標自訂偵錯工具設定。 這些檔案位於名為 [*啟動. vs. json*] 的設定檔中， *`.vs`* 位於專案根目錄的資料夾中。 啟動設定檔在大部分的偵錯工具案例中很有用，因為您可以設定並儲存您的偵錯工具設定詳細資料。 此檔案有三個進入點：

- [**調試] 功能表：** 從主功能表選取 [ **debug] > debug And 啟動 $ {activeDebugTarget}** 的 [設定]，以自訂作用中 debug 目標的特定 Debug 設定。 如果您未選取 [debug] 目標，此選項會呈現灰色。

![[調試] 功能表進入點](media/cmake-debug-menu.png "[調試] 功能表進入點")

- **目標 View：** 流覽至方案總管中的 [**目標] View** 。 然後，以滑鼠右鍵按一下 debug 目標，然後選取 [新增] [**調試**設定]，以自訂所選目標的特定調試設定。

![目標 view 進入點](media/cmake-targets-add-debug-configuration.png "目標 view 進入點")

- **根 remote monitoring.h cmakelists.txt .txt：** 以滑鼠右鍵按一下根*remote monitoring.h cmakelists.txt* ，然後選取 [**新增**] [偵測設定] 以開啟 [**選取偵錯工具**] 對話方塊。 此對話方塊可讓您新增*任何*類型的 debug 設定，但您必須手動指定要透過`projectTarget`屬性叫用的 CMake 目標。

![[選取偵錯工具] 對話方塊](media/cmake-select-a-debugger.png "[選取偵錯工具] 對話方塊")

您可以編輯*啟動檔案與 json*檔案，為任何數目的 CMake 目標建立偵錯工具設定。 當您儲存檔案時，Visual Studio 會在 [**啟動專案**] 下拉式清單中為每個新的設定建立專案。

## <a name="reference-keys-in-cmakesettingsjson"></a>CMakeSettings 中的參考索引鍵

若要參考*CMakeSettings json*檔案中的任何索引鍵， `cmake.`請在 [啟動] 中加上其前面的 [*與 json*]。 下列範例顯示簡單的*啟動檔案與 json*檔案，此檔案會針對目前選取的設定`remoteCopySources` ，提取*CMakeSettings*中的機碼值：

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

在*CMakeSettings*中定義的`${env.VARIABLE_NAME}`**環境變數**也可以在使用語法的 [啟動] 和 [json] 中使用。 在 Visual Studio 2019 16.4 版和更新版本中，會使用您在*CMakeSettings*中指定的環境，自動啟動 debug 目標。 您可以將環境變數設定為**null**，以將其取消設定。

## <a name="launchvsjson-reference"></a>啟動. 與 json 參考

有許多*啟動和 json*屬性可支援您的所有偵錯工具案例。 下列屬性通用於所有的調試設定，包括遠端和本機：

- `projectTarget`：指定要在建立專案時叫用的 CMake 目標。 如果您從 [**調試] 功能表**或 [**目標] 視圖**輸入 [*啟動. vs. json* ]，Visual Studio 會自動此屬性。 這個值必須符合 [**啟動專案**] 下拉式清單中所列的現有 [偵錯工具] 目標名稱。

- `env`：要使用語法新增的其他環境變數：

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`：傳遞給程式以進行 debug 的命令列引數。

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>針對遠端專案和 WSL，啟動. vs. json 參考

在 Visual Studio 2019 16.6 版中，我們新增了的`type: cppgdb`新 debug 設定，以簡化遠端系統和 WSL 的調試。 仍然支援舊的`type: cppdbg` debug 設定。

### <a name="configuration-type-cppgdb"></a>設定類型`cppgdb`

- `name`：用來識別 [**啟動專案**] 下拉式清單中設定的易記名稱。
- `project`：指定專案檔的相對路徑。 一般來說，在調試 CMake 專案時，您不需要變更此路徑。
- `projectTarget`：指定要在建立專案時叫用的 CMake 目標。 如果您從 [**調試] 功能表**或 [**目標] 視圖**輸入 [*啟動. vs. json* ]，Visual Studio 會自動此屬性。 此目標值必須符合 [**啟動專案**] 下拉式清單中所列的現有 [偵錯工具] 目標名稱。
- `debuggerConfiguration`：表示要使用的一組調試預設值。 在 Visual Studio 2019 16.6 版中，唯一有效的選項`gdb`是。 較舊的版本`gdbserver`也支援。
- `args`：啟動時傳遞至正在進行偵錯工具的命令列引數。
- `env`：傳遞給正在進行偵錯工具的其他環境變數。 例如： `{"DISPLAY": "0.0"}` 。
- `processID`：要附加的 Linux 處理序識別碼。 只有在附加至遠端進程時才會使用。 如需詳細資訊，請參閱[使用 GDB 進行附加至進程的疑難排解](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

#### <a name="additional-options-for-the-gdb-configuration"></a>設定的其他選項`gdb`

- `program`：預設為`"${debugInfo.fullTargetPath}"`。 要進行偵錯工具的 Unix 路徑。 只有在組建或部署位置中的目標可執行檔不同時才需要。
- `remoteMachineName`：預設為`"${debugInfo.remoteMachineName}"`。 主控程式來進行 debug 的遠端系統名稱。 只有在與組建系統不同時才需要。 在[連線管理員](../linux/connect-to-your-remote-linux-computer.md)中必須有現有的專案。 按**Ctrl + 空格鍵**，以查看所有現有遠端連線的清單。
- `cwd`：預設為`"${debugInfo.defaultWorkingDirectory}"`。 遠端系統`program`上執行之目錄的 Unix 路徑。 此目錄必須已存在。
- `gdbpath`：預設為`/usr/bin/gdb`。 用來進行 debug 的`gdb`完整 Unix 路徑。 只有在使用自訂版本的`gdb`時才需要。
- `preDebugCommand`：要在叫用之前立即執行的`gdb`Linux 命令。 `gdb`在命令完成之前不會啟動。 您可以使用選項，在執行之前先執行腳本`gdb`。

#### <a name="deployment-options"></a>部署選項

使用下列選項，將您的組建電腦（定義于 CMakeSettings 中）與遠端偵錯程式隔開。

- `remoteMachineName`：遠端 debug 電腦。 只有在與組建電腦不同時才需要。 在[連線管理員](../linux/connect-to-your-remote-linux-computer.md)中必須有現有的專案。 按**Ctrl + 空格鍵**，以查看所有現有遠端連線的清單。
- `disableDeploy`：預設為`false`。 指出是否停用組建/調試區分隔。 當`false`時，此選項允許在兩部不同的電腦上執行組建和 debug。
- `deployDirectory`：要將可執行檔案複製到`remoteMachineName`其中之目錄的完整 Unix 路徑。
- `deploy`：先進部署設定的陣列。 當您想要更細微地控制部署程式時，您只需要設定這些設定。 根據預設，只會將進行 debug 的程式所需的檔案部署到遠端的「偵錯工具」電腦。
  - `sourceMachine`：複製檔案或目錄的來源電腦。 按**Ctrl + 空格鍵**，即可查看儲存在連接管理員中的所有遠端連線的清單。 在 WSL 上以原生方式建立時，會忽略此選項。
  - `targetMachine`：複製檔案或目錄的目的電腦。 按**Ctrl + 空格鍵**，即可查看儲存在連接管理員中的所有遠端連線的清單。
  - `sourcePath`：上`sourceMachine`的檔案或目錄位置。
  - `targetPath`：上`targetMachine`的檔案或目錄位置。
  - `deploymentType`：部署類型的描述。 `LocalRemote`支援`RemoteRemote`和。 `LocalRemote`表示從本機檔案系統複製到啟動時`remoteMachineName`所指定的遠端系統。 *vs. json*。 `RemoteRemote`表示從*CMakeSettings*中指定的遠端組建系統複製到*啟動. 與 json*中指定的不同遠端系統。
  - `executable`：指出部署的檔案是否為可執行檔。

### <a name="execute-custom-gdb-commands"></a>執行自`gdb`定義命令

Visual Studio 支援執行自`gdb`定義命令，以便直接與基礎偵錯工具互動。 如需詳細資訊，請參閱[執行自訂`gdb` lldb 命令](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)。

### <a name="enable-logging"></a>啟用記錄

啟用 MIEngine 記錄，以查看要傳送至`gdb`哪些命令、輸出`gdb`傳回的內容，以及每個命令所需的時間長度。 [深入了解](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>設定類型`cppdbg`

當您使用`cppdbg`設定類型在遠端系統或 WSL 上進行調試時，可以使用下列選項。 在 Visual Studio 2019 16.6 或更新版本中，建議`cppgdb`使用設定類型。

- `name`：用來識別 [**啟動專案**] 下拉式清單中設定的易記名稱。

- `project`：指定專案檔的相對路徑。 一般來說，在 CMake 專案的調試時，您不需要變更此值。

- `projectTarget`：指定要在建立專案時叫用的 CMake 目標。 如果您從 [**調試] 功能表**或 [**目標] 視圖**輸入 [*啟動. vs. json* ]，Visual Studio 會自動此屬性。 這個值必須符合 [**啟動專案**] 下拉式清單中所列的現有 [偵錯工具] 目標名稱。

- `args`：啟動時傳遞至正在進行偵錯工具的命令列引數。

- `processID`：要附加的 Linux 處理序識別碼。 只有在附加至遠端進程時才會使用。 如需詳細資訊，請參閱[使用 GDB 進行附加至進程的疑難排解](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

- `program`：預設為`"${debugInfo.fullTargetPath}"`。 要進行偵錯工具的 Unix 路徑。 只有在組建或部署位置中的目標可執行檔不同時才需要。

- `remoteMachineName`：預設為`"${debugInfo.remoteMachineName}"`。 主控程式來進行 debug 的遠端系統名稱。 只有在與組建系統不同時才需要。 在[連線管理員](../linux/connect-to-your-remote-linux-computer.md)中必須有現有的專案。 按**Ctrl + 空格鍵**，以查看所有現有遠端連線的清單。

- `cwd`：預設為`"${debugInfo.defaultWorkingDirectory}"`。 遠端系統`program`上執行之目錄的完整 Unix 路徑。 此目錄必須已存在。

- `environment`：傳遞給正在進行偵錯工具的其他環境變數。 例如，

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

- `pipeArgs`：傳遞至管道程式以設定連接的命令列引數陣列。 管道程式是用來轉送 Visual Studio 和`gdb`之間的標準輸入/輸出。 在調試 CMake 專案時 **，不需要自訂**此陣列中的大部分。 例外狀況是`${debuggerCommand}`，它會在`gdb`遠端系統上啟動。 您可以將它修改為：

  - 匯出 Linux 系統上的環境變數顯示值。 在下列範例中，這個值是`:1`。

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

  - 在執行之前，先執行腳本`gdb`。 請確定已在您的腳本上設定執行許可權。

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

- `stopOnEntry`：布林值，指定是否要在啟動進程時立即中斷。 預設值為 false。

- `visualizerFile`：要在對這個進程進行偵錯工具時使用的[natvis](/visualstudio/debugger/create-custom-views-of-native-objects)檔案。 此選項與美觀的`gdb`列印不相容。 當您`showDisplayString`設定這個屬性時也要設定。

- `showDisplayString`：在指定時`visualizerFile`啟用顯示字串的布林值。 將此選項設定`true`為，可能會在進行調試過程時導致效能變慢。

- `setupCommands`：要執行的`gdb`一或多個命令，以設定基礎偵錯工具。

- `miDebuggerPath`：的完整路徑`gdb`。 若未指定，Visual Studio 會先針對偵錯工具搜尋路徑。

- 最後，設定類型也可以使用`cppgdb` `cppdbg`所有為 configuration 類型定義的部署選項。

### <a name="debug-using-gdbserver"></a>使用 Debug`gdbserver`

您可以使用`gdbserver`將`cppdbg`設定設為 debug。 如需更多詳細資料和範例啟動設定，請到 Microsoft c + + 小組 Blog 文章[使用`gdbserver`來調試 Linux CMake 專案](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>請參閱

[Visual Studio 中的 CMake 專案](cmake-projects-in-visual-studio.md)\
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)\
[連接到您的遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)\
[自訂 CMake 組建設定](customize-cmake-settings.md)\
[設定 CMake 的調試階段](configure-cmake-debugging-sessions.md)\
[部署、執行及偵錯工具您的 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)

::: moniker-end
