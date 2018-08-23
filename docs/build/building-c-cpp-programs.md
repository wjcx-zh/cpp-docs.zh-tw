---
title: 建置 C/c + + 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs:
- C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fa07308d04d14395b0ca9773e2a0c81ed0c2bc2
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572252"
---
# <a name="building-cc-programs"></a>建置 C/C++ 程式

您可以在 Visual Studio 中或命令列上，建置 Visual C++ 專案。 使用 Visual Studio IDE [MSBuild](../build/msbuild-visual-cpp.md)建置專案和方案。 在命令列上，您可以使用 C/C++ 編譯器 (cl.exe) 及連結器 (link.exe)，來建置簡單的專案。 若要在命令列上建置更複雜的專案，您可以使用 MSBuild 或[NMAKE](../build/nmake-reference.md)。 如需有關如何使用 Visual Studio 來建置專案和方案的概觀，請參閱[編譯和建置](/visualstudio/ide/compiling-and-building-in-visual-studio)。  
  
## <a name="in-this-section"></a>本節內容  

[在 Visual Studio 中建置 C++ 專案](../ide/building-cpp-projects-in-visual-studio.md)  
討論如何使用 Visual Studio IDE，來建置 C/C++ 專案。  
  
[在命令列上建置 C/C++ 程式碼](../build/building-on-the-command-line.md)  
討論如何使用 Visual Studio 中包含的 C/C++ 命令列編譯器及建置工具。  
  
[建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
描述 Windows 桌面應用程式的部署模型，其基於隔離應用程式及並存組件的想法。  
  
[C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)  
提供參考文章連結，包含以 C++ 建置程式，和編譯器及連結器選項，以及各種建置工具的連結。  
  
[針對 64 位元 x64 目標設定 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md)  
說明如何設定 Visual Studio 及命令列以使用 64 位元工具組，及如何將 64 位元架構做為目標，以及討論當程式碼移至 64 位元架構時常見的移轉問題。  
  
[針對 ARM 處理器設定 Visual C++](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
描述 ARM 處理器所使用的慣例，以及討論當程式碼移至 ARM 架構時常見的移轉問題。  
  
[為 Windows XP 設定程式](../build/configuring-programs-for-windows-xp.md)  
描述如何設定平台工具組，以將 Windows XP 開發做為目標。  
  
## <a name="related-sections"></a>相關章節  
 [編譯和建置](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 說明 Visual Studio 建置系統和工具。