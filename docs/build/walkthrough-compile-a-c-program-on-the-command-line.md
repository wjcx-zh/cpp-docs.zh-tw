---
title: 逐步解說：在命令列上編譯 C 程式
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335255"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>逐步解說：在命令列上編譯 C 程式

Visual C++ 包含 C 編譯器，可讓您用來建立從基本主控台程式到完整 Windows 桌面應用程式、行動應用程式等專案的所有內容。

本逐步解說示範如何使用文字編輯器來建立基本的 "Hello，World" 樣式 C 程式，然後在命令列上進行編譯。 如果您想要在命令列上使用 c + +，請參閱[逐步解說：在命令列上編譯原生 c + + 程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果您想要嘗試 Visual Studio 的 IDE，而不是使用命令列，請參閱[逐步解說：使用專案和方案（c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 Visual Studio IDE 進行 c + + 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須安裝 Visual Studio 和選用的 Visual C++ 元件，或 Visual Studio 的組建工具。

Visual Studio 是功能強大的整合式開發環境，可支援許多語言和平臺的完整功能編輯器、資源管理員、偵錯工具和編譯器。 如需這些功能的詳細資訊，以及如何下載和安裝 Visual Studio，包括免費的 Visual Studio Community 版本，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

Visual Studio 版 Visual Studio 的組建工具只會安裝命令列工具組、編譯器、工具，以及建立 C 和 c + + 程式所需的程式庫。 這適用于組建實驗室或教室練習，並以相對快速的方式進行安裝。 若只要安裝命令列工具組，請從 [ [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)] 頁面下載 Visual Studio 的組建工具，然後執行安裝程式。 在 Visual Studio 安裝程式中，選取 [ **c + + build tools** ] 工作負載，然後選擇 [**安裝**]。

在您可以在命令列上建立 C 或 c + + 程式之前，您必須先確認工具已安裝，而且您可以從命令列存取它們。 Visual C++ 具有命令列環境的複雜需求，以尋找所使用的工具、標頭和程式庫。 **在純文字命令提示字元視窗中，您無法使用 Visual C++，** 而不需要進行一些準備。 您需要 [*開發人員命令提示*字元] 視窗，這是一般的 [命令提示字元] 視窗，其中已設定所有必要的環境變數。 幸好，Visual C++ 會安裝快捷方式，以啟動已設定命令列組建之環境的開發人員命令提示字元。 可惜的是，開發人員命令提示字元快捷方式及其所在位置的名稱，在幾乎每個 Visual C++ 版本和不同的 Windows 版本中都不同。 您的第一個逐步解說工作是尋找要使用的正確快捷方式。

> [!NOTE]
> 開發人員命令提示字元快捷方式會自動設定適用于編譯器和工具，以及任何必要標頭和程式庫的正確路徑。 其中有些值對每個組建設定都不同。 如果您不使用其中一個快捷方式，就必須自行設定這些環境值。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。 由於組建環境很複雜，因此強烈建議您使用開發人員命令提示字元快捷方式，而不是自行建立。

這些指示會根據您使用的 Visual Studio 版本而有所不同。 若要查看您慣用版本 Visual Studio 的檔，請使用**版本**選取器控制項。 您可在此頁面的目錄頂端找到該檔案。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 中開啟開發人員命令提示字元

如果您已在 Windows 10 上安裝 Visual Studio 2019，請開啟 [開始] 功能表，然後向下滾動並開啟 [ **Visual Studio 2019** ] 資料夾（而不是 Visual Studio 2019 應用程式）。 選擇 [**適用于 VS 2019 的開發人員命令提示字元**] 以開啟 [命令提示字元] 視窗。

如果您使用的是不同版本的 Windows，請在 [開始] 功能表或 [起始頁] 中，尋找包含開發人員命令提示字元快捷方式的 Visual Studio 工具] 資料夾。 您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇哪一個符合您安裝的 Visual Studio 版本。 使用快捷方式來開啟 [命令提示字元] 視窗。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>在 Visual Studio 2017 中開啟開發人員命令提示字元

如果您已在 Windows 10 上安裝 Visual Studio 2017，請開啟 [開始] 功能表，然後向下滾動並開啟 [ **Visual Studio 2017** ] 資料夾（而不是 Visual Studio 2017 應用程式）。 選擇 [**適用于 VS 2017 的開發人員命令提示字元**] 以開啟 [命令提示字元] 視窗。

如果您執行的是不同版本的 Windows，請在 [開始] 功能表或 [起始頁] 中，尋找包含開發人員命令提示字元快捷方式的 Visual Studio 工具] 資料夾。 您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇哪一個符合您安裝的 Visual Studio 版本。 使用快捷方式來開啟 [命令提示字元] 視窗。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>在 Visual Studio 2015 中開啟開發人員命令提示字元

如果您已在 Windows 10 上安裝 Microsoft Visual C++ Build Tools 2015，請開啟 [**開始**] 功能表，然後向下滾動並開啟 [ **Visual C++ 組建工具**] 資料夾。 選擇 [ **Visual C++ 2015 x86 Native Tools 命令提示字元**] 以開啟 [命令提示字元] 視窗。

如果您執行的是不同版本的 Windows，請在 [開始] 功能表或 [起始頁] 中，尋找包含開發人員命令提示字元快捷方式的 Visual Studio 工具] 資料夾。 您也可以使用 Windows 搜尋函式來搜尋「開發人員命令提示字元」，並選擇哪一個符合您安裝的 Visual Studio 版本。 使用快捷方式來開啟 [命令提示字元] 視窗。

::: moniker-end

接下來，確認 Visual C++ 的開發人員命令提示字元已正確設定。 在 [命令提示字元] 視窗`cl`中，輸入並確認輸出看起來像這樣：

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

根據 Visual C++ 版本和任何安裝的更新而定，目前目錄或版本號碼可能會有所不同。 如果上述輸出類似于您所看到的內容，則您可以在命令列中建立 C 或 c + + 程式。

> [!NOTE]
> 如果您收到錯誤，例如「' cl ' 無法辨識為內部或外部命令、可執行檔程式或批次檔」、「錯誤 C1034 或錯誤 LNK1104，當您執行**cl**命令時，可能是因為您未使用開發人員命令提示字元，或安裝 Visual C++ 時發生問題。 您必須先修正此問題，才能繼續。

如果您找不到開發人員命令提示字元快捷方式，或是在輸入`cl`時收到錯誤訊息，則您的 Visual C++ 安裝可能會發生問題。 如果您使用 Visual Studio 2017 或更新版本，請嘗試在 Visual Studio 安裝程式中重新安裝**使用 c + + 的桌面開發**工作負載。 如需詳細資訊，請參閱[在 Visual Studio 中安裝 c + + 支援](vscpp-step-0-installation.md)。 或者，從 [ [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)] 頁面重新安裝組建工具。 請不要進入下一節，直到這種情況生效。 如需安裝和疑難排解 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 視電腦上的 Windows 版本和系統安全性設定而定，您可能必須以滑鼠右鍵按一下開啟 [開發人員命令提示字元] 快捷方式的快捷方式功能表，然後選擇 [以**系統管理員身分執行**]，成功建立並執行您依照本逐步解說所建立的程式。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>建立 C 原始程式檔並在命令列上進行編譯

1. 在 [開發人員命令提示字元] `cd c:\`視窗中，輸入，將目前的工作目錄變更為 C：磁片磁碟機的根目錄。 接下來， `md c:\simple`輸入以建立目錄，然後輸入`cd c:\simple`以變更至該目錄。 此目錄會保留您的來源檔案和已編譯的程式。

1. 在`notepad simple.c`開發人員命令提示字元中輸入。 在彈出的 [記事本] 警示對話方塊中，選擇 [**是]** ，在您的工作目錄中建立新的簡單 .c 檔案。

1. 在 [記事本] 中，輸入下列程式程式碼：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在 [記事本] 功能表列上 **，選擇 [** > 檔案] [**儲存**]，以在您的工作目錄中儲存簡單的 .c。

1. 切換回 [開發人員命令提示字元] 視窗。 在`dir`命令提示字元中輸入，以列出 c:\simple 目錄的內容。 您應該會在目錄清單中看到原始檔 simple. c，如下所示：

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

   您的電腦上的日期和其他詳細資料會有所不同。 如果您沒有看到您的原始程式碼檔案，請確定您已變更為您所建立的 c:\simple 目錄，然後在 [記事本] 中，確定您已將原始程式檔儲存在此目錄中。 也請確定您已儲存副檔名為 .c 的原始程式碼，而不是 .txt 副檔名。

1. 若要編譯您的程式`cl simple.c` ，請在開發人員命令提示字元中輸入。

   在編譯器所顯示的輸出資訊行中，您可以看到可執行程式名稱 simple .exe：

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
   > 如果您收到錯誤，例如「' cl ' 無法辨識為內部或外部命令、可運作的程式或批次檔、錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元並未正確設定。 如需如何修正此問題的相關資訊，請回到**開啟開發人員命令提示**字元一節。

   > [!NOTE]
   > 如果您收到不同的編譯器或連結器錯誤或警告，請檢查您的原始程式碼以更正任何錯誤，然後儲存並再次執行編譯器。 如需特定錯誤的詳細資訊，請使用此頁面頂端的 [搜尋] 方塊來尋找錯誤號碼。

1. 若要執行您的程式`simple` ，請在命令提示字元中輸入。

   程式會顯示下列文字並結束：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜，您已使用命令列編譯並執行 C 程式。

## <a name="next-steps"></a>後續步驟

這個 "Hello，World" 範例就跟 C 程式可以取得的一樣簡單。 真實世界的程式具有標頭檔和更多來源檔案、程式庫中的，以及執行有用的工作。

您可以使用本逐步解說中的步驟來建立您自己的 C 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建立許多 C 程式碼範例程式，以在其他地方找到。 若要編譯具有其他原始程式碼檔案的程式，請在命令列上輸入這些檔案，如下所示：

`cl file1.c file2.c file3.c`

編譯器會輸出名為 file1 的程式。 若要將名稱變更為 program1，請新增[/out](reference/out-output-file-name.md)連結器選項：

`cl file1.c file2.c file3.c /link /out:program1.exe`

若要自動攔截更多程式設計錯誤，建議您使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告層級選項進行編譯：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

編譯器（cl）有更多的選項，可讓您套用以建立、優化、分析和分析您的程式碼。 如需快速清單，請`cl /?`在開發人員命令提示字元中輸入。 您也可以分別編譯和連結，並在更複雜的組建案例中套用連結器選項。 如需編譯器和連結器選項和使用方式的詳細資訊，請參閱[C/c + + 建立參考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和 makefile，或 MSBuild 和專案檔，在命令列上設定並建立更複雜的專案。 如需使用這些工具的詳細資訊，請參閱[NMAKE 參考](reference/nmake-reference.md)和[MSBuild](msbuild-visual-cpp.md)。

C 和 c + + 語言類似，但並不相同。 Microsoft C/c + + 編譯器（MSVC）會使用一個簡單的規則，來決定在編譯器代碼時所要使用的語言。 根據預設，MSVC 編譯器會將以. c 結尾的所有檔案視為 C 原始程式碼，並將所有以 .cpp 結尾的檔案當做 c + + 原始程式碼。 若要強制編譯器將所有檔案視為 C 非相依的副檔名，請使用[/tc](reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

MSVC 與 ISO C99 標準相容，但不符合嚴格規範。 在大部分情況下，可移植的 C 程式碼會如預期般編譯並執行。 Visual C++ 不支援 ISO C11 中的大部分變更。 某些程式庫函式和 POSIX 函數名稱已被 MSVC 取代。 支援函數，但慣用的名稱已變更。 如需詳細資訊，請參閱 CRT 和[編譯器警告（層級3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)[中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="see-also"></a>請參閱

[逐步解說：建立標準 C++ 程式 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 語言參考](../c-language/c-language-reference.md)<br/>
[專案和建置系統](projects-and-build-systems-cpp.md)<br/>
[相容性](../c-runtime-library/compatibility.md)
