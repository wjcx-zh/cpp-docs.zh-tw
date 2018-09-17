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
ms.openlocfilehash: 2792b49d7d3d3f107e39931ff62e6c4137c9c5ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723264"
---
# <a name="building-cc-programs"></a>建置 C/C++ 程式

您可以在 Visual Studio 中或命令列上，建置 Visual C++ 專案。 使用 Visual Studio IDE [MSBuild](../build/msbuild-visual-cpp.md)建置專案和方案。 在命令列上，您可以使用 C/C++ 編譯器 (cl.exe) 及連結器 (link.exe)，來建置簡單的專案。 若要在命令列上建置更複雜的專案，您可以使用 MSBuild 或[NMAKE](../build/nmake-reference.md)。 如需有關如何使用 Visual Studio 來建置專案和方案的概觀，請參閱[編譯和建置](/visualstudio/ide/compiling-and-building-in-visual-studio)。

## <a name="in-this-section"></a>本節內容

[建置 Visual Studio 中的 c + + 專案](../ide/building-cpp-projects-in-visual-studio.md)討論如何使用 Visual Studio IDE 來建置 C/c + + 專案。

[在命令列上建置 C/c + + 程式碼](../build/building-on-the-command-line.md)討論如何使用 C/c + + 命令列編譯器和建置工具隨附於 Visual Studio。

[建置 C/c + + 隔離應用程式和並排顯示組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)描述 Windows 桌面應用程式，隔離的應用程式和並排顯示組件的概念為基礎的部署模型。

[C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)提供連結至 c + +、 編譯器和連結器選項建置程式的參考文件，以及各種建置工具。

[設定 Visual c + + 64 位元 x64 目標](../build/configuring-programs-for-64-bit-visual-cpp.md)說明如何設定 Visual Studio 及命令列使用 64 位元工具組，以及如何以 64 位元架構為目標，並討論常見的移轉問題，當程式碼移到 64 位元架構。

[適用於 ARM 處理器設定 Visual c + +](../build/configuring-programs-for-arm-processors-visual-cpp.md)描述 ARM 處理器所使用的慣例，並討論常見的移轉問題，當程式碼移至 ARM 架構。

[設定 Windows XP 程式](../build/configuring-programs-for-windows-xp.md)描述如何設定目標 Windows XP 開發的平台工具組。

## <a name="related-sections"></a>相關章節

[編譯和建置](/visualstudio/ide/compiling-and-building-in-visual-studio)說明 Visual Studio 會建置系統和工具。