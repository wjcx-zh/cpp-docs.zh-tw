---
title: '架構參考上的 tasks.vs.js(c + +) '
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: a2aea1b64d5a6c62604c680bf1a4a26478b7b52a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844986"
---
# <a name="tasksvsjson-schema-reference-c"></a>架構參考上的 tasks.vs.js(c + +) 

若要告訴 Visual Studio 如何在開啟的資料夾專案中建立您的原始程式碼，請在檔案 * 上加入tasks.vs.js* 。 您可以在這裡定義任意工作，然後從 **方案總管** 內容功能表叫用它。 CMake 專案不會使用這個檔案，因為所有的組建命令都是在 *CMakeLists.txt*中指定。 針對 CMake 以外的組建系統， *tasks.vs.json* ，您可以在其中指定組建命令和叫用組建腳本。 如需有關使用 *tasks.vs.js的*一般資訊，請參閱 [自訂「開啟資料夾」開發的組建和偵錯工具](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

工作有一個 `type` 屬性，可能有四個值的其中一個： `default` 、 `launch` 、 `remote` 或 `msbuild` 。 `launch`除非需要遠端連線，否則大部分的工作都應該使用。

## <a name="default-properties"></a>預設屬性

預設屬性可用於所有類型的工作：

|屬性|類型|描述|
|-|-|-|
|`taskLabel`|字串|  (必要項。 ) 指定使用者介面中使用的工作標籤。|
|`appliesTo`|字串| 需要 (。 ) 指定可執行命令的檔案。 支援使用萬用字元，例如： "*"、"*.cpp"、"/* .txt"|
|`contextType`|字串| 允許的值：「自訂」、「組建」、「清理」、「重建」。 決定工作會出現在內容功能表中的哪個位置。 預設為「自訂」。|
|`output`|字串| 指定工作的輸出標記。|
|`inheritEnvironments`|array| 指定一組繼承自多個來源的環境變數。 您可以定義檔案中的變數，例如 *CMakeSettings.json* 或 *CppProperties.js* ，並使其可供工作內容使用。 **Visual Studio 16.4：**：使用語法針對每個工作指定環境變數 `env.VARIABLE_NAME` 。 若要取消設定變數，請將它設定為 "null"。|
|`passEnvVars`|boolean| 指定是否要在工作內容中包含其他環境變數。 這些變數與使用屬性定義的變數不同 `envVars` 。 預設值為 "true"。|

## <a name="launch-properties"></a>啟動屬性

當工作類型為時 `launch` ，可以使用這些屬性：

|屬性|類型|描述|
|-|-|-|
|`command`|字串| 指定要啟動之進程或腳本的完整路徑。|
|`args`|array| 指定傳遞至命令的引數清單（以逗號分隔）。|
|`launchOption`|字串| 允許的值： "None"、"ContinueOnError"、"IgnoreError"。 指定當發生錯誤時，如何繼續執行命令。|
|`workingDirectory`|字串| 指定將執行命令的目錄。 預設為專案的目前工作目錄。|
|`customLaunchCommand`|字串| 指定要在執行命令之前套用的全域範圍自訂。 適用于設定環境變數，例如% PATH%。|
|`customLaunchCommandArgs`|字串| 指定要 customLaunchCommand 的引數。  (需要 `customLaunchCommand` 。 ) |
 `env`| 指定自訂環境變數的索引鍵/值清單。 例如，"myEnv"： "myVal"|
|`commands`|array| 指定要依順序叫用的命令清單。|

### <a name="example"></a>範例

下列工作會在資料夾中提供 makefile 時叫用 *make.exe* `Mingw64` ，且環境已在 *CppProperties.js*中定義，如 [ 架構參考上的CppProperties.js](cppproperties-schema-reference.md#user_defined_environments)所示：

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

當您安裝使用 c + + 的 Linux 開發工作負載，並使用 Visual Studio 連線管理員將連接新增至遠端電腦時，會啟用遠端工作。 遠端工作會在遠端系統上執行命令，也可以將檔案複製到其中。

當工作類型為時 `remote` ，可以使用這些屬性：

|屬性|類型|描述|
|-|-|-|
|`remoteMachineName`|字串|遠端電腦的名稱。 必須符合 **連線管理員**中的電腦名稱稱。|
|`command`|字串|要傳送至遠端電腦的命令。 根據預設，命令會在遠端系統上的 $HOME 目錄中執行。|
|`remoteWorkingDirectory`|字串|遠端電腦上的目前工作目錄。|
|`localCopyDirectory`|字串|要複製到遠端電腦的本機目錄。 預設為目前的工作目錄。|
|`remoteCopyDirectory`|字串|遠端電腦上複製的目錄 `localCopyDirectory` 。|
|`remoteCopyMethod`|字串| 要用於複製的方法。 允許的值： "none"、"sftp"、"rsync"。 針對大型專案，建議使用 rsync。|
|`remoteCopySourcesOutputVerbosity`|字串| 允許的值：「正常」、「詳細資訊」、「診斷」。|
|`rsyncCommandArgs`|字串|預設值為 "-t--delete"。|
|`remoteCopyExclusionList`|array|中要排除複製作業的檔案清單（以逗號分隔） `localCopyDirectory` 。|

### <a name="example"></a>範例

當您以滑鼠右鍵按一下**方案總管**中的*主要 .cpp*時，內容功能表中將會出現下列工作。 這取決於 `ubuntu` 在 **連線管理員**中呼叫的遠端電腦。 工作會將 Visual Studio 中目前開啟的資料夾複製到 `sample` 遠端電腦上的目錄，然後再叫用 g + + 來建立程式。

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

當工作類型為時 `msbuild` ，可以使用這些屬性：

|屬性|類型|描述|
|-|-|-|
|`verbosity`|字串| 指定 MSBuild 專案組建輸出 verbosityAllowed 值：「安靜」、「基本」、「正常」、「詳細」、「診斷」。|
|`toolsVersion`|字串| 指定要建立專案的工具組版本，例如 "2.0"、"3.5"、"4.0"、"Current"。 預設為「目前」。|
|`globalProperties`|物件 (object)|指定要傳遞至專案的全域屬性索引鍵/值清單，例如 "Configuration"： "Release"|
|`properties`|物件 (object)| 指定其他專案專用屬性的索引鍵/值清單。|
|`targets`|array| 依序指定要在專案上叫用的目標清單。 如果未指定，則會使用專案的預設目標。|
