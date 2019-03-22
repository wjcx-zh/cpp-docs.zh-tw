---
title: CMakeSettings.json 結構描述參考
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 893bc5c8efe3fdae80a4a0de8204d391baa63d07
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356110"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 結構描述參考

**Cmakesettings.json**' 檔案包含指定 Visual Studio 應該如何互動以建置專案，以供指定的平台的 CMake 的資訊。 使用此檔案儲存環境變數或 cmake.exe 環境引數等資訊。

## <a name="environments"></a>環境

`environments` 陣列包含定義「環境」之類型 `object` 的 `items` 清單。 環境可用來將一組變數套用至 `configuration`。 `environments` 陣列中的每個項目都包含：

- `namespace`：命名環境，以便從表單 `namespace.variable` 中的組態參考其變數。 預設的環境物件稱為 `env`，以特定的系統環境變數填入，包括 `%USERPROFILE%`。
- `environment`：唯一識別此變數群組。 稍後在 `inheritEnvironments` 項目中允許繼承該群組。
- `groupPriority`：整數，在評估這些變數時指定其優先順序。 先評估數值較高的項目。
- `inheritEnvironments`：值陣列，指定此群組繼承的環境組。 可以使用任何自訂的環境，或這些預先定義的環境：
 
  - linux_arm：從遠端鎖定 ARM Linux。
  - linux_x64：從遠端鎖定 x64 Linux。
  - linux_x86：從遠端鎖定 x86 Linux。
  - msvc_arm：鎖定含 MSVC 編譯器的 ARM Windows。
  - msvc_arm_x64：鎖定含 64 位元 MSVC 編譯器的 ARM Windows。
  - msvc_arm64：鎖定含 MSVC 編譯器的 ARM64 Windows。
  - msvc_arm64_x64：鎖定含 64 位元 MSVC 編譯器的 ARM64 Windows。
  - msvc_x64：鎖定含 MSVC 編譯器的 x64 Windows。
  - msvc_x64_x64：鎖定含 64 位元 MSVC 編譯器的 x64 Windows。
  - msvc_x86：鎖定含 MSVC 編譯器的 x86 Windows。
  - msvc_x86_x64：鎖定含 64 位元 MSVC 編譯器的 x86 Windows。

## <a name="configurations"></a>組態

`configurations` 陣列的組成物件，代表套用至相同資料夾中 CMakeLists.txt 檔案的 CMake 組態。 您可以使用這些物件來定義多個組建組態，並可在 IDE 中輕鬆切換它們。 

`configuration` 有這些屬性：
- `name`：命名組態。
- `description`：此組態的描述會出現在功能表中。
- `generator`：指定要用於此組態的 CMake 產生器。 可能是下列其中之一：

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix Makefiles
  - Ninja

- `configurationType`：針對所選產生器指定組建類型組態。 可能是下列其中之一：
 
  - 偵錯
  - 版本
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`：指定此組態依賴的一或多個環境。 可以是任何自訂的環境，或預先定義的環境之一。
- `buildRoot`：指定目錄，CMake 會在此產生所選產生器的組建指令碼。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `installRoot`：指定目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `cmakeCommandArgs`：指定為產生快取而叫用時，會傳遞到 CMake 的其他命令列選項。
- `cmakeToolchain`：指定工具鏈檔案。 這會使用 -DCMAKE_TOOLCHAIN_FILE 傳遞給 CMake。
- `buildCommandArgs`：指定在 --build -- 之後傳遞到 CMake 的原生組建參數。
- `ctestCommandArgs`：指定執行測試時，會傳遞到 CTest 的其他命令列選項。
- `codeAnalysisRuleset`：指定執行程式碼分析時要使用的規則集。 這可以是完整的路徑，或是 Visual Studio 安裝之規則集檔案的檔案名稱。
- `intelliSenseMode`：指定計算 Intellisense 資訊時所使用的模式。 可能是下列其中之一：
 
  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `cacheRoot`：指定 CMake 快取的路徑。 此目錄應包含現有 CMakeCache.txt 檔案。
- `remoteMachineName`：指定裝載 CMake、組建和偵錯工具之遠端 Linux 電腦的名稱。 使用連線管理員新增新的 Linux 電腦。 支援的巨集包括 `${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`：指定從來源到遠端電腦的複製作業詳細資訊層級。 可能為「正常」、「詳細資訊」或「診斷」其中之一。
- `remoteCopySourcesConcurrentCopies`：指定將來源同步處理到遠端電腦期間，所用的並行複本數目。
- `remoteCopySourcesMethod`：指定將檔案複製到遠端電腦的方法。 可能為 "rsync" 或 "sftp"。
- `remoteCMakeListsRoot`：指定遠端電腦上包含 CMake 專案的目錄。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteBuildRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的組建指令碼。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}`、`${env.VARIABLE}`。
- `remoteInstallRoot`：指定遠端電腦上的目錄，CMake 會在此產生所選產生器的安裝目標。 支援的巨集包括 `${workspaceRoot}`、`${workspaceHash}`、`${projectFile}`、`${projectDir}`、`${thisFile}`、`${thisFileDir}`、`${name}`、`${generator}` 和 `${env.VARIABLE}`，其中 `VARIABLE` 是已在系統、使用者或工作階段層級定義的環境變數。
- `remoteCopySources`：`boolean`，指定 Visual Studio 是否應該將來源檔案複製到遠端電腦。 預設值為 true。 如果自行管理檔案同步處理，請設定為 false。
- `remoteCopyBuildOutput`：`boolean`，指定是否要從遠端系統複製組建輸出。
- `rsyncCommandArgs`：指定一組傳遞給 rsync 的額外命令列選項。
- `remoteCopySourcesExclusionList`：`array`指定複製來源檔案時要排除的路徑清單：路徑可以是檔案/目錄名稱，或複本根目錄的相對路徑。 萬用字元 \\\"*\\\" 和 \\\"?\\\" 可以用於 Glob 模式比對。
- `cmakeExecutable`：指定 CMake 程式可執行檔的完整路徑，包括檔案名稱與副檔名。
- `remotePreGenerateCommand`：指定執行 CMake 以剖析 CMakeLists.txt 之前必須執行的命令。
- `remotePrebuildCommand`：指定建置之前必須對遠端電腦執行的命令。
- `remotePostbuildCommand`：指定建置之後必須對遠端電腦執行的命令。
- `variables`：`array`，指定傳遞至 CMake 作為 -Dname1=value1 -Dname2=value2 等的變數。 


