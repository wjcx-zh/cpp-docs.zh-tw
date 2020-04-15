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

Visual C++ 包括 C 編譯器,可用於創建從基本主控台程式到完整 Windows 桌面應用程式、行動應用等的所有內容。

本演練演示如何使用文本編輯器創建基本的"你好,世界"風格的C程式,然後在命令行上編譯它。 如果您希望在命令列上C++工作,請參閱[演練:在命令列上編譯本機C++程式](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果要嘗試視覺化工作室 IDE 而不是使用命令列,請參閱[演練:使用專案和解決方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或使用[視覺化工作室 IDE C++桌面開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>Prerequisites

要完成本演練,必須安裝 Visual Studio 和可選的可視化C++元件,或安裝可視化工作室的生成工具。

Visual Studio 是一個強大的整合式開發環境,支援多種語言和平臺的全功能編輯器、資源管理器、調試器和編譯器。 有關這些功能以及如何下載和安裝 Visual Studio 的資訊,包括免費的視覺工作室社區版,請參閱[安裝視覺化工作室](/visualstudio/install/install-visual-studio)。

Visual Studio 的可視化工作室版本的"構建工具"僅安裝構建 C 和C++程式所需的命令列工具集、編譯器、工具和庫。 它非常適合構建實驗室或課堂練習,安裝速度相對較快。 要僅安裝命令列工具集,請從[Visual Studio 下載](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)頁面下載可視化工作室的建構工具並運行安裝程式。 在可視化工作室安裝程式中,選擇**C++生成工具**工作負載,然後選擇 **「安裝**」。。

在命令列上建構 C 或 C++ 程式之前,必須驗證工具是否已安裝,以及是否可以從命令列存取這些工具。 可視化C++對命令行環境具有複雜的要求,用於查找它使用的工具、標頭和庫。 如果不進行一些準備 **,就不能在普通命令提示視窗中使用 Visual C++。** 您需要一個*開發人員命令提示*視窗,這是一個常規命令提示視窗,它設置了所有必需的環境變數。 幸運的是,Visual C++ 安裝快捷方式,用於啟動已為命令行生成設置環境的開發人員命令提示。 遺憾的是,在幾乎每個版本的 Visual C++ 和不同版本的 Windows 中,開發人員命令提示快捷方式的名稱及其位置都不同。 您的第一個演練任務是找到要使用的正確快捷方式。

> [!NOTE]
> 開發人員命令提示快捷方式會自動設置編譯器和工具以及任何必需標頭和庫的正確路徑。 對於每個生成配置,其中一些值是不同的。 如果不使用其中一個快捷方式,則必須自己設置這些環境值。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。 由於生成環境很複雜,因此強烈建議您使用開發人員命令提示快捷方式,而不是構建自己的快捷方式。

這些說明因您使用的 Visual Studio 版本而異。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 開啟開發人員指令提示

如果在 Windows 10 上安裝了 Visual Studio 2019,請打開"開始"菜單,然後向下滾動並打開**Visual Studio 2019**資料夾(不是 Visual Studio 2019 應用)。 選擇**VS 2019 的開發人員命令提示符**以打開命令提示視窗。

如果您使用的是 Windows 的不同版本,請查看「開始」功能表或「開始」頁,查看包含開發人員命令提示快捷方式的 Visual Studio 工具資料夾。 您還可以使用 Windows 搜尋功能搜尋「開發人員命令提示符」,並選擇與已安裝版本的 Visual Studio 相匹配的函數。 使用快捷方式打開命令提示視窗。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>在 Visual Studio 2017 開啟開發人員指令提示

如果在 Windows 10 上安裝了 Visual Studio 2017,請打開"開始"菜單,然後向下滾動並打開**Visual Studio 2017**資料夾(不是 Visual Studio 2017 應用)。 選擇**VS 2017 的開發人員命令提示符**以打開命令提示視窗。

如果您正在執行不同版本的 Windows,請查看「開始」功能表或「開始」頁,查看包含開發人員命令提示快捷方式的 Visual Studio 工具資料夾。 您還可以使用 Windows 搜尋功能搜尋「開發人員命令提示符」,並選擇與已安裝版本的 Visual Studio 相匹配的函數。 使用快捷方式打開命令提示視窗。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>在 Visual Studio 2015 開啟開發者指令提示

如果在 Windows 10 上安裝了 Microsoft 視覺C++構建工具 2015,請打開 **「開始」** 選單,然後向下滾動並打開 **「視覺C++生成工具」** 資料夾。 選擇**視覺C++ 2015 x86 本機工具命令提示符**以打開命令提示視窗。

如果您正在執行不同版本的 Windows,請查看「開始」功能表或「開始」頁,查看包含開發人員命令提示快捷方式的 Visual Studio 工具資料夾。 您還可以使用 Windows 搜尋功能搜尋「開發人員命令提示符」,並選擇與已安裝版本的 Visual Studio 相匹配的函數。 使用快捷方式打開命令提示視窗。

::: moniker-end

接下來,驗證可視化C++開發人員命令提示是否設置正確。 在指令提示視窗中,輸入`cl`並驗證輸出是否所示:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

當前目錄或版本號可能存在差異,具體取決於 Visual C++的版本和安裝的任何更新。 如果上述輸出與您所看到的類似,那麼您就可以在命令行生成 C 或 C++程式。

> [!NOTE]
> 如果收到錯誤,如"'cl'未識別為內部或外部命令、可操作程式或批處理檔",則在運行**cl**命令時出現錯誤 C1034 或錯誤 LNK1104,則表示您未使用開發人員命令提示符,或者安裝 Visual C++時出現問題。 必須先解決此問題,然後才能繼續。

如果找不到開發人員命令提示快捷方式,或者在輸入`cl`時收到錯誤消息,則 Visual C++安裝可能有問題。 如果您使用的是 Visual Studio 2017 或更高版本,請試著在 Visual Studio 安裝程式中重新安裝**具有C++工作負載的桌面開發**。 有關詳細資訊,請參閱[在可視化工作室中安裝C++支援](vscpp-step-0-installation.md)。 或者,從[可視化工作室下載](https://visualstudio.microsoft.com/downloads/)頁面重新安裝生成工具。 在此工作之前,不要繼續下一節。 有關安裝視覺工作室和故障排除的詳細資訊,請參閱[安裝可視化工作室](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 根據電腦上的 Windows 版本和系統安全設定,您可能需要右鍵單擊才能打開開發人員命令提示快捷方式的快捷方式選單,然後選擇 **「作為管理員執行」** 才能成功生成並運行透過本演練創建的程式。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>建立 C 源檔案並在命令列上編譯

1. 在開發人員命令提示視窗中,輸入`cd c:\`以將當前工作目錄更改為 C: 驅動器的根目錄。 接下來,輸入`md c:\simple`以創建目錄,然後輸入`cd c:\simple`更改為該目錄。 此目錄將儲存您的源檔和編譯的程式。

1. 在`notepad simple.c`開發人員命令提示符處輸入。 在彈出的記事本警報對話框中,選擇 **「是」** 以在工作目錄中創建新的 simple.c 檔。

1. 在記事本中,輸入以下代碼行:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在記事本選單欄上,選擇 **「檔案** > **儲存」** 以儲存工作目錄中的簡單.c。

1. 切換回開發人員命令提示視窗。 在`dir`命令提示符處輸入以列出 c:_簡單目錄的內容。 您應該在目錄清單中看到源檔 simple.c,如下所示:

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

   您的電腦上的日期和其他詳細資訊會有所不同。 如果看不到原始碼檔 simple.c,請確保已更改為創建的 c:_簡單目錄,並在記事本中,請確保將源檔儲存到此目錄中。 還要確保使用 .c 檔名副檔名而不是 .txt 擴展名保存了原始碼。

1. 要編譯程式,`cl simple.c`請輸入開發者命令提示符。

   您可以在編譯器顯示的輸出資訊列中看到可執行程式名稱 simple.exe:

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
   > 如果收到錯誤,如"'cl'未識別為內部或外部命令、可操作程式或批處理檔"、"錯誤 C1034"或錯誤 LNK1104,則開發人員命令提示符設置不正確。 有關如何解決此問題的資訊,請造訪 **「打開開發人員命令提示符」** 部分。

   > [!NOTE]
   > 如果收到其他編譯器或連結器錯誤或警告,請查看原始程式碼以更正任何錯誤,然後保存它並再次運行編譯器。 有關特定錯誤的資訊,請使用此頁面頂部的搜索框查找錯誤編號。

1. 要運行程式,請在命令`simple`提示符處輸入。

   程式會顯示下列文字並結束：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜您,您已經使用命令列編譯並運行了 C 程式。

## <a name="next-steps"></a>後續步驟

這個"你好,世界"的例子就像C程式可以得到的一樣簡單。 現實世界的程式有頭檔和更多的源檔,在庫中連結,並做有用的工作。

您可以使用本演練中的步驟構建自己的 C 代碼,而不是鍵入顯示的範例代碼。 您還可以構建許多 C 代碼範例程式,這些程式在其他地方找到。 要編譯具有其他原始碼檔案的程式,請在命令列中全部輸入它們,例如:

`cl file1.c file2.c file3.c`

編譯器輸出一個稱為 file1.exe 的程式。 要將名稱更改為程式1.exe,加入[/out](reference/out-output-file-name.md)連結器選項:

`cl file1.c file2.c file3.c /link /out:program1.exe`

為了自動捕捉更多的程式設計錯誤,我們建議您使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告等級選項進行編譯:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

編譯器(cl.exe)還有更多選項可用於構建、優化、調試和分析代碼。 有關快速清單,`cl /?`請輸入開發人員命令提示符。 您還可以單獨編譯和連結,並在更複雜的生成方案中應用連結器選項。 有關編譯器和連結器選項和使用方式的詳細資訊,請參閱[C/C++建築參考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和 makefile,或 MSBuild 和專案檔來配置和生成命令列上更複雜的專案。 有關使用這些工具的詳細資訊,請參閱[NMAKE 參考](reference/nmake-reference.md)與[MSBuild](msbuild-visual-cpp.md)。

C 和C++語言相似,但不同。 Microsoft C/C++ 編譯器 (MSVC) 使用一個簡單的規則來確定在編譯代碼時使用哪種語言。 預設情況下,MSVC 編譯器將以 .c 結尾的所有檔視為 C 原始程式碼,並將以 .cpp 結尾的所有檔案視為C++原始碼。 要強制編譯器將所有文件視為不依賴於檔名擴展名的 C,請使用[/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

MSVC 符合 ISO C99 標準,但不符合嚴格要求。 在大多數情況下,便攜式 C 代碼將按預期編譯和運行。 可視C++不支援 ISO C11 中的大部分更改。 MSVC 會棄用某些庫函數和 POSIX 函數名。 支援函數,但首選名稱已更改。 有關詳細資訊,請參閱 CRT 和[編譯器警告 (級別 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)[中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="see-also"></a>另請參閱

[逐步解說：建立標準 C++ 程式 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 語言參考](../c-language/c-language-reference.md)<br/>
[專案和建置系統](projects-and-build-systems-cpp.md)<br/>
[相容性](../c-runtime-library/compatibility.md)
