---
title: 逐步解說： 編譯 C 程式中的，在命令列 |Microsoft Docs
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da1b645e85542631ce3e656ccaebdfbccf01137
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397893"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>逐步解說： 編譯 C 程式中，在命令列上

Visual c + + 包含 C 編譯器，您可以使用它來建立所有項目從基本的主控台程式到完整 Windows 桌面應用程式、 行動應用程式，和更多功能。

本逐步解說示範如何建立基本"Hello，World"-樣式 C 程式中使用文字編輯器 中，並在命令列上進行編譯。 如果您而是會在 c + + 中工作，在命令列上，請參閱[逐步解說： 編譯命令列上的原生 c + + 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果您想要試用 Visual Studio IDE，而不是使用命令列，請參閱 <<c0> [ 逐步解說： 使用專案和方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或是[使用 Visual Studio IDE 進行 c + + 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說中，您必須已安裝 Visual Studio 和選擇性的 Visual c + + 元件或 Build Tools for Visual Studio。

Visual Studio 是用於許多語言與平台支援的功能完整的編輯器時，資源管理員、 偵錯工具和編譯器功能強大的整合式的開發環境。 如需這些功能，以及如何下載並安裝 Visual Studio 中，包括免費的 Visual Studio Community edition，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

Build Tools for Visual Studio 版本的 Visual Studio 只會安裝命令列工具組、 編譯器、 工具和建置 C 和 c + + 程式所需的程式庫。 它非常適合建置實驗室或課堂練習和相對快速安裝。 若要安裝的命令列工具組，請下載[Build Tools for Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721)執行安裝程式。

您可以在命令列上建置的 C 或 c + + 程式之前，您必須確認，則會安裝工具，以及您可以從命令列存取它們。 Visual c + + 以找出工具、 標頭和程式庫，它會使用具有命令列環境的複雜需求。 **您無法使用 Visual c + + 中的純文字的命令提示字元視窗**而不需要一些準備工作。 您需要*開發人員命令提示字元*視窗中，也就是已設定的所有必要的環境變數的規則的命令提示字元視窗。 幸運的是，Visual c + + 會安裝為您啟動已設定的命令列組建環境的開發人員命令提示字元捷徑。 不幸的是，開發人員命令提示字元捷徑和它們的所在位置的名稱是不同的 Visual c + + 和不同版本的 Windows 上幾乎每個版本中。 您的第一個逐步解說工作是尋找要使用正確的快顯。

> [!NOTE]
> 開發人員命令提示字元 捷徑會自動設定編譯器和工具，以及任何必要的標頭和程式庫的正確路徑。 其中有些值是每個組建組態不同。 您必須設定這些環境值自行如果您未使用其中一個捷徑。 如需詳細資訊，請參閱 <<c0> [ 設定的路徑和環境變數的命令列建置](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。 因為在建置環境很複雜，強烈建議您改用建置您自己的開發人員命令提示字元捷徑。

## <a name="open-a-developer-command-prompt"></a>開啟開發人員命令提示字元

1. 如果您已安裝 Visual Studio 2017 在 Windows 10 上，開啟 [開始] 功能表，然後向下捲動並開啟**Visual Studio 2017**資料夾 （而不的 Visual Studio 2017 應用程式）。 選擇**適用於 VS 2017 開發人員命令提示字元**以開啟 [命令提示字元] 視窗。

   如果您已安裝 Microsoft Visual c + + Build Tools 2015 在 Windows 10 上，開啟**開始**功能表，然後向下的捲動並開啟**Visual c + + Build Tools**資料夾。 選擇**Visual c + + 2015 x86 Native Tools 命令提示字元**以開啟 [命令提示字元] 視窗。

   如果您使用不同版本的 Visual Studio，或執行不同版本的 Windows，在 開始 功能表中尋找，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows 搜尋函式來搜尋 「 開發人員命令提示字元 並選擇符合您已安裝的 Visual Studio 版本的其中一個。 使用捷徑來開啟 [命令提示字元] 視窗。

2. 接下來，確認 Visual c + + 開發人員命令提示字元已正確設定。 在 [命令提示字元] 視窗中，輸入`cl`並確認，輸出看起來像這樣：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]

   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>
   ```

   可能會有目前的目錄或版本號碼，並根據 Visual c + + 和安裝任何更新的版本中的差異。 如果這是類似於您所看到的內容，您已準備好要建置以 C 或 c + + 程式，在命令列。

   > [!NOTE]
   > 如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，當您執行**cl**命令，則可能您不使用開發人員命令提示字元，或有問題的 Visual c + + 的安裝。 您可以繼續之前，您必須修正此問題。

   如果您找不到開發人員命令提示字元 捷徑，或如果您收到錯誤訊息，當您輸入`cl`，則您的 Visual c + + 安裝可能會有問題。 如果您使用 Visual Studio 2017，請嘗試重新安裝**使用 c + + 的桌面開發**Visual Studio 安裝程式中的工作負載。 如需詳細資訊，請參閱 < [Visual Studio 中的安裝 c + + 支援](../build/vscpp-step-0-installation.md)。 或者，您也可以重新安裝[Build Tools for Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721)。 不要繼續進行下一節直到其運作方式。 如需有關安裝和疑難排解 Visual Studio 的詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根據電腦和系統安全性設定上的 Windows 版本，您可能必須按一下滑鼠右鍵以開啟 開發人員命令提示字元捷徑的捷徑功能表，然後選擇**系統管理員身分執行**至已成功建置並執行您依照本逐步解說中建立的程式。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>建立 C 原始程式檔，並在命令列上編譯

1. 在 [開發人員命令提示字元] 視窗中，輸入**cd c:\\** 目前工作目錄變更至您的 c： 磁碟機的根目錄。 接下來，輸入**md c:\simple**來建立目錄，然後輸入**cd c:\simple**變更至該目錄。 這是將包含原始程式檔和編譯的程式的目錄。

2. 請輸入**記事本 simple.c**在開發人員命令提示字元。 在彈出的 [記事本] 警示的對話方塊，選擇**是**工作目錄中建立新的 simple.c 檔案。

3. 在記事本中，輸入下列程式碼行：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

4. 在 記事本 功能表列上選擇 **檔案**，**儲存**將 simple.c 儲存在您的工作目錄。

5. 切換回 [開發人員命令提示字元] 視窗。 請輸入**dir**在命令提示字元，若要列出 c:\simple 的目錄的內容。 您應該會看到來源檔案 simple.c，在目錄清單中，看起來像這樣：

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

6. 若要編譯您的程式，請輸入**cl simple.c**在開發人員命令提示字元。

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

7. 若要執行您的程式，請輸入**簡單**在命令提示字元。

   程式會顯示下列文字並結束：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜，您只編譯並執行 C 程式中使用命令列。

## <a name="next-steps"></a>後續步驟

這個"Hello，World"範例是簡單 C 程式中可以取得。 真實世界的程式有標頭檔和多個原始程式檔，在程式庫，連結，並執行有用的工作。

您可以使用在本逐步解說的步驟，來建置您自己的 C 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建置許多 C 程式碼的範例程式，您在其他地方找到。 若要編譯的程式，有多個原始程式碼檔，輸入全部在命令列中，像這樣：

`cl file1.c file2.c file3.c`

編譯器輸出 file1.exe 程式。 若要將名稱變更為 program1.exe，新增[/out](../build/reference/out-output-file-name.md)連結器選項：

`cl file1.c file2.c file3.c /link /out:program1.exe`

自動攔截更多的程式設計錯誤，我們建議您編譯使用其中一種[/w3](../build/reference/compiler-option-warning-level.md)或是[/w4](../build/reference/compiler-option-warning-level.md)警告層級的選項：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

編譯器、 cl.exe，有許多更多選項，您可以套用於建置、 最佳化、 偵錯和分析您的程式碼。 如需快速的清單中，輸入**cl /？** 在開發人員命令提示字元。 您也可以編譯和連結個別，套用在更複雜的建置案例的連結器選項。 如需有關編譯器和連結器選項，以及使用方式的詳細資訊，請參閱 < [C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)。

若要設定及命令列上建置更複雜的專案，您可以使用 NMAKE 和 makefile 或 MSBuild 和專案檔。 如需有關如何使用這些工具的詳細資訊，請參閱 < [NMAKE 參考](../build/nmake-reference.md)並[MSBuild](../build/msbuild-visual-cpp.md)。

C 和 c + + 語言很類似，但不是相同。 Visual c + + 編譯器會使用簡單的規則來決定要編譯您的程式碼時所使用的語言。 根據預設，Visual C++ 編譯器會將以 .c 結尾的所有檔案都視為 C 原始程式碼，並會將以 .cpp 結尾的所有檔案都視為 C++ 原始程式碼。 若要強制編譯器忽視副檔名視為 C 的所有檔案，請使用[/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

Visual c + + C 編譯器是通常相容於 ISO C99 標準，但不是會完全遵循網路標準。 在大部分情況下，可移植的 C 程式碼會編譯，並如預期般執行。 Visual c + + 不支援 ISO C11 中的大部分變更。 Visual c + + 編譯器已被取代特定的程式庫函式和 POSIX 函式名稱。 支援的函式，但是慣用的名稱已變更。 如需詳細資訊，請參閱 < [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)並[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>另請參閱

[逐步解說：建立標準 C++ 程式 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 語言參考](../c-language/c-language-reference.md)<br/>
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)<br/>
[相容性](../c-runtime-library/compatibility.md)
