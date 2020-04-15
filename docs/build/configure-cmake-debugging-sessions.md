---
title: 在 Visual Studio 中設定 CMake 偵錯工作階段
description: 描述如何使用可視化工作室配置 CMake 調試器設置。
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

本機 CMake 支援可在 Visual Studio 2017 及更高版本提供。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end

::: moniker range=">=vs-2017"

[一般]**** 工具列的 [啟動項目]**** 下拉式清單中會顯示所有可執行的 CMake 目標。 選擇一個啟動除錯工作階段並啟動除錯器。

![CMake 啟動項目下拉清單](media/cmake-startup-item-dropdown.png "CMake 啟動項目下拉清單")

您還可以從解決方案資源管理器啟動除錯工作階段。 首先,在**解決方案資源管理器**視窗中切換到 **「CMake 目標檢視**」。

![CMake [Targets View] \(目標檢視\) 按鈕](media/cmake-targets-view.png  "CMake 目標 檢視選單項目")

然後, 右鍵按下執行檔並選擇**除錯**。 此命令根據活動設定自動開始調試選取的目標。

## <a name="customize-debugger-settings"></a>自訂偵錯工具設定

您可以自定義專案中任何可執行的 CMake 目標的調試器設定。 它們位於專案根目錄的*`.vs`* 資料夾中,位於一個名為 *「啟動.vs.json」* 的設定檔中。 啟動設定檔在大多數調試方案中都很有用,因為您可以配置和保存除錯設定詳細資訊。 此檔案有三個入口點:

- **除錯選單:** 從主選單**中選擇"調試>調試和啟動設置[活動調試目標],** 以自定義特定於活動調試目標的調試配置。 如果未選擇調試目標,則此選項將灰顯。

![除錯選單入口點](media/cmake-debug-menu.png "除錯選單入口點")

- **目標檢視:** 導覽到解決方案資源管理員**中的目標檢視**。 然後,右鍵單擊調試目標並選擇 **「添加調試配置**」以自定義特定於所選目標的調試配置。

![目標檢視入口點](media/cmake-targets-add-debug-configuration.png "目標檢視入口點")

- **根組清單.txt:** 右鍵按下根*CMakelists.txt*並選擇 **「新增除錯設定**」以開啟 **「選擇除錯器」** 對話框。 該對話框允許您添加*任何類型的*調試配置,但您必須手動`projectTarget`指定通過 屬性呼叫的 CMake 目標。

![選擇除錯器對話框](media/cmake-select-a-debugger.png "選擇除錯器對話框")

您可以編輯*啟動.vs.json*檔,為任意數量的 CMake 目標創建調試配置。 儲存檔案時,Visual Studio 會在 **「啟動專案」** 下拉清單中為每個新配置創建一個項目。

## <a name="reference-keys-in-cmakesettingsjson"></a>CMakeSettings.json 中的參考鍵

要引用*CMakeSettings.json*檔中的任何鍵`cmake.`,在*啟動*中準備它。 下面的範例顯示了一個簡單的*啟動.vs.json*檔,該`remoteCopySources`檔在*CMakeSettings.json*檔中拉取目前選取設定的金鑰的值:

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

*CMakeSettings.json*中定義`${env.VARIABLE_NAME}`的**環境變數**也可以用於啟動. vs.json 使用語法 。 在 Visual Studio 2019 版本 16.4 及更高版本中,調試目標將使用您在*CMakeSettings.json*中指定的環境自動啟動。 可以通過將環境變數設置為**null**來取消設定環境變數。

## <a name="launchvsjson-reference"></a>啟動.vs.json 參考

有許多*啟動.vs.json*屬性來支援您的所有調試方案。 以下屬性是所有除錯設定(遠端設定及本地端)共有的:

- `projectTarget`:指定生成專案時要調用的 CMake 目標。 如果從**調試功能表**或**目標檢視**輸入*啟動.vs.json,Visual* Studio 會自動填充此屬性。 此值必須與**啟動項**下拉清單中列出的現有調試目標的名稱匹配。

- `env`:使用語法添加的其他環境變數:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`:命令列參數傳遞給程式以進行除錯。

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>啟動.vs.json 遠端項目和 WSL 參考

在 Visual Studio 2019 版本 16.6 中,`type: cppgdb`我們添加了新的調試配置,以簡化遠端系統和 WSL 上的調試。 仍然支援的舊`type: cppdbg`調試配置。

### <a name="configuration-type-cppgdb"></a>設定類型`cppgdb`

- `name`:用於標識**啟動項**下拉清單中的配置的友好名稱。
- `project`:指定項目檔的相對路徑。 通常,除錯 CMake 專案時不需要更改此路徑。
- `projectTarget`:指定生成專案時要調用的 CMake 目標。 如果從**調試功能表**或**目標檢視**輸入*啟動.vs.json,Visual* Studio 會自動填充此屬性。 此目標值必須與**啟動項**下拉清單中列出的現有調試目標的名稱匹配。
- `debuggerConfiguration`指示要使用的調試預設值集。 在 Visual Studio 2019 版`gdb`16.6 中,唯一有效的選項是 。 早期版本也支援`gdbserver`。
- `args`:在啟動時將命令列參數傳遞給正在調試的程式。
- `env`:傳遞給正在調試的程式的其他環境變數。 例如： `{"DISPLAY": "0.0"}` 。
- `processID`:要附加到的 Linux 進程 ID。 僅在附加到遠程進程時使用。 有關詳細資訊,請參閱使用[GDB 附加到行程的疑難排解](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

#### <a name="additional-options-for-the-gdb-configuration"></a>`gdb`設定的其他選項

- `program`:預設值為`"${debugInfo.fullTargetPath}"`。 要調試的應用程式的 Unix 路徑。 僅當與生成或部署位置中的目標可執行檔不同時,才需要。
- `remoteMachineName`:預設值為`"${debugInfo.remoteMachineName}"`。 承載要調試的程式的遠端系統的名稱。 僅當與生成系統不同時才需要。 [連接管理器](../linux/connect-to-your-remote-linux-computer.md)中必須具有現有條目。 按**Ctrl+空間**以查看所有現有遠端連接的清單。
- `cwd`:預設值為`"${debugInfo.defaultWorkingDirectory}"`。 運行遠端系統上`program`目錄的 Unix 路徑。 此目錄必須已存在。
- `gdbpath`:預設值為`/usr/bin/gdb`。 用於調試的完整`gdb`Unix 路徑。 只使用的`gdb`自訂版本 時才需要 。
- `preDebugCommand`:在呼叫`gdb`之前立即執行的 Linux 命令。 `gdb`直到命令完成才能啟動。 可以使用 選項執行之前執行文稿`gdb`。

#### <a name="deployment-options"></a>部署選項

使用以下選項將生成計算機(在 CMakeSettings.json 中定義)與遠端調試電腦分開。

- `remoteMachineName`:遠端調試機。 僅當與生成計算機不同時才需要。 [連接管理器](../linux/connect-to-your-remote-linux-computer.md)中必須具有現有條目。 按**Ctrl+空間**以查看所有現有遠端連接的清單。
- `disableDeploy`:預設值為`false`。 指示是否禁用生成/調試分離。 當`false`時,此選項允許在兩個單獨的計算機上進行生成和調試。
- `deployDirectory`:可執行檔案複製到的目錄`remoteMachineName`的完整 Unix 路徑。
- `deploy`:高級部署設置的陣列。 僅當需要更精細地控制部署過程時,才需要配置這些設置。 默認情況下,只有調試過程所需的檔才會部署到遠端調試電腦。
  - `sourceMachine`:從中複製檔或目錄的計算機。 按**Ctrl_Space**以檢視儲存在連接管理器中的所有遠端連接的清單。 在 WSL 上本機產生時,將忽略此選項。
  - `targetMachine`:將檔案或目錄複製到的計算機。 按**Ctrl_Space**以檢視儲存在連接管理器中的所有遠端連接的清單。
  - `sourcePath`:上的檔案`sourceMachine`或目錄位置。
  - `targetPath`:上的檔案`targetMachine`或目錄位置。
  - `deploymentType`:部署類型的說明。 `LocalRemote`並且`RemoteRemote`受支援。 `LocalRemote`從本地檔案系統複製到`remoteMachineName`*啟動*中指定的遠端系統。 `RemoteRemote`意味著從*CMakeSettings.json*中指定的遠端生成系統複製到*啟動*中指定的不同遠端系統。
  - `executable`:指示部署的檔是否是可執行檔。

### <a name="execute-custom-gdb-commands"></a>執行自訂`gdb`指令

Visual Studio`gdb`支援執行 自訂命令,以便直接與基礎調試器進行交互。 關於詳細資訊,請參閱[執行自`gdb`訂 lldb 指令](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)。

### <a name="enable-logging"></a>啟用記錄

啟用 MIEngine 紀錄記錄以查看發送到哪些`gdb`命令`gdb`,輸出返回什麼,以及每個命令需要多長時間。 [深入了解](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>設定類型`cppdbg`

使用配置類型在遠端系統或 WSL 上進行除錯`cppdbg`時, 可以使用以下選項。 在 Visual Studio 2019 版`cppgdb`16.6 或更高版本中,建議配置類型。

- `name`:用於標識**啟動項**下拉清單中的配置的友好名稱。

- `project`:指定項目檔的相對路徑。 通常,除錯 CMake 專案時不需要更改此值。

- `projectTarget`:指定生成專案時要調用的 CMake 目標。 如果從**調試功能表**或**目標檢視**輸入*啟動.vs.json,Visual* Studio 會自動填充此屬性。 此值必須與**啟動項**下拉清單中列出的現有調試目標的名稱匹配。

- `args`:在啟動時將命令列參數傳遞給正在調試的程式。

- `processID`:要附加到的 Linux 進程 ID。 僅在附加到遠程進程時使用。 有關詳細資訊,請參閱使用[GDB 附加到行程的疑難排解](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB)。

- `program`:預設值為`"${debugInfo.fullTargetPath}"`。 要調試的應用程式的 Unix 路徑。 僅當與生成或部署位置中的目標可執行檔不同時,才需要。

- `remoteMachineName`:預設值為`"${debugInfo.remoteMachineName}"`。 承載要調試的程式的遠端系統的名稱。 僅當與生成系統不同時才需要。 [連接管理器](../linux/connect-to-your-remote-linux-computer.md)中必須具有現有條目。 按**Ctrl+空間**以查看所有現有遠端連接的清單。

- `cwd`:預設值為`"${debugInfo.defaultWorkingDirectory}"`。 運行遠端系統上`program`目錄的完整 Unix 路徑。 此目錄必須已存在。

- `environment`:傳遞給正在調試的程式的其他環境變數。 例如，

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

- `pipeArgs`: 傳遞給導管程式以設定連接的命令列參數陣列。 管道程式用於在 Visual Studio 和`gdb`之間中繼標準輸入/輸出。 除錯 CMake 專案時 **,不需要自訂**大多數此陣列。 例外情況是在遠端系統上`${debuggerCommand}``gdb`啟動的 。 它可以變更為:

  - 在 Linux 系統上匯出環境變數 DISPLAY 的值。 在下面的範例中,此值為`:1`。

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

  - 在執行 之前執行文`gdb`稿 。 確保在腳本上設置了執行許可權。

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

- `stopOnEntry`:指定在進程啟動后立即是否中斷的布爾。 預設值為 false。

- `visualizerFile`:除錯此過程時要使用[.natvis 檔案](/visualstudio/debugger/create-custom-views-of-native-objects)。 此選項與漂亮的列印不`gdb`相容。 在設置`showDisplayString`此屬性時也設置。

- `showDisplayString`:指定`visualizerFile`時 啟用顯示字串的布林。 將此選項設置為`true`可能會導致調試期間性能降低。

- `setupCommands`:要執行的`gdb`一個或多個命令,以設置基礎調試器。

- `miDebuggerPath`:`gdb`到的完整路徑。 未指定時,可視化工作室將首先搜索 PATH 以搜索調試器。

- 最後,為`cppgdb`配置類型定義的所有部署選項也可以由`cppdbg`配置類型使用。

### <a name="debug-using-gdbserver"></a>使用除錯`gdbserver`

您可以設定`cppdbg`設定設定為使用`gdbserver`除錯。 您可以在 Microsoft C++ 團隊部落格文章[使用除`gdbserver`錯 Linux CMake 專案](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/)中找到更多詳細資訊和啟動配置範例。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>另請參閱

[在視覺工作室中製作專案](cmake-projects-in-visual-studio.md)\
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)\
[連接到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)\
[自訂「製作」構建設定](customize-cmake-settings.md)\
[設定「製作」除錯工作階段](configure-cmake-debugging-sessions.md)\
[部署、執行及除錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)

::: moniker-end
