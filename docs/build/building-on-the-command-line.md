---
title: 在命令列上建置 C/c + + 程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc4ec1034d4d77542df4a4241ad3ba5c087602ae
ms.sourcegitcommit: 78e5e5cdbafd29e2a6ccf68d4cce215136952907
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>在命令列上建置 C/c + + 程式碼

您可以使用 Visual Studio 中所包含的工具來建置命令列上的 C 和 c + + 應用程式。

## <a name="how-to-get-the-command-line-tools"></a>如何取得命令列工具

當您在 Visual Studio 安裝程式選擇其中一個 c + + 工作負載時，它會安裝 Visual Studio*平台工具組*。 平台工具組都有特定的 Visual Studio 版本，包括 C/c + + 編譯器、 連結器、 組譯工具和其他建置工具，以及比對文件庫的所有 C 和 c + + 工具。 您可以在命令列中，使用這些工具，它們也會使用在內部 Visual Studio IDE。 有不同的裝載 x86 和 x64 裝載編譯器和工具建置的程式碼，針對 x86、 x64、 ARM 和 ARM64 目標。 每一特定的主控件和目標建置架構的工具組會儲存在它自己的目錄。

正常運作，工具會需要設定幾個特定的環境變數。 這些用來將其加入至路徑，並設定包括檔案、 程式庫檔及 SDK 的位置。 若要讓您輕鬆地設定這些環境變數時，安裝程式會建立自訂*命令檔*，或安裝期間的批次檔。 您可以執行其中一個命令檔案在命令提示字元視窗中設定特定主控件和目標建置架構、 Windows SDK 版本、 目標平台，以及平台工具組。 為了方便起見，安裝程式也會建立捷徑開始 功能表中 (在 Windows 上的 開始 頁面或 8.x)，開始使用這些命令檔，因此所有必要的環境變數會設定就緒可供使用的開發人員命令提示字元視窗。

必要的環境變數專安裝建置架構選擇，也可能會變更產品更新或升級。 因此，強烈建議您其中一個已安裝的命令提示字元 捷徑或命令檔案而不是環境變數中設定 Windows 自行進行使用。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。

命令列工具組、 指令檔和已安裝的命令提示字元捷徑取決於您電腦的處理器以及在安裝期間選取的選項。 最小值，會安裝 32 位元 x86 裝載工具，建置 32 位元 x86 原生程式碼，並跨建置 64 位元 x64 原生程式碼的工具。 如果您有 64 位元 Windows，也會一併安裝 64 位元 x64 裝載工具，建置 64 位元原生程式碼，並跨建置 32 位元原生程式碼的工具。 如果您選擇安裝選擇性的 c + + 通用 Windows 平台工具，會一併安裝的 32 位元和 64 位元原生工具建置 ARM 程式碼。 其他工作負載可能會安裝額外的工具。

## <a name="developer-command-prompt-shortcuts"></a>開發人員命令提示字元 捷徑

命令提示字元 捷徑會安裝在 開始 功能表中的特定版本的 Visual Studio 資料夾。 以下是一份基底的命令提示字元捷徑和它們所支援的組建架構：

- **開發人員命令提示字元**-設定環境以使用 32 位元、 x86 native tools 建置 32 位元、 x86 原生程式碼。
- **x86 native Tools 命令提示字元**-設定環境以使用 32 位元、 x86 native tools 建置 32 位元、 x86 原生程式碼。
- **x64 native Tools 命令提示字元**-設定環境以使用 64 位元、 x64 native tools 建置 64 位元、 x64 原生程式碼。
- **x86_x64 Cross Tools 命令提示字元**-設定環境以使用 32 位元、 x86 native tools 建置 64 位元、 x64 原生程式碼。
- **x64_x86 Cross Tools 命令提示字元**-設定環境以使用 64 位元、 x64 native tools 建置 32 位元、 x86 原生程式碼。

如果您將其中一個，實際的開始功能表資料夾和捷徑名稱也不同取決於您安裝 Visual Studio 版本和安裝暱稱。 例如，如果您有 Visual Studio 2017 安裝，且您已指定它安裝暱稱的*預覽*，名為開發人員命令提示字元捷徑**VS 2017 （預覽）的開發人員命令提示字元**，名為的資料夾中**Visual Studio 2017**。

如果您已安裝[建置工具的 Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) （其中也包括 Visual Studio 2015 Update 3 編譯器工具組），只有特定架構的原生或跨工具開發人員命令提示字元安裝選項並不是一般**開發人員命令提示字元**捷徑。

<a name="developer_command_prompt"></a>
### <a name="to-open-a-developer-command-prompt-window"></a>若要開啟 開發人員命令提示字元視窗

1. 在桌面上，開啟 Windows**啟動** 功能表，然後捲動至 尋找和開啟您的 Visual Studio 版本的資料夾，例如**Visual Studio 2017**。 在子資料夾，在某些較舊版本的 Visual Studio 中，會快速鍵**Visual Studio Tools**。

1. 在資料夾中，選擇 **開發人員命令提示字元**您的 Visual Studio 版本。 此快速鍵啟動會使用預設建置架構的 32 位元、 x86 原生工具來建置 32 位元、 x86 原生程式碼的開發人員命令提示字元視窗。 如果您偏好的非預設建置架構，選擇其中一個原生或跨工具命令提示字元來指定主控件和目標架構。

若要開啟 [開發人員命令提示字元視窗更快的方式是輸入*開發人員命令提示字元*桌面搜尋] 方塊中，然後選擇所要的結果。

## <a name="developer-command-files-and-locations"></a>開發人員命令檔和位置

如果您想要在現有的 [命令提示字元] 視窗中設定建置架構環境，您可以設定所需的環境中使用其中一個命令檔案 （批次檔） 安裝程式所建立。 我們只建議您在新的命令提示字元視窗中，進行此作業並不建議您更新的交換器環境，在相同的命令視窗。 這些檔案的位置取決於您安裝 Visual Studio 版本以及位置並命名您在安裝期間所做的選擇。 Visual Studio 2017，對於在 64 位元電腦上的一般安裝位置位於 \Program 檔案 (x86) \Microsoft Visual Studio\2017\\*edition*，其中*edition*可能是社群Professional、 Enterprise、 BuildTools 或您所提供的另一個名稱。 Visual Studio 2015，一般安裝位置是 \Program Files (x86) \Microsoft Visual Studio 14.0。

主要的開發人員命令提示字元命令檔，VsDevCmd.bat，位於安裝目錄 Common7\Tools 子目錄中。 未指定任何參數，此設定環境及在主機與目標建立時要使用 32 位元 x86 原生工具來建置 32 位元 x86 架構程式碼。

其他的命令檔可用來設定特定的組建架構中，根據您的處理器架構的 Visual Studio 工作負載和已安裝的選項。 在 Visual Studio 2017，這些都位於 Visual Studio 安裝目錄的 VC\Auxiliary\Build 子目錄中。 在 Visual Studio 2015 中，這些都位於 VC、 VC\bin 或 VC\bin\\*架構*子目錄的安裝目錄，其中*架構*是其中一個原生或跨平台編譯器選項。 這些命令檔設定預設參數，並呼叫 VsDevCmd.bat 設定指定的組建架構環境。 一般安裝中可能包含這些指令檔：

|命令檔|主機和目標架構|
|---|---|
|**vcvars32.bat**| 使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。|
|**vcvars64.bat**| 使用 64 位元 x64 原生工具來建置 64 位元 x64 程式碼。|
|**vcvarsx86_amd64.bat**| 使用 32 位元 x86 原生跨工具來建置 64 位元 x64 程式碼。|
|**vcvarsamd64_x86.bat**| 使用 64 位元 x64 原生跨工具來建置 32 位元 x86 程式碼。|
|**vcvarsx86_arm.bat**| 您可以使用 32 位元 x86 原生跨工具來建立 ARM 程式碼。|
|**vcvarsamd64_arm.bat**| 您可以使用 64 位元 x64 原生跨工具來建立 ARM 程式碼。|
|**vcvarsall.bat**| 使用指定的主機和目標架構，以及 SDK 和平台選擇的參數。 如需支援選項的清單，使用呼叫**/help**參數。|

> [!CAUTION]
> Vcvarsall.bat 檔案和其他 Visual Studio 命令檔，可能會不同電腦。 請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。 重新執行 Visual Studio 安裝程式來取代遺失的檔案。
>
> 在不同的版本上，vcvarsall.bat 也可能不同。 如果也有舊版的 Visual Studio 的電腦上已安裝的 Visual Studio 目前版本，不會執行 vcvarsall.bat 或另一個 Visual Studio 命令檔從相同的命令提示字元視窗中的不同版本。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在現有的 [命令] 視窗中使用的開發人員工具

若要在現有的 [命令] 視窗中指定特定組建架構最簡單的方式是使用 vcvarsall.bat 檔案。 您可以設定環境變數，以設定命令列針對原生 32 位元或 64 位元編譯中，或為 x86、 x64 或 ARM 處理器; 交互編譯中使用 vcvarsall.bat以 Microsoft Store、 通用 Windows 平台或 Windows 桌面平台為目標若要指定要使用; 哪個 Windows SDK與指定的平台工具組版本。 如果沒有提供任何引數，則 vcvarsall.bat 會設定環境變數，適用於 x86 使用目前的 32 位元原生編譯器的 Windows 桌面的目標。 不過，您可以使用它來設定任何的原生或跨編譯器工具。 如果您指定未安裝或不在組建電腦架構的編譯器組態時，會顯示錯誤訊息。

### <a name="vcvarsall-syntax"></a>vcvarsall 語法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
此選擇性引數指定要使用的主機和目標架構。 如果*架構*未指定，會使用預設建置環境。 支援這些引數：

|*architecture*|編譯器|主機電腦架構|組建輸出 （目標） 架構|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位元原生|x86、x64|x86|
|**x86\_amd64**或**x86\_x64**|在 x86 x64 cross|x86、x64|X64|
|**x86_arm**|ARM on x86 (跨平台)|x86、x64|ARM|
|**x86_arm64**|在 x86 跨 ARM64|x86、x64|ARM64|
|**amd64**或**x64**|x64 64 位元原生|X64|X64|
|**amd64\_x86**或**x64\_x86**|x64 x86 cross|X64|x86|
|**amd64\_arm**或**x64\_arm**|ARM 上 x64 cross|X64|ARM|
|**amd64\_arm64**或**x64\_arm64**|在 x64 cross ARM64|X64|ARM64|

*platform_type*<br/>
此選擇性引數可讓您指定**儲存**或**uwp**做為平台類型。 根據預設，會將環境設定為建置桌面或主控台應用程式。

*winsdk_version*<br/>
選擇性地指定要使用的 Windows sdk 版本。 根據預設，會使用最新已安裝的 Windows SDK。 若要指定的 Windows SDK 版本，您可以使用完整的 Windows 10 SDK 號碼例如**10.0.10240.0**，或指定**8.1**若要使用 Windows 8.1 SDK。

*vcversion*<br/>
（選擇性） 指定要使用 Visual Studio 編譯器工具組。 根據預設，環境設定為使用目前的 Visual Studio 2017 編譯器工具組。 使用**-vcvars_ver = 14.0**指定 Visual Studio 2015 編譯器工具組。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>若要設定現有的 [命令提示字元] 視窗中的建置環境

1. 在命令提示字元中，使用 CD 命令來切換至 Visual Studio 安裝目錄。 然後，使用 CD 再次變更包含的組態特定命令檔的子目錄。 Visual Studio 2017，這是 VC\Auxiliary\Build 子目錄。 Visual Studio 2015 中，使用 VC 子目錄。

1. 輸入命令，為您慣用的開發人員的環境。 例如，若要建置 ARM 程式碼 UWP 64 位元平台上使用最新版 Windows SDK 及 Visual Studio 2017 RTM 編譯器工具組，請使用此命令列：

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>建立您自己的命令提示字元捷徑

如果您開啟 屬性 對話方塊，其中一個現有的開發人員命令提示字元 捷徑，您可以查看使用的命令目標。 例如，針對目標**x64 Native Tools 命令提示字元，如 VS 2017**快顯是類似的項目：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

架構特定批次檔組*架構*參數並呼叫 vcvarsall.bat。 您可以傳遞至 vcvarsall.bat，或您只可以直接呼叫 vcvarsall.bat，您可以將相同的其他選項傳遞這些批次檔案。 若要指定命令捷徑的參數，將它們加入雙引號中的命令的結尾。 比方說，若要設定捷徑，以 UWP 為建置 ARM 程式碼在 64 位元平台上使用最新版 Windows SDK 及 Visual Studio 2017 RTM 編譯器工具組，使用類似此命令目標在您的捷徑：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

您必須先調整路徑，以反映您的 Visual Studio 安裝目錄。

## <a name="command-line-tools"></a>命令列工具

若要在命令列上建置 C/c + + 專案，Visual Studio 會提供這些命令列工具：

[CL](../build/reference/compiling-a-c-cpp-program.md)<br/>
使用編譯器 (cl.exe)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。

[Link](../build/reference/linking.md)<br/>
使用連結器 (link.exe)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
若要建置 Visual c + + 專案和 Visual Studio 方案中使用 MSBuild (msbuild.exe)。 這就相當於執行**建置**專案或**建置方案**Visual Studio IDE 中的命令。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
與命令列參數結合使用 DEVENV (devenv.exe) — 比方說，**建置**或**/清除**— 若要執行特定建置而不會顯示在 Visual Studio IDE 命令。

[NMAKE](../build/nmake-reference.md)<br/>
使用 NMAKE (nmake.exe)，以自動化利用傳統 makefile，建置 Visual c + + 專案的工作。

當您建置命令列上時，不供立即協助 F1 命令。 相反地，您可以使用搜尋引擎，若要取得警告、 錯誤和訊息的相關資訊，或者您可以使用離線說明檔案。 若要使用搜尋 中的[docs.microsoft.com](https://docs.microsoft.com/cpp/)，在頁面頂端的 [搜尋] 方塊中輸入搜尋字串。

## <a name="in-this-section"></a>本節內容

文件中本區段的文章顯示如何在命令列上建置應用程式，描述如何自訂命令列建置環境，以使用 64 位元工具組並將目標設定為 x86、x64 及 ARM 平台，以及示範如何使用命令列建置工具 MSBuild 及 NMAKE。

[逐步解說：在命令列上編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供範例，顯示如何在命令列上建立及編譯簡單的 C++ 程式。

[逐步解說： 編譯 C 程式命令列上](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
描述如何編譯以 C 程式設計語言撰寫的程式。

[逐步解說：在命令列上編譯 C++/CLI 程式](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 .NET Framework 的 C++/CLI 程式。

[逐步解說：在命令列上編譯 C++/CX 程式](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
描述如何建立及編譯使用 Windows 執行階段的 C++/CX 程式。

[設定命令列建置的路徑及環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
描述如何啟動命令提示字元視窗，並具有必要的環境變數設定命令列建置目標 x86、 x64 和 ARM 平台，使用 32 位元或 64 位元工具組。

[NMAKE 參考](../build/nmake-reference.md)<br/>
提供指向描述 Microsoft Program Maintenance Utility (NMAKE.EXE) 之文章的連結。

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
提供指向討論如何使用 MSBuild.EXE 之文章的連結。

## <a name="related-sections"></a>相關章節

[/MD、/MT、/LD (使用執行階段程式庫)](../build/reference/md-mt-ld-use-run-time-library.md)<br/>
描述如何使用這些編譯器選項，來使用偵錯或發行執行階段程式庫。

[C/c + + 編譯器選項](../build/reference/compiler-options.md)<br/>
提供指向討論 C 及 C++ 編譯器選項及 CL.exe 之文章的連結。

[連結器選項](../build/reference/linker-options.md)<br/>
提供指向討論連結器選項及 LINK.exe 之文章的連結。

[C/C++ 建置工具](../build/reference/c-cpp-build-tools.md)<br/>
提供連結 C/c + + 建置工具隨附於 Visual Studio。

## <a name="see-also"></a>另請參閱

[建置 C/C++ 程式](../build/building-c-cpp-programs.md)