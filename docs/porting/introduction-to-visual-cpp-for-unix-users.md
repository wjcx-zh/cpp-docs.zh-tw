---
title: Microsoft C++ For UNIX 使用者簡介
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 791c513553acbd300204746ae1e1dddf7a3ae5c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626993"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>Microsoft C++ For UNIX 使用者簡介

本主題提供的資訊適用于各種 UNIX 的使用者，這是 Visual Studio 的新手，而且想要從C++命令列或使用 Visual Studio 提高生產力。 您可以使用 Visual Studio 搭配 Microsoft C++編譯器以 Windows 為目標。 您也可以在 UNIX 環境（例如遠端 Linux 電腦、MinGW-w64 和適用于 Linux 的 Windows 子系統）中搭配使用 Visual Studio IDE 與 GCC 或 Clang。 若要C++在 Visual Studio 中使用，必須安裝使用**C++** 工作負載的桌面開發。 開啟 Visual Studio 安裝程式以安裝工作負載，或新增或移除選用的元件。 如果您要將目標設為遠端 linux 電腦，也可以**使用C++** 工作負載來安裝 Linux 開發。 針對 Android 或 iOS 開發，請**使用C++** 工作負載來安裝行動裝置開發。

## <a name="getting-started-on-the-command-line"></a>命令列使用者入門

您可以從命令列C++使用 Microsoft 編譯器，方法與使用 UNIX 命令列環境類似。 您可以從命令提示字元，使用命令列 C 和 C++ 編譯器 (CL.EXE)、連結器 (LINK.EXE) 和其他工具進行編譯，包括 Microsoft 版的 UNIX make 公用程式 NMAKE.EXE。

在 UNIX 中，命令會安裝在通用資料夾中，例如 /usr/bin。 在 Visual Studio 中，命令列工具會安裝在您的 Visual Studio 安裝目錄 (VC\bin 子目錄中) 及其子目錄中。 不同於 UNIX，這些工具無法從一般命令提示字元視窗存取。 若要使用命令列工具，您必須使用特殊的開發人員命令提示字元，設定編譯C++程式所需的路徑和其他環境變數。 如需詳細資訊，請參閱[在命令列上建置 C/C++ 程式碼](../build/building-on-the-command-line.md)和[逐步解說：在命令列上編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。

## <a name="debugging-your-code"></a>偵錯您的程式碼

您可以從命令列或從 IDE C++中，使用適用于 Microsoft 專案的 [Visual Studio 偵錯工具]。 使用[/Z7、/zi、/zi （Debug 資訊格式）](../build/reference/z7-zi-zi-debug-information-format.md)參數進行編譯，以啟用逐步執行來源。 如需詳細資訊，請參閱[偵錯原生程式碼](/visualstudio/debugger/debugging-native-code)和[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

對於以 GCC 或 Clang 編譯的程式，Visual Studio 會叫用 GDB、LLDB 或您指定的任何自訂偵錯工具。

## <a name="visual-studio-project-system"></a>Visual Studio 專案系統

Visual Studio 專案系統稱為 MSBuild。 它使用 XML 格式的專案檔;C++專案檔的副檔名為 .vcxproj。 應用程式是由多個程式庫和可執行檔所組成，並儲存在屬於單一「方案」的多個專案中，其中每個程式庫和可執行檔可能是以一組不同的編譯器選項，或甚至不同的語言所建置。 方案是將多個專案群組在一起的抽象容器。 方案的相關資訊會儲存在副檔名為 .sln 的方案檔中。 如需詳細資訊，請參閱 [Visual Studio 中的方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)和[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 從主功能表中 **，選擇 [** 檔案] > [**新增** > **專案**]，以查看可用的 Visual Studio 專案範本。

從 Visual Studio 2017 開始，會加入 CMake 專案的支援，以及使用 Microsoft C++編譯器搭配任何任意組建系統的選項，或使用原始程式檔的鬆散資料夾，而且沒有任何專案檔。 如需詳細資訊，請參閱[Visual Studio 中的 CMake 專案](../build/cmake-projects-in-visual-studio.md)和[Visual Studio 中的開啟資料夾專案](../build/open-folder-projects-cpp.md)。

## <a name="microsoft-specific-modifiers"></a>Microsoft 特定修飾詞

Microsoft C++ 編譯器實作標準 C++ 程式設計語言的數個延伸模組，以支援 Windows 作業系統的程式設計。 這些擴充功能可用來指定儲存類別屬性、函式呼叫慣例和基底定址等。 如需所有支援之 C++ 延伸模組的完整清單，請參閱 [Microsoft 專用的修飾詞](../cpp/microsoft-specific-modifiers.md)。

您可以使用 `/Za` 編譯器選項，來停用 C++ 的所有 Microsoft 特定擴充功能。 如果您想要撰寫程式碼以在多個平台上執行，建議使用這個選項。 如需 `/Za` 編譯器選項的詳細資訊，請參閱 [/Za、/Ze (停用語言延伸模組)](../build/reference/za-ze-disable-language-extensions.md)。 如需C++編譯器一致性的詳細資訊，請參閱[Microsoft C++語言一致性資料表](../overview/visual-cpp-language-conformance.md)和[非標準行為](../cpp/nonstandard-behavior.md)。

## <a name="precompiled-headers"></a>先行編譯標頭檔

Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。

根據預設，會在 *pch.h* 與 *pch.cpp* (在 Visual Studio 2017 與較舊版本中則為 *stdafx.h* 與 *stdafx.cpp*) 檔案中指定所有先行編譯的程式碼。 如需先行編譯標頭檔的詳細資訊，請參閱[建立先行編譯標頭檔](../build/creating-precompiled-header-files.md)。

## <a name="related-sections"></a>相關章節

如需詳細資訊，請參閱[在 Windows 上執行 Linux 程式](../porting/porting-from-unix-to-win32.md)。

## <a name="see-also"></a>請參閱

[專案和建置系統](../build/projects-and-build-systems-cpp.md)
