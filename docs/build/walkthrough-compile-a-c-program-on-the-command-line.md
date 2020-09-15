---
title: 逐步解說：在命令列編譯 C 程式
description: 說明如何建立簡單 Hello World 樣式 C 程式的逐步解說。
ms.custom: conceptual
ms.date: 9/10/2020
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 57276f61ca8ff848db0313935bc1841de50f9874
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075604"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>逐步解說：在命令列編譯 C 程式

Visual C++ 包含 C 編譯器，可讓您用來建立基本主控台程式的所有專案，以及完整的 Windows 傳統型應用程式、行動應用程式等等。

本逐步解說示範如何使用文字編輯器來建立基本的 "Hello，World" 樣式 C 程式，然後在命令列上進行編譯。 如果您想要在命令列上使用 c + +，請參閱 [逐步解說：在命令列上編譯原生 c + + 程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果您想要嘗試 Visual Studio IDE，而不是使用命令列，請參閱 [逐步解說：使用專案和方案 (c + +) ](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 或 [使用 Visual Studio IDE 進行 c + + 桌面開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須安裝 Visual Studio 和選用的 Visual C++ 元件，或適用于 Visual Studio 的組建工具。

Visual Studio 是功能強大的整合式開發環境，可針對許多語言和平臺支援功能完整的編輯器、資源管理員、偵錯工具和編譯器。 如需這些功能的詳細資訊，以及如何下載及安裝 Visual Studio （包括 free Visual Studio Community edition）的詳細資訊，請參閱 [安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

Visual Studio 版 Visual Studio 的 Build Tools 只會安裝您建立 C 和 c + + 程式所需的命令列工具組、編譯器、工具和程式庫。 它很適合用於組建實驗室或教室練習，而且安裝速度相對較快。 若只要安裝命令列工具組，請從 [Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) 下載] 頁面下載 Visual Studio 的 Build Tools，然後執行安裝程式。 在 Visual Studio 安裝程式中，選取 [ **c + + build tools** ] 工作負載，然後選擇 [ **安裝**]。

在命令列上建立 C 或 c + + 程式之前，您必須先確認已安裝工具，而且您可以從命令列存取這些工具。 Visual C++ 針對命令列環境具有複雜的需求，以尋找其使用的工具、標頭和程式庫。 **您不能在一般的命令提示字元視窗中使用 Visual C++，** 而不需要進行一些準備工作。 您需要 *開發人員命令提示* 字元視窗，也就是已設定所有必要環境變數的一般命令提示字元視窗。 幸運的是，Visual C++ 會安裝快捷方式，讓您啟動已為命令列組建設定環境的開發人員命令提示字元。 可惜的是，開發人員命令提示字元快捷方式的名稱以及它們所在的位置，在幾乎每個版本的 Visual C++ 和不同版本的 Windows 上都不同。 第一個逐步解說工作是尋找要使用的正確快捷方式。

> [!NOTE]
> 開發人員命令提示字元快捷方式會自動設定編譯器和工具以及任何必要標頭和程式庫的正確路徑。 每個組建設定的其中一些值都不同。 如果您未使用其中一個快捷方式，您必須自行設定這些環境值。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。 由於組建環境很複雜，因此強烈建議您使用開發人員命令提示字元快捷方式，而不是建立您自己的。

這些指示會依您使用的 Visual Studio 版本而有所不同。 若要查看您慣用 Visual Studio 版本的檔，請使用 **版本** 選擇器控制項。 您可在此頁面的目錄頂端找到此檔案。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 中開啟開發人員命令提示字元

如果您已在 Windows 10 上安裝 Visual Studio 2019，請開啟 [開始] 功能表，然後向下並開啟 **Visual Studio 2019** 資料夾， (Visual Studio) 2019 應用程式。 選擇 [ **VS 2019 開發人員命令提示字元** ] 以開啟 [命令提示字元] 視窗。

如果您使用的是不同版本的 Windows，請在 [開始] 功能表或 [開始] 頁面中，尋找包含開發人員命令提示字元快捷方式的 Visual Studio 工具資料夾。 您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇符合已安裝之 Visual Studio 版本的命令提示字元。 使用快速鍵來開啟 [命令提示字元] 視窗。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟開發人員命令提示字元

如果您已在 Windows 10 上安裝 Visual Studio 2017，請開啟 [開始] 功能表，然後向下並開啟 **Visual Studio 2017** 資料夾， (Visual Studio) 2017 應用程式。 選擇 [ **VS 2017 開發人員命令提示字元** ] 以開啟 [命令提示字元] 視窗。

如果您執行的是不同版本的 Windows，請在 [開始] 功能表或 [開始] 頁面中，尋找包含開發人員命令提示字元快捷方式的 Visual Studio 工具資料夾。 您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇符合已安裝之 Visual Studio 版本的命令提示字元。 使用快速鍵來開啟 [命令提示字元] 視窗。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>在 Visual Studio 2015 中開啟開發人員命令提示字元

如果您已在 Windows 10 上安裝 Microsoft Visual C++ Build Tools 2015，請開啟 [開始] 功能表，然後按 [ **開始** ] 功能表，並開啟 [ **Visual C++ Build tools** ] 資料夾。 選擇 **Visual C++ 2015 x86 Native Tools 命令提示字元** 以開啟 [命令提示字元] 視窗。

如果您執行的是不同版本的 Windows，請在 [開始] 功能表或 [開始] 頁面中，尋找包含開發人員命令提示字元快捷方式的 Visual Studio 工具資料夾。 您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇符合已安裝之 Visual Studio 版本的命令提示字元。 使用快速鍵來開啟 [命令提示字元] 視窗。

::: moniker-end

接下來，確認已正確設定 Visual C++ 開發人員命令提示字元。 在 [命令提示字元] 視窗中，輸入 `cl` 並確認輸出看起來像這樣：

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

根據 Visual C++ 版本和安裝的任何更新，目前的目錄或版本號碼可能會有差異。 如果上述輸出與您看到的類似，您就可以在命令列中建立 C 或 c + + 程式。

> [!NOTE]
> 如果您收到錯誤，例如「' cl ' 無法辨識為內部或外部命令、可執行檔程式或批次檔」、「錯誤 C1034，或是當您執行 **cl** 命令時發生錯誤 LNK1104，則表示您不是使用開發人員命令提示字元，或您的 Visual C++ 安裝有問題。 您必須修正此問題，才能繼續進行。

如果您找不到開發人員命令提示字元快捷方式，或在您輸入時收到錯誤訊息 `cl` ，表示您的 Visual C++ 安裝可能發生問題。 如果您使用的是 Visual Studio 2017 或更新版本，請嘗試在 Visual Studio 安裝程式中 **使用 c + +** 工作負載來重新安裝桌面開發。 如需詳細資訊，請參閱 [在 Visual Studio 中安裝 c + + 支援](vscpp-step-0-installation.md)。 或者，從 Visual Studio 的 [ [下載](https://visualstudio.microsoft.com/downloads/) ] 頁面重新安裝 Build Tools。 請不要繼續進行下一節，直到這樣才能運作。 如需有關安裝和疑難排解 Visual Studio 的詳細資訊，請參閱 [安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 視電腦上的 Windows 版本和系統安全性設定而定，您可能必須以滑鼠右鍵按一下來開啟 [開發人員命令提示字元] 快捷方式的快捷方式功能表，然後選擇 [以 **系統管理員身分執行** ]，以依照本逐步解說的指示，成功建立並執行您所建立的程式。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>建立 C 原始程式檔並在命令列上進行編譯

1. 在開發人員命令提示字元視窗中，輸入 `cd c:\` 以將目前的工作目錄變更為 C：磁片磁碟機的根目錄。 接著，輸入 `md c:\simple` 以建立目錄，然後輸入 `cd c:\simple` 以變更至該目錄。 此目錄將會保存您的原始程式檔和編譯的程式。

1. `notepad simple.c`在開發人員命令提示字元中輸入。 在快顯的 [記事本警示] 對話方塊中，選擇 [ **是]** ，在您的工作目錄中建立新的簡單 .c 檔。

1. 在 [記事本] 中，輸入下列程式程式碼：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在 [記事本] 功能表列上 **，選擇 [** 檔案  >  **儲存**]，在您的工作目錄中儲存 simple. c。

1. 切換回開發人員命令提示字元視窗。 在命令提示字元中輸入， `dir` 以列出 c:\simple 目錄的內容。 您應該會在目錄清單中看到原始檔 simple. c，如下所示：

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   日期和其他詳細資料將會在您的電腦上有所不同。 如果您沒有看到您的原始程式碼檔案，請確定您已變更為所建立的 c:\simple 目錄，然後在 [記事本] 中，確定已將原始程式檔儲存在此目錄中。 此外，請確定您已儲存副檔名為 .c 的原始程式碼，而不是副檔名 .txt。

1. 若要編譯您的程式，請 `cl simple.c` 在開發人員命令提示字元中輸入。

   您可以在編譯器顯示的輸出資訊行中查看可執行程式名稱 simple.exe：

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > 如果您收到錯誤，例如「' cl ' 無法辨識為內部或外部命令、可操作的程式或批次檔」、「錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元未正確設定。 如需如何修正此問題的詳細資訊，請返回 [ **開啟開發人員命令提示** 字元] 一節。

   > [!NOTE]
   > 如果您收到不同的編譯器或連結器錯誤或警告，請檢查原始程式碼以更正任何錯誤，然後儲存並重新執行編譯器。 如需特定錯誤的詳細資訊，請使用此頁面頂端的 [搜尋] 方塊來尋找錯誤號碼。

1. 若要執行程式，請 `simple` 在命令提示字元中輸入。

   程式會顯示下列文字並結束：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜，您已使用命令列編譯並執行 C 程式。

## <a name="next-steps"></a>後續步驟

這個「Hello，World」範例就像 C 程式可以取得的一樣簡單。 真實世界的程式具有標頭檔和更多原始程式檔、程式庫中的連結，以及執行有用的工作。

您可以使用本逐步解說中的步驟來建立您自己的 C 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建立許多您在其他地方找到的 C 程式碼範例程式。 若要編譯具有其他原始程式碼檔的程式，請在命令列上全部輸入，如下所示：

`cl file1.c file2.c file3.c`

編譯器會輸出稱為 file1.exe 的程式。 若要將名稱變更為 program1.exe，請新增 [/out](reference/out-output-file-name.md) 連結器選項：

`cl file1.c file2.c file3.c /link /out:program1.exe`

若要自動捕捉更多程式設計錯誤，建議您使用 [/W3](reference/compiler-option-warning-level.md) 或 [/W4](reference/compiler-option-warning-level.md) 警告層級選項進行編譯：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

編譯器 cl.exe 有更多選項可供您用來建立、優化、偵測及分析您的程式碼。 如需快速清單，請 `cl /?` 在開發人員命令提示字元中輸入。 您也可以在更複雜的組建案例中，個別編譯和連結並套用連結器選項。 如需編譯器和連結器選項和使用方式的詳細資訊，請參閱  [c/c + + 建立參考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和 makefile，或是 MSBuild 和專案檔，在命令列上設定和建立更複雜的專案。 如需使用這些工具的詳細資訊，請參閱 [NMAKE 參考](reference/nmake-reference.md) 和 [MSBuild](msbuild-visual-cpp.md)。

C 和 c + + 語言很類似，但不同。 Microsoft C/c + + 編譯器 (MSVC) 使用簡單的規則來決定要在編譯器代碼時使用的語言。 根據預設，MSVC 編譯器會將以 .c 結尾的所有檔案視為 C 原始程式碼，並將以 .cpp 結尾的所有檔案視為 c + + 原始程式碼。 若要強制編譯器將所有檔案視為 C 非相依的副檔名，請使用 [/tc](reference/tc-tp-tc-tp-specify-source-file-type.md) 編譯器選項。

MSVC 與 ISO C99 standard 相容，但不完全符合規範。 在大部分的情況下，可移植的 C 程式碼會如預期般編譯和執行。 Visual C++ 針對 ISO C11/C17 中的變更提供支援。 若要使用 C11/C17 支援進行編譯，請使用編譯器旗標 `/std:c11` 或 `/std:c17` 。 MSVC 會取代某些程式庫函式和 POSIX 函數名稱。 支援函式，但慣用的名稱已變更。 如需詳細資訊，請參閱 [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md) 和 [編譯器警告 (層級 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>另請參閱

[逐步解說：建立標準 C++ 程式 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 語言參考](../c-language/c-language-reference.md)<br/>
[專案與建置系統](projects-and-build-systems-cpp.md)<br/>
[相容性](../c-runtime-library/compatibility.md)
