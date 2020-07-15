---
title: 逐步解說：在命令列上編譯原生 C++ 程式
description: 從命令提示字元使用 Microsoft c + + 編譯器。
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: 8af104598f56aa6c8eb5a9a87905324700da3d37
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373667"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>逐步解說：在命令列上編譯原生 C++ 程式

Visual Studio 包含命令列 C 和 c + + 編譯器。 您可以使用它來建立從基本主控台應用程式到通用 Windows 平臺應用程式、桌面應用程式、設備磁碟機和 .NET 元件的所有專案。

在本逐步解說中，您會使用文字編輯器來建立基本的 "Hello，World" 樣式 c + + 程式，然後在命令列上進行編譯。 如果您想要嘗試 Visual Studio 的 IDE，而不是使用命令列，請參閱[逐步解說：使用專案和方案（c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 Visual Studio IDE 進行 c + + 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在此逐步解說中，您可以使用自己的 c + + 程式，而不是輸入所顯示的程式。 或者，您可以使用其他說明文章中的 c + + 程式碼範例。

## <a name="prerequisites"></a>先決條件

若要完成此逐步解說，您必須安裝 Visual Studio 和選用的**桌面開發與 c + +** 工作負載，或是 Visual Studio 的命令列組建工具。

Visual Studio 是*整合式開發環境*（IDE）。 它支援許多語言和平臺的功能完整編輯器、資源管理員、偵錯工具和編譯器。 可用的版本包括免費的 Visual Studio Community edition，而且全部都可以支援 C 和 c + + 開發。 如需有關如何下載及安裝 Visual Studio 的詳細資訊，請參閱[在 Visual Studio 中安裝 c + + 支援](vscpp-step-0-installation.md)。

Visual Studio 的組建工具只會安裝您建立 C 和 c + + 程式所需的命令列編譯器、工具和程式庫。 這適用于組建實驗室或教室練習，並以相對快速的方式進行安裝。 若只要安裝命令列工具，請在 [ [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)] 頁面上尋找 Visual Studio 的組建工具。

在您可以在命令列上建立 C 或 c + + 程式之前，請先確認已安裝工具，而且您可以從命令列存取它們。 Visual C++ 具有命令列環境的複雜需求，以尋找所使用的工具、標頭和程式庫。 **您不能在一般的命令提示字元視窗中使用 Visual C++，** 而不需要做一些準備工作。 幸好，Visual C++ 會安裝快捷方式，以啟動已設定命令列組建環境的開發人員命令提示字元。 可惜的是，開發人員命令提示字元快捷方式及其所在位置的名稱，在幾乎每個 Visual C++ 版本和不同的 Windows 版本中都不同。 您的第一個逐步解說工作是尋找要使用的正確一個。

> [!NOTE]
> 開發人員命令提示字元快捷方式會自動設定適用于編譯器和工具，以及任何必要標頭和程式庫的正確路徑。 如果您使用一般的 [**命令提示**字元] 視窗，就必須自行設定這些環境值。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。 建議您使用開發人員命令提示字元快捷方式，而不是自行建立。

### <a name="open-a-developer-command-prompt"></a>開啟開發人員命令提示字元

1. 如果您已在 Windows 10 上安裝 Visual Studio 2017 或更新版本，請開啟 [開始] 功能表，然後選擇 [**所有應用程式**]。 向下並開啟 [ **Visual Studio** ] 資料夾（而不是 Visual Studio 應用程式）。 選擇 [**針對 VS 開發人員命令提示字元**]，開啟 [命令提示字元] 視窗。

   如果您已在 Windows 10 上安裝 Microsoft Visual C++ Build Tools 2015，請開啟 [**開始**] 功能表，然後選擇 [**所有應用程式**]。 向下滾動並開啟 [ **Visual C++ 組建工具**] 資料夾。 選擇 [ **Visual C++ 2015 x86 Native Tools 命令提示字元**] 以開啟 [命令提示字元] 視窗。

   您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇哪一個符合您安裝的 Visual Studio 版本。 使用快捷方式來開啟 [命令提示字元] 視窗。

1. 接下來，確認 Visual C++ 的開發人員命令提示字元已正確設定。 在 [命令提示字元] 視窗中，輸入 `cl` 並確認輸出看起來像這樣：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   目前目錄或版本號碼可能有差異。 這些值取決於 Visual C++ 的版本以及任何已安裝的更新。 如果上述輸出類似于您所看到的內容，則您可以在命令列中建立 C 或 c + + 程式。

   > [!NOTE]
   > 如果您收到錯誤，例如「' cl ' 無法辨識為內部或外部命令、可執行檔程式或批次檔」、「錯誤 C1034 或錯誤 LNK1104，當您執行命令時， **`cl`** 可能是因為您未使用開發人員命令提示字元，或您安裝 Visual C++ 時發生問題。 您必須先修正此問題，才能繼續。

   如果您找不到開發人員命令提示字元快捷方式，或是在輸入時收到錯誤訊息 `cl` ，則您的 Visual C++ 安裝可能會發生問題。 請嘗試重新安裝 Visual Studio 中的 Visual C++ 元件，或重新安裝 Microsoft Visual C++ 組建工具。 請不要進入下一節，直到 **`cl`** 命令運作為止。 如需安裝和疑難排解 Visual C++ 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 視電腦上的 Windows 版本和系統安全性設定而定，您可能必須以滑鼠右鍵按一下開啟 [開發人員命令提示字元] 快捷方式的快捷方式功能表，然後選擇 [以**系統管理員身分執行**]，成功建立並執行您依照本逐步解說所建立的程式。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>建立 Visual C++ 原始程式檔，並在命令列上進行編譯

1. 在 [開發人員命令提示字元] 視窗中，輸入 `md c:\hello` 以建立目錄，然後輸入 `cd c:\hello` 以變更至該目錄。 此目錄是您在其中建立來源檔案和已編譯器的位置。

1. `notepad hello.cpp`在 [命令提示字元] 視窗中輸入。

   當 [記事本] 提示您建立檔案時，選擇 [**是]** 。 此步驟會開啟空白的 [記事本] 視窗，您可以在名為 hello .cpp 的檔案中輸入您的程式碼。

1. 在 [記事本] 中，輸入下列程式程式碼：

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   這段程式碼是一個簡單的程式，會在螢幕上書寫一行文字，然後結束。 若要將錯誤數降至最低，請複製此程式碼，再將其貼到記事本中。

1. 儲存您的工作！ 在 [記事本] 的 [檔案] **** 功能表中，選擇 [儲存] ****。

   恭喜，您已建立可供編譯的 c + + 原始程式檔（即 hello .cpp）。

1. 切換回 [開發人員命令提示字元] 視窗。 在命令提示字元中輸入， `dir` 以列出 c:\hello 目錄的內容。 您應該會在目錄清單中看到來源檔案 hello .cpp，如下所示：

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   您的電腦上的日期和其他詳細資料會有所不同。 如果您沒有看到*您的原始程式碼檔案，請*確定您已變更為您所建立的*c： \\ hello*目錄。 在 [記事本] 中，請確定您已將原始程式檔儲存在此目錄中。 此外，也請確定您已儲存具有副檔名的原始程式碼 *`.cpp`* ，而不是 *`.txt`* 延伸模組。

1. 在開發人員命令提示字元中，輸入 `cl /EHsc hello.cpp` 以編譯您的程式。

   cl.exe 編譯器會產生內含編譯後之程式碼的 .obj 檔案，然後執行連結器，以建立名為 basic.exe 的可執行程式。 此名稱會出現在編譯器所顯示輸出資訊行中。 編譯器的輸出看起來應該像這樣：

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > 如果您收到錯誤，例如「' cl ' 無法辨識為內部或外部命令、可運作的程式或批次檔、錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元並未正確設定。 如需如何修正此問題的相關資訊，請回到**開啟開發人員命令提示**字元一節。

   > [!NOTE]
   > 如果您收到不同的編譯器或連結器錯誤或警告，請檢查您的原始程式碼以更正任何錯誤，然後儲存並再次執行編譯器。 如需特定錯誤的詳細資訊，請使用 [搜尋] 方塊尋找錯誤號碼。

1. 若要執行 hello.exe 程式，請在命令提示字元下，輸入 `hello`。

   程式會顯示下列文字並結束：

   ```Output
   Hello, world, from Visual C++!
   ```

   恭喜，您已使用命令列工具來編譯並執行 c + + 程式。

## <a name="next-steps"></a>後續步驟

這個 "Hello，World" 範例就像 c + + 程式可以取得的一樣簡單。 真實世界的程式通常會有標頭檔、更多的來源檔案，以及程式庫。

您可以使用本逐步解說中的步驟來建立您自己的 c + + 程式碼，而不是輸入所顯示的範例程式碼。 這些步驟也可讓您建立多個在其他地方找到的 c + + 程式碼範例程式。 您可以將原始程式碼放在任何可寫入的目錄中，並建立應用程式。 根據預設，Visual Studio IDE 會在 [*來源 \\ 存放庫*] 子資料夾中，于您的使用者資料夾中建立專案。 較舊的版本可能會將專案放在*檔 \\ Visual Studio \<version> \\ *專案] 資料夾中。

若要編譯具有其他原始程式碼檔案的程式，請在命令列上輸入這些檔案，如下所示：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc`命令列選項會指示編譯器啟用標準 c + + 例外狀況處理行為。 如果沒有它，擲回的例外狀況可能會導致 undestroyed 物件和資源流失。 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](reference/eh-exception-handling-model.md)。

當您提供其他來源檔案時，編譯器會使用第一個輸入檔來建立程式名稱。 在此情況下，它會輸出名為 file1.exe 的程式。 若要將名稱變更為 program1.exe，請新增[/out](reference/out-output-file-name.md)連結器選項：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

若要自動攔截更多程式設計錯誤，建議您使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告層級選項進行編譯：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

編譯器（cl.exe）有更多選項。 您可以將它們套用至組建、優化、程式碼和分析。 如需快速清單，請 `cl /?` 在開發人員命令提示字元中輸入。 您也可以分別編譯和連結，並在更複雜的組建案例中套用連結器選項。 如需編譯器和連結器選項和使用方式的詳細資訊，請參閱[C/c + + 建立參考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和 makefile、MSBuild 和專案檔，或 CMake，在命令列上設定並建立更複雜的專案。 如需使用這些工具的詳細資訊，請參閱[Visual Studio 中的](cmake-projects-in-visual-studio.md) [NMAKE 參考](reference/nmake-reference.md)、 [MSBuild](msbuild-visual-cpp.md)和 CMake 專案。

C 和 c + + 語言類似，但並不相同。 MSVC 編譯器會使用一個簡單的規則，來決定在編譯器代碼時所要使用的語言。 根據預設，MSVC 編譯器會處理以 C 原始程式碼結尾的檔案 *`.c`* ，以及以 *`.cpp`* c + + 原始程式碼結尾的檔案。 若要強制編譯器將所有檔案視為與副檔名無關的 c + +，請使用[/tp](reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

MSVC 編譯器包含符合 ISO C99 標準的 C 執行時間程式庫（CRT），但有次要例外狀況。 可移植程式碼通常會如預期般編譯並執行。 某些過時的程式庫函式和數個 POSIX 函式名稱，已由 MSVC 編譯器取代。 支援函數，但慣用的名稱已變更。 如需詳細資訊，請參閱 CRT 和[編譯器警告（層級3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)[中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[專案與建置系統](projects-and-build-systems-cpp.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
