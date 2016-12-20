---
title: "如何：在命令列啟用 64 位元 Visual C++ 工具組 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "64 位元編譯器 [C++], 命令列用法"
  - "64 位元編譯器 [C++], 在命令列啟用工具組"
  - "命令列 [C++], 64 位元編譯器"
  - "IPF"
  - "IPF, 命令列編譯器"
  - "Itanium [C++]"
  - "Itanium [C++], 命令列編譯器"
  - "x64 [C++]"
  - "x64 [C++], 命令列編譯器"
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：在命令列啟用 64 位元 Visual C++ 工具組
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 包含的編譯器可以用來建立在 32 位元、64 位元或 ARM 架構 Windows 作業系統上執行的應用程式。  
  
> [!NOTE]
>  如需每個 Visual C\+\+ 版本隨附之特定工具的詳細資訊，請參閱 [Visual Studio 版本中的 Visual C\+\+ 工具和樣板](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)。  
>   
>  如需如何使用 Visual Studio IDE 建立 64 位元應用程式的詳細資訊，請參閱 [如何：將 Visual C\+\+ 專案設定成以 64 位元平台為目標](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 包含適用於 x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 ARM 目標的 32 位元、x86 裝載、原生和跨平台編譯器。  當 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安裝在 64 位元 Windows 作業系統上時，會為每個目標 \(x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 ARM\) 安裝 32 位元、x86 裝載的原生和跨平台編譯器，以及 64 位元、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 裝載的原生和跨平台編譯器。  每個目標的 32 位元和 64 位元編譯器都會產生相同的程式碼，但是 64 位元編譯器為先行編譯標頭符號和整個程式最佳化 \([\/GL](../build/reference/gl-whole-program-optimization.md)、[\/LTCG](../build/reference/ltcg-link-time-code-generation.md)\) 選項支援較多的記憶體。  如果使用 32 位元編譯器時遇到記憶體限制，請嘗試使用 64 位元編譯器。  
  
 當 Visual Studio 安裝在 64 位元的 Windows 作業系統上時，64 位元的原生 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 與 x86 跨平台編譯器會有額外的命令提示字元捷徑可用。  若要在 Windows 8 存取這些命令提示字元，請開啟 \[**開始**\] 畫面中的 \[**所有應用程式**\]。  在已安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]\] 的版本下，開啟 \[Visual Studio Tools\]，然後選擇其中一個原生工具或跨工具命令提示字元。  在舊版 Windows 中，選擇 \[**開始**\]，展開 \[**所有程式**\]、\[**[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]**\]、\[**Visual Studio Tools**\]，然後選擇命令列提示字元。  
  
## Vcvarsall.bat  
 執行 vcvarsall.bat 命令檔設定啟用編譯器工具組的路徑和環境變數，即可在命令列使用任何編譯器。  由於沒有 \[命令提示字元\] 捷徑來讓 64 位元工具組將 x86 或 ARM 平台做為目標，因此請在 \[命令提示字元\] 視窗中使用 vcvarsall.bat，以改用 64 位元工具組。  如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 下列步驟顯示如何設定 \[命令提示字元\]，來使用 64 位元原生工具組，將 x86、x64 和 ARM 平台做為目標。  
  
#### 執行 vcvarsall.bat 以使用 64 位元工具組  
  
1.  在命令提示字元下，變更至 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 安裝目錄   \(該位置視系統和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安裝而定，但一般位置為 C:\\Program Files \(x86\)\\Microsoft Visual Studio *version*\\VC\\\)。例如，輸入：  
  
     cd "\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\\VC"  
  
2.  若要針對將 x64 平台做為目標的 64 位元命令列組建，設定此 \[命令提示字元\] 視窗，請在命令提示字元下，輸入：  
  
     `vcvarsall amd64`  
  
3.  若要針對將 x86 平台做為目標的 64 位元命令列組建，設定此 \[命令提示字元\] 視窗，請在命令提示字元下，輸入：  
  
     `vcvarsall amd64_x86`  
  
4.  若要針對將 ARM 平台做為目標的 64 位元命令列組建，設定此 \[命令提示字元\] 視窗，請在命令提示字元下，輸入：  
  
     `vcvarsall amd64_arm`  
  
## 請參閱  
 [為 64 位元設定程式](../build/configuring-programs-for-64-bit-visual-cpp.md)