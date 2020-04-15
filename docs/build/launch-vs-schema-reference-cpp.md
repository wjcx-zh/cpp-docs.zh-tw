---
title: 啟動.vs.json 架構參考 (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323058"
---
# <a name="launchvsjson-schema-reference-c"></a>啟動.vs.json 架構參考 (C++)

使用*啟動.vs.json*檔配置調試參數。 建立檔案。 右鍵按下**解決方案資源管理員**中的執行檔,然後選擇**除錯和啟動設定**。 選擇與專案最匹配的選項,然後根據需要使用以下屬性修改配置。 有關除錯 CMake 專案的詳細資訊,請參考[設定 CMake 除錯工作階段](/cpp/build/configure-cmake-debugging-sessions)。

## <a name="default-properties"></a>預設屬性

||||
|-|-|-|
|**屬性**|**型別**|**說明**|
|`name`|字串|在除錯目標下拉清單中指定條目的名稱。|
|`type`|字串|指定項目是 dll 還是 .exe(預設值為 .exe)|
|`project`|字串|指定項目檔的相對路徑。|
|`projectTarget`|字串|指定生成`project`時調用的可選目標。 這`projectTarget`必須已經存在,並且與**調試目標**下拉清單中的名稱匹配。|
|`debugType`|字串|根據代碼類型(本機、託管或混合)指定調試模式。 除非設置了此參數,否則將自動檢測到此參數。 允許的值:「本機」、「託管」、「混合」。|
|`inheritEnvironments`|array|指定從多個源繼承的一組環境變數。 您可以在檔(如*CMakeSettings.json 或* *CppProperties.json)* 中定義一些變數,並使它們可用於調試上下文。  **Visual Studio 16.4:**: 使用`env.VARIABLE_NAME`語法根據每個目標指定環境變數。 要取消設定變數,將其設置為"null"。|
|`args`|array|指定傳遞給啟動程式的命令列參數。|
|`currentDir`|字串|指定生成目標的完整目錄路徑。 除非設置了此參數,否則將自動檢測到此參數。|
|`noDebug`|boolean|指定是否調試啟動的程式。 如果未指定此參數`false`的預設值。|
|`stopOnEntry`|boolean|指定在啟動進程並附加除錯器時是否立即中斷。 這裡的預設值為`false`。|
|`remoteMachine`|字串|指定啟動程式的遠端電腦的名稱。|
|`env`|array| 指定自定義環境變數的鍵值清單。 env:{"我的恩夫":"米瓦爾"。|
|`portName`|字串|指定附加到正在運行的進程時的埠名稱。|
|`buildConfigurations`|array| 指定要應用配置的生成模式的名稱的鍵值對。 例如,`Debug``Release`或和根據所選生成模式要使用的配置。

## <a name="c-linux-properties"></a>C++ Linux 屬性

||||
|-|-|-|
|**屬性**|**型別**|**說明**|
|`program`|字串|遠端電腦上程式可執行的完整路徑。 使用 CMake`${debugInfo.fullTargetPath}`時, 巨集可用作此欄位的值。|
|`processId`|integer|將除錯程式附加到的可選程序 ID。|
|`sourceFileMap`|物件 (object)|傳遞給調試引擎的可選源檔映射。 格式:`{ "\<Compiler source location>": "\<Editor source location>" }``{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`或 。 範例：`{ "/home/user/foo": "C:\\foo" }` 或 `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`。 請參考[來源檔映射選項](#source_file_map_options)。|
|`additionalProperties`|字串|源檔映射選項之一。 (請參閱下方。)|
|`MIMode`|字串|指示 MIDebugEngine 將連接到的啟用 MI 控制台調試器的類型。 允許的值是"gdb","lldb"。|
|`args`|array|傳遞給程式的命令列參數。|
|`environment`|array|要添加到程式環境的環境變數。 範例: [ 名稱":"魷魚" 值":"clam" = [ ]|
|`targetArchitecture`|字串|調試器的體系結構。 除非設置了此參數,否則將自動檢測到此參數。 允許的值是 x86、手臂、臂 64、默劇、x64、amd64、x86_64。|
|`visualizerFile`|字串|.natvis 檔案,用於調試此過程時。 此選項與 GDB 漂亮列印不相容。 如果使用此設置,請參閱"顯示顯示字串"。|
|`showDisplayString`|boolean|指定視覺化工具檔時,ShowDisplayString 將啟用顯示字串。 啟用此選項可能會導致調試期間性能降低。|
|`remoteMachineName`|字串|承載 gdb 和要除錯的程式的遠端 Linux 電腦。 使用連線管理員新增新的 Linux 電腦。 使用 CMake`${debugInfo.remoteMachineName}`時, 巨集可用作此欄位的值。|
|`cwd`|字串|遠端電腦上的目標的工作目錄。 使用 CMake`${debugInfo.defaultWorkingDirectory}`時, 巨集可用作此欄位的值。 默認值是遠端工作區根,除非在*CMakelists.txt*檔中重寫。|
|`miDebuggerPath`|字串|啟用 MI 除錯器(如 gdb)的路徑。 未指定時,它將首先搜索 PATH 以查找調試器。|
|`miDebuggerServerAddress`|字串|要連接到的啟用 MI 的除錯器伺服器的網路位址。 示例:本地主機:1234。|
|`setupCommands`|array|要執行一個或多個 GDB/LLDB 命令,以便設置基礎調試器。 範例： `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. 請參考[啟動設定指令](#launch_setup_commands)。|
|`customLaunchSetupCommands`|array|如果提供,這將用一些其他命令替換用於啟動目標的預設命令。 例如,這可以是"目標附加",以便附加到目標進程。 空命令清單將啟動命令替換為任何內容,如果調試器作為命令列選項提供啟動選項,則該命令非常有用。 範例： `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|字串|完全設置調試器後要執行的命令,以便使目標進程運行。 允許的值是"執行運行"、"執行-繼續"、"無"。 默認值為執行運行。|
|`debugServerPath`|字串|調試要啟動的伺服器的可選完整路徑。 預設值為 null。|
|`debugServerArgs`|字串|可選除錯伺服器args。 預設值為 null。|
|`filterStderr`|boolean|搜索伺服器啟動的模式和日誌穩占器以調試輸出的穩穩流流。 預設為 `false`。|
|`coreDumpPath`|字串|指定程式的核心轉儲檔的可選完整路徑。 預設值為 null。|
外部主控台|boolean|如果為 true,則為調試器啟動主控主台。 如果未`false`啟動主控台。 預設為 `false`。 注: 在某些情況下,由於技術原因,此選項將被忽略。|
|`pipeTransport`|字串|如果存在,這將告訴除錯器使用另一個可執行檔連接到遠端電腦,作為管道,它將在 Visual Studio 和啟用 MI 的調試器(如 gdb)之間中繼標準輸入/輸出。 允許的值:一個或多個[導管傳輸選項](#pipe_transport_options)。|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>啟動設定指令

與`setupCommands`屬性一起使用:

||||
|-|-|-|
|`text`|字串|要執行的調試器命令。|
|`description`|字串|命令的可選說明。|
|`ignoreFailures`|boolean|如果為 true,則應忽略命令中的失敗。 預設為 `false`。|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>導管運輸選項

與`pipeTransport`屬性一起使用:

||||
|-|-|-|
|`pipeCwd`|字串|管道程式工作目錄的完全限定路徑。|
|`pipeProgram`|字串|要執行的完全限定的管道命令。|
|`pipeArgs`|array|傳遞給管道程式的命令列參數以配置連接。|
|`debuggerPath`|字串|目標電腦上的除錯器的完整路徑,例如 /usr/bin/gdb。|
|`pipeEnv`|物件 (object)|傳遞給管道程序的環境變數。|
|`quoteArgs`|boolean|如果單個參數包含字元(如空格或製表元),是否應引用它? 如果`false`,調試器命令將不再自動引用。 預設值為 `true`。|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>來源檔案對應選項

與屬性一`sourceFileMap`起使用:

||||
|-|-|-|
|`editorPath`|字串|要查找的原始程式碼的位置。|
|`useForBreakpoints`|boolean|設置斷點時,應使用此源映射。 如果`false`,則僅使用檔名和行號來設置斷點。 如果`true`,只有在使用此源映射時,才會使用檔和行號的完整路徑設置斷點。 否則,在設置斷點時將只使用檔名和行號。 預設值為 `true`。|
