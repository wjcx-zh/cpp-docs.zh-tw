---
title: 從命令列C++使用 Microsoft 工具組
description: 在 Visual Studio IDE 外部從命令列使用 MicrosoftC++ 編譯器工具鏈 (MSVC)。
ms.custom: conceptual
ms.date: 11/12/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: ec30cba8e119f96efc5bca156fa565db77904520
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856783"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>從命令列C++使用 Microsoft 工具組

您可以使用 Visual Studio 中包含的工具，在命令列上建置 C 和 C++ 應用程式。 Microsoft C++ （MSVC）編譯器工具組也可下載為不包含 Visual Studio IDE 的獨立套件。

## <a name="download-and-install-the-tools"></a>下載並安裝工具

如果您已安裝 Visual Studio 和C++工作負載，則會有所有的命令列工具。 如需有關如何安裝C++和 Visual Studio 的詳細資訊，請參閱[在 Visual Studio 中安裝C++支援](vscpp-step-0-installation.md)。 如果您只想要命令列工具組，請下載[Visual Studio 的組建工具](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)。 當您執行下載的可執行檔時，它會更新並執行 Visual Studio 安裝程式。 若只要安裝C++開發所需的工具，請選取 [  **C++組建工具**] 工作負載。 您可以選取要包含在**安裝詳細資料**底下的選用程式庫和工具組。 若要使用 Visual Studio 2015 或2017工具組來建立程式碼，請選取選擇性的 MSVC v140 或 MSVC v141 build tools。 當您滿意所做的選擇之後，請選擇 [**安裝**]。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令列工具

當您選擇 Visual Studio 安裝程式中的其中一個 C++ 工作負載時，它將會安裝 Visual Studio *平台工具組*。 平臺工具組具有特定 Visual Studio 版本的C++所有 C 和工具。 這些工具組括 C/C++編譯器、連結器、組合器和其他組建工具，以及相符的程式庫。 您可以在命令列中使用所有這些工具。 它們也是由 Visual Studio IDE 在內部使用。 有不同的 x86 裝載和 x64 裝載的編譯器和工具，可為 x86、x64、ARM 和 ARM64 目標建立程式碼。 特定主機和目標組建架構適用的每一組工具都會儲存在其本身的目錄中。

若要正常運作，工具必須設定數個特定的環境變數。 這些變數是用來將工具新增至路徑，並設定包含檔案、程式庫檔案和 SDK 位置。 為了方便您設定這些環境變數，安裝程式在安裝期間會建立自訂*命令檔*或批次檔。 您可以執行下列其中一個命令檔來設定特定的主機和目標群組建架構、Windows SDK 版本和平臺工具組。 為了方便起見，安裝程式也會在 [開始] 功能表中建立快捷方式。 快捷方式會針對主機和目標的特定組合使用這些命令檔，來啟動開發人員命令提示字元視窗。 這些快速鍵可確保所有必要的環境變數都已設定並可供使用。

必要的環境變數專屬於您的安裝以及您選擇的組建架構。 產品更新或升級也可能會變更它們。 這就是為什麼我們建議您使用已安裝的命令提示字元快捷方式或命令檔，而不是自行設定環境變數。 如需詳細資訊，請參閱[設定命令列組建的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。

安裝的工具組、命令檔和快捷方式取決於您的電腦處理器，以及您在安裝期間選取的選項。 系統一律會安裝建立 x86 和 x64 程式碼的 x86 主控工具和跨工具。 如果您有64位 Windows，則也會安裝建立 x86 和 x64 程式碼的 x64 主控工具和跨工具。 如果您選擇選用C++的通用 Windows 平臺工具，則建立 ARM 和 ARM64 程式碼的 x86 和 x64 工具也會一併安裝。 其他工作負載可能會安裝其他工具。

## <a name="developer_command_prompt_shortcuts"></a> 開發人員命令提示字元捷徑

命令提示字元捷徑會在您的 [開始] 功能表中安裝於特定版本的 Visual Studio 資料夾內。 以下列出基礎命令提示字元捷徑及其支援的組建架構：

- **開發人員命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 32 位元、x86 原生程式碼。
- **x86 Native Tools 命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 32 位元、x86 原生程式碼。
- **x64 Native Tools 命令提示字元** - 將環境設定為使用 64 位元、x64 原生工具來建置 64 位元、x64 原生程式碼。
- **x86_x64 Cross Tools 命令提示字元** - 將環境設定為使用 32 位元、x86 原生工具來建置 64 位元、x64 原生程式碼。
- **x64_x86 Cross Tools 命令提示字元** - 將環境設定為使用 64 位元、x64 原生工具來建置 32 位元、x86 原生程式碼。

::: moniker range=">= vs-2019"

[開始] 功能表資料夾和快捷方式名稱會根據已安裝的 Visual Studio 版本而有所不同。 如果您設定一個，它們也會相依于安裝**昵稱**。 例如，假設您已安裝 Visual Studio 2019，而您為它提供了*最新*的昵稱。 開發人員命令提示字元快捷方式在名為**Visual Studio 2019**的資料夾中，名為**開發人員命令提示字元 for VS 2019 （最新）** 。

::: moniker-end
::: moniker range="= vs-2017"

[開始] 功能表資料夾和快捷方式名稱會根據已安裝的 Visual Studio 版本而有所不同。 如果您設定一個，它們也會相依于安裝**昵稱**。 例如，假設您已安裝 Visual Studio 2017，而您為它提供了*最新*的昵稱。 開發人員命令提示字元快捷方式在名為**Visual Studio 2017**的資料夾中，名為**開發人員命令提示字元 for VS 2017 （最新）** 。

::: moniker-end
::: moniker range="< vs-2017"

[開始] 功能表資料夾和快捷方式名稱會根據已安裝的 Visual Studio 版本而有所不同。 例如，假設您已安裝 Visual Studio 2015。 開發人員命令提示字元快捷方式會命名為**開發人員命令提示字元，適用于 VS 2015**。

::: moniker-end

### <a name="developer_command_prompt"></a> 開啟開發人員命令提示字元視窗

1. 在桌面上開啟 Windows 的 [開始] 功能表，然後藉由捲動找出您的 Visual Studio 版本的資料夾 (例如 **Visual Studio 2019**)，並加以開啟。

1. 在該資料夾中，針對您的 Visual Studio 版本選擇 [開發人員命令提示字元]。 此捷徑會啟動開發人員命令提示字元視窗，並使用 32 位元、x86 原生工具的預設組建架構來建置 32 位元、x86 原生程式碼。 如果您偏好使用非預設組建架構，請選擇其中一個原生或跨平台工具命令提示字元，以指定主機和目標架構。

如需更快速的方法來開啟開發人員命令提示字元，請在 [桌面搜尋] 方塊中輸入「*開發人員命令提示*字元」。 然後選擇您想要的結果。

## <a name="developer_command_file_locations"></a> 開發人員命令檔案位置

如果您想要在現有的 [命令提示字元] 視窗中設定組建環境，您可以使用安裝程式所建立的其中一個命令檔。 我們建議您在新的 [命令提示字元] 視窗中設定環境。 我們不建議您稍後在同一個命令視窗中切換環境。

::: moniker range=">= vs-2019"

命令檔位置取決於您安裝的 Visual Studio 版本，以及您在安裝期間所做的選擇。 針對 Visual Studio 2019，64位系統上的一般安裝位置是在 \\Program Files （x86）\\Microsoft Visual Studio\\2019\\*版本*中。 *版本*可以是 [社區]、[Professional]、[Enterprise]、[BuildTools] 或您提供的其他昵稱。

::: moniker-end
::: moniker range="= vs-2017"

命令檔位置取決於您安裝的 Visual Studio 版本，以及您在安裝期間所做的選擇。 針對 Visual Studio 2017，64位系統上的一般安裝位置是在 \\Program Files （x86）\\Microsoft Visual Studio\\2017\\*版本*中。 *版本*可以是 [社區]、[Professional]、[Enterprise]、[BuildTools] 或您提供的其他昵稱。

::: moniker-end
::: moniker range="< vs-2017"

命令檔位置取決於 Visual Studio 版本和安裝目錄。 針對 Visual Studio 2015，一般安裝位置是在 \\Program Files （x86）\\Microsoft Visual Studio 14.0 中。

::: moniker-end

主要的開發人員命令提示字元命令檔 Vsdevcmd.bat 是位於 Common7\\Tools 子目錄中。 若未指定任何參數，則會將環境設定為使用 x86 原生工具來建立32位 x86 程式碼。

::: moniker range=">= vs-2017"

有更多命令檔可用來設定特定的組建架構。 可用的命令檔取決於您已安裝的 Visual Studio 工作負載和選項。 在 Visual Studio 2017 和 Visual Studio 2019 中，您會在 VC\\輔助\\組建子目錄中找到它們。

::: moniker-end
::: moniker range="< vs-2017"

有更多命令檔可用來設定特定的組建架構。 可用的命令檔取決於您已安裝的 Visual Studio 工作負載和選項。 在 Visual Studio 2015 中，它們位於 VC、VC\\bin 或 VC\\bin\\*架構*子目錄中，其中的*架構*是其中一個原生或跨編譯器選項。

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
|**vcvarsall.bat**| 使用參數來指定主機和目標架構、Windows SDK 和平臺選擇。 如需支援的選項清單，請使用 **/help** 參數來呼叫。|

> [!CAUTION]
> 在不同的電腦上，vcvarsall.bat 檔案和其他 Visual Studio 命令可能有所不同。 請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。 重新執行 Visual Studio 安裝程式以取代遺漏的檔案。
>
> 在不同的版本上，vcvarsall.bat 也可能不同。 如果安裝最新版 Visual Studio 的電腦上也有舊版的 Visual Studio，請不要在同一個命令提示字元視窗中執行不同版本的 vcvarsall.bat 或其他 Visual Studio 命令檔。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在現有的命令視窗中使用開發人員工具

要在現有的命令視窗中指定特定的組建架構，最簡單的方式是使用 vcvarsall.bat 檔案。 使用 vcvarsall.bat 設定環境變數，以設定原生32位或64位編譯的命令列。 引數可讓您指定跨編譯 x86、x64、ARM 或 ARM64 處理器。 您可以將 Microsoft Store、通用 Windows 平臺或 Windows 桌面平臺作為目標。 您甚至可以指定要使用的 Windows SDK，然後選取平臺工具組版本。

搭配沒有引數使用時，vcvarsall.bat 會設定環境變數，以針對32位 Windows 桌面目標使用目前的 x86 原生編譯器。 您可以新增引數，將環境設定為使用任何原生或跨編譯器工具。 如果您指定的設定在您的電腦上未安裝或無法使用，vcvarsall.bat 會顯示錯誤訊息。

### <a name="vcvarsall-syntax"></a>vcvarsall 語法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
這個選擇性引數會指定要使用的主機和目標架構。 如果未指定*架構*，則會使用預設的組建環境。 支援的引數如下：

|*architecture*|編譯器|主機電腦架構|組建輸出 (目標) 架構|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位元原生|x86、x64|x86|
|**x86\_amd64** 或 **x86\_x64**|x64 on x86 (跨平台)|x86、x64|x64|
|**x86_arm**|ARM on x86 (跨平台)|x86、x64|ARM|
|**x86_arm64**|ARM64 on x86 (跨平台)|x86、x64|ARM64|
|**amd64** 或 **x64**|x64 64 位元原生|x64|x64|
|**amd64\_x86** 或 **x64\_x86**|x86 on x64 (跨平台)|x64|x86|
|**amd64\_arm** 或 **x64\_arm**|ARM on x64 (跨平台)|x64|ARM|
|**amd64\_arm64** 或 **x64\_arm64**|ARM64 on x64 (跨平台)|x64|ARM64|

*platform_type*<br/>
這個選擇性引數可讓您將 **store** 或 **uwp** 指定為平台類型。 根據預設，環境會設定為建置桌面或主控台應用程式。

*winsdk_version*<br/>
選擇性地指定要使用的 Windows SDK 版本。 根據預設，會使用最新安裝的 Windows SDK。 若要指定 Windows SDK 版本，您可以使用完整的 Windows 10 SDK 號碼 (例如 **10.0.10240.0**)，或指定 **8.1** 以使用 Windows 8.1 SDK。

*vcversion*<br/>
選擇性地指定要使用的 Visual Studio 編譯器工具組。 根據預設，環境會設定為使用目前的 Visual Studio 編譯器工具組。

::: moniker range=">= vs-2019"

請使用 **-vcvars_ver = 14.2 yyyyy**來指定特定版本的 Visual Studio 2019 編譯器工具組。

使用 **-vcvars_ver = v14.16**來指定最新版的 Visual Studio 2017 編譯器工具組。

::: moniker-end
::: moniker range="= vs-2017"

使用 **-vcvars_ver = v14.16**來指定最新版的 Visual Studio 2017 編譯器工具組。

使用 **-vcvars_ver = 14.1 yyyyy**指定特定版本的 Visual Studio 2017 編譯器工具組。

::: moniker-end

使用 **-vcvars_ver = 14.0**來指定 Visual Studio 2015 編譯器工具組。

#### <a name="vcvarsall"></a>在現有的命令提示字元視窗中設定組建環境

1. 在命令提示字元中，使用 CD 命令切換至 Visual Studio 安裝目錄。 然後，再次使用 CD 變更至包含組態特定指令檔的子目錄。 針對 Visual Studio 2019 和 Visual Studio 2017，請使用*VC\\輔助\\組建*子目錄。 針對 Visual Studio 2015，請使用*VC*子目錄。

1. 針對您慣用的開發人員環境輸入命令。 例如，若要使用最新的 Windows SDK 和 Visual Studio 編譯器工具組，在64位平臺上建立 UWP 的 ARM 程式碼，請使用此命令列：

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>建立您自己的命令提示字元捷徑

::: moniker range=">= vs-2019"

開啟 [開發人員命令提示字元] 快捷方式的 [屬性] 對話方塊，以查看所使用的命令目標。 例如，**VS 2019 的 x64 Native Tools 命令提示字元**捷徑的目標會類似於：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

開啟 [開發人員命令提示字元] 快捷方式的 [屬性] 對話方塊，以查看所使用的命令目標。 例如，適用于**VS 2017**快捷方式的 x64 Native Tools 命令提示字元的目標與下列類似：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

開啟 [開發人員命令提示字元] 快捷方式的 [屬性] 對話方塊，以查看所使用的命令目標。 例如， **VS2015 x64 Native Tools 命令提示字元**快捷方式的目標，就像這樣：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

架構特定批次檔會設定 *architecture* 參數並呼叫 vcvarsall.bat。 當您傳遞至 vcvarsall.bat 時，您可以將相同的選項傳遞至這些批次檔，或者只是直接呼叫 vcvarsall.bat。 若要為您自己的命令捷徑指定參數，請將參數新增至命令結尾處，並以雙引號括住。 例如，這裡有一個快捷方式，可使用最新的 Windows SDK，在64位平臺上建立 UWP 的 ARM 程式碼。 若要使用舊版的編譯器工具組，請指定版本號碼。 請在您的捷徑中使用如下的命令目標：

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

調整路徑以反映您的 Visual Studio 安裝目錄。 Vcvarsall.bat 檔案含有關於特定版本號碼的其他資訊。

## <a name="command-line-tools"></a>命令列工具

若要在命令提示C++字元中建立 C/專案，Visual Studio 提供下列命令列工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用編譯器 (cl.exe)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。

[連結](reference/linking.md)<br/>
使用連結器 (link.exe)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和專案檔 (.vcxproj) 來設定組建並間接叫用工具組。 這相當於在 Visual Studio IDE 中執行 [**組建**專案] 或 [**建立方案**] 命令。 從命令列執行 MSBuild 是一個先進的案例，並不是一般建議的做法。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
使用 DEVENV （devenv）與命令列參數（例如 **/Build**或 **/Clean** ）結合，以執行特定組建命令，而不顯示 Visual Studio IDE。 一般而言，因為您可以讓 Visual Studio 處理 MSBuild 的複雜性，所以慣用的是直接使用 MSBuild。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe) 根據傳統 Makefile 建置 C++ 專案。

當您在命令列上建立時，F1 命令無法提供立即協助。 此時，您可以使用搜尋引擎來取得警告、錯誤和訊息的相關資訊，或者可以使用離線說明檔案。 若要使用[docs.microsoft.com](https://docs.microsoft.com/cpp/)中的搜尋，請使用頁面頂端的 [搜尋] 方塊。

## <a name="in-this-section"></a>本節內容

這些文章說明如何在命令列上建立應用程式，並說明如何自訂命令列組建環境。 其中一些示範如何使用64位工具組，並以 x86、x64、ARM 和 ARM64 平臺為目標。 它們也會說明如何使用命令列組建工具 MSBuild 和 NMAKE。

[逐步解說：在命令C++行上編譯原生程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供範例，說明如何在命令列上建立和C++編譯器。

[逐步解說：在命令列上編譯 C 程式](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
描述如何編譯以 C 程式設計語言撰寫的程式。

[逐步解說：在C++命令列上編譯/cli 程式](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 .NET Framework 的 C++/CLI 程式。

[逐步解說：在C++命令列上編譯/cx 程式](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 Windows 執行階段的 C++/CX 程式。

[設定命令列組建的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
如何設定環境變數以使用32位或64位工具組，以 x86、x64、ARM 和 ARM64 平臺為目標。

[NMAKE 參考](reference/nmake-reference.md)<br/>
提供指向描述 Microsoft Program Maintenance Utility (NMAKE.EXE) 之文章的連結。

[命令列上的 MSBuild - C++](msbuild-visual-cpp.md)<br/>
提供連結以供存取討論如何從命令列使用 msbuild.exe 的文章。

## <a name="related-sections"></a>相關章節

[/MD、/MT、/LD （使用執行時間程式庫）](reference/md-mt-ld-use-run-time-library.md)<br/>
描述如何使用這些編譯器選項，來使用偵錯或發行執行階段程式庫。

[C/C++編譯器選項](reference/compiler-options.md)<br/>
提供指向討論 C 及 C++ 編譯器選項及 CL.exe 之文章的連結。

[MSVC 連結器選項](reference/linker-options.md)<br/>
提供指向討論連結器選項及 LINK.exe 之文章的連結。

[其他 MSVC 建置工具](reference/c-cpp-build-tools.md)<br/>
提供 Visual Studio 中包含的 C/C++ 建置工具的連結。

## <a name="see-also"></a>另請參閱

[專案和建置系統](projects-and-build-systems-cpp.md)
