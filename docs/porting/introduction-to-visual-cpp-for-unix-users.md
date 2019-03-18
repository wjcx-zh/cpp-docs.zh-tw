---
title: 針對 UNIX 使用者的 Visual C++ 簡介
ms.date: 09/01/2017
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 6522461cf1f08eee9187a8f739cb21fe01e755f5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747004"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>針對 UNIX 使用者的 Visual C++ 簡介

本主題提供資訊給剛開始使用 Visual Studio，並想更有效率使用 C++ 和 Visual Studio 整合式開發環境 (IDE) 的 UNIX 使用者。

## <a name="getting-started-on-the-command-line"></a>從命令列開始使用

您可以透過與使用 UNIX 命令列環境類似的方式，從命令列使用 C++ 編譯器。 您可以從命令提示字元，使用命令列 C 和 C++ 編譯器 (CL.EXE)、連結器 (LINK.EXE) 和其他工具進行編譯，包括 Microsoft 版的 UNIX make 公用程式 NMAKE.EXE。

在 UNIX 中，命令會安裝在通用資料夾中，例如 /usr/bin。 在 Visual Studio 中，命令列工具會安裝在您的 Visual Studio 安裝目錄 (VC\bin 子目錄中) 及其子目錄中。 不同於 UNIX，這些工具無法從一般命令提示字元視窗存取。 若要使用命令列工具，請使用開發人員命令提示字元捷徑，或執行開發人員命令檔案 (例如 vcvarsall.bat)。 這會設定從命令列編譯 C++ 程式所需的路徑和其他環境變數。 如需詳細資訊，請參閱[在命令列上建置 C/C++ 程式碼](../build/building-on-the-command-line.md)和[逐步解說：在命令列編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。

若要開啟開發人員命令提示字元捷徑，請在桌面搜尋控制項中輸入「開發人員命令提示字元」，然後選擇適用於您 Visual Studio 版本的 [開發人員命令提示字元] 結果。 若要選擇針對特定主機和目標架構預先設定的開發人員命令提示字元，請開啟 [開始] 功能表 (桌面角落的 Windows 圖示)，然後捲動至您 Visual Studio 版本的資料夾 (例如 **Visual Studio 2017**)。 開啟資料夾，然後針對您慣用的主機和目標架構選擇命令提示字元捷徑。

若要利用更強大的功能，例如 Visual Studio 偵錯工具、IntelliSense 程式碼查閱和陳述式完成、視覺化設計工具、專案管理等，您需要使用 Visual Studio IDE。

## <a name="debugging-your-code"></a>偵錯您的程式碼

如果您使用命令列並在開發工作站上執行應用程式，當您的程式碼遇到記憶體存取違規、未處理的例外狀況或其他無法復原的錯誤時，便會顯示一個可執行 Visual Studio 偵錯工具的對話方塊。 如果您按一下 [確定]，則會啟動 Visual Studio 開發環境，並將偵錯工具開啟到失敗點。 您可以透過這個方式來偵錯應用程式，在這種情況下，只有在以 [/Z7、/Zi、/ZI (偵錯資訊格式)](../build/reference/z7-zi-zi-debug-information-format.md) 參數編譯時，才能使用原始程式碼。 如需詳細資訊，請參閱[偵錯原生程式碼](/visualstudio/debugger/debugging-native-code)和[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="using-the-development-environment"></a>使用開發環境

使用開發環境編輯和建置「專案」中的原始程式碼會比較容易。 專案是來源和相關檔案的集合，這些檔案會編譯成一個單位，例如程式庫或可執行檔。 專案也包含檔案建置方式的相關資訊。 專案的相關資訊會儲存在副檔名為 .prj 的專案檔中。

應用程式是由多個程式庫和可執行檔所組成，並儲存在屬於單一「方案」的多個專案中，其中每個程式庫和可執行檔可能是以一組不同的編譯器選項，或甚至不同的語言所建置。 方案是將多個專案群組在一起的抽象容器。 方案的相關資訊會儲存在副檔名為 .sln 的方案檔中。 如需詳細資訊，請參閱 [Visual Studio 中的方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)和[使用 Visual Studio IDE 進行 C++ 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="importing-your-existing-code"></a>匯入現有的程式碼

您可以使用 C++ 編譯器來建置現有的程式碼，並將其設定為以 Makefile 或不以 Makefile 編譯，然後放入 Visual Studio 專案中。 如需詳細資訊，請參閱[如何：從現有的程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)。

## <a name="creating-a-new-project"></a>建立新專案

您可以在開發環境中建立新專案。 Visual Studio 提供許多範本，其中的標準程式碼適用於各種常見專案。 您可以使用應用程式精靈，來產生具有適用於各種應用程式類型之程式碼大綱的專案。

您可以使用 [主控台應用程式 (Win32) 精靈]，從空專案開始。 選取 [空專案] 核取方塊。 您可以稍後再將新的和現有的檔案加入專案。

當您建立專案時，您必須命名專案。 根據預設，專案名稱等於從專案建置之動態連結程式庫 (DLL) 或可執行檔的名稱。 如需詳細資訊，請參閱[建立方案與專案](/visualstudio/ide/creating-solutions-and-projects)。

## <a name="microsoft-specific-modifiers"></a>Microsoft 專有的修飾詞

Microsoft Visual C++ 編譯器實作標準 C++ 程式設計語言的數個延伸模組，以支援 Windows 作業系統的程式設計。 這些擴充功能可用來指定儲存類別屬性、函式呼叫慣例和基底定址等。 如需所有支援之 C++ 延伸模組的完整清單，請參閱 [Microsoft 專用的修飾詞](../cpp/microsoft-specific-modifiers.md)。

您可以使用 `/Za` 編譯器選項，來停用 C++ 的所有 Microsoft 特定擴充功能。 如果您想要撰寫程式碼以在多個平台上執行，建議使用這個選項。 如需 `/Za` 編譯器選項的詳細資訊，請參閱 [/Za、/Ze (停用語言延伸模組)](../build/reference/za-ze-disable-language-extensions.md)。 如需有關 C++ 編譯器一致性的詳細資訊，請參閱 [Visual C++ 語言一致性](../visual-cpp-language-conformance.md)與[非標準行為](../cpp/nonstandard-behavior.md)。

## <a name="precompiled-headers"></a>先行編譯標頭檔

Microsoft C 和 C++ 編譯器提供對任何 C 或 C++ 程式碼進行先行編譯的選項，包括內嵌程式碼。 您可以使用這項效能功能來編譯穩定的程式碼主體，並將程式碼的編譯狀態儲存在檔案中，然後在後續編譯期間，將先行編譯的程式碼與仍在開發中的程式碼結合。 由於穩定的程式碼不需要重新編譯，因此每個後續編譯的速度會更快。

根據預設，會在 stdafx.h 和 stdafx.cpp 檔案中指定所有先行編譯的程式碼。 除非您取消選取 [先行編譯標頭檔] 選項，否則 [新增專案精靈] 會自動為您建立這些檔案。 如需先行編譯標頭檔的詳細資訊，請參閱[建立先行編譯標頭檔](../build/reference/creating-precompiled-header-files.md)。

## <a name="related-sections"></a>相關章節

如需詳細資訊，請參閱[從 UNIX 移植到 Win32](../porting/porting-from-unix-to-win32.md)。

## <a name="see-also"></a>另請參閱

[建置 C/C++ 程式](../build/building-c-cpp-programs.md)
