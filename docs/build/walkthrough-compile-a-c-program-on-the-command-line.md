---
title: 逐步解說：編譯 C 程式中，在命令列上
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 03876ba47270252caa21d7e2994a4f8321a6d59e
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877191"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>逐步解說：編譯 C 程式中，在命令列上

視覺化C++包含 C 編譯器，您可以使用它來建立所有項目從基本的主控台程式到完整 Windows 桌面應用程式、 行動應用程式，和更多功能。

本逐步解說示範如何建立基本"Hello，World"-樣式 C 程式中使用文字編輯器 中，並在命令列上進行編譯。 如果您偏好使用C++命令列中，請參閱[逐步解說：在命令列編譯原生 C++ 程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果您想要試用 Visual Studio IDE，而不是使用命令列，請參閱[逐步解說：使用專案和方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或是[使用 Visual Studio IDE 的C++的桌面開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說中，您必須已安裝 Visual Studio 和選擇性的視覺效果C++元件或適用於 Visual Studio Build Tools。

Visual Studio 是用於許多語言與平台支援的功能完整的編輯器時，資源管理員、 偵錯工具和編譯器功能強大的整合式的開發環境。 如需這些功能，以及如何下載並安裝 Visual Studio 中，包括免費的 Visual Studio Community edition，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

如需 Visual Studio 版本的 Visual Studio Build Tools 安裝僅命令列工具組、 編譯器、 工具和程式庫，您必須先建置 C 和C++程式。 它非常適合建置實驗室或課堂練習和相對快速安裝。 若要安裝的命令列工具組，請下載 Build Tools for Visual Studio [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面，並執行安裝程式。

您可以建立 C 之前或C++程式命令列上，您必須確認確認已安裝的工具，而且您可以從命令列存取它們。 視覺化C++來尋找工具、 標頭和程式庫，它會使用命令列環境的複雜需求。 **您無法使用視覺效果C++中的純文字的命令提示字元視窗**而不需要一些準備工作。 您需要*開發人員命令提示字元*視窗中，也就是已設定的所有必要的環境變數的規則的命令提示字元視窗。 幸好 VisualC++會安裝為您啟動已設定的命令列組建環境的開發人員命令提示字元捷徑。 不幸的是，開發人員命令提示字元捷徑和它們所在的名稱是視覺效果的幾乎每個版本中C++在不同版本的 Windows。 您的第一個逐步解說工作是尋找要使用正確的快顯。

> [!NOTE]
> 開發人員命令提示字元 捷徑會自動設定編譯器和工具，以及任何必要的標頭和程式庫的正確路徑。 其中有些值是每個組建組態不同。 您必須設定這些環境值自行如果您未使用其中一個捷徑。 如需詳細資訊，請參閱 <<c0> [ 設定的路徑和環境變數的命令列建置](setting-the-path-and-environment-variables-for-command-line-builds.md)。 因為在建置環境很複雜，強烈建議您改用建置您自己的開發人員命令提示字元捷徑。

這些指示，端視您所使用的 Visual Studio 版本而有所不同。 在繼續之前，請確定左上版本選擇器的此頁面會設定正確。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 開啟開發人員命令提示字元

如果您已安裝 Visual Studio 2019 Windows 10 上，開啟 [開始] 功能表中，然後向下捲動並開啟**Visual Studio 2019**資料夾 （而不的 Visual Studio 2019 應用程式）。 選擇**VS 2019 的開發人員命令提示字元**以開啟 [命令提示字元] 視窗。

如果您使用不同版本的 Windows，在 開始 功能表中尋找，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows 搜尋函式來搜尋 「 開發人員命令提示字元 並選擇符合您已安裝的 Visual Studio 版本的其中一個。 使用捷徑來開啟 [命令提示字元] 視窗。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Visual Studio 2017 中開啟開發人員命令提示字元

如果您已安裝 Visual Studio 2017 在 Windows 10 上，開啟 [開始] 功能表，然後向下捲動並開啟**Visual Studio 2017**資料夾 （而不的 Visual Studio 2017 應用程式）。 選擇**適用於 VS 2017 開發人員命令提示字元**以開啟 [命令提示字元] 視窗。

如果您執行不同版本的 Windows，在 開始 功能表中尋找，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows 搜尋函式來搜尋 「 開發人員命令提示字元 並選擇符合您已安裝的 Visual Studio 版本的其中一個。 使用捷徑來開啟 [命令提示字元] 視窗。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Visual Studio 2015 中開啟開發人員命令提示字元

如果您已安裝 Microsoft Visual C++ Build Tools 2015 在 Windows 10 中，開啟**啟動**功能表，然後向下的捲動並開啟**視覺化C++Build Tools**資料夾。 選擇**Visual C++ 2015 x86 Native Tools 命令提示字元**以開啟 [命令提示字元] 視窗。

如果您執行不同版本的 Windows，在 開始 功能表中尋找，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows 搜尋函式來搜尋 「 開發人員命令提示字元 並選擇符合您已安裝的 Visual Studio 版本的其中一個。 使用捷徑來開啟 [命令提示字元] 視窗。
   
::: moniker-end


接下來，確認視覺效果C++開發人員命令提示字元已正確設定。 在 [命令提示字元] 視窗中，輸入`cl`並確認，輸出看起來像這樣：

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

可能會有差異的目前目錄或版本號碼，根據視覺效果的版本C++並安裝任何更新。 如果上述的輸出會類似您看到的內容，則您可以開始建置 C 或C++在命令列程式。

> [!NOTE]
> 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，當您執行**cl**命令，則可能您不使用開發人員命令提示字元，或有問題的視覺效果的安裝C++。 您可以繼續之前，您必須修正此問題。

如果您找不到開發人員命令提示字元捷徑，或當您輸入時，收到錯誤訊息`cl`，然後將視覺效果C++安裝可能會有問題。 如果您使用 Visual Studio 2017 或更新版本中，請嘗試重新安裝**使用的桌面開發C++** 在 Visual Studio 安裝程式中的工作負載。 如需詳細資訊，請參閱 <<c0> [ 安裝C++Visual Studio 中支援](vscpp-step-0-installation.md)。</c0> 或者，您也可以重新安裝建置工具，從[Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面。 不要繼續進行下一節直到其運作方式。 如需有關安裝和疑難排解 Visual Studio 的詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 根據電腦和系統安全性設定上的 Windows 版本，您可能必須按一下滑鼠右鍵以開啟 開發人員命令提示字元捷徑的捷徑功能表，然後選擇**系統管理員身分執行**至已成功建置並執行您依照本逐步解說中建立的程式。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>建立 C 原始程式檔，並在命令列上編譯

1. 在 [開發人員命令提示字元] 視窗中，輸入`cd c:\`目前工作目錄變更至您的 c： 磁碟機的根目錄。 接下來，輸入`md c:\simple`來建立目錄，然後輸入`cd c:\simple`變更至該目錄。 此目錄會保留原始程式檔和已編譯的程式。

1. 輸入`notepad simple.c`在開發人員命令提示字元。 在彈出的 [記事本] 警示的對話方塊，選擇**是**工作目錄中建立新的 simple.c 檔案。

1. 在記事本中，輸入下列程式碼行：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在 記事本 功能表列上選擇 **檔案** > **儲存**將 simple.c 儲存在您的工作目錄。

1. 切換回 [開發人員命令提示字元] 視窗。 輸入`dir`在命令提示字元，若要列出 c:\simple 的目錄的內容。 您應該會看到在目錄清單中，看起來像是來源檔案 simple.c:

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

   日期，以及其他詳細資料會在您的電腦上的不同。 如果您沒有看到您的原始程式碼檔，simple.c，請確定您已變更為您所建立的 c:\simple 目錄，並在 [記事本]，請確定您在此目錄中儲存原始程式檔。 也請確定您儲存的原始碼，副檔名為.c 檔案名稱，不使用副檔名.txt。

1. 若要編譯您的程式，請輸入`cl simple.c`在開發人員命令提示字元。

   您可以看到可執行程式的名稱，simple.exe，則編譯器會顯示的輸出資訊行中：

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
   > 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元未正確設定。 如需如何修正此問題的資訊，請回到**開啟開發人員命令提示字元**一節。

   > [!NOTE]
   > 如果您收到不同的編譯器或連結器錯誤或警告，請檢閱您的程式碼，以更正任何錯誤，然後將它儲存，並再次執行編譯器。 如需特定錯誤的資訊，在此頁面頂端使用搜尋方塊尋找的錯誤號碼。

1. 若要執行您的程式，請輸入`simple`在命令提示字元。

   程式會顯示下列文字並結束：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜，您已經編譯並執行 C 程式中使用命令列。

## <a name="next-steps"></a>後續步驟

這個"Hello，World"範例是簡單 C 程式中可以取得。 真實世界的程式有標頭檔和多個原始程式檔，在程式庫，連結，並執行有用的工作。

您可以使用在本逐步解說的步驟，來建置您自己的 C 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建置許多 C 程式碼的範例程式，您在其他地方找到。 若要編譯程式的其他原始程式碼檔，輸入所有命令列上，例如：

`cl file1.c file2.c file3.c`

編譯器輸出 file1.exe 程式。 若要將名稱變更為 program1.exe，新增[/out](reference/out-output-file-name.md)連結器選項：

`cl file1.c file2.c file3.c /link /out:program1.exe`

自動攔截更多的程式設計錯誤，我們建議您編譯使用其中一種[/w3](reference/compiler-option-warning-level.md)或是[/w4](reference/compiler-option-warning-level.md)警告層級的選項：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

編譯器、 cl.exe，有許多更多選項，您可以套用於建置、 最佳化、 偵錯和分析您的程式碼。 如需快速的清單中，輸入`cl /?`在開發人員命令提示字元。 您也可以編譯和連結個別，套用在更複雜的建置案例的連結器選項。 如需有關編譯器和連結器選項，以及使用方式的詳細資訊，請參閱 < [C /C++建置參考](reference/c-cpp-building-reference.md)。

若要設定及命令列上建置更複雜的專案，您可以使用 NMAKE 和 makefile 或 MSBuild 和專案檔。 如需有關如何使用這些工具的詳細資訊，請參閱 < [NMAKE 參考](reference/nmake-reference.md)並[MSBuild](msbuild-visual-cpp.md)。

C 和C++語言十分相似，但不是相同。 Microsoft C /C++編譯器 (MSVC) 會使用簡單的規則來判斷要編譯您的程式碼時所使用的語言。 根據預設，MSVC 編譯器會將以 c# 原始程式碼，.c 結尾的所有檔案和所有結尾為.cpp 的檔案C++原始程式碼。 若要強制編譯器將視為 C 非相依檔案副檔名的所有檔案，請使用[/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

MSVC 是相容於 ISO C99 標準，但不是會完全遵循網路標準。 在大部分情況下，可移植的 C 程式碼會編譯，並如預期般執行。 視覺化C++不支援 ISO C11 中的大部分的變更。 MSVC 取代特定的程式庫函式和 POSIX 函式名稱。 支援的函式，但是慣用的名稱已變更。 如需詳細資訊，請參閱 < [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)並[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>另請參閱

[逐步解說：建立標準 C++ 程式 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 語言參考](../c-language/c-language-reference.md)<br/>
[專案和建置系統](projects-and-build-systems-cpp.md)<br/>
[相容性](../c-runtime-library/compatibility.md)
