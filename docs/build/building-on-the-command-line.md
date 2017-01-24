---
title: "在命令列中建置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "組建 [C++], 命令列"
  - "命令列 [C++], 建置於"
  - "命令列 [C++], 編譯器"
  - "命令列組建 [C++]"
  - "編譯原始程式碼 [C++], 命令列"
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在命令列中建置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中所包含的工具，在命令列上，建置 C 及 C\+\+ 應用程式。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的每一個版本都會安裝包括編譯器、連結器及其他建置工具的命令列工具組，以及用於設定所需建置環境的命令檔案。  根據預設，這些工具會安裝在 *drive*:\\Program Files \(x86\)\\Microsoft Visual Studio *version*\\VC\\bin\\ 中   \(您電腦上的實際目錄取決於系統、[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本及安裝選項\)。  
  
 若要正確運作，[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令列工具需要針對安裝所自訂的數個環境變數。  安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 時，它會建立 vcvarsall.bat 命令列，您可以執行用來設定所需的環境變數。  它還會建立用於啟動 \[開發人員命令提示字元\] 視窗的捷徑，在該視窗中，已經設定這些變數。  這些環境變數專用於您的安裝，在產品更新或升級時，可能會變更。  因此，我們建議您使用 vcvarsall.bat 或 \[開發人員命令提示字元\] 捷徑，而不是自己設定這些變數。  如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
### 開啟 \[開發人員命令提示字元\] 視窗  
  
1.  在 Windows 8 \[開始\] 畫面，輸入 Visual Studio Tools。  請注意，搜尋結果會隨著您的輸入而變更，當出現 \[Visual Studio Tools\] 時，請選擇它。  
  
     在舊版 Windows 中，選擇 \[開始\]，然後在搜尋方塊中，輸入 Visual Studio Tools。  當搜尋結果中出現 \[Visual Studio Tools\] 時，請選擇它。  
  
2.  在 \[Visual Studio Tools\] 資料夾中，針對您的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本，開啟 \[開發人員命令列提示字元\]。  
  
 若要在命令列上建置 C\/C\+\+ 專案，您可以使用這些 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令列工具：  
  
 [CL](../build/reference/compiling-a-c-cpp-program.md)  
 使用編譯器 \(cl.exe\)，來編譯原始程式碼檔，並將其連結至應用程式、程式庫及 DLL。  
  
 [連結](../build/reference/linking.md)  
 使用連結器 \(link.exe\)，將已編譯的物件檔及程式庫，連結至應用程式及 DLL。  
  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)  
 使用 MSBuild \(msbuild.exe\)，來建置 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 專案及 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 方案。  此作業相當於在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 中，執行 \[建置\] 專案，或 \[建置方案\] 命令。  
  
 [DEVENV](../Topic/Devenv%20Command%20Line%20Switches.md)  
 使用 DEVENV \(devenv.exe\)，搭配命令列參數 \(例如 **\/Build** 或 **\/Clean**\),以在不顯示 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的情況下，執行特定建置命令。  
  
 [NMAKE](../build/nmake-reference.md)  
 使用 NMAKE \(nmake.exe\)，以自動化利用傳統 Makefile，建置 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 專案的工作。  
  
 當您在命令列上進行建置時，您可以透過啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 然後在功能表列上選擇 \[說明\]、\[搜尋\]，以取得警告、錯誤及訊息的相關資訊。  
  
## 在本節中  
 文件中本區段的文章顯示如何在命令列上建置應用程式，描述如何自訂命令列建置環境，以使用 64 位元工具組並將目標設定為 x86、x64 及 ARM 平台，以及示範如何使用命令列建置工具 MSBuild 及 NMAKE。  
  
 [逐步解說：在命令列上編譯原生 C\+\+ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
 提供範例，顯示如何在命令列上建立及編譯簡單的 C\+\+ 程式。  
  
 [逐步解說：在命令列上編譯 C 程式](../Topic/Walkthrough:%20Compiling%20a%20C%20Program%20on%20the%20Command%20Line.md)  
 描述如何編譯以 C 程式設計語言撰寫的程式。  
  
 [逐步解說：在命令列上編譯 C\+\+\/CLI 程式](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
 描述如何建立及編譯使用 .NET Framework 的 C\+\+\/CLI 程式。  
  
 [逐步解說：在命令列上編譯 C\+\+\/CX 程式](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
 描述如何建立及編譯使用 Windows 執行階段的 C\+\+\/CX 程式。  
  
 [設定命令列建置的路徑及環境變數。](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
 描述如何啟動 \[命令提示字元\] 視窗，以針對命令列建置，設定必要環境變數，這些命令列建置會使用 32 位元或 64 位元工具組，將 x86、x64 及 ARM 平台設為目標。  
  
 [NMAKE 參考](../build/nmake-reference.md)  
 提供指向描述 Microsoft Program Maintenance Utility \(NMAKE.EXE\) 之文章的連結。  
  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)  
 提供指向討論如何使用 MSBuild.EXE 之文章的連結。  
  
## 相關章節  
 [\/MD、\/MT、\/LD \(使用執行階段程式庫\)](../build/reference/md-mt-ld-use-run-time-library.md)  
 描述如何使用這些編譯器選項，來使用偵錯或發行執行階段程式庫。  
  
 [C\/C\+\+ 編譯器選項](../build/reference/compiler-options.md)  
 提供指向討論 C 及 C\+\+ 編譯器選項及 CL.exe 之文章的連結。  
  
 [連結器選項](../build/reference/linker-options.md)  
 提供指向討論連結器選項及 LINK.exe 之文章的連結。  
  
 [C\/C\+\+ 建置工具](../build/reference/c-cpp-build-tools.md)  
 提供指向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中所包含之 C\/C\+\+ 建置工具的連結。  
  
## 請參閱  
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)