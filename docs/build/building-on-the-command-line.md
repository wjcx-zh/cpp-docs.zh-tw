---
title: 使用 MSVC 工具組，從命令列-Visual Studio
description: 使用 Microsoft c + + 編譯器工具鏈 (MSVC) 從 Visual Studio IDE 外部命令列。
ms.custom: conceptual
ms.date: 12/10/2018
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 21d1c9063a1d6dd154de8d2caca913ea3fd0ce37
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812118"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>使用 MSVC 工具組，從命令列

您可以使用隨附於 Visual Studio 的工具來建置 C 和 c + + 命令列上的應用程式。 您也可以下載編譯器工具組，作為從獨立封裝[Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721)。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令列工具

當您選擇的 c + + 工作負載的其中一個 Visual Studio 安裝程式時，它會安裝 Visual Studio*平台工具組*。 平台工具組都有特定的 Visual Studio 版本，包括 C/c + + 編譯器、 連結器、 組譯工具和其他建置工具，以及相符的程式庫的所有 C 和 c + + 工具。 您可以在命令列中，使用所有這些工具，它們也可供在內部 Visual Studio IDE。 有個別 x86 架構和 x64 架構的編譯器和工具來建置程式碼，針對 x86、 x64、 ARM 及 ARM64 目標。 適用於特定的主機和目標組建架構工具的每一組會儲存在它自己的目錄。

已安裝的編譯器工具組，取決於您電腦的處理器以及在安裝期間選取的選項。 最小值，會安裝 32 位元 x86 架構工具，建置 32 位元 x86 原生程式碼和跨建置 64 位元 x64 原生程式碼的工具。 如果您有 64 位元 Windows，也會安裝 64 位元裝載 x64 的工具，建置 64 位元原生程式碼，並跨建置 32 位元原生程式碼的工具。 如果您選擇安裝選用性的 c + + 通用 Windows 平台工具，然後也會安裝 32 位元和 64 位元原生工具建置的 ARM 程式碼。 其他工作負載可能會安裝其他工具。

## <a name="environment-variables-and-developer-command-prompts"></a>環境變數和開發人員命令提示字元

正常運作，工具會需要設定幾個特定的環境變數。 這些用來將它們新增至路徑，並設定包含檔案、 程式庫檔案，以及 SDK 的位置。 若要讓您輕鬆地設定這些環境變數，安裝程式會建立自訂*命令檔*，或在安裝期間的批次檔。 您可以在命令提示字元視窗中設定特定的主機和目標組建架構、 Windows SDK 版本，目標平台，以及平台工具組來執行其中一個命令檔案。 為了方便起見，安裝程式也會在您開始使用這些命令檔，因此所有必要的環境變數設定且可供使用的開發人員命令提示字元 視窗的開始功能表中建立捷徑。

必要的環境變數專安裝到組建架構選擇，並可能變更產品更新或升級。 因此，強烈建議您其中一個已安裝的命令提示字元 捷徑或命令檔案而不是環境變數中設定 Windows 自行進行使用。 如需詳細資訊，請參閱 <<c0> [ 設定的路徑和環境變數的命令列建置](setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="developer_command_prompt_shortcuts"></a> 開發人員命令提示字元捷徑

命令提示字元 捷徑會安裝在您的 開始 功能表中的特定版本的 Visual Studio 資料夾中。 以下是一份基底的命令提示字元 捷徑，以及它們所支援的組建架構：

- **開發人員命令提示字元**-設定環境以使用 32 位元、 x86 native tools 建置 32 位元、 x86 原生程式碼。
- **x86 native Tools 命令提示字元**-設定環境以使用 32 位元、 x86 native tools 建置 32 位元、 x86 原生程式碼。
- **x64 native Tools 命令提示字元**-設定環境以使用 64 位元、 x64 native tools 建置 64 位元、 x64 原生程式碼。
- **x86_x64 Cross Tools 命令提示字元**-設定環境以使用 32 位元、 x86 native tools 建置 64 位元、 x64 原生程式碼。
- **x64_x86 Cross Tools 命令提示字元**-設定環境以使用 64 位元、 x64 native tools 建置 32 位元、 x86 原生程式碼。

如果您設定其中一個的則根據您已安裝，Visual Studio 的版本和安裝暱稱中實際的開始功能表 資料夾和捷徑名稱而有所不同。 例如，如果您有 Visual Studio 2017 安裝，而且您之後就安裝暱稱的*Preview*，在名為開發人員命令提示字元捷徑**開發人員命令提示字元，適用於 VS 2017 （預覽）**，在名為的資料夾**Visual Studio 2017**。

如果您已安裝[Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721) （也包括 Visual Studio 2015 Update 3 的編譯器工具組），只有特定架構的原生或跨工具開發人員命令提示字元安裝選項並不是一般**開發人員命令提示字元**捷徑。

## <a name="developer_command_prompt"></a> 若要開啟 [開發人員命令提示字元] 視窗

1. 在桌面上，開啟 Windows**開始**功能表，然後尋找並開啟您版本的 Visual Studio 中，資料夾，例如，然後捲動**Visual Studio 2017**。 呼叫的子資料夾中，在某些較舊版本的 Visual Studio 中，是捷徑**Visual Studio Tools**。

1. 在資料夾中，選擇**開發人員命令提示字元**針對您的 Visual Studio 版本。 此快速鍵啟動會使用預設組建架構的 32 位元、 x86 原生工具來建置 32 位元、 x86 原生程式碼的開發人員命令提示字元視窗。 如果您偏好的非預設建置架構時，選擇其中一個原生或跨工具命令提示字元，以指定的主機和目標架構。

若要開啟 [開發人員命令提示字元視窗更快的方式是輸入*開發人員命令提示字元*桌面搜尋] 方塊中，然後選擇所要的結果。

## <a name="developer_command_file_locations"></a> 開發人員命令檔案位置

如果您想要在現有的 [命令提示字元] 視窗中設定建置架構環境，您可以使用其中一個命令檔案 （批次檔） 安裝程式所建立，若要設定所需的環境。 我們只建議您在新的命令提示字元視窗中，執行這項操作，並不建議您在相同的命令視窗中的更新版本切換環境。 這些檔案的位置取決於您已安裝，Visual Studio 的版本和位置，並命名您在安裝期間所做的選擇。 對於 Visual Studio 2017，在 64 位元電腦上的一般安裝位置位於 \Program 檔案 (x86) \Microsoft Visual Studio\2017\\*edition*，其中*edition*可能是社群Professional、 Enterprise、 BuildTools 或您提供的另一個名稱。 Visual Studio 2015，一般安裝位置是 \Program 檔案 (x86) \Microsoft Visual Studio 14.0。

主要的開發人員命令提示字元命令檔，VsDevCmd.bat，位於安裝目錄 Common7\Tools 子目錄。 當未指定任何參數，這會設定環境，而主機和目標建置所要使用 32 位元 x86 原生工具來建置 32 位元 x86 架構程式碼。

額外的命令檔可用於設定特定組建的架構，視您的處理器架構和 Visual Studio 工作負載和您已安裝的選項而定。 在 Visual Studio 2017 中，這些全都位於 Visual Studio 安裝目錄的 VC\Auxiliary\Build 子目錄。 在 Visual Studio 2015，這些全都位於 VC、 VC\bin 或 VC\bin\\*架構*子目錄的安裝目錄，其中*架構*是其中一個原生或跨編譯器選項。 這些命令檔設定預設參數，而且呼叫來設定指定的組建架構環境的 VsDevCmd.bat。 一般安裝可能會包含這些指令檔：

|命令檔|主機和目標架構|
|---|---|
|**vcvars32.bat**| 使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。|
|**vcvars64.bat**| 使用 64 位元 x64 原生工具來建置 64 位元 x64 程式碼。|
|**vcvarsx86_amd64.bat**| 使用 32 位元 x86 原生跨工具來建置 64 位元 x64 程式碼。|
|**vcvarsamd64_x86.bat**| 使用 64 位元 x64 原生跨工具來建置 32 位元 x86 程式碼。|
|**vcvarsx86_arm.bat**| 您可以使用 32 位元 x86 原生跨工具來建置 ARM 程式碼。|
|**vcvarsamd64_arm.bat**| 使用 64 位元 x64 原生跨工具來建置 ARM 程式碼。|
|**vcvarsall.bat**| 您可以使用參數來指定主機和目標架構，以及 SDK 和平台的選項。 如需支援的選項中，使用呼叫 **/help**參數。|

> [!CAUTION]
> Vcvarsall.bat 檔案以及其他 Visual Studio 命令檔案，可能會不同的電腦。 請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。 重新執行 Visual Studio 安裝程式，以取代遺失的檔案。
>
> 在不同的版本上，vcvarsall.bat 也可能不同。 如果已安裝 Visual Studio 的目前版本，也有舊版的 Visual Studio 的電腦上，無法執行 vcvarsall.bat 或另一個 Visual Studio 命令檔案在相同的 [命令提示字元] 視窗中的不同版本。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在現有的 [命令] 視窗中使用開發人員工具

在現有的 [命令] 視窗中指定特定組建架構的最簡單方式是使用 vcvarsall.bat 檔案。 您可以使用 vcvarsall.bat 設定環境變數，以設定命令列進行原生 32 位元或 64 位元編譯，或針對 x86、 x64 或 ARM 處理器; 交互編譯以 Microsoft Store、 通用 Windows 平台或 Windows 桌面平台; 為目標若要指定要使用哪個 Windows SDK與指定的平台工具組版本。 如果沒有提供任何引數，則 vcvarsall.bat 會設定環境變數以供使用目前的 32 位元原生編譯器的 x86 Windows 桌面的目標。 不過，您可以使用它來設定任何原生，或是跨編譯器工具。 如果您指定的編譯器組態，未安裝或不在組建電腦架構上，會顯示一則錯誤訊息。

### <a name="vcvarsall-syntax"></a>vcvarsall 語法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
這個選擇性的引數會指定要使用的主機和目標架構。 如果*架構*未指定，會使用預設的組建環境。 支援這些引數：

|*architecture*|編譯器|主機電腦架構|建置輸出 （目標） 架構|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位元原生|x86、x64|x86|
|**x86\_amd64**或是**x86\_x64**|在 x86 x64 cross|x86、x64|X64|
|**x86_arm**|ARM on x86 (跨平台)|x86、x64|ARM|
|**x86_arm64**|在 x86 跨 ARM64|x86、x64|ARM64|
|**amd64**或**x64**|x64 64 位元原生|X64|X64|
|**amd64\_x86**或是**x64\_x86**|x86 x64 cross|X64|x86|
|**amd64\_arm**或是**x64\_arm**|在 x64 cross ARM|X64|ARM|
|**amd64\_arm64**或是**x64\_arm64**|在 x64 cross ARM64|X64|ARM64|

*platform_type*<br/>
這個選擇性的引數可讓您指定**儲存**或是**uwp**做為平台類型。 根據預設，環境是設定為建置傳統型或主控台應用程式。

*winsdk_version*<br/>
選擇性地指定要使用的 Windows SDK 的版本。 根據預設，會使用最新已安裝的 Windows SDK。 若要指定的 Windows SDK 版本，您可以使用完整的 Windows 10 SDK 號碼這類**10.0.10240.0**，或指定**8.1**若要使用 Windows 8.1 SDK。

*vcversion*<br/>
（選擇性） 指定要使用 Visual Studio 編譯器工具組。 根據預設，環境是設定為使用目前的 Visual Studio 2017 編譯器工具組。 使用 **-vcvars_ver=14.0 = 14.0**指定 Visual Studio 2015 的編譯器工具組。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>若要設定建置環境中現有的 [命令提示字元] 視窗

1. 在命令提示字元中，使用 CD 命令來切換至 Visual Studio 安裝目錄。 然後，變更至子目錄，其中包含的特定組態指令檔再次使用 CD。 Visual Studio 2017 中，這是 VC\Auxiliary\Build 子目錄。 Visual Studio 2015 中，使用 VC 子目錄。

1. 輸入命令，為您慣用的開發人員的環境。 例如，若要建立 ARM 程式碼適用於 UWP 的 64 位元平台上使用最新的 Windows SDK 和 Visual Studio 2017 RTM 編譯器工具組，使用這個命令列：

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>建立您自己的命令提示字元捷徑

如果您開啟 [屬性] 對話方塊，其中一個現有的開發人員命令提示字元捷徑，您可以看到使用的命令目標。 例如，針對目標**x64 Native Tools 命令提示字元，適用於 VS 2017**捷徑會類似：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

架構特定批次檔組*架構*參數並呼叫 vcvarsall.bat。 您會將它傳遞給 vcvarsall.bat，或您只可以直接呼叫 vcvarsall.bat，您可以將相同的其他選項傳遞給這些批次檔中。 若要指定您自己的命令捷徑的參數，將它們加入雙引號括住命令的結尾。 比方說，若要設定使用最新的 Windows SDK 和 Visual Studio 2017 RTM 編譯器工具組，適用於 UWP 建置 ARM 程式碼的 64 位元平台上的捷徑使用類似此命令目標，在您的捷徑：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

您必須先調整路徑，以反映您的 Visual Studio 安裝目錄。

## <a name="command-line-tools"></a>命令列工具

若要在命令列上建置 C/c + + 專案，Visual Studio 會提供這些命令列工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用編譯器 (cl.exe)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。

[連結](reference/linking.md)<br/>
使用連結器 (link.exe)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和專案檔 (.vcxproj) 來設定組建和間接叫用的工具組。 這相當於執行**建置**專案或**建置方案**命令在 Visual Studio IDE 中。 從命令列執行 MSBuild 是進階的案例，而且通常不建議。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
使用 DEVENV (devenv.exe) 結合命令列切換 — 比方說， **/組建**或 **/清除**— 若要執行特定建置而不會顯示在 Visual Studio IDE 命令。 通常這是慣用使用 MSBuild，直接因為您可以讓 Visual Studio 會處理 MSBuild 的複雜性。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe)，來建置傳統 makefile 為基礎的 c + + 專案。

當您建置命令列上時，F1 命令不適用於立即協助。 相反地，您可以使用搜尋引擎，若要取得警告、 錯誤和訊息的相關資訊，或者您可以使用離線說明檔案。 若要使用搜尋 中的[docs.microsoft.com](https://docs.microsoft.com/cpp/)，在頁面頂端的 [搜尋] 方塊中輸入搜尋字串。

## <a name="in-this-section"></a>本節內容

文件中本區段的文章顯示如何在命令列上建置應用程式，描述如何自訂命令列建置環境，以使用 64 位元工具組並將目標設定為 x86、x64 及 ARM 平台，以及示範如何使用命令列建置工具 MSBuild 及 NMAKE。

[逐步解說：在命令列編譯原生 C++ 程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供範例，顯示如何在命令列上建立及編譯簡單的 C++ 程式。

[逐步解說：編譯 C 程式中，在命令列上](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
描述如何編譯以 C 程式設計語言撰寫的程式。

[逐步解說：在命令列編譯 C++/CLI 程式](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 .NET Framework 的 C++/CLI 程式。

[逐步解說：在命令列編譯 C++/CX 程式](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 Windows 執行階段的 C++/CX 程式。

[設定命令列建置的路徑及環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
描述如何啟動命令提示字元視窗，並具有必要的環境變數設定命令列建置目標 x86、 x64 和 ARM 平台，使用 32 位元或 64 位元工具組。

[NMAKE 參考](reference/nmake-reference.md)<br/>
提供指向描述 Microsoft Program Maintenance Utility (NMAKE.EXE) 之文章的連結。

[MSBuild 命令列-c + +](msbuild-visual-cpp.md)<br/>
提供討論如何使用 msbuild.exe 從命令列的文章連結。

## <a name="related-sections"></a>相關章節

[/MD、/MT、/LD (使用執行階段程式庫)](reference/md-mt-ld-use-run-time-library.md)<br/>
描述如何使用這些編譯器選項，來使用偵錯或發行執行階段程式庫。

[C/c + + 編譯器選項](reference/compiler-options.md)<br/>
提供指向討論 C 及 C++ 編譯器選項及 CL.exe 之文章的連結。

[MSVC 連結器選項](reference/linker-options.md)<br/>
提供指向討論連結器選項及 LINK.exe 之文章的連結。

[其他 MSVC 建置工具](reference/c-cpp-build-tools.md)<br/>
提供連結至 C/c + + 建置工具隨附於 Visual Studio。

## <a name="see-also"></a>另請參閱

[專案和組建系統](projects-and-build-systems-cpp.md)