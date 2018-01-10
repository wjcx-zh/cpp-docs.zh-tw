---
title: "在命令列上建置 C/c + + 程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5780fb725ab9ccfbba189894c22c991c415f6c2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>在命令列上建置 C/c + + 程式碼

您可以使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中所包含的工具，在命令列上，建置 C 及 C++ 應用程式。

當您選擇中的 c + + 工作負載的其中一個[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安裝程式，它會安裝包含的 C/c + + 編譯器、 連結器工具組和其他建置工具。 這些工具由[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]IDE，而且它們也可用在命令列。 有不同的裝載 x86 和 x64 裝載編譯器和工具來建置 x86、 x64 和 ARM 目標的程式碼。 每一特定的主控件和目標建置架構的工具組會儲存在它自己的目錄。 若要正常運作，這些工具需要數個特定的環境變數，將它們加入路徑，並設定包括檔案、 程式庫檔及 SDK 的位置。 若要讓您輕鬆地設定這些環境變數時，安裝程式會在安裝期間建立自訂的命令檔，也稱為批次檔。 您可以在命令提示字元視窗中，若要設定特定的組建架構來執行這些命令檔案。 為了方便起見，安裝程式也會建立捷徑開始 功能表中 (在 Windows 上的 開始 頁面或 8.x)，開始使用這些命令檔，因此所有必要的環境變數會設定就緒可供使用的開發人員命令提示字元視窗。 

必要的環境變數專安裝建置架構選擇，也可能會變更產品更新或升級。 因此，強烈建議您其中一個已安裝的命令提示字元 捷徑或命令檔案而不是環境變數中設定 Windows 自行進行使用。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  

命令列工具組、 指令檔和已安裝的命令提示字元捷徑取決於您電腦的處理器以及在安裝期間選取的選項。 最小值，會安裝 32 位元 x86 裝載工具，建置 32 位元 x86 原生程式碼，並跨建置 64 位元 x64 原生程式碼的工具。 如果您有 64 位元 Windows，也會一併安裝 64 位元 x64 裝載工具，建置 64 位元原生程式碼，並跨建置 32 位元原生程式碼的工具。 如果您選擇安裝選擇性的 c + + 通用 Windows 平台工具，會一併安裝的 32 位元和 64 位元原生工具建置 ARM 程式碼。 其他工作負載可能會安裝額外的工具。

<a name="developer_command_prompt_shortcuts"></a>
## <a name="developer-command-prompt-shortcuts"></a>開發人員命令提示字元 捷徑

命令提示字元 捷徑會安裝在特定版本[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]開始 功能表中的資料夾。 以下是一份基底的命令提示字元捷徑和它們所支援的組建架構：

- **開發人員命令提示字元**設定環境以使用 32 位元、 x86 native tools 建置 32 位元、 x86 原生程式碼。  
- **x86 native Tools 命令提示字元**設定環境以使用 32 位元、 x86 native tools 建置 32 位元、 x86 原生程式碼。  
- **x64 native Tools 命令提示字元**設定環境以使用 64 位元、 x64 native tools 建置 64 位元、 x64 原生程式碼。  
- **x86_x64 Cross Tools 命令提示字元**設定環境以使用 32 位元、 x86 native tools 建置 64 位元、 x64 原生程式碼。  
- **x64_x86 Cross Tools 命令提示字元**設定環境以使用 64 位元、 x64 native tools 建置 32 位元、 x86 原生程式碼。  

實際的開始功能表 資料夾和快顯名稱的版本而異[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]您已安裝，以及安裝暱稱，如果您將其中一個。 例如，如果您有 Visual Studio 2017 安裝，您已獲得它 15.3 安裝暱稱，開發人員命令提示字元捷徑名為**VS 2017 (15.3) 的開發人員命令提示字元**，名為的資料夾中**Visual Studio 2017**。 

如果您已安裝[建置工具的 Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931)或[Visual c + + 2015年建置工具](http://landinghub.visualstudio.com/visual-cpp-build-tools)版本中，只能有特定的原生或跨工具開發人員命令提示字元選項。 

<a name="developer_command_prompt"></a>
## <a name="to-open-a-developer-command-prompt-window"></a>若要開啟 開發人員命令提示字元視窗  
  
1.  在桌面上，開啟 Windows**啟動** 功能表，然後捲動至 尋找和開啟您的 Visual Studio 版本的資料夾，例如**Visual Studio 2017**。 在子資料夾，在某些較舊版本的 Visual Studio 中，會快速鍵**Visual Studio Tools**。  
  
2.  在資料夾中，選擇 **開發人員命令提示字元**您的 Visual Studio 版本。 此快速鍵啟動會使用預設建置架構的 32 位元、 x86 原生工具來建置 32 位元、 x86 原生程式碼的開發人員命令提示字元視窗。 如果您偏好的非預設建置架構，選擇其中一個原生或跨工具命令提示字元來指定主控件和目標架構。 

若要開啟 [開發人員命令提示字元視窗更快的方式是輸入*開發人員命令提示字元*桌面搜尋] 方塊中，然後選擇所要的結果。

<a name="developer_command_files"></a>
## <a name="developer-command-files-and-locations"></a>開發人員命令檔和位置

如果您想要在現有的 [命令提示字元] 視窗中設定建置架構環境，您可以使用其中一個安裝程式所建立的命令檔。 這些檔案的位置而定的新版[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]您已安裝，並進行安裝期間上的位置和命名的選擇。 Visual Studio 2017，對於在 64 位元電腦上的一般安裝位置位於 \Program 檔案 (x86) \Microsoft Visual Studio\2017\\*edition*，其中*edition*可能是社群Professional、 Enterprise、 BuildTools 或您所提供的另一個名稱。 Visual Studio 2015，一般安裝位置是 \Program Files (x86) \Microsoft Visual Studio 14.0。 

主要的開發人員命令提示字元命令檔，VsDevCmd.bat，位於安裝目錄 Common7\Tools 子目錄中。 當未不指定任何參數時，這會設定的環境及組建的架構使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。

其他的命令檔可用於設定特定的組建架構中，根據您的處理器架構和[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]工作負載和已安裝的選項。 在 Visual Studio 2017，這些都位於 VC\Auxiliary\Build 子目錄中[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安裝目錄。 在 Visual Studio 2015 中，這些都位於 VC、 VC\bin 或 VC\bin\\*架構*子目錄的安裝目錄，其中*架構*是其中一個原生或跨編譯器選項。 這些命令檔設定參數，然後呼叫 VsDevCmd.bat 設定指定的組建架構環境。 一般安裝中可能包含這些指令檔：

- **vcvars32.bat**使用 32 位元 x86 原生工具來建置 32 位元 x86 程式碼。  
- **vcvars64.bat**使用 64 位元 x64 原生工具來建置 64 位元 x64 程式碼。  
- **vcvarsx86_amd64.bat**使用 32 位元 x86 原生跨工具來建置 64 位元 x64 程式碼。  
- **vcvarsamd64_x86.bat**使用 64 位元 x64 原生跨工具來建置 32 位元 x86 程式碼。  
- **vcvarsx86_arm.bat**使用 32 位元 x86 原生跨工具建置 ARM 程式碼。  
- **vcvarsamd64_arm.bat**使用 64 位元 x64 原生跨工具建置 ARM 程式碼。  
- **vcvarsall.bat**使用參數來指定主機的目標架構，以及 SDK 與平台的選項。 使用呼叫`/help`參數選項的清單。  

> [!CAUTION]
>  Vcvarsall.bat 檔案和其他命令檔，可能會不同電腦。 請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。 請重新執行[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安裝程式以取代遺失的檔案。  
>   
> 在不同的版本上，vcvarsall.bat 也可能不同。 如果也有較早版本的 Visual c + + 的電腦上安裝目前版本的 Visual c + +，不會執行 vcvarsall.bat 或另一個命令檔從相同的命令提示字元視窗中的不同版本。  
 
若要在現有的 [命令] 視窗中指定特定組建架構最簡單的方式是使用 vcvarsall.bat 檔案。 您可以設定環境變數，以設定命令列針對原生 32 位元或 64 位元編譯中，或為 x86、 x64 或 ARM 處理器; 交互編譯中使用 vcvarsall.bat以 Windows 市集、 通用 Windows 平台或 Windows 桌面平台為目標若要指定要使用; 哪個 Windows SDK與指定的平台工具組版本。 如果沒有提供任何引數，則 vcvarsall.bat 會設定環境變數，適用於 x86 使用目前的 32 位元原生編譯器的 Windows 桌面的目標。 不過，您可以使用它來設定任何的原生或跨編譯器工具。 如果您指定未安裝或不在組建電腦架構的編譯器組態時，會顯示錯誤訊息。 下表顯示支援的架構引數：  
  
|Vcvarsall.bat 架構引數|編譯器|主機電腦架構|組建輸出架構|  
|----------------------------|--------------|----------------------------------|-------------------------------|  
|x86|x86 32 位元原生|x86、x64|x86|  
|x86\_amd64 或 x86\_x64|在 x86 x64 cross|x86、x64|X64|  
|x86_arm|ARM on x86 (跨平台)|x86、x64|ARM|  
|amd64 或 x64|x64 64 位元原生|X64|X64|  
|amd64\_x86 或 x64\_x86|x64 x86 cross|X64|x86|  
|amd64\_arm 或 x64\_arm|ARM 上 x64 cross|X64|ARM|  
  
您可以使用**儲存**或**uwp**選項，以指定的平台類型，或兩者都不指定桌面應用程式。 若要指定的 Windows SDK 版本，您可以使用完整的 Windows 10 SDK 數字，例如 10.0.10240.0，，或指定要使用 Windows 8.1 SDK 8.1。 使用指定的 Visual Studio 2015 編譯器工具組; 14.0根據預設，會將環境設定為使用 Visual Studio 2017 編譯器工具組。

<a name="vcvarsall"></a>
## <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>若要設定現有的 [命令提示字元] 視窗中的建置環境  
  
1.  在命令提示字元中，使用 CD 命令來切換至 Visual Studio 安裝目錄。 然後，使用 CD 再次變更包含的組態特定命令檔的子目錄。 Visual Studio 2017，這是 VC\Auxiliary\Build 子目錄。 Visual Studio 2015 中，使用 VC 子目錄。  
  
1.  若要設定此命令提示字元視窗，以使用 32 位元工具來建置程式碼適用於 x86 平台，在命令提示字元中，輸入：  
  
     `vcvarsall`  

1.  若要設定此命令提示字元視窗，以使用 32 位元工具來建置程式碼適用於 x64 平台，在命令提示字元中，輸入：  
  
     `vcvarsall x86_amd64`  
  
1.  若要設定此命令提示字元視窗，以使用 32 位元工具來建置程式碼對於 ARM 平台，在命令提示字元中，輸入：  
  
     `vcvarsall x86_arm`  
  
1.  若要設定此命令提示字元視窗，以使用 64 位元工具來建置程式碼適用於 x64 平台，在命令提示字元中，輸入：  
  
     `vcvarsall amd64`  
  
1.  若要設定此命令提示字元視窗，以使用 64 位元工具來建置程式碼適用於 x86 平台，在命令提示字元中，輸入：  
  
     `vcvarsall amd64_x86`  
  
1.  若要設定此命令提示字元視窗，以使用 64 位元工具來建置程式碼對於 ARM 平台，在命令提示字元中，輸入：  
  
     `vcvarsall amd64_arm`  

命令檔會設定必要的環境變數路徑的建置工具、 程式庫和標頭。 您現在可以使用這個命令提示字元視窗，才能執行命令列編譯器及工具。  
  
如果您使用[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)命令列組建，vcvarsall.bat 或其他命令檔所設定的環境不會影響您的建置，除非您同時指定**/useenv**選項。  

## <a name="command-line-tools"></a>命令列工具
  
若要在命令列上建置 C/c + + 專案，您可以使用這些 Visual c + + 命令列工具：  
  
[CL](../build/reference/compiling-a-c-cpp-program.md)  
使用編譯器 (cl.exe)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。  
  
[連結](../build/reference/linking.md)  
使用連結器 (link.exe)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
使用 MSBuild (msbuild.exe) 建置 Visual c + + 專案和[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]解決方案。 這就相當於執行**建置**專案或**建置方案**命令[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]IDE。  
  
[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)  
與命令列參數結合使用 DEVENV (devenv.exe) — 比方說，**建置**或**/清除**— 若要執行特定建置而不會顯示命令[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]IDE。  
  
[NMAKE](../build/nmake-reference.md)  
使用 NMAKE (nmake.exe)，以自動化利用傳統 makefile，建置 Visual c + + 專案的工作。  
  
當您建置命令列上時，您可以取得警告、 錯誤和訊息的相關資訊。 啟動[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]然後在功能表列上選擇**協助**，**搜尋**。  
  
## <a name="in-this-section"></a>本節內容  

文件中本區段的文章顯示如何在命令列上建置應用程式，描述如何自訂命令列建置環境，以使用 64 位元工具組並將目標設定為 x86、x64 及 ARM 平台，以及示範如何使用命令列建置工具 MSBuild 及 NMAKE。  
  
[逐步解說：在命令列上編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
提供範例，顯示如何在命令列上建立及編譯簡單的 C++ 程式。  
  
[逐步解說： 編譯 C 程式命令列上](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
描述如何編譯以 C 程式設計語言撰寫的程式。  
  
[逐步解說：在命令列上編譯 C++/CLI 程式](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
描述如何建立及編譯使用 .NET Framework 的 C++/CLI 程式。  
  
[逐步解說：在命令列上編譯 C++/CX 程式](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
描述如何建立及編譯使用 Windows 執行階段的 C++/CX 程式。  
  
[設定命令列建置的路徑及環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
描述如何啟動命令提示字元視窗，並具有必要的環境變數設定命令列建置目標 x86、 x64 和 ARM 平台，使用 32 位元或 64 位元工具組。  
  
[NMAKE 參考](../build/nmake-reference.md)  
提供指向描述 Microsoft Program Maintenance Utility (NMAKE.EXE) 之文章的連結。  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
提供指向討論如何使用 MSBuild.EXE 之文章的連結。  
  
## <a name="related-sections"></a>相關章節  

[/MD、 /MT、 /LD （使用執行階段程式庫）](../build/reference/md-mt-ld-use-run-time-library.md)  
描述如何使用這些編譯器選項，來使用偵錯或發行執行階段程式庫。  
  
[C/c + + 編譯器選項](../build/reference/compiler-options.md)  
提供指向討論 C 及 C++ 編譯器選項及 CL.exe 之文章的連結。  
  
[連結器選項](../build/reference/linker-options.md)  
提供指向討論連結器選項及 LINK.exe 之文章的連結。  
  
[C/C++ 建置工具](../build/reference/c-cpp-build-tools.md)  
提供指向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中所包含之 C/C++ 建置工具的連結。  
  
## <a name="see-also"></a>請參閱  

[建置 C/C++ 程式](../build/building-c-cpp-programs.md)