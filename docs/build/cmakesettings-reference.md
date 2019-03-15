---
title: CMakeSettings.json 結構描述參考
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: d80829b1475e8718e1c4188ff4fb7d42a1d4b3b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825945"
---
# <a name="cmakesettingsjson-schema-reference"></a>CMakeSettings.json 結構描述參考

`cmakesettings.json`檔案包含指定 Visual Studio 應該如何互動以建置專案，以供指定的平台的 CMake 的資訊。 使用此檔案來儲存環境變數或引數為 cmake.exe 環境等資訊。

## <a name="environments"></a>環境

`environments`陣列包含一份`items`型別的`object`以定義的 「 環境 」。 環境可用來將一組變數，以套用`configuration`。 在每個項目`environments`陣列所組成：

- `namespace`： 名稱的環境，以便可以從表單中的組態參考其變數`namespace.variable`。 預設環境的物件稱為`env`並填入特定系統環境變數，包括`%USERPROFILE%`。
- `environment`： 唯一識別這個群組的變數。 可讓稍後繼承群組`inheritEnvironments`項目。
- `groupPriority`：整數，方便評估時指定這些變數的優先順序。 會先評估更高的項目數目。
- `inheritEnvironments`：指定此群組會繼承的環境組的值陣列。 可以使用任何自訂的環境，或這些預先定義的環境：
 
  - linux_arm:遠端目標 ARM Linux。
  - linux_x64:鎖定 x64 Linux 遠端。
  - linux_x86:鎖定 x86 Linux 遠端。
  - msvc_arm:目標含 MSVC 編譯器的 ARM Windows。
  - msvc_arm_x64:目標與 64 位元 MSVC 編譯器的 ARM Windows。
  - msvc_arm64:目標含 MSVC 編譯器的 ARM64 Windows。
  - msvc_arm64_x64:目標與 64 位元 MSVC 編譯器的 ARM64 Windows。
  - msvc_x64:含 MSVC 編譯器的 x64 Windows。
  - msvc_x64_x64:使用 64 位元 MSVC 編譯器的 x64 Windows。
  - msvc_x86:含 MSVC 編譯器的目標 x86 Windows。
  - msvc_x86_x64:使用 64 位元 MSVC 編譯器的目標 x86 Windows。

## <a name="configurations"></a>組態

`configurations`陣列包含這些物件表示套用至相同的資料夾中 CMakeLists.txt 檔案的 CMake 組態。 您可以使用這些物件來定義多個組建組態，並輕鬆切換其在 IDE 中。 

A`configuration`具有下列屬性：
- `name`： 設定的名稱。
- `description`： 這項設定將出現在功能表中的描述。
- `generator`： 指定要用於此組態的 CMake 產生器。 可能是其中之一：

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Unix Makefile
  - 忍者

- `configurationType`： 指定所選產生器的組建類型組態。 可能是其中之一：
 
  - 偵錯
  - 版本
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`： 指定此設定支援的一或多個環境。 可能是任何自訂的環境，或其中一個預先定義的環境。
- `buildRoot`： 比較目錄中的 CMake 產生組建指令碼所選擇的產生器。 支援的巨集包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。 」
- `installRoot`： 指定在其中 CMake 產生安裝目標所選擇的產生器的目錄。 支援的巨集包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。 」
- `cmakeCommandArgs`： 指定其他命令列選項傳遞至 CMake 時叫用來產生快取。 」
- `cmakeToolchain`： 指定工具鏈檔案。 這會傳遞至 CMake 使用-DCMAKE_TOOLCHAIN_FILE。 」
- `buildCommandArgs`： 指定-組建-之後傳遞到 CMake 的原生組建參數。 」
- `ctestCommandArgs`： 指定其他命令列選項在執行測試時，要傳遞到 CTest。 」
- `codeAnalysisRuleset`： 指定執行程式碼分析時要使用的規則集。 這可以是完整路徑或 Visual Studio 所安裝的規則集檔案的檔案名稱。 」
- `intelliSenseMode`： 指定用於計算 intellisense 資訊的模式 」。 可能是其中之一：
 
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

- `cacheRoot`： 指定的 CMake 快取的路徑。 這個目錄應該包含現有的 CMakeCache.txt 檔案。
- `remoteMachineName`： 指定裝載 CMake、 組建和偵錯工具的遠端 Linux 電腦的名稱。 使用連接管理員加入新的 Linux 機器。 支援的巨集包括`${defaultRemoteMachineName}`。
- `remoteCopySourcesOutputVerbosity`： 指定來源到遠端電腦的複製作業的詳細資訊層級。 可能是其中一種 「 「 正常 」、 「 詳細資訊 」 或 「 診斷 」。
- `remoteCopySourcesConcurrentCopies`： 指定的來源，以在遠端電腦的同步處理期間所使用的並行複製數目。
- `remoteCopySourcesMethod`： 指定要將檔案複製到遠端電腦的方法。 可能是"rsync 」 或 「 sftp 」。
- `remoteCMakeListsRoot`： 指定包含 CMake 專案的遠端電腦上的目錄。 支援的巨集包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。
- `remoteBuildRoot`： 指定的目錄中的 CMake 產生組建指令碼，所選擇的產生器的遠端電腦上。 支援的巨集包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`， `${env.VARIABLE}`。
- `remoteInstallRoot`： 指定的目錄中的 CMake 產生安裝目標所選擇的產生器的遠端電腦上。 支援的巨集包括`${workspaceRoot}`， `${workspaceHash}`， `${projectFile}`， `${projectDir}`， `${thisFile}`， `${thisFileDir}`， `${name}`， `${generator}`，並`${env.VARIABLE}`其中`VARIABLE`是有環境變數已定義在系統、 使用者或工作階段層級。
- `remoteCopySources`：A`boolean`指定 Visual Studio 是否應該將原始程式檔複製到遠端電腦。 預設值為 true。 如果您管理檔案同步處理您自己，設定為 false。
- `remoteCopyBuildOutput`：A `boolean` ，指定是否要從遠端系統複製組建輸出。
- `rsyncCommandArgs`： 指定一組傳遞給 rsync 的其他命令列選項。
- `remoteCopySourcesExclusionList`：A `array` ，指定的複製來源檔案時要排除的路徑清單： 路徑可以是檔案/目錄或複製的根目錄的相對路徑的名稱。 萬用字元\\ \" * \\ \"並\\ \"？\\\"可以用於 glob 模式比對。
- `cmakeExecutable`： 指定 CMake 程式可執行檔，包括檔名和副檔名的完整路徑。
- `remotePreGenerateCommand`： 指定要執行，才能執行 CMake 以剖析 CMakeLists.txt 檔案的命令。
- `remotePrebuildCommand`： 指定要建置前在遠端電腦上執行的命令。
- `remotePostbuildCommand`： 指定要在建置之後，在遠端電腦上執行的命令。
- `variables`：A`array`指定變數傳遞至 CMake 作為-Dname1 = value1-Dname2 = value2，依此類推。 


