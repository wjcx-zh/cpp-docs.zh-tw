---
title: 使用 MicrosoftC++從命令列工具組
description: 在 Visual Studio IDE 外部從命令列使用 MicrosoftC++ 編譯器工具鏈 (MSVC)。
ms.custom: conceptual
ms.date: 06/06/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: b5e9bf266d79ee86cae84535641a52c7c52be391
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821146"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>使用 MicrosoftC++從命令列工具組

您可以使用 Visual Studio 中包含的工具，在命令列上建置 C 和 C++ 應用程式。 Microsoft C++ (MSVC) 編譯器工具組也是作為獨立封裝從可下載[Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面。 它的一部分**Build Tools for Visual Studio**封裝。 您可以選擇下載只將所需的工具C++開發。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令列工具

當您選擇 Visual Studio 安裝程式中的其中一個 C++ 工作負載時，它將會安裝 Visual Studio *平台工具組*。 平台工具組具有所有 C 和C++針對特定的 Visual Studio 版本的工具。 這些工具包括 C /C++編譯器、 連結器、 組譯工具和其他建置工具與相符的程式庫。 您可以使用所有這些工具在命令列。 這些認證也會用在內部由 Visual Studio IDE。 有個別的 x86 架構和 x64 架構的編譯器和工具來建置的程式碼 x86、 x64、 ARM、 及 ARM64 為目標。 特定主機和目標組建架構適用的每一組工具都會儲存在其本身的目錄中。

若要正常運作，工具必須設定數個特定的環境變數。 這些變數用來新增至路徑，並設定工具包括檔案、 程式庫檔案，以及 SDK 的位置。 為了方便您設定這些環境變數，安裝程式在安裝期間會建立自訂*命令檔*或批次檔。 您可以執行這些命令檔，以便設定特定的主機和目標組建架構、 Windows SDK 版本，以及平台工具組的其中一個。 為了方便起見，安裝程式也會在 [開始] 功能表中建立捷徑。 快速鍵啟動開發人員命令提示字元 視窗的主機和目標的特定組合使用這些命令檔。 這些快速鍵，請確定所有必要的環境變數所設定且可供使用。

必要的環境變數專安裝您所選擇的組建架構。 它們也可能會變更產品更新或升級。 這就是為什麼我們建議您搭配使用已安裝的命令提示字元捷徑或命令檔案，而不是自行設定環境變數。 如需詳細資訊，請參閱 <<c0> [ 設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。

工具組、 指令檔和安裝的快速鍵取決於您電腦的處理器以及您在安裝期間選取的選項。 一律會安裝 x86 架構工具及建置 x86 和 x64 的程式碼的跨工具。 如果您有 64 位元 Windows，裝載 x64 的工具與建置 x86 和 x64 的程式碼的跨工具也會安裝。 如果您選擇選擇性C++通用 Windows 平台工具，再建置 ARM 及 ARM64 的程式碼的 x86 和 x64 工具也會安裝。 其他工作負載可能會安裝其他工具。

## <a name="developer_command_prompt_shortcuts"></a> 開發人員命令提示字元捷徑

命令提示字元捷徑會在您的 [開始] 功能表中安裝於特定版本的 Visual Studio 資料夾內。 以下列出基礎命令提示字元捷徑及其支援的組建架構：

- **開發人員命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 32 位元、x86 原生程式碼。
- **x86 Native Tools 命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 32 位元、x86 原生程式碼。
- **x64 Native Tools 命令提示字元** - 將環境設定為使用 64 位元、x64 原生工具來建置 64 位元、x64 原生程式碼。
- **x86_x64 Cross Tools 命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 64 位元、x64 原生程式碼。
- **x64_x86 Cross Tools 命令提示字元** - 將環境設定為使用 64 位元、x64 原生工具來建置 32 位元、x86 原生程式碼。

::: moniker range=">= vs-2019"

開始功能表 資料夾和捷徑名稱需視安裝的 Visual Studio 版本而有所不同。 如果您將設定時，它們也取決於安裝**暱稱**。 例如，假設您安裝 Visual Studio 2019，而且您指定的暱稱*最新*。 名為開發人員命令提示字元捷徑**VS 2019 （最新版） 的開發人員命令提示字元**，在名為的資料夾**Visual Studio 2019**。

::: moniker-end
::: moniker range="= vs-2017"

開始功能表 資料夾和捷徑名稱需視安裝的 Visual Studio 版本而有所不同。 如果您將設定時，它們也取決於安裝**暱稱**。 例如，假設您已安裝 Visual Studio 2017 中，而您指定的暱稱*最新*。 名為開發人員命令提示字元捷徑**適用於 VS 2017 （最新版） 的開發人員命令提示字元**，在名為的資料夾**Visual Studio 2017**。

::: moniker-end
::: moniker range="< vs-2017"

開始功能表 資料夾和捷徑名稱需視安裝的 Visual Studio 版本而有所不同。 例如，假設您已安裝 Visual Studio 2015。 名為開發人員命令提示字元捷徑**VS 2015 的開發人員命令提示字元**。

::: moniker-end

## <a name="developer_command_prompt"></a> 開啟開發人員命令提示字元視窗

1. 在桌面上開啟 Windows 的 [開始]  功能表，然後藉由捲動找出您的 Visual Studio 版本的資料夾 (例如 **Visual Studio 2019**)，並加以開啟。

1. 在該資料夾中，針對您的 Visual Studio 版本選擇 [開發人員命令提示字元]  。 此捷徑會啟動開發人員命令提示字元視窗，並使用 32 位元、x86 原生工具的預設組建架構來建置 32 位元、x86 原生程式碼。 如果您偏好使用非預設組建架構，請選擇其中一個原生或跨平台工具命令提示字元，以指定主機和目標架構。

若要開啟 [開發人員命令提示字元時甚至更快的方式，請輸入*開發人員命令提示字元*桌面搜尋] 方塊中。 然後選擇您想要的結果。

## <a name="developer_command_file_locations"></a> 開發人員命令檔案位置

如果您想要在現有的 [命令提示字元] 視窗中設定建置環境，您可以使用其中一個安裝程式所建立的命令檔。 我們建議您在新的 [命令提示字元] 視窗中設定的環境。 我們不建議您在相同的命令視窗中的更新版本切換環境。

::: moniker range=">= vs-2019"

命令檔案位置取決於您安裝時，Visual Studio 版本以及您在安裝期間所做的選擇。 Visual Studio 2019，64 位元系統上的一般安裝位置是在\\Program Files (x86)\\Microsoft Visual Studio\\2019年\\*edition*。 *Edition*可能 Community、 Professional、 Enterprise、 BuildTools 或您提供的另一個暱稱。

::: moniker-end
::: moniker range="= vs-2017"

命令檔案位置取決於您安裝時，Visual Studio 版本以及您在安裝期間所做的選擇。 Visual Studio 2017，在 64 位元系統上的一般安裝位置是在\\Program Files (x86)\\Microsoft Visual Studio\\2017年\\*edition*。 *Edition*可能 Community、 Professional、 Enterprise、 BuildTools 或您提供的另一個暱稱。

::: moniker-end
::: moniker range="< vs-2017"

命令檔案位置取決於 Visual Studio 版本和安裝目錄。 一般安裝位置是在 Visual Studio 2015 中， \\Program Files (x86)\\Microsoft Visual Studio 14.0。

::: moniker-end

主要的開發人員命令提示字元命令檔，VsDevCmd.bat，位於 Common7\\Tools 子目錄。 當未不指定任何參數時，它會設定環境，以使用 x86 原生工具來建置 32 位元 x86 程式碼。

::: moniker range=">= vs-2017"

更多的命令檔可用於設定特定組建的架構。 可用的命令檔取決於 Visual Studio 工作負載和您已安裝的選項。 在 Visual Studio 2017 和 Visual Studio 2019，就可以看到在 VC\\輔助\\建立子目錄。

::: moniker-end
::: moniker range="< vs-2017"

更多的命令檔可用於設定特定組建的架構。 可用的命令檔取決於 Visual Studio 工作負載和您已安裝的選項。 在 Visual Studio 2015 中，它們位於 VC，VC\\分類收納或 VC\\bin\\*架構*子目錄，其中*架構*是其中一個原生或跨編譯器選項。

::: moniker-end

這些命令檔會設定預設參數並呼叫 VsDevCmd.bat，以設定指定的組建架構環境。 一般安裝可能會包含下列命令檔：

|命令檔|主機和目標架構|
|---|---|
|**vcvars32.bat**| 使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。|
|**vcvars64.bat**| 使用 64 位元 x64 原生工具來建置 64 位元 x64 程式碼。|
|**vcvarsx86_amd64.bat**| 使用 32 位元 x86 原生跨平台工具來建置 64 位元 x64 程式碼。|
|**vcvarsamd64_x86.bat**| 使用 64 位元 x64 原生跨平台工具來建置 32 位元 x86 程式碼。|
|**vcvarsx86_arm.bat**| 使用 32 位元 x86 原生跨平台工具來建置 ARM 程式碼。|
|**vcvarsamd64_arm.bat**| 使用 64 位元 x64 原生跨平台工具來建置 ARM 程式碼。|
|**vcvarsall.bat**| 使用參數來指定主機和目標架構、 Windows SDK 及平台的選項。 如需支援的選項清單，請使用 **/help** 參數來呼叫。|

> [!CAUTION]
> 在不同的電腦上，vcvarsall.bat 檔案和其他 Visual Studio 命令可能有所不同。 請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。 重新執行 Visual Studio 安裝程式以取代遺漏的檔案。
>
> 在不同的版本上，vcvarsall.bat 也可能不同。 如果安裝最新版 Visual Studio 的電腦上也有舊版的 Visual Studio，請不要在同一個命令提示字元視窗中執行不同版本的 vcvarsall.bat 或其他 Visual Studio 命令檔。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在現有的命令視窗中使用開發人員工具

要在現有的命令視窗中指定特定的組建架構，最簡單的方式是使用 vcvarsall.bat 檔案。 您可以使用 vcvarsall.bat 設定環境變數，若要設定 32 位元或 64 位元的原生編譯的命令列。 引數可讓您指定為 x86，x64、 ARM、 交互編譯或 ARM64 處理器。 您可以針對 Microsoft Store、 通用 Windows 平台或 Windows 桌面平台。 甚至，您可以指定哪些 Windows SDK，才能使用此項目，並選取平台工具組版本。

當不搭配任何引數，則 vcvarsall.bat 會設定環境變數，以使用目前的 x86 原生編譯器為 32 位元 Windows 桌面的目標。 您可以新增至環境設定成使用任何原生，或是跨編譯器工具的引數。 vcvarsall.bat 會顯示錯誤訊息，如果您指定的組態未安裝，或在電腦上。

### <a name="vcvarsall-syntax"></a>vcvarsall 語法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
這個選擇性引數會指定要使用的主機和目標架構。 如果*架構*未指定，使用預設組建環境。 支援的引數如下：

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
選擇性地指定要使用的 Visual Studio 編譯器工具組。 根據預設，環境會設定為使用目前的 Visual Studio 編譯器工具組。

::: moniker range=">= vs-2019"

使用 **-vcvars_ver=14.0 = 14.2 x.yyyyy**來指定特定版本的 Visual Studio 2019 編譯器工具組。

使用 **-vcvars_ver=14.0 = 14.16**指定最新版的 Visual Studio 2017 編譯器工具組。

::: moniker-end
::: moniker range="= vs-2017"

使用 **-vcvars_ver=14.0 = 14.16**指定最新版的 Visual Studio 2017 編譯器工具組。

使用 **-vcvars_ver=14.0 = 14.1 x.yyyyy**來指定特定版本的 Visual Studio 2017 編譯器工具組。

::: moniker-end

使用 **-vcvars_ver=14.0 = 14.0**指定 Visual Studio 2015 的編譯器工具組。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>在現有的命令提示字元視窗中設定組建環境

1. 在命令提示字元中，使用 CD 命令切換至 Visual Studio 安裝目錄。 然後，再次使用 CD 變更至包含組態特定指令檔的子目錄。 Visual Studio 2019 和 Visual Studio 2017，請使用*VC\\輔助\\建置*子目錄。 針對 Visual Studio 2015 中，使用*VC*子目錄。

1. 針對您慣用的開發人員環境輸入命令。 比方說，若要建置適用於 UWP 的 ARM 程式碼，使用最新 Windows SDK 和 Visual Studio 編譯器工具組，在 64 位元平台上使用這個命令列：

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>建立您自己的命令提示字元捷徑

::: moniker range=">= vs-2019"

開啟開發人員命令提示字元 捷徑，以查看使用的命令目標的 屬性 對話方塊。 例如，**VS 2019 的 x64 Native Tools 命令提示字元**捷徑的目標會類似於：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

開啟開發人員命令提示字元 捷徑，以查看使用的命令目標的 屬性 對話方塊。 例如，針對目標**x64 Native Tools 命令提示字元，適用於 VS 2017**捷徑會類似：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

開啟開發人員命令提示字元 捷徑，以查看使用的命令目標的 屬性 對話方塊。 例如，針對目標**VS2015 x64 Native Tools 命令提示字元**捷徑會類似：

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64`

::: moniker-end

架構特定批次檔會設定 *architecture* 參數並呼叫 vcvarsall.bat。 您會將它傳遞給 vcvarsall.bat，或您只可以直接呼叫 vcvarsall.bat，您可以將相同的選項傳遞給這些批次檔中。 若要為您自己的命令捷徑指定參數，請將參數新增至命令結尾處，並以雙引號括住。 比方說，這裡是使用最新的 Windows SDK 的 64 位元平台上，建置適用於 UWP 的 ARM 程式碼的捷徑。 若要使用舊版的編譯器工具組，指定的版本號碼。 請在您的捷徑中使用如下的命令目標：

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.16"`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.0"`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64 -vcvars_ver=12.0`

::: moniker-end

調整以反映您的 Visual Studio 安裝目錄的路徑。 Vcvarsall.bat 檔案含有關於特定版本號碼的其他資訊。

## <a name="command-line-tools"></a>命令列工具

若要建置 C /C++專案中的，於命令提示字元中，Visual Studio 提供這些命令列工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用編譯器 (cl.exe)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。

[連結](reference/linking.md)<br/>
使用連結器 (link.exe)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和專案檔 (.vcxproj) 來設定組建並間接叫用工具組。 它相當於執行**建置**專案或**建置方案**命令在 Visual Studio IDE 中。 從命令列執行 MSBuild 是進階的案例，並不常見建議。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
使用 DEVENV (devenv.exe) 這類結合使用命令列參數 **/組建**或是 **/clean**執行特定建置而不會顯示在 Visual Studio IDE 命令。 一般情況下，DEVENV，而不要使用 MSBuild 直接，因為您可以讓 Visual Studio 處理 MSBuild 的複雜性。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe) 根據傳統 Makefile 建置 C++ 專案。

當您建置命令列上時，就有一個 F1 命令不適用於立即協助。 此時，您可以使用搜尋引擎來取得警告、錯誤和訊息的相關資訊，或者可以使用離線說明檔案。 若要使用搜尋 中的[docs.microsoft.com](https://docs.microsoft.com/cpp/)，使用在頁面頂端的 [搜尋] 方塊。

## <a name="in-this-section"></a>本節內容

這些文章會示範如何在命令列上建置應用程式，並說明如何自訂命令列組建環境。 部分顯示如何使用 64 位元工具組，並以目標 x86、 x64、 ARM、 及 ARM64 平台。 它們也描述如何使用命令列建置工具 MSBuild 及 NMAKE。

[逐步解說：在命令列編譯原生 C++ 程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供範例，示範如何建立及編譯C++命令列上的程式。

[逐步解說：在命令列編譯 C 程式](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
描述如何編譯以 C 程式設計語言撰寫的程式。

[逐步解說：在命令列編譯 C++/CLI 程式](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 .NET Framework 的 C++/CLI 程式。

[逐步解說：在命令列編譯 C++/CX 程式](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 Windows 執行階段的 C++/CX 程式。

[設定命令列建置的路徑及環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
如何設定環境變數，以使用目標 x86、 x64、 ARM，32 位元或 64 位元工具組和 ARM64 平台。

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
