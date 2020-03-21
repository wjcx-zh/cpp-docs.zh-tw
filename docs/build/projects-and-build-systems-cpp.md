---
title: Visual Studio 中C++的 C/專案和組建系統
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 3d82ac4569e06a4472047a79da60032ad2db43ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078465"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Visual Studio 中C++的 C/專案和組建系統

您可以使用 Visual Studio 來編輯、編譯及建立具有C++完整 IntelliSense 支援的任何程式碼基底，而不需要將該程式碼轉換成 Visual Studio 專案，或使用 MSVC 工具組進行編譯。 例如，您可以在 Windows 電腦的 Visual Studio 中編輯跨平臺 CMake 專案，然後在遠端 Linux 電腦上使用 g + + 針對 Linux 進行編譯。

## <a name="c-compilation"></a>C++編譯

若*build*要建立C++程式，您可以從一或多個檔案編譯原始程式碼，然後將這些檔案連結到可執行檔（.exe）、動態載入程式庫（.dll）或靜態程式庫（.lib）。

基本C++編譯牽涉到三個主要步驟：

- C++預處理器會轉換每個原始程式檔中的所有 #directives 和巨集定義。 這會建立*轉譯單位*。
- C++編譯器會將每個轉譯單位編譯成物件檔（.obj），套用任何已設定的編譯器選項。
- *連結器*會將物件檔案合併成單一可執行檔，並套用已設定的連結器選項。

## <a name="the-msvc-toolset"></a>MSVC 工具組

Microsoft C++編譯器、連結器、標準程式庫和相關的公用程式，都包含 MSVC 編譯器工具組（也稱為工具鏈或「組建工具」）。 這些包含在 Visual Studio 中。 您也可以從[適用于 Visual Studio 2019 下載位置的 Build Tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)免費下載並使用工具組作為獨立封裝。

您可以直接從命令列叫用 MSVC 編譯器（cl）來建立簡單的程式。 下列命令會接受單一原始程式碼檔，並叫用 cl 來建立名為*hello .exe*的可執行檔：

```cmd
cl /EHsc hello.cpp
```

請注意，在這裡，編譯器（cl）會自動叫C++用預處理器和連結器，以產生最終的輸出檔。  如需詳細資訊，請參閱在[命令列上建立](building-on-the-command-line.md)。

## <a name="build-systems-and-projects"></a>組建系統和專案

大部分的真實世界程式都會使用某種*組建系統*來管理針對多個設定（也就是 debug 與 release）、多個平臺（x86、X64、ARM 等等）編譯多個來源檔案的複雜性、自訂的組建步驟，甚至是必須以特定順序編譯的多個可執行檔。 您會在組建設定檔中進行設定，而組建系統會接受該檔案做為輸入，然後再叫用編譯器。 建立可執行檔所需的一組原始程式碼檔案和組建設定檔稱為「專案」（ *project*）。

下列清單顯示 Visual Studio 專案的各種選項- C++：

- 使用 Visual Studio IDE 建立 Visual Studio 專案，並使用屬性頁加以設定。 Visual Studio 專案會產生在 Windows 上執行的程式。 如需總覽，請參閱 Visual Studio 檔中的[編譯和建立](/visualstudio/ide/compiling-and-building-in-visual-studio)。

- 開啟包含 Remote monitoring.h cmakelists.txt 檔案的資料夾。 CMake 支援已整合到 Visual Studio 中。 您可以使用 IDE 來編輯、測試和調試，而不需要以任何方式修改 CMake 檔。 這可讓您在相同的 CMake 專案中工作，而其他人可能會使用不同的編輯器。 CMake 是跨平臺開發的建議方法。 如需詳細資訊，請參閱[CMake projects](cmake-projects-in-visual-studio.md)。

- 開啟沒有專案檔之原始檔的鬆散資料夾。 Visual Studio 將使用啟發學習法來建立檔案。 這是簡單的方法，可讓您編譯和執行小型主控台應用程式。 如需詳細資訊，請參閱[開啟資料夾專案](open-folder-projects-cpp.md)。

- 開啟包含 makefile 或任何其他組建系統設定檔的資料夾。 您可以藉由將 JSON 檔案新增至資料夾，將 Visual Studio 設定為叫用任何任意的組建命令。 如需詳細資訊，請參閱[開啟資料夾專案](open-folder-projects-cpp.md)。

- 在 Visual Studio 中開啟 Windows makefile。 如需詳細資訊，請參閱[NMAKE 參考](reference/nmake-reference.md)。

## <a name="msbuild-from-the-command-line"></a>來自命令列的 MSBuild

您可以從命令列叫用 MSBuild，方法是將 .vcxproj 檔案連同命令列選項一起傳遞。 這種方法需要充分瞭解 MSBuild，而且只有在絕對必要時才建議使用。 如需詳細資訊，請參閱 [MSBuild](msbuild-visual-cpp.md)。

## <a name="in-this-section"></a>本節內容

[Visual Studio 專案](creating-and-managing-visual-cpp-projects.md)如何使用其原生組建系統（ C++ MSBuild）在 Visual Studio 中建立、設定和建立專案。

[CMake 專案](cmake-projects-in-visual-studio.md)如何在 Visual Studio 中撰寫程式碼、建立及部署 CMake 專案。

[開啟資料夾專案](open-folder-projects-cpp.md)如何使用 Visual Studio 來撰寫程式碼、建立及C++部署以任意組建系統為基礎的專案，或無組建系統。 完全。

[發行組建](release-builds.md)如何建立優化的發行組建並進行疑難排解，以供部署至使用者。

[從命令列使用 MSVC 工具組](building-on-the-command-line.md)<br/>
討論如何直接從命令列使用C++ C/編譯器和 build 工具，而不是使用 Visual Studio IDE。

[在 Visual Studio 中建立 dll](dlls-in-visual-cpp.md)如何在 Visual Studio 中建立、調試和部署C++ C/dll （共用程式庫）。

[逐步解說：建立和使用靜態程式庫](walkthrough-creating-and-using-a-static-library-cpp.md)如何建立 .lib 二進位檔案。

[建立 C/C++隔離的應用程式和並存元件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)根據隔離應用程式和並存元件的概念，描述 Windows 桌面應用程式的部署模型。

[設定C++ 64 位、x64 目標的專案](configuring-programs-for-64-bit-visual-cpp.md)如何使用 MSVC build tools 以64位 x64 硬體為目標。

[為C++ ARM 處理器設定專案](configuring-programs-for-arm-processors-visual-cpp.md)如何使用 MSVC build tools 以 ARM 硬體為目標。

[優化您的程式碼](optimizing-your-code.md)如何以各種方式優化程式碼，包括程式指引優化。

設定[WINDOWS XP 的程式](configuring-programs-for-windows-xp.md)如何使用 MSVC build tools 以 Windows XP 為目標。

[C/C++ 建置參考](reference/c-cpp-building-reference.md)<br/>
提供參考文章連結，包含以 C++ 建置程式，和編譯器及連結器選項，以及各種建置工具的連結。
