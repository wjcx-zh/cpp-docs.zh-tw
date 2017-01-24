---
title: "支援的平台 (Visual C++) | Microsoft Docs"
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
  - "平台 [C++]"
  - "Visual C++, 支援的平台"
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支援的平台 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 所建置的應用程式可以在各種平台上做為目標執行，如下所示。  
  
|作業系統|x86|x64|ARM|  
|----------|---------|---------|---------|  
|Windows XP|X\*|X\*||  
|[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|X\*|X\*||  
|Windows Vista|X|X||  
|Windows Server 2008|X|X||  
|Windows 7|X|X||  
|Windows Server 2012 R2|X|X||  
|Windows 8|X|X|X|  
|Windows 8.1|X|X|X|  
|Windows 10|X|X|X|  
|Android \*\*|X|X|X|  
|iOS \*\*|X|X|X|  
  
 \* 您可以使用 Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 Update 1 \(含\) 以後版本隨附的 Windows XP 平台工具組，建置 Windows XP 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 專案。  如需如何使用這個平台工具組的相關資訊，請參閱[為 Windows XP 設定 C\+\+ 11 程式](../build/configuring-programs-for-windows-xp.md)。  如需變更平台工具組的相關資訊，請參閱[如何：修改目標 Framework 和平台工具組](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
 \*\* 您可以安裝 Visual Studio 2015 安裝程式中的選擇性 Visual C\+\+ for Cross Platform Mobile Development 元件，將 iOS 或 Android 平台設為目標。  如需指示，請參閱[安裝 Visual C\+\+ for Cross\-Platform Mobile Development](../Topic/Install%20Visual%20C++%20for%20Cross-Platform%20Mobile%20Development.md)。  若要建置 iOS 程式碼，您必須具有 Mac 電腦，並且符合其他需求。  如需必要條件清單和安裝指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../Topic/Install%20And%20Configure%20Tools%20to%20Build%20using%20iOS.md)。  您可以配合目標硬體來建置 x86 或 ARM 程式碼。  使用 x86 組態為 iOS 模擬器、Microsoft Visual Studio Emulator for Android 和一些 Android 裝置進行建置。  使用 ARM 組態為 iOS 裝置和大部分 Android 裝置進行建置。  
  
 如需如何設定目標平台組態的相關資訊，請參閱[如何：將 Visual C\+\+ 專案設定成以 64 位元平台為目標](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。  
  
## 請參閱  
 [Visual Studio 版本中的 Visual C\+\+ 工具和樣板](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)   
 [快速入門](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md)