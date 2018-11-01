---
title: 逐步解說：在命令列上編譯原生 C++ 程式
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: 2d02560f9a76ee6f7a2aa7170f2bca6a95fe3ce8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602250"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>逐步解說：在命令列上編譯原生 C++ 程式

Visual c + + 包含命令列 c + + 編譯器，您可以使用從通用 Windows 平台應用程式的基本主控台應用程式、 傳統型應用程式、 裝置驅動程式和.NET 元件建立的所有項目。

在此逐步解說中，您會建立基本"Hello，World"-使用文字編輯器 中，樣式 c + + 程式，然後在命令列上進行編譯。 如果您想要試用 Visual Studio IDE，而不是使用命令列，請參閱 <<c0> [ 逐步解說： 使用專案和方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或是[使用 Visual Studio IDE 進行 c + + 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在此逐步解說中，您可以使用自己的 Visual C++ 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 Visual C++ 程式碼範例。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說中，您必須已安裝 Visual Studio 和選擇性**使用 c + + 的桌面開發**工作負載或適用於 Visual Studio 命令列建置工具。

Visual Studio 是用於許多語言與平台支援的功能完整的編輯器時，資源管理員、 偵錯工具和編譯器功能強大的整合式的開發環境 (IDE)。 如需如何下載並安裝 Visual Studio 中，包括免費的 Visual Studio Community edition，以及包含適用於 C/c + + 開發的支援資訊，請參閱[Visual Studio 中的安裝 c + + 支援](../build/vscpp-step-0-installation.md)。

Build Tools for Visual Studio 會安裝僅命令列編譯器、 工具和您要建置 C 和 c + + 程式庫。 它非常適合建置實驗室或課堂練習和相對快速安裝。 若要安裝命令列工具，下載[Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721)。

您可以在命令列上建置的 C 或 c + + 程式之前，您必須確認，則會安裝工具，以及您可以從命令列存取它們。 Visual c + + 有複雜需求來尋找工具、 標頭和程式庫，它會使用命令列環境。 **您無法使用 Visual c + + 中的純文字的命令提示字元視窗**而不進行一些準備工作。 幸運的是，Visual c + + 會安裝為您啟動已設定的命令列組建環境的開發人員命令提示字元捷徑。 不幸的是，開發人員命令提示字元捷徑和它們所在的名稱是幾乎每個版本的 Visual c + + 和不同版本的 Windows 中的。 您的第一個逐步解說工作尋找要使用正確的一個。

> [!NOTE]
> 開發人員命令提示字元 捷徑會自動設定編譯器和工具，以及任何必要的標頭和程式庫的正確路徑。 如果您必須設定這些環境值自行使用一般**命令提示字元**視窗。 如需詳細資訊，請參閱 <<c0> [ 設定的路徑和環境變數的命令列建置](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。 我們建議您改用建置您自己的開發人員命令提示字元捷徑。

### <a name="open-a-developer-command-prompt"></a>開啟開發人員命令提示字元

1. 如果您已安裝 Visual Studio 2017 在 Windows 10 上，開啟 [開始] 功能表並選擇**所有應用程式**。 向下捲動並開啟**Visual Studio 2017**資料夾 （而不的 Visual Studio 2017 應用程式）。 選擇**適用於 VS 2017 開發人員命令提示字元**以開啟 [命令提示字元] 視窗。

   如果您已安裝 Microsoft Visual c + + Build Tools 2015 在 Windows 10 上，開啟**開始**功能表，然後選擇**所有應用程式**。 向下捲動並開啟**Visual c + + Build Tools**資料夾。 選擇**Visual c + + 2015 x86 Native Tools 命令提示字元**以開啟 [命令提示字元] 視窗。

   如果您使用不同版本的 Visual Studio，或執行不同版本的 Windows，在 開始 功能表中尋找，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows 搜尋函式來搜尋 「 開發人員命令提示字元 並選擇符合您已安裝的 Visual Studio 版本的其中一個。 使用捷徑來開啟 [命令提示字元] 視窗。

1. 接下來，確認 Visual c + + 開發人員命令提示字元已正確設定。 在 [命令提示字元] 視窗中，輸入`cl`並確認，輸出看起來像這樣：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   可能會有目前的目錄或版本號碼，並根據 Visual c + + 和安裝任何更新的版本中的差異。 如果您看到類似上述的輸出，您便準備好要建置以 C 或 c + + 程式，在命令列。

   > [!NOTE]
   > 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，當您執行**cl**命令，則可能您不使用開發人員命令提示字元，或有問題的 Visual c + + 的安裝。 您可以繼續之前，您必須修正此問題。

   如果您找不到開發人員命令提示字元 捷徑，或如果您收到錯誤訊息，當您輸入`cl`，則您的 Visual c + + 安裝可能會有問題。 請嘗試重新安裝 Visual c + + 元件，在 Visual Studio 中，或重新安裝 Microsoft Visual c + + Build Tools。 不要繼續進行下一節直到其運作方式。 如需有關安裝和疑難排解 Visual c + + 的詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根據電腦和系統安全性設定上的 Windows 版本，您可能必須按一下滑鼠右鍵以開啟 開發人員命令提示字元捷徑的捷徑功能表，然後選擇**系統管理員身分執行**至已成功建置並執行您依照本逐步解說中建立的程式。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>建立 Visual c + + 原始程式檔，並在命令列上編譯

1. 在 [開發人員命令提示字元] 視窗中，輸入`md c:\hello`來建立目錄，然後輸入`cd c:\hello`變更至該目錄。 此目錄會是原始程式檔和已編譯的程式中建立位置。

1. 輸入`notepad hello.cpp`在命令提示字元 視窗中。

   選擇**是**當 [記事本] 會提示您建立的檔案。 此步驟會開啟空白的 [記事本] 視窗，供您輸入您的程式碼，在名為 basic.cpp。

1. 在記事本中，輸入下列程式碼行：

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   此程式碼是簡單的程式，將會在螢幕上書寫一行文字，然後結束。 若要將錯誤數降至最低，請複製此程式碼，再將其貼到記事本中。

1. 儲存您的工作！ 在 [記事本] 的 [檔案]  功能表中，選擇 [儲存] 。

   恭喜，您已建立 Visual c + + 原始程式檔，hello.cpp，準備好要編譯的。

1. 切換回 [開發人員命令提示字元] 視窗。 輸入`dir`在命令提示字元，若要列出 c:\hello 目錄的內容。 您應該會看到在目錄清單中，看起來像是來源檔案 hello.cpp:

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

   日期，以及其他詳細資料會在您的電腦上的不同。 如果您沒有看到您的原始程式碼檔，hello.cpp，請確定您已變更為您所建立的 c:\hello 目錄，並在 [記事本]，請確定您在此目錄中儲存原始程式檔。 也請確定您儲存的原始碼，副檔名為.cpp 檔案名稱，不使用副檔名.txt。

1. 在開發人員命令提示字元中，輸入`cl /EHsc hello.cpp`編譯您的程式。

   cl.exe 編譯器會產生內含編譯後之程式碼的 .obj 檔案，然後執行連結器，以建立名為 basic.exe 的可執行程式。 此名稱會出現在編譯器所顯示輸出資訊行中。 編譯器的輸出應該看起來像：

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
   > 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元未正確設定。 如需如何修正此問題的資訊，請回到**開啟開發人員命令提示字元**一節。

   > [!NOTE]
   > 如果您收到不同的編譯器或連結器錯誤或警告，請檢閱您的程式碼，以更正任何錯誤，然後將它儲存，並再次執行編譯器。 如需特定錯誤的資訊，此 MSDN 頁面上使用搜尋方塊尋找的錯誤號碼。

1. 若要執行 hello.exe 程式，請在命令提示字元下，輸入 `hello`。

   程式會顯示下列文字並結束：

   ```Output
   Hello, world, from Visual C++!
   ```

   恭喜，您已經編譯並執行 c + + 程式所使用的命令列工具。

## <a name="next-steps"></a>後續步驟

這個"Hello，World"範例是簡單的 c + + 程式可以取得。 真實世界的程式有標頭檔和多個原始程式檔，在程式庫，連結，並執行有用的工作。

您可以使用在本逐步解說的步驟，來建置您自己的 c + + 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建置許多 c + + 程式碼的範例程式，您在其他地方找到。 您可以將您的原始程式碼，並建置您的應用程式，在任何可寫入的目錄中。 根據預設，Visual Studio IDE 會在文件 資料夾中名為您的 Visual Studio 版本適用的 Visual Studio 資料夾的專案子資料夾中建立專案。

若要編譯程式的其他原始程式碼檔，輸入所有命令列上，例如：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` 命令列選項會指示編譯器啟用 C++ 例外狀況處理。 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](../build/reference/eh-exception-handling-model.md)。

當您提供其他原始程式檔時，編譯器會使用第一個輸入的檔來建立程式名稱。 在此情況下，它會輸出稱為 file1.exe 程式。 若要將名稱變更為 program1.exe，新增[/out](../build/reference/out-output-file-name.md)連結器選項：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

自動攔截更多的程式設計錯誤，我們建議您編譯使用其中一種[/w3](../build/reference/compiler-option-warning-level.md)或是[/w4](../build/reference/compiler-option-warning-level.md)警告層級的選項：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

編譯器、 cl.exe，有許多更多選項，您可以套用於建置、 最佳化、 偵錯和分析您的程式碼。 如需快速的清單中，輸入`cl /?`在開發人員命令提示字元。 您也可以編譯和連結個別，套用在更複雜的建置案例的連結器選項。 如需有關編譯器和連結器選項，以及使用方式的詳細資訊，請參閱 < [C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)。

若要設定及命令列上建置更複雜的專案，您可以使用 NMAKE 和 makefile 或 MSBuild 和專案檔。 如需有關如何使用這些工具的詳細資訊，請參閱 < [NMAKE 參考](../build/nmake-reference.md)並[MSBuild](../build/msbuild-visual-cpp.md)。

C 和 c + + 語言很類似，但不是相同。 Visual c + + 編譯器會使用簡單的規則來決定要編譯您的程式碼時所使用的語言。 根據預設，Visual C++ 編譯器會將以 .c 結尾的所有檔案都視為 C 原始程式碼，並會將以 .cpp 結尾的所有檔案都視為 C++ 原始程式碼。 若要強制編譯器將視為 c + + 檔案名稱的擴充功能上的非依存的所有檔案，請使用[/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

Visual c + + 編譯器包含 C 執行階段程式庫 (CRT) 相容於 ISO C99 標準，但不會完全遵循網路標準。 在大部分情況下，可攜式程式碼會編譯，並如預期般執行。 Visual c + + 不支援的 CRT 變更一些 ISO C11 中。 Visual c + + 編譯器已被取代特定的程式庫函式和 POSIX 函式名稱。 支援的函式，但是慣用的名稱已變更。 如需詳細資訊，請參閱 < [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)並[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)<br/>
[編譯器選項](../build/reference/compiler-options.md)
