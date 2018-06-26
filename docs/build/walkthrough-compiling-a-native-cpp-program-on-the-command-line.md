---
title: 逐步解說： 編譯原生 c + + 程式命令列上 |Microsoft 文件
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb0d7aab8000febdf07288370da058f437767387
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322429"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>逐步解說：在命令列上編譯原生 C++ 程式

Visual c + + 包含命令列的 c + + 編譯器可讓您建立的所有項目從基本的主控台應用程式通用 Windows 平台應用程式、 傳統型應用程式、 裝置驅動程式和.NET 元件。

在本逐步解說，您會建立"Hello，World"的基本-樣式 c + + 程式，使用文字編輯器 中，，然後在命令列進行編譯。 如果您想要再試一次 Visual Studio IDE，而不是使用命令列，請參閱[逐步解說： 使用專案和方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在此逐步解說中，您可以使用自己的 Visual C++ 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 Visual C++ 程式碼範例。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須已安裝 Visual Studio 和選擇性**的 c + + 桌面應用程式開發**工作負載或適用於 Visual Studio 命令列建置工具。

Visual Studio 為許多語言和平台支援全功能的編輯器，資源管理員，、 偵錯工具和編譯器的功能強大的整合式的開發環境 (IDE)。 如需如何下載並安裝 Visual Studio，包括免費的 Visual Studio Community 版本，以及包含對 C/c + + 開發的支援資訊，請參閱[安裝 c + + 支援 Visual Studio 中的](../build/vscpp-step-0-installation.md)。

Build Tools for Visual Studio 只會安裝命令列編譯器、 工具和您要建立 C 和 c + + 程式庫。 它非常適合組建實驗室或教室會執行，並會安裝相當快速。 若要只安裝命令列工具，下載[建置工具的 Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721)。

您可以在命令列上建置 C 或 c + + 程式之前，您必須確認確認已安裝的工具，以及您可以從命令列存取它們。 Visual c + + 為了尋找工具、 標頭和程式庫，它會使用具有複雜的命令列環境的需求。 **您無法使用 Visual c + + 中的純文字的命令提示字元視窗**而不會進行一些準備工作。 幸運的是，Visual c + + 會安裝為您啟動已設定為命令列組建環境開發人員命令提示字元捷徑。 不幸的是，開發人員命令提示字元 捷徑，和它們的所在位置的名稱是幾乎每個版本的 Visual c + +，並在不同版本的 Windows 中。 您的第一個逐步解說工作發現正確的其中一個使用。

> [!NOTE]
> 開發人員命令提示字元捷徑會自動設定編譯器和工具，以及任何必要的標頭和程式庫的正確路徑。 您必須設定這些環境值自行如果您使用一般的命令提示字元視窗。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。 我們建議您使用而非建立您自己的開發人員命令提示字元捷徑。

### <a name="open-a-developer-command-prompt"></a>開啟開發人員命令提示字元

1. 如果您已安裝 Visual Studio 2017 Windows 10 上，開啟 開始 功能表，然後選擇 **所有應用程式**。 向下捲動並開啟**Visual Studio 2017**資料夾 （不 Visual Studio 2017 應用程式）。 選擇**VS 2017 的開發人員命令提示字元**以開啟命令提示字元視窗。

   如果您已安裝 Microsoft Visual c + + 建置工具 2015 Windows 10 上，開啟**啟動**功能表，然後選擇 **所有應用程式**。 向下捲動並開啟**Visual c + + 建置工具**資料夾。 選擇**Visual c + + 2015 x86 Native Tools 命令提示字元**以開啟命令提示字元視窗。

   如果您使用不同版本的 Visual Studio，或是執行不同版本的 Windows，尋找您的 開始 功能表中，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows search 函數來搜尋 」 開發人員命令提示字元，然後選擇符合您的 Visual Studio 安裝的版本。 使用捷徑來開啟 [命令提示字元] 視窗。

2. 接下來，確認 Visual c + + 開發人員命令提示字元已正確設定。 在命令提示字元 視窗中，輸入`cl`並確認輸出看起來像下面這樣：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   可能會有差異，在目前的目錄或版本號碼，視 Visual c + + 和安裝任何更新的版本而定。 如果這是類似您所看到的內容，則您必須準備好要建置 C 或 c + + 程式，在命令列。

   > [!NOTE]
   > 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，當您執行**cl**命令時，則可能您不使用開發人員命令提示字元，或有問題的 Visual c + + 安裝。 您必須先修正此問題，然後才能繼續。

   如果您找不到開發人員命令提示字元 捷徑，或如果您收到錯誤訊息，當您輸入`cl`，Visual c + + 安裝可能會有問題。 請嘗試重新安裝 Visual c + + 元件，在 Visual Studio 中，或重新安裝 Microsoft Visual c + + 建置工具。 不要繼續進行下一節之前可以這麼做。 如需安裝和 Visual c + + 疑難排解的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根據電腦等系統安全性設定的 Windows 版本，您可能必須按一下滑鼠右鍵以開啟 開發人員命令提示字元捷徑的捷徑功能表，然後選擇**系統管理員身分執行**至已成功建置並執行您依照本逐步解說建立的程式。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>建立 Visual c + + 原始程式檔和命令列上進行編譯

1. 在 [開發人員命令提示字元] 視窗中，輸入**md c:\hello**建立的目錄，然後輸入**cd c:\hello**變更到該目錄。 這是原始程式檔和編譯的程式所建立的目錄。

2. 輸入**notepad basic.cpp**在命令提示字元 視窗中。

   選擇**是**當 [記事本] 會提示您建立的檔案。 這會開啟空白的 [記事本] 視窗，讓您在名為 hello.cpp 檔案中輸入您的程式碼。

3. 在記事本中，輸入下列程式碼：

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   這是非常簡單的程式，會在螢幕上書寫一行文字，然後結束。 若要將錯誤數降至最低，請複製此程式碼，再將其貼到記事本中。

4. 儲存您的工作！ 在 [記事本] 的 [檔案]  功能表中，選擇 [儲存] 。

   恭喜，您已建立 Visual c + + 原始程式檔 hello.cpp 準備好要編譯的。

5. 切換回開發人員命令提示字元視窗。 輸入**dir**在命令提示字元中列出 c:\hello 目錄的內容。 您應該會看到類似如下的目錄清單中的來源檔案 hello.cpp:

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

   日期及其他詳細資料會不同於您的電腦。 如果您沒有看到您的原始程式碼檔，請確定您已變更至您所建立，c:\hello 目錄 hello.cpp，並在 [記事本]，請確定您在此目錄中儲存原始程式檔。 也請確定您儲存的原始程式碼以.cpp 檔案名稱副檔名，不副檔名為.txt。

6. 在開發人員命令提示字元中輸入`cl /EHsc hello.cpp`編譯您的程式。

   cl.exe 編譯器會產生內含編譯後之程式碼的 .obj 檔案，然後執行連結器，以建立名為 basic.exe 的可執行程式。 此名稱會出現在編譯器所顯示輸出資訊行中。 編譯器的輸出類似如下：

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
   > 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元未正確設定。 如需如何修正此問題的資訊，請回到**開啟開發人員命令提示字元**> 一節。

   > [!NOTE]
   > 如果您收到不同的編譯器或連結器錯誤或警告，請檢閱您的原始程式碼，更正任何錯誤，然後加以儲存，並再次執行編譯器。 如需特定錯誤的資訊，此 MSDN 頁面上使用 [搜尋] 方塊尋找錯誤號碼。

7. 若要執行 hello.exe 程式，請在命令提示字元下，輸入 `hello`。

   程式會顯示下列文字並結束：

   ```Output
   Hello, world, from Visual C++!
   ```

   恭喜，您只編譯並執行 c + + 程式，使用命令列工具。

## <a name="next-steps"></a>後續步驟

這個"Hello，World"範例是大約像簡單的 c + + 程式可以取得。 真實世界的程式有標頭檔和多個原始程式檔，在程式庫，連結，然後執行有用的工作。

您可以使用在本逐步解說的步驟來建置您自己的 c + + 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建立許多 c + + 程式碼的範例程式，您會發現其他位置。 您可以將您的原始程式碼和建置您的應用程式中任何可寫入的目錄。 根據預設，Visual Studio IDE 會在文件 資料夾中名為您的 Visual Studio 版本的 Visual Studio 資料夾專案子資料夾中建立專案。

若要編譯的程式有多個原始程式碼檔，請在命令列中，像這樣中輸入：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

**/EHsc** 命令列選項會指示編譯器啟用 C++ 例外狀況處理。 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](../build/reference/eh-exception-handling-model.md)。

當您提供像這樣的多個來源檔案時，編譯器會使用第一個輸入的檔來建立程式名稱。 在此情況下，它會輸出名 file1.exe 程式。 若要變更 program1.exe 名稱，加入[/out](../build/reference/out-output-file-name.md)連結器選項：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

以自動擷取更多的程式設計錯誤，我們建議您編譯使用[/W3](../build/reference/compiler-option-warning-level.md)或[/W4](../build/reference/compiler-option-warning-level.md)警告層級的選項：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

編譯器，cl.exe，有許多其他選項，您可以套用建置、 最佳化、 偵錯及分析您的程式碼。 如需快速的清單中，輸入**cl /？** 在開發人員命令提示字元。 您也可以編譯和個別連結，連結器選項建置更複雜的案例中套用。 如需有關編譯器和連結器選項和使用方式的詳細資訊，請參閱[C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)。

您可以使用 NMAKE makefile 或 MSBuild 和專案檔來設定和在命令列上建置更複雜的專案。 如需有關使用這些工具的詳細資訊，請參閱[NMAKE 參考](../build/nmake-reference.md)和[MSBuild](../build/msbuild-visual-cpp.md)。

C 和 c + + 語言非常類似，但不是相同。 Visual c + + 編譯器會使用簡單的規則來決定在編譯程式碼時使用的語言。 根據預設，Visual C++ 編譯器會將以 .c 結尾的所有檔案都視為 C 原始程式碼，並會將以 .cpp 結尾的所有檔案都視為 C++ 原始程式碼。 若要強制編譯器忽視副檔名將所有的檔案都視為 c + +，請使用[/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

Visual c + + 編譯器包含 C 執行階段程式庫 (CRT) 相容 ISO C99 標準，但不完全相容。 在大部分情況下，可攜式程式碼會編譯，並如預期般執行。 Visual c + + 不支援的 CRT 變更某些 ISO C11 中。 Visual c + + 編譯器已被取代特定的程式庫函式和 POSIX 函式名稱。 支援的函式，但慣用的名稱已變更。 如需詳細資訊，請參閱[CRT 中安全性功能](../c-runtime-library/security-features-in-the-crt.md)和[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)  
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)  
[編譯器選項](../build/reference/compiler-options.md)  
