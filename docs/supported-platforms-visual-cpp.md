---
title: "支援的平台 (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 0192e9bd6ef9d93e274c43c24137a27e5aa53dab
ms.openlocfilehash: c0c209c16ad4a264b851321a2879104112da81f2
ms.lasthandoff: 02/24/2017

---
# <a name="supported-platforms-visual-c"></a>支援的平台 (Visual C++)
使用 [!INCLUDE[vsprvs](assembler/masm/includes/vsprvs_md.md)] 所建置的應用程式可以在各種平台上做為目標執行，如下所示。  
  
|作業系統|x86|x64|ARM|  
|----------------------|---------|---------|---------|  
|Windows XP|X*|X*||  
|[!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)]|X*|X*||  
|Windows Vista|X|X||  
|Windows Server 2008|X|X||  
|Windows 7|X|X||  
|Windows Server 2012 R2|X|X||  
|Windows 8|X|X|X|  
|Windows 8.1|X|X|X|  
|Windows 10|X|X|X|  
|Android **|X|X|X|  
|iOS **|X|X|x|  
  
 \* 您可以使用 Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 Update 1 (含) 以後版本隨附的 Windows XP 平台工具組，建置 Windows XP 和 [!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)] 專案。 如需如何使用這個平台工具組的相關資訊，請參閱[為 Windows XP 設定程式](build/configuring-programs-for-windows-xp.md)。 如需變更平台工具組的其他資訊，請參閱[如何：修改目標 Framework 和平台工具組](build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
 ** 您可以安裝 Visual Studio 2015 安裝程式中的選擇性 Visual C++ for Cross Platform Mobile Development 元件，將 iOS 或 Android 平台設為目標。 如需指示，請參閱[安裝適用於跨平台行動裝置開發的 Visual C++](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)。 若要建置 iOS 程式碼，您必須具有 Mac 電腦，並且符合其他需求。 如需必要條件清單和安裝指示，請參閱[安裝和設定工具以使用 iOS 建置](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios)。 您可以配合目標硬體來建置 x86 或 ARM 程式碼。 使用 x86 組態為 iOS 模擬器、Microsoft Visual Studio Emulator for Android 和一些 Android 裝置進行建置。 使用 ARM 組態為 iOS 裝置和大部分 Android 裝置進行建置。  
  
 如需如何設定目標平台組態的資訊，請參閱[如何：將 Visual C++ 專案設定成以 64 位元平台為目標](build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 版本中的 Visual C++ 工具和功能](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)   
 [快速入門](/visualstudio/ide/getting-started-with-visual-cpp-in-visual-studio)
