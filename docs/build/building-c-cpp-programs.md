---
title: "建置 C/C++ 程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vcbuilding"
  - "buildingaprogramVC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "組建 [C++]"
  - "組建 [C++], 選項"
  - "專案 [C++], 建置"
  - "Visual C++ 專案, 建置"
  - "Visual C++, 建置選項"
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置 C/C++ 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在 Visual Studio 中或命令列上，建置 Visual C\+\+ 專案。  Visual Studio IDE 使用 [MSBuild](../build/msbuild-visual-cpp.md)，來建置專案和方案。  在命令列上，您可以使用 C\/C\+\+ 編譯器 \(cl.exe\) 及連結器 \(link.exe\)，來建置簡單的專案。  如要在命令列上建置更複雜的專案，可以使用 MSBuild 或 [NMAKE](../build/nmake-reference.md)。  如需使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 建置專案和方案的概觀，請參閱[Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)。  
  
## 在本節中  
 [在 Visual Studio 中建置 C\+\+ 專案](../ide/building-cpp-projects-in-visual-studio.md)  
 討論如何使用 Visual Studio IDE，來建置 C\/C\+\+ 專案。  
  
 [在命令列中建置](../build/building-on-the-command-line.md)  
 討論如何使用 Visual Studio 中包含的 C\/C\+\+ 命令列編譯器及建置工具。  
  
 [建置 C\/C\+\+ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
 描述 Windows 桌面應用程式的部署模型，其基於隔離應用程式及並存組件的想法。  
  
 [C\/C\+\+ 建置參考](../build/reference/c-cpp-building-reference.md)  
 提供參考文章連結，包含以 C\+\+ 建置程式，和編譯器及連結器選項，以及各種建置工具的連結。  
  
 [為 64 位元設定程式](../build/configuring-programs-for-64-bit-visual-cpp.md)  
 說明如何設定 Visual Studio 及命令列以使用 64 位元工具組，及如何將 64 位元架構做為目標，以及討論當程式碼移至 64 位元架構時常見的移轉問題。  
  
 [為 ARM 處理器設定程式](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
 描述 ARM 處理器所使用的慣例，以及討論當程式碼移至 ARM 架構時常見的移轉問題。  
  
 [為 Windows XP 設定 C\+\+ 11 程式](../build/configuring-programs-for-windows-xp.md)  
 描述如何設定平台工具組，以將 Windows XP 開發做為目標。  
  
## 相關章節  
 [NIB: Samples Included in Visual C\+\+](http://msdn.microsoft.com/zh-tw/c9ec56b3-2bbd-49b4-8a4c-9ed4b78b7a84)  
 提供展示 Visual C\+\+ 及它所支援各種程式庫和技術之能力的範例程式碼連結。  
  
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)  
 說明 Visual Studio 建置系統和工具。