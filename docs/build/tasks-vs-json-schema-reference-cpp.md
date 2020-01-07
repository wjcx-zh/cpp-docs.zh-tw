---
title: tasks. vs. json 架構參考（C++）
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556652"
---
# <a name="tasksvsjson-schema-reference-c"></a>tasks. vs. json 架構參考（C++）

若要告訴 Visual Studio 如何在開啟的資料夾專案中建立原始程式碼，請新增*tasks. vs. json*檔案。 您可以在此定義任何任意工作，然後從 [**方案總管**] 操作功能表叫用它。 CMake projects 不會使用這個檔案，因為所有的組建命令都是在*remote monitoring.h cmakelists.txt*中指定。 針對 CMake 以外的組建*系統，您可以在其中*指定組建命令並叫用組建腳本。 如需使用工作 *. 與 json*的一般資訊，請參閱[自訂「開啟資料夾」開發的組建和偵錯工具](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

工作具有 `type` 屬性，其中可能有下列四個值的其中一個： `default`、`launch`、`remote`或 `msbuild`。 大部分的工作都應該使用 `launch`，除非需要遠端連線。

## <a name="default-properties"></a>預設屬性

預設屬性可在所有類型的工作上使用：

||||
|-|-|-|
|**Property**|**Type**|**描述**|
|`taskLabel`|string| （必要）。指定使用者介面中使用的工作標籤。|
|`appliesTo`|string| （必要）。指定命令可執行檔檔案。 支援使用萬用字元，例如： "*"、"*.cpp"、"/* .txt"|
|`contextType`|string| 允許的值： [自訂]、[組建]、[清除]、[重建]。 決定工作會在內容功能表中出現的位置。 預設為 "custom"。|
|`output`|string| 指定工作的輸出標記。|
|`inheritEnvironments`|陣列。| 指定一組繼承自多個來源的環境變數。 您可以在*CMakeSettings*或*CppProperties*等檔案中定義變數，並將其提供給工作內容使用。 **Visual Studio 16.4：**：使用 `env.VARIABLE_NAME` 語法，依據每個工作指定環境變數。 若要取消設定變數，請將它設為 "null"。|
|`passEnvVars`|boolean| 指定是否要在工作內容中包含其他環境變數。 這些變數與使用 `envVars` 屬性所定義的變數不同。 預設為 "true"。|

## <a name="launch-properties"></a>啟動屬性

`launch`工作類型時，可以使用下列屬性：

||||
|-|-|-|
|**Property**|**Type**|**描述**|
|`command`|string| 指定要啟動之進程或腳本的完整路徑。|
|`args`|陣列。| 指定傳遞至命令的引數清單（以逗號分隔）。|
|`launchOption`|string| 允許的值： "None"、"ContinueOnError"、"IgnoreError"。 指定發生錯誤時，如何繼續執行命令。|
|`workingDirectory`|string| 指定將執行命令的目錄。 預設為專案目前的工作目錄。|
|`customLaunchCommand`|string| 指定執行命令之前要套用的全域範圍自訂。 適用于設定環境變數，例如% PATH%。|
|`customLaunchCommandArgs`|string| 指定要 customLaunchCommand 的引數。 （需要 `customLaunchCommand`）。|
 `env`| 指定自訂環境變數的索引鍵/值清單。 例如，"myEnv"： "myVal"|
|`commands`|陣列。| 指定要依序叫用的命令清單。|

### <a name="example"></a>範例

下列工作會在資料夾中提供 makefile 時叫用*make .exe* ，並在*CppProperties*中定義 `Mingw64` 環境，如[CppProperties 架構參考](cppproperties-schema-reference.md#user_defined_environments)中所示：

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

當您以滑鼠右鍵按一下**方案總管**中的 *.cpp*檔案時，可以從內容功能表叫用這些工作。

## <a name="remote-properties"></a>遠端屬性

當您安裝使用C++工作負載的 Linux 開發，並使用 Visual Studio 連線管理員將連接新增至遠端電腦時，就會啟用遠端作業。 遠端工作會在遠端系統上執行命令，而且也可以將檔案複製到其中。

`remote`工作類型時，可以使用下列屬性：

||||
|-|-|-|
|**Property**|**Type**|**描述**|
|`remoteMachineName`|string|遠端電腦的名稱。 必須符合**連線管理員**中的電腦名稱稱。|
|`command`|string|要傳送至遠端電腦的命令。 根據預設，命令會在遠端系統上的 $HOME 目錄中執行。|
|`remoteWorkingDirectory`|string|遠端電腦上的目前工作目錄。|
|`localCopyDirectory`|string|要複製到遠端電腦的本機目錄。 預設為目前的工作目錄。|
|`remoteCopyDirectory`|string|要在其中複製 `localCopyDirectory` 之遠端電腦上的目錄。|
|`remoteCopyMethod`|string| 要用於複製的方法。 允許的值： "none"、"sftp"、"rsync"。 針對大型專案，建議使用 rsync。|
|`remoteCopySourcesOutputVerbosity`|string| 允許的值： [一般]、[詳細資訊]、[診斷]。|
|`rsyncCommandArgs`|string|預設為 "-t--delete"。|
|`remoteCopyExclusionList`|陣列。|`localCopyDirectory` 中要從複製作業排除的檔案清單（以逗號分隔）。|

### <a name="example"></a>範例

當您以滑鼠右鍵按一下**方案總管**中的*main .cpp*時，內容功能表中會出現下列工作。 這取決於**連線管理員**中名為 `ubuntu` 的遠端電腦。 工作會將 Visual Studio 中目前開啟的資料夾複製到遠端電腦上的 `sample` 目錄，然後叫用 g + + 來建立程式。

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>MSBuild 屬性

`msbuild`工作類型時，可以使用下列屬性：

||||
|-|-|-|
|**Property**|**Type**|**描述**|
|`verbosity`|string| 指定 MSBuild 專案組建輸出 verbosityAllowed 值：「無訊息」、「最小」、「正常」、「詳細」、「診斷」。|
|`toolsVersion`|string| 指定要建立專案的工具組版本，例如 "2.0"、"3.5"、"4.0"、"Current"。 預設為 "Current"。|
|`globalProperties`|物件|指定要傳遞至專案之全域屬性的索引鍵/值清單，例如 "Configuration"： "Release"|
|`properties`|物件| 指定其他僅限專案屬性的索引鍵/值清單。|
|`targets`|陣列。| 依序指定專案上要叫用的目標清單。 如果沒有指定，則會使用專案的預設目標。|
