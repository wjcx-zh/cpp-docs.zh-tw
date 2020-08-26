---
title: '架構參考上的 launch.vs.js(c + +) '
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 1161e8fa8ac3751ca8cc2b96ec063cd6063bb245
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841983"
---
# <a name="launchvsjson-schema-reference-c"></a>架構參考上的 launch.vs.js(c + +) 

使用檔案 * 上的launch.vs.js* 來設定調試參數。 建立檔案。 以滑鼠右鍵按一下 **方案總管** 中的可執行檔，然後選擇 [ **Debug] 和 [啟動設定**]。 選擇最符合您專案的選項，然後使用下列屬性，視需要修改設定。 如需有關偵錯工具 CMake 專案的詳細資訊，請參閱 [設定 CMake 調試](/cpp/build/configure-cmake-debugging-sessions)程式。

## <a name="default-properties"></a>預設屬性

|屬性|類型|描述|
|-|-|-|
|`name`|字串|在 [偵錯工具目標] 下拉式清單中指定專案的名稱。|
|`type`|字串|指定專案是否為 dll 或 .exe (預設為 .exe) |
|`project`|字串|指定專案檔的相對路徑。|
|`projectTarget`|字串|指定建立時所叫用的選擇性目標 `project` 。 這 `projectTarget` 必須已經存在，並符合 [ **調試目標** ] 下拉式清單中的名稱。|
|`debugType`|字串|根據程式碼類型 (原生、managed 或混合) 來指定偵錯工具模式。 除非已設定此參數，否則會自動偵測此參數。 允許的值：「原生」、「managed」、「混合」。|
|`inheritEnvironments`|array|指定一組繼承自多個來源的環境變數。 您可以在檔案中定義一些變數，例如 *CMakeSettings.json* 或 *CppProperties.js* ，並使其可供 debug 內容使用。  **Visual Studio 16.4：**：使用語法來指定每個目標的環境變數 `env.VARIABLE_NAME` 。 若要取消設定變數，請將它設定為 "null"。|
|`args`|array|指定傳遞至已啟動之程式的命令列引數。|
|`currentDir`|字串|指定組建目標的完整目錄路徑。 除非已設定此參數，否則會自動偵測此參數。|
|`noDebug`|boolean|指定是否要對啟動的程式進行偵錯工具。 如果未指定此參數的預設值，則為 **`false`** 。|
|`stopOnEntry`|boolean|指定是否要在進程啟動並附加偵錯工具時，立即中斷。 此參數的預設值為 **`false`** 。|
|`remoteMachine`|字串|指定啟動程式的遠端電腦名稱稱。|
|`env`|array| 指定自訂環境變數的索引鍵/值清單。 env： {"myEnv"： "myVal"}。|
|`portName`|字串|指定連接到執行中進程時的埠名稱。|
|`buildConfigurations`|array| 指定要套用設定之組建模式名稱的索引鍵/值組。 例如， `Debug` 或， `Release` 以及要根據選取的組建模式使用的設定。

## <a name="c-linux-properties"></a>C + + Linux 屬性

|屬性|類型|描述|
|-|-|-|
|`program`|字串|遠端電腦上程式可執行檔的完整路徑。 使用 CMake 時，宏 `${debugInfo.fullTargetPath}` 可以用來做為此欄位的值。|
|`processId`|integer|要附加偵錯工具的選擇性處理序識別碼。|
|`sourceFileMap`|物件 (object)|傳遞至調試引擎的選擇性來源檔案對應。 格式： `{ "\<Compiler source location>": "\<Editor source location>" }` 或 `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }` 。 範例：`{ "/home/user/foo": "C:\\foo" }` 或 `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`。 請參閱 [原始檔對應選項](#source_file_map_options)。|
|`additionalProperties`|字串|其中一個 sourceFileMapOptions。 (請參閱下方。)|
|`MIMode`|字串|表示 MIDebugEngine 將連接之 MI 的主控台偵錯工具類型。 允許的值為 "gdb"、"lldb"。|
|`args`|array|傳遞至程式的命令列引數。|
|`environment`|array|要加入至程式環境的環境變數。 範例： [{"name"： "squid"，"value"： "蛤蜊"}]。|
|`targetArchitecture`|字串|偵錯工具的架構。 除非已設定此參數，否則會自動偵測此參數。 允許的值為 x86、arm、arm64、mips、x64、amd64 x86_64。|
|`visualizerFile`|字串|要在進行此程式的偵錯工具時使用的 natvis 檔案。 此選項與 GDB 整齊列印不相容。 如果使用此設定，請參閱 "showDisplayString"。|
|`showDisplayString`|boolean|當指定 visualizerFile 時，showDisplayString 將會啟用顯示字串。 開啟此選項可能會在調試過程中導致效能變慢。|
|`remoteMachineName`|字串|裝載 gdb 和程式以進行偵錯工具的遠端 Linux 電腦。 使用連線管理員新增新的 Linux 電腦。 使用 CMake 時，宏 `${debugInfo.remoteMachineName}` 可以用來做為此欄位的值。|
|`cwd`|字串|遠端電腦上目標的工作目錄。 使用 CMake 時，宏 `${debugInfo.defaultWorkingDirectory}` 可以用來做為此欄位的值。 除非在 *CMakeLists.txt* 檔案中覆寫，否則預設值為遠端工作區根目錄。|
|`miDebuggerPath`|字串|啟用 MI 的偵錯工具的路徑 (例如 gdb) 。 如果未指定，它會先搜尋偵錯工具的路徑。|
|`miDebuggerServerAddress`|字串|要連接之已啟用 MI 的偵錯工具伺服器的網路位址。 範例： localhost：1234。|
|`setupCommands`|array|要執行的一或多個 GDB/LLDB 命令，以便設定基礎偵錯工具。 範例： `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. 請參閱 [啟動安裝程式命令](#launch_setup_commands)。|
|`customLaunchSetupCommands`|array|如果有提供，這會取代用來以其他命令啟動目標的預設命令。 例如，這可以是「-目標-附加」，以便附加至目標進程。 空白的命令清單會以 nothing 取代啟動命令，如果偵錯工具是以命令列選項的形式提供啟動選項，這會很有用。 範例： `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|字串|在完成設定偵錯工具之後要執行的命令，以使目標進程執行。 允許的值為 "exec-run"、"exec-continue"、"None"。 預設值為 "exec-run"。|
|`debugServerPath`|字串|要啟動之 debug server 的選擇性完整路徑。 預設值為 null。|
|`debugServerArgs`|字串|選擇性的 debug server 引數。 預設值為 null。|
|`filterStderr`|boolean|搜尋 stderr 串流以瞭解伺服器啟動的模式，並將 stderr 記錄到偵錯工具輸出。 預設為 **`false`** 。|
|`coreDumpPath`|字串|指定之程式核心傾印檔案的選擇性完整路徑。 預設值為 null。|
externalConsole|boolean|若為 true，則會啟動偵錯工具的主控台。 如果 **`false`** 為，則不會啟動主控台。 預設為 **`false`** 。 注意：基於技術因素，在某些情況下會忽略此選項。|
|`pipeTransport`|字串|如果有的話，這會告知偵錯工具使用另一個可執行檔來連接到遠端電腦，以在 Visual Studio 和已啟用 MI 的偵錯工具 (（例如 gdb) ）之間轉送標準輸入/輸出。 允許的值：一或多個 [管道傳輸選項](#pipe_transport_options)。|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a> 啟動安裝程式命令

與屬性搭配使用 `setupCommands` ：

|屬性|類型|描述|
|-|-|-|
|`text`|字串|要執行的偵錯工具命令。|
|`description`|字串|命令的選擇性描述。|
|`ignoreFailures`|boolean|若為 true，則應忽略來自命令的失敗。 預設為 **`false`** 。|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a> 管道傳輸選項

與屬性搭配使用 `pipeTransport` ：

|屬性|類型|描述|
|-|-|-|
|`pipeCwd`|字串|管道程式之工作目錄的完整路徑。|
|`pipeProgram`|字串|要執行的完整管道命令。|
|`pipeArgs`|array|傳遞至管道程式以設定連接的命令列引數。|
|`debuggerPath`|字串|目的電腦上偵錯工具的完整路徑，例如/usr/bin/gdb。|
|`pipeEnv`|物件 (object)|傳遞至管道程式的環境變數。|
|`quoteArgs`|boolean|如果個別引數包含字元 (例如空格或索引標籤) ，是否應該加上引號？ 如果 **`false`** 為，則偵錯工具命令將不會再自動加上引號。 預設值為 **`true`** 。|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a> 來源檔案對應選項

與屬性搭配使用 `sourceFileMap` ：

|屬性|類型|描述|
|-|-|-|
|`editorPath`|字串|要尋找之編輯器的原始程式碼位置。|
|`useForBreakpoints`|boolean|設定中斷點時，應使用此來源對應。 如果 **`false`** 為，則只會使用檔案名和行號來設定中斷點。 如果為 **`true`** ，則只有在使用此來源對應時，才會使用檔案的完整路徑和行號設定中斷點。 否則，會在設定中斷點時使用檔案名和行號。 預設值為 **`true`** 。|
