---
title: "設定命令列建置的路徑和環境變數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "include"
  - "Lib"
  - "Path"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器 [C++], 環境變數"
  - "編譯原始程式碼 [C++], 從命令列"
  - "環境變數 [C++]"
  - "環境變數 [C++], CL 編譯器"
  - "INCLUDE 保留字"
  - "LIB 環境變數"
  - "LINK 工具 [C++], 環境變數"
  - "LINK 工具 [C++], 路徑"
  - "PATH 保留字"
  - "VCVARS32.bat 檔"
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 設定命令列建置的路徑和環境變數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令列建置工具需要針對安裝所自訂的數個環境變數。  當安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 時，它會建立設定必要環境變數的命令檔，然後建立啟動 \[命令提示字元\] 視窗的捷徑，在該視窗中，已設定這些變數。  當您想要使用命令列工具時，您可以執行其中一個捷徑，或者您可以開啟純文字 \[命令提示字元\] 視窗，然後執行 vcvarsall.bat 命令檔案。  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令列工具會使用 PATH、TMP、INCLUDE、LIB 及 LIBPATH 環境變數，也可能使用工具專屬環境變數。  由於這些是安裝專屬的環境變數值，且可以由產品更新或升級變更，因此我們建議您使用 vcvarsall.bat 或 \[開發人員命令提示字元\]，而不是自己對它們進行設定。  如需編譯器和連結器所使用之專屬環境變數的詳細資訊，請參閱 [CL 環境變數](../build/reference/cl-environment-variables.md)和 [LINK 環境變數](../build/reference/link-environment-variables.md)。  
  
> [!NOTE]
>  數個命令列工具或工具選項需要系統管理員權限。  若要使用它們，建議您使用 \[以系統管理員身分執行\] 選項 \(在您要開啟之 \[命令提示字元\] 視窗的捷徑功能表上\)，來開啟 \[命令提示字元\] 視窗。  
  
## 使用 \[命令提示字元\] 捷徑  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 每一個版本中都包含的 \[開發人員命令提示字元\] 捷徑會開啟 \[命令提示字元\] 視窗，並會將環境設定為使用 32 位元 x86 原生工具組，以將 x86 處理器設定為目標。  同時提供以 x64 和 ARM 平台為目標之 32 位元跨編譯器的 \[命令提示字元\]。  根據您的系統及所安裝的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本，還可能提供以 x64 處理器為目標之 64 位元 x64 原生工具組的 \[命令提示字元\] 捷徑，以及以 x86 處理器為目標之 64 位元跨編譯器的 \[命令提示字元\] 捷徑。  這些版本的命令列工具組在 Visual Studio 的所有版本中都有提供：  
  
 x86 on x86  
 使用此工具組，可以建立 x86 電腦的輸出檔。  它會以 32 位元處理序執行，在 x86 機器上為原生，而在 64 位元 Windows 作業系統上則需要 WOW64。  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] on x86 \([!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 跨平台編譯器\)  
 使用此工具組，可以建立 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 的輸出檔。  它會以 32 位元處理序執行，在 x86 機器上為原生，而在 64 位元 Windows 作業系統上則需要 WOW64。  
  
 ARM on x86 \(ARM 跨平台編譯器\)  
 使用此工具組，可以建立 ARM 電腦的輸出檔。  它會以 32 位元處理序執行，在 x86 機器上為原生，而在 64 位元 Windows 作業系統上則需要 WOW64。  
  
 這些版本的命令列工具組，在 64 位元平台上提供：  
  
 x86 on [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]  
 使用此工具組，可以建立 x86 電腦的輸出檔。  它在 64 位元 Windows 作業系統上是以原生處理序執行。  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] on [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]  
 使用此工具組，可以建立 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 電腦的輸出檔。  它在 64 位元 Windows 作業系統上是以原生處理序執行。  
  
 ARM on x64 \(ARM 跨平台編譯器\)  
 使用此工具組，可以建立 ARM 電腦的輸出檔。  它在 64 位元 Windows 作業系統上是以原生 64 位元處理序執行。  
  
#### 開啟 \[開發人員命令提示字元\] 視窗  
  
1.  在顯示 Windows 8 \[開始\] 畫面的情況下，輸入 Visual Studio Tools。  請注意，搜尋結果會隨著您的輸入而變更，當出現 \[Visual Studio Tools\] 時，請選擇它。  
  
     在舊版 Windows 中，選擇 \[開始\]，然後在搜尋方塊中，輸入 Visual Studio Tools。  當搜尋結果中出現 \[Visual Studio Tools\] 時，請選擇它。  
  
2.  在 \[Visual Studio Tools\] 資料夾中，針對您的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本，開啟 \[開發人員命令列提示字元\]   \(若要以系統管理員身分執行，請開啟 \[開發人員命令提示字元\] 的捷徑功能表，然後選擇 \[以系統管理員身分執行\]\)。  
  
 \[開發人員命令提示字元\] 會將環境設定為使用 32 位元原生工具組，以將 x86 處理器設定為目標。  選擇 \[x64 Cross Tools 命令提示字元\]，以使用 32 位元原生工具組，將 x64 處理器設定為目標。  選擇 \[ARM Cross Tools 命令提示字元\]，以使用 32 位元原生工具組，將 ARM 處理器設定為目標。  選擇 \[x64 Native Tools 命令提示字元\]，以使用 64 位元原生工具組，將 x64 處理器設定為目標。  
  
## 在 \[命令提示字元\] 視窗中使用 vcvarsall.bat  
 透過在純文字 \[命令提示字元\] 視窗中執行 vcvarsall.bat，您可以設定環境變數，以將原生 32 位元或 64 位元編譯，或跨平台編譯的命令列，設定為  x86、x64 或 ARM 處理器。  如果未提供引數，則 vcvarsall.bat 會設定環境變數，以便針對 x86 目標使用 32 位元原生編譯器。  不過，您可以使用這個檔案來設定任何編譯器。  如果您指定了組建電腦架構未安裝或無法使用的編譯器組態，則會顯示錯誤訊息。  下表顯示支援的引數。  
  
|Vcvarsall.bat 引數|編譯器|組建電腦架構|組建輸出架構|  
|----------------------|---------|------------|------------|  
|x86|x86 32 位元原生|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86|  
|x86\_amd64|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] on x86 \(跨平台\)|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|x86\_arm|ARM on x86 \(跨平台\)|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|ARM|  
|amd64|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 64 位元原生|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|amd64\_x86|x86 on [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] \(跨平台\)|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86|  
|amd64\_arm|ARM on [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] \(跨平台\)|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|ARM|  
  
 下列步驟顯示如何設定 \[命令提示字元\]，以使用 32 位元原生工具組，將 x86 平台設定為目標。  
  
#### 執行 vcvarsall.bat  
  
1.  在命令提示字元下，變更至 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 安裝目錄   \(該位置取決於系統和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安裝，但一般位置為 C:\\Program Files \(x86\)\\Microsoft Visual Studio *version*\\VC\\\)。例如，輸入：  
  
     cd "\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\\VC"  
  
2.  若要設定 32 位元 x86 命令列建置的這個 \[命令列提示字元\] 視窗，請在命令提示字元下，輸入：  
  
     `vcvarsall x86`  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 還會提供 vcvars32.bat，以設定命令列環境。  vcvars32.bat 檔案僅限於設定適當的環境變數，以啟用 32 位元 x86 命令列建置。  它相當於 `vcvarsall x86` 命令。  
  
 如果您針對命令列建置使用 [DEVENV](../Topic/Devenv%20Command%20Line%20Switches.md)，則 vcvarsall.bat 或 vcvars32.bat 設定的環境不會影響您的建置，除非您同時指定 **\/useenv** 選項。  
  
> [!CAUTION]
>  在不同的電腦上，vcvarsall.bat 檔案可能也不同。  請勿使用其他電腦上的檔案，來取代遺失或損毀的 vcvarsall.bat 檔案。  請重新執行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安裝，以取代遺失的檔案。  
>   
>  在不同的版本上，vcvarsall.bat 也可能不同。  如果安裝最新版本 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 的電腦上還安裝有舊版 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，請勿在同一個 \[命令提示字元\] 視窗中，執行不同版本的 vcvarsall.bat 或 vcvars32.bat。  
  
## 請參閱  
 [在命令列中建置](../build/building-on-the-command-line.md)   
 [連結](../build/reference/linking.md)   
 [連結器選項](../build/reference/linker-options.md)   
 [編譯 C\/C\+\+ 程式](../build/reference/compiling-a-c-cpp-program.md)   
 [編譯器選項](../build/reference/compiler-options.md)