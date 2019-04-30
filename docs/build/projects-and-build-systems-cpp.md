---
title: C /C++專案，並建置在 Visual Studio 中的系統
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 12/08/2018
f1_keywords:
- vcbuilding
- buildingaprogramVC
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.openlocfilehash: 73797f3817338c48e8ff11eaaadff71263374fd0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341160"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>C /C++專案，並建置在 Visual Studio 中的系統

您可以使用 Visual Studio 2017 來編輯、 編譯和建置任何C++程式碼基底使用完整的 IntelliSense 支援，而不需要將該程式碼轉換成 Visual Studio 專案或 MSVC 工具組的編譯。 例如，您可以編輯在 Windows 電腦上，Visual Studio 中的跨平台 」 的 CMake 專案，然後編譯適用於 Linux 的遠端 Linux 機器上使用 g + +。

## <a name="c-compilation"></a>C++編譯

若要*建置*C++程式可編譯原始程式碼，從一或多個檔案，然後將這些檔案連結至可執行檔 (.exe)、 動態載入程式庫 (.dll) 或靜態程式庫 (.lib)。 

基本C++編譯牽涉到三個主要步驟：

- C++前置處理器會將每個原始程式檔中的所有 #directives 和巨集定義的都轉換。 這會建立*轉譯單位*。
- C++編譯器會編譯到目的檔 (.obj)，每個轉譯單位套用已設定任何編譯器選項。
- *連結器*將物件檔案合併成單一的可執行檔，套用已設定連結器選項。 

## <a name="the-msvc-toolset"></a>MSVC 工具組

MicrosoftC++編譯器、 連結器、 標準程式庫和相關的公用程式組成 MSVC 編譯器工具組 （也稱為工具鏈或 「 建置工具 」）。 這些都包含在 Visual Studio。 您也可以下載並從免費使用工具組，作為獨立封裝[Build Tools for Visual Studio 2017 下載位置](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)。

您可以藉由叫用 MSVC 編譯器 (cl.exe) 直接從命令列建置簡單的程式。 下列命令會接受單一原始程式碼檔，並叫用來建置呼叫的可執行檔的 cl.exe *hello.exe*: 

```cmd
cl /EHsc hello.cpp
```
請注意，這裡編譯器 (cl.exe) 會自動叫用C++前置處理器和連結器產生的最後輸出檔。  如需詳細資訊，請參閱 <<c0> [ 命令列上建置](building-on-the-command-line.md)。

## <a name="build-systems-and-projects"></a>建置系統和專案

大部分的真實世界程式使用某些種類的*建置系統*來管理複雜的編譯多重原始程式檔，對於多個組態 （也就是偵錯與發行），多個平台 (x86、 x64、 ARM，等等)，自訂建置步驟，以及多個可執行檔，必須以特定順序編譯。 您在 組建組態檔案，進行設定，並建置系統會接受做為輸入該檔案之前，它叫用編譯器。 一組原始程式檔和建置的可執行檔所需的建置組態檔稱為*專案*。 

下列清單顯示各種選項，Visual Studio 專案- C++:

- 使用 Visual Studio IDE 中建立 Visual Studio 專案，並將它設定使用屬性頁。 Visual Studio 專案會產生在 Windows 執行的程式。 如需概觀，請參閱[編譯和建置](/visualstudio/ide/compiling-and-building-in-visual-studio)Visual Studio 文件中。

- 開啟包含 CMakeLists.txt 檔案的資料夾。 CMake 支援已整合到 Visual Studio。 您可以使用 IDE 來編輯、 測試和偵錯，而不需修改 CMake 檔案，以任何方式。 這可讓您能夠在相同 CMake 專案與其他人對可能會使用不同的編輯器。 CMake 會是跨平台開發的建議的方法。 如需詳細資訊，請參閱 < [CMake 專案](cmake-projects-in-visual-studio.md)。
 
- 沒有專案檔案中開啟鬆散來源檔案的資料夾。 Visual Studio 會使用啟發學習法，來建置的檔案。 這是用來編譯及執行小型的主控台應用程式。 如需詳細資訊，請參閱 <<c0> [ 開啟資料夾 」 專案](open-folder-projects-cpp.md)。

- 開啟包含 makefile 或任何其他組建系統組態檔的資料夾。 您可以設定 Visual Studio 來叫用任何任意的建置命令，將 JSON 檔案新增至資料夾。 如需詳細資訊，請參閱 <<c0> [ 開啟資料夾 」 專案](open-folder-projects-cpp.md)。
 
- Visual Studio 中開啟 Windows makefile。 如需詳細資訊，請參閱 < [NMAKE 參考](reference/nmake-reference.md)。

## <a name="msbuild-from-the-command-line"></a>MSBuild 從命令列 

您可以叫用 MSBuild 從命令列傳遞的.vcxproj 檔案，以及命令列選項。 此方法需要 MSBuild，深入了解，並只在絕對必要時，建議使用。 如需詳細資訊，請參閱 [MSBuild](msbuild-visual-cpp.md)。

## <a name="in-this-section"></a>本節內容

[Visual Studio 專案](creating-and-managing-visual-cpp-projects.md)如何建立、 設定和建置C++在 Visual Studio 中使用原生專案建置系統 (MSBuild)。

[CMake 專案](cmake-projects-in-visual-studio.md)如何撰寫程式碼、 建置及部署 Visual Studio 中的 CMake 專案。

[開啟資料夾 」 專案](open-folder-projects-cpp.md)如何使用 Visual Studio 程式碼、 建置和部署C++任何任意建置系統或完全不需要為基礎的專案建置系統。 在所有項目。 

[發行組建](release-builds.md)如何建立與疑難排解最佳化的發行組建部署至使用者。

[從命令列使用 MSVC 工具組](building-on-the-command-line.md)<br/>
討論如何使用 C /C++直接從命令列，而不是使用 Visual Studio IDE 的編譯器及建置工具。

[建置在 Visual Studio 中的 Dll](dlls-in-visual-cpp.md)如何建立、 偵錯和部署 C /C++ Visual Studio 中的 Dll （共用程式庫）。

[逐步解說：建立和使用靜態程式庫](walkthrough-creating-and-using-a-static-library-cpp.md)如何建立.lib 二進位檔案。

[建置 C /C++隔離的應用程式和並排顯示組件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)描述 Windows 桌面應用程式，隔離的應用程式和並排顯示組件的概念為基礎的部署模型。

[設定C++適用於 64 位元，x64 專案目標](configuring-programs-for-64-bit-visual-cpp.md)如何為目標的 64 位元 x64 硬體使用 MSVC 建置工具。

[設定C++專案，適用於 ARM 處理器](configuring-programs-for-arm-processors-visual-cpp.md)如何針對 ARM 硬體使用 MSVC 建置工具。

[最佳化您的程式碼](optimizing-your-code.md)如何最佳化您的程式碼，包括 「 引導式的程式最佳化的各種方式。

[設定 Windows XP 程式](configuring-programs-for-windows-xp.md)如何以 Windows XP MSVC 建置工具的目標。

[C/C++ 建置參考](reference/c-cpp-building-reference.md)<br/>
提供參考文章連結，包含以 C++ 建置程式，和編譯器及連結器選項，以及各種建置工具的連結。
