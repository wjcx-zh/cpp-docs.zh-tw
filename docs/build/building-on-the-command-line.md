---
title: 從命令列使用 MSVC 工具組 - Visual Studio
description: 在 Visual Studio IDE 外部從命令列使用 MicrosoftC++ 編譯器工具鏈 (MSVC)。
ms.custom: conceptual
ms.date: 05/16/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 97626455ace0d3ad47b9011594e82c144d7ea27d
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837120"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>從命令列使用 MSVC 工具組

您可以使用 Visual Studio 中包含的工具，在命令列上建置 C 和 C++ 應用程式。 您也可以從 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面下載編譯器工具組，作為獨立套件。 這是 **Build Tools for Visual Studio** 套件的一部分；您可以選擇僅下載 C++ 開發所需的工具。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令列工具

當您選擇 Visual Studio 安裝程式中的其中一個 C++ 工作負載時，它將會安裝 Visual Studio *平台工具組*。 平台工具組具有特定 Visual Studio 版本適用的所有 C 和 C++ 工具，包括 C/C++ 編譯器、連結器、組譯工具和其他建置工具，以及相符的程式庫。 您可以在命令列中使用這些工具，也可以透過 Visual Studio IDE 在內部使用。 這些是個別的 x86 架構和 x64 架構的編譯器和工具，可用來建置 x86、x64、ARM 和 ARM64 目標的程式碼。 特定主機和目標組建架構適用的每一組工具都會儲存在其本身的目錄中。

安裝的編譯器工具組取決於您的電腦處理器以及在安裝期間選取的選項。 至少會安裝建置 32 位元 x86 原生程式碼的 32 位元 x86 架構工具，以及建置 64 位元 x64 原生程式碼的跨平台工具。 如果您具有 64 位元 Windows，則也會安裝建置 64 位元原生程式碼的 64 位元 x64 架構工具，以及建置 32 位元原生程式碼的跨平台工具。 如果您選擇安裝選擇性的 C++ 通用 Windows 平台工具，則也會安裝建置 ARM 程式碼的 32 位元和 64 位元原生工具。 其他工作負載可能會安裝其他工具。

## <a name="environment-variables-and-developer-command-prompts"></a>環境變數和開發人員命令提示字元

若要正常運作，工具必須設定數個特定的環境變數。 這些變數會用來將其新增至路徑，並設定 Include 檔案、程式庫檔案和 SDK 的位置。 為了方便您設定這些環境變數，安裝程式在安裝期間會建立自訂*命令檔*或批次檔。 您可以在命令提示字元視窗中執行其中一個命令檔，以設定特定的主機和目標組建架構、Windows SDK 版本、目標平台和平台工具組。 為了方便起見，安裝程式也會在您的 [開始] 功能表中建立可使用這些命令檔啟動開發人員命令提示字元視窗的捷徑，讓所有必要的環境變數完成設定且可供使用。

必要的環境變數專用於您的安裝和您所選擇的組建架構，在產品更新或升級時可能會變更。 因此，強烈建議您使用其中一個已安裝的命令提示字元捷徑或命令檔，而不要在 Windows 中自行設定環境變數。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="developer_command_prompt_shortcuts"></a> 開發人員命令提示字元捷徑

命令提示字元捷徑會在您的 [開始] 功能表中安裝於特定版本的 Visual Studio 資料夾內。 以下列出基礎命令提示字元捷徑及其支援的組建架構：

- **開發人員命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 32 位元、x86 原生程式碼。
- **x86 Native Tools 命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 32 位元、x86 原生程式碼。
- **x64 Native Tools 命令提示字元** - 將環境設定為使用 64 位元、x64 原生工具來建置 64 位元、x64 原生程式碼。
- **x86_x64 Cross Tools 命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 64 位元、x64 原生程式碼。
- **x64_x86 Cross Tools 命令提示字元** - 將環境設定為使用 64 位元、x64 原生工具來建置 32 位元、x86 原生程式碼。

實際的 [開始] 功能表資料夾和捷徑名稱，會隨著您已安裝的 Visual Studio 版本和您所設定的安裝暱稱而不同。 例如，如果您已安裝 Visual Studio 2019，且您為其指定了安裝暱稱 *Preview*，則開發人員命令提示字元捷徑的名稱會是 **VS 2019 的開發人員命令提示字元**，且位於名為 **Visual Studio 2019** 的資料夾中。

## <a name="developer_command_prompt"></a> 開啟開發人員命令提示字元視窗

1. 在桌面上開啟 Windows 的 [開始] 功能表，然後藉由捲動找出您的 Visual Studio 版本的資料夾 (例如 **Visual Studio 2019**)，並加以開啟。 在某些較舊的 Visual Studio 版本中，捷徑會位於名為 **Visual Studio Tools** 的子資料夾中。

1. 在該資料夾中，針對您的 Visual Studio 版本選擇 [開發人員命令提示字元]。 此捷徑會啟動開發人員命令提示字元視窗，並使用 32 位元、x86 原生工具的預設組建架構來建置 32 位元、x86 原生程式碼。 如果您偏好使用非預設組建架構，請選擇其中一個原生或跨平台工具命令提示字元，以指定主機和目標架構。

更快速開啟開發人員命令提示字元視窗的方式，是在桌面搜尋方塊中輸入*開發人員命令提示字元*，然後選擇所需的結果。

## <a name="developer_command_file_locations"></a> 開發人員命令檔案位置

如果您想要在現有的命令提示字元視窗中設定組建架構環境，您可以使用安裝程式所建立的其中一個命令檔 (批次檔) 來設定所需的環境。 我們僅建議您在新的命令提示字元視窗中執行這項操作，且不建議您後續在相同的命令視窗中切換環境。 這些檔案的位置取決於您已安裝的 Visual Studio 版本，以及您在安裝期間所選擇的位置和命名。 Visual Studio 2019 在 64 位元電腦上的安裝位置通常為 \Program Files (x86)\Microsoft Visual Studio\2019\*edition*，其中，*edition* 可以是 Community、Professional、Enterprise、BuildTools 或您提供的其他名稱。 Visual Studio 2017 的位置也相類似。 Visual Studio 2015 的安裝位置通常為 \Program Files (x86)\Microsoft Visual Studio 14.0。

主要開發人員命令提示字元命令檔 VsDevCmd.bat 位於安裝目錄的 Common7\Tools 子目錄中。 未指定任何參數時，這會將環境以及主機和目標組建架構設定為使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。

此外，根據您的處理器架構和 Visual Studio 工作負載以及您已安裝的選項，還有其他命令檔可用來設定特定的組建架構。 在 Visual Studio 2017 和 Visual Studio 2019 中，這些檔案位於 Visual Studio 安裝目錄的 VC\Auxiliary\Build 子目錄中。 在 Visual Studio 2015 中，這些檔案位於安裝目錄的 VC、VC\bin 或 VC\bin\\*architectures* 子目錄中，其中，*architectures* 是原生或跨平台編譯器選項之一。 這些命令檔會設定預設參數並呼叫 VsDevCmd.bat，以設定指定的組建架構環境。 一般安裝可能會包含下列命令檔：

|命令檔|主機和目標架構|
|---|---|
|**vcvars32.bat**| 使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。|
|**vcvars64.bat**| 使用 64 位元 x64 原生工具來建置 64 位元 x64 程式碼。|
|**vcvarsx86_amd64.bat**| 使用 32 位元 x86 原生跨平台工具來建置 64 位元 x64 程式碼。|
|**vcvarsamd64_x86.bat**| 使用 64 位元 x64 原生跨平台工具來建置 32 位元 x86 程式碼。|
|**vcvarsx86_arm.bat**| 使用 32 位元 x86 原生跨平台工具來建置 ARM 程式碼。|
|**vcvarsamd64_arm.bat**| 使用 64 位元 x64 原生跨平台工具來建置 ARM 程式碼。|
|**vcvarsall.bat**| 使用參數來指定主機和目標架構以及 SDK 和平台選項。 如需支援的選項清單，請使用 **/help** 參數來呼叫。|

> [!CAUTION]
> 在不同的電腦上，vcvarsall.bat 檔案和其他 Visual Studio 命令可能有所不同。 請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。 重新執行 Visual Studio 安裝程式以取代遺漏的檔案。
>
> 在不同的版本上，vcvarsall.bat 也可能不同。 如果安裝最新版 Visual Studio 的電腦上也有舊版的 Visual Studio，請不要在同一個命令提示字元視窗中執行不同版本的 vcvarsall.bat 或其他 Visual Studio 命令檔。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在現有的命令視窗中使用開發人員工具

要在現有的命令視窗中指定特定的組建架構，最簡單的方式是使用 vcvarsall.bat 檔案。 您可以使用 vcvarsall.bat 設定環境變數，以設定命令列來進行原生 32 位元或 64 位元編譯，或進行 x86、x64 或 ARM 處理器的跨平台編譯；以 Microsoft Store、通用 Windows 平台或 Windows 桌面平台為目標；指定要使用的 Windows SDK，以及指定平台工具組版本。 如果未提供引數，則 vcvarsall.bat 會設定環境變數，以將目前的 32 位元原生編譯器用於 x86 Windows 桌面目標。 不過，您可以使用此檔案來設定任何原生或跨平台編譯器工具。 如果您指定了組建電腦架構未安裝或無法使用的編譯器組態，則會顯示錯誤訊息。

### <a name="vcvarsall-syntax"></a>vcvarsall 語法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
這個選擇性引數會指定要使用的主機和目標架構。 若未指定 *architecture*，則會使用預設的組建環境。 支援的引數如下：

|*architecture*|編譯器|主機電腦架構|組建輸出 (目標) 架構|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位元原生|x86、x64|x86|
|**x86\_amd64** 或 **x86\_x64**|x64 on x86 (跨平台)|x86、x64|X64|
|**x86_arm**|ARM on x86 (跨平台)|x86、x64|ARM|
|**x86_arm64**|ARM64 on x86 (跨平台)|x86、x64|ARM64|
|**amd64** 或 **x64**|x64 64 位元原生|X64|X64|
|**amd64\_x86** 或 **x64\_x86**|x86 on x64 (跨平台)|X64|x86|
|**amd64\_arm** 或 **x64\_arm**|ARM on x64 (跨平台)|X64|ARM|
|**amd64\_arm64** 或 **x64\_arm64**|ARM64 on x64 (跨平台)|X64|ARM64|

*platform_type*<br/>
這個選擇性引數可讓您將 **store** 或 **uwp** 指定為平台類型。 根據預設，環境會設定為建置桌面或主控台應用程式。

*winsdk_version*<br/>
選擇性地指定要使用的 Windows SDK 版本。 根據預設，會使用最新安裝的 Windows SDK。 若要指定 Windows SDK 版本，您可以使用完整的 Windows 10 SDK 號碼 (例如 **10.0.10240.0**)，或指定 **8.1** 以使用 Windows 8.1 SDK。

*vcversion*<br/>
選擇性地指定要使用的 Visual Studio 編譯器工具組。 根據預設，環境會設定為使用目前的 Visual Studio 編譯器工具組。 您可以使用 **-vcvars_ver=14.0** 指定 Visual Studio 2015 編譯器工具組，或使用 **-vcvars_ver=15.0** 指定 Visual Studio 2017 編譯器工具組。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>在現有的命令提示字元視窗中設定組建環境

1. 在命令提示字元中，使用 CD 命令切換至 Visual Studio 安裝目錄。 然後，再次使用 CD 變更至包含組態特定指令檔的子目錄。 Visual Studio 2017 和 Visual Studio 2019 的這個子目錄為 VC\Auxiliary\Build。 若為 Visual Studio 2015，請使用 VC 子目錄。

1. 針對您慣用的開發人員環境輸入命令。 例如，若要使用最新的 Windows SDK 和 Visual Studio 2019 編譯器工具組在 64 位元平台上建置適用於 UWP 的 ARM 程式碼，請使用下列命令列：

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>建立您自己的命令提示字元捷徑

如果您開啟其中一個現有開發人員命令提示字元捷徑的 [屬性] 對話方塊，您可以看到使用的命令目標。 例如，**VS 2019 的 x64 Native Tools 命令提示字元**捷徑的目標會類似於：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

架構特定批次檔會設定 *architecture* 參數並呼叫 vcvarsall.bat。 您可以比照傳至 vcvarsall.bat 的方式將相同的其他選項傳至這些批次檔，或者，您可以直接呼叫 vcvarsall.bat。 若要為您自己的命令捷徑指定參數，請將參數新增至命令結尾處，並以雙引號括住。 例如，若要設定使用最新的 Windows SDK 和早於最新版本的編譯器工具組在 64 位元平台上為 UWP 建置 ARM 程式碼的捷徑，您必須指定版本號碼。 請在您的捷徑中使用如下的命令目標：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=15.0"`

您必須調整路徑以反映您的 Visual Studio 安裝目錄。 Vcvarsall.bat 檔案含有關於特定版本號碼的其他資訊。

## <a name="command-line-tools"></a>命令列工具

若要在命令列上建置 C/C++ 專案，請使用 Visual Studio 提供的下列命令列工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用編譯器 (cl.exe)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。

[連結](reference/linking.md)<br/>
使用連結器 (link.exe)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和專案檔 (.vcxproj) 來設定組建並間接叫用工具組。 此作業相當於在 Visual Studio IDE 中執行**建置**專案或**建置方案**命令。 從命令列執行 MSBuild 是進階案例，在一般情況下不建議使用。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
使用 DEVENV (devenv.exe) 搭配命令列參數 (例如 **/Build** 或 **/Clean**)，以在不顯示 Visual Studio IDE 的情況下執行特定建置命令。 一般多半會採用此方式，而非直接使用 MSBuild，因為您可以讓 Visual Studio 處理 MSBuild 的複雜性。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe) 根據傳統 Makefile 建置 C++ 專案。

當您使用命令列建置時，將無法使用 F1 命令取得立即說明。 此時，您可以使用搜尋引擎來取得警告、錯誤和訊息的相關資訊，或者可以使用離線說明檔案。 若要在 [docs.microsoft.com](https://docs.microsoft.com/cpp/) 中使用搜尋，請在頁面頂端的搜尋方塊中輸入搜尋字串。

## <a name="in-this-section"></a>本節內容

文件中本區段的文章顯示如何在命令列上建置應用程式，描述如何自訂命令列建置環境，以使用 64 位元工具組並將目標設定為 x86、x64 及 ARM 平台，以及示範如何使用命令列建置工具 MSBuild 及 NMAKE。

[逐步解說：在命令列編譯原生 C++ 程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供範例，顯示如何在命令列上建立及編譯簡單的 C++ 程式。

[逐步解說：在命令列編譯 C 程式](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
描述如何編譯以 C 程式設計語言撰寫的程式。

[逐步解說：在命令列編譯 C++/CLI 程式](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 .NET Framework 的 C++/CLI 程式。

[逐步解說：在命令列編譯 C++/CX 程式](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 Windows 執行階段的 C++/CX 程式。

[設定命令列建置的路徑及環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
說明如何啟動命令提示字元視窗，以針對使用 32 位元或 64 位元工具組將 x86、x64 和 ARM 平台設為目標的命令列建置，設定必要的環境變數。

[NMAKE 參考](reference/nmake-reference.md)<br/>
提供指向描述 Microsoft Program Maintenance Utility (NMAKE.EXE) 之文章的連結。

[命令列上的 MSBuild - C++](msbuild-visual-cpp.md)<br/>
提供連結以供存取討論如何從命令列使用 msbuild.exe 的文章。

## <a name="related-sections"></a>相關章節

[/MD、/MT、/LD (使用執行階段程式庫)](reference/md-mt-ld-use-run-time-library.md)<br/>
描述如何使用這些編譯器選項，來使用偵錯或發行執行階段程式庫。

[C/C++ 編譯器選項](reference/compiler-options.md)<br/>
提供指向討論 C 及 C++ 編譯器選項及 CL.exe 之文章的連結。

[MSVC 連結器選項](reference/linker-options.md)<br/>
提供指向討論連結器選項及 LINK.exe 之文章的連結。

[其他 MSVC 建置工具](reference/c-cpp-build-tools.md)<br/>
提供 Visual Studio 中包含的 C/C++ 建置工具的連結。

## <a name="see-also"></a>另請參閱

[專案和建置系統](projects-and-build-systems-cpp.md)