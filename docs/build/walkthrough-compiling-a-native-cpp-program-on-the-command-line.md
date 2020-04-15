---
title: 逐步解說：在命令列上編譯原生 C++ 程式
description: 使用命令提示符中的 Microsoft C++編譯器。
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335236"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>逐步解說：在命令列上編譯原生 C++ 程式

Visual Studio 包括命令列 C 和C++編譯器。 您可以使用它創建從基本控制台應用到通用 Windows 平臺應用、桌面應用、裝置驅動程式和 .NET 元件的所有內容。

在本演練中,您可以使用文本編輯器創建基本"你好,世界"風格的C++程式,然後在命令行上編譯它。 如果要嘗試視覺化工作室 IDE 而不是使用命令列,請參閱[演練:使用專案和解決方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或使用[視覺化工作室 IDE C++桌面開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在本演練中,您可以使用自己的C++程式,而不是鍵入顯示的程式。 或者,您可以使用其他説明文章中C++代碼示例。

## <a name="prerequisites"></a>Prerequisites

要完成本演練,您必須安裝具有C++工作負載的可視化工作室和可選**桌面開發**,或者安裝可視化工作室的命令行構建工具。

可視化工作室是一*個集成的開發環境*(IDE)。 它支援多種語言和平臺的全功能編輯器、資源管理器、調試器和編譯器。 可用的版本包括免費的視覺工作室社區版本,所有版本都可以支援 C 和C++開發。 有關如何下載和安裝可視化工作室的資訊,請參閱[在可視化工作室中安裝C++支援](vscpp-step-0-installation.md)。

Visual Studio 的建構工具僅安裝編譯 C 和C++程式所需的命令列編譯器、工具和庫。 它非常適合構建實驗室或課堂練習,安裝速度相對較快。 要僅安裝命令列工具,請在[可視化工作室下載](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)頁面上查找可視化工作室的構建工具。

在命令列上建構 C 或 C++ 程式之前,請驗證工具是否已安裝,並且可以從命令列存取這些工具。 可視化C++對命令行環境具有複雜的要求,用於查找它使用的工具、標頭和庫。 如果不進行一些準備 **,就不能在普通命令提示視窗中使用 Visual C++。** 幸運的是,Visual C++安裝快捷方式,以便啟動具有為命令行生成設置環境的開發人員命令提示。 遺憾的是,在幾乎每個版本的 Visual C++ 和不同版本的 Windows 中,開發人員命令提示快捷方式的名稱及其位置都不同。 您的第一個演練任務是找到合適的任務。

> [!NOTE]
> 開發人員命令提示快捷方式會自動設置編譯器和工具以及任何必需標頭和庫的正確路徑。 如果使用常規**命令提示**視窗,則必須自己設置這些環境值。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](setting-the-path-and-environment-variables-for-command-line-builds.md)。 我們建議您使用開發人員命令提示快捷方式,而不是構建自己的快捷方式。

### <a name="open-a-developer-command-prompt"></a>開啟開發人員指令提示

1. 如果您在 Windows 10 上安裝了 Visual Studio 2017 或更高版本,請打開"開始"功能表並選擇 **"所有應用**"。 向下滾動並打開**可視化工作室**資料夾(不是可視化工作室應用程式)。 選擇**VS 的開發人員命令提示符**以開啟命令提示視窗。

   如果您在 Windows 10 上安裝了 Microsoft 視覺C++構建工具 2015,請打開 **「開始」** 選單並選擇 **「所有應用**」。 向下滾動並打開 **「視覺C++生成工具」** 資料夾。 選擇**視覺C++ 2015 x86 本機工具命令提示符**以打開命令提示視窗。

   您還可以使用 Windows 搜尋功能搜尋「開發人員命令提示符」,並選擇與已安裝版本的 Visual Studio 相匹配的函數。 使用快捷方式打開命令提示視窗。

1. 接下來,驗證可視化C++開發人員命令提示是否設置正確。 在指令提示視窗中,輸入`cl`並驗證輸出是否所示:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   當前目錄或版本號可能存在差異。 這些值取決於 Visual C++ 版本和安裝的任何更新。 如果上述輸出與您所看到的類似,那麼您就可以在命令行生成 C 或 C++程式。

   > [!NOTE]
   > 如果收到錯誤,如"'cl'未識別為內部或外部命令、可操作程式或批處理檔",則在運行**`cl`** 該命令時出現錯誤 C1034 或錯誤 LNK1104,則表示您未使用開發人員命令提示符,或者安裝 Visual C++時出現問題。 必須先解決此問題,然後才能繼續。

   如果找不到開發人員命令提示快捷方式,或者在輸入`cl`時收到錯誤消息,則 Visual C++安裝可能有問題。 請嘗試在可視化工作室中重新安裝視覺C++元件,或重新安裝 Microsoft 視覺C++構建工具。 在命令工作之前,不要轉到下一**`cl`** 節。 有關安裝和故障排除視覺C++的詳細資訊,請參閱[安裝可視化工作室](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根據電腦上的 Windows 版本和系統安全設定,您可能需要右鍵單擊才能打開開發人員命令提示快捷方式的快捷方式選單,然後選擇 **「以管理員身份執行」** 才能成功生成並運行透過本演練創建的程式。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>建立視覺化C++源檔並在命令列上編譯

1. 在開發人員命令提示視窗中,輸入`md c:\hello`以創建目錄,然後輸入`cd c:\hello`更改為該目錄。 此目錄是創建源檔和編譯程式的位置。

1. 在`notepad hello.cpp`命令提示視窗中輸入。

   當記事本提示您建立檔時,請選擇「**是**」 。 此步驟將打開一個空白的記事本視窗,隨時允許您在名為 hello.cpp 的檔中輸入代碼。

1. 在記事本中,輸入以下代碼行:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   此代碼是一個簡單的程式,將在螢幕上編寫一行文本,然後退出。 若要將錯誤數降至最低，請複製此程式碼，再將其貼到記事本中。

1. 儲存您的工作！ 在 [記事本] 的 [檔案] **** 功能表中，選擇 [儲存] ****。

   恭喜您,您已經創建了一個C++源檔,hello.cpp,該檔可以編譯。

1. 切換回開發人員命令提示視窗。 在`dir`命令提示符處輸入以列出 c:\hello 目錄的內容。 您應該在目錄清單中看到源檔 hello.cpp,如下所示:

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

   您的電腦上的日期和其他詳細資訊會有所不同。 如果您沒有看到原始碼檔 *,hello.cpp,* 請確保您已更改為*c:hello\\*目錄。 在記事本中,請確保將源檔儲存到此目錄中。 還要確保使用*`.cpp`* 檔案名擴展名*`.txt`* 而不是 擴展名保存了原始碼。

1. 在開發人員命令提示符處,`cl /EHsc hello.cpp`輸入以編譯程式。

   cl.exe 編譯器會產生內含編譯後之程式碼的 .obj 檔案，然後執行連結器，以建立名為 basic.exe 的可執行程式。 此名稱會出現在編譯器所顯示輸出資訊行中。 編譯器的輸出應如下所示:

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
   > 如果收到錯誤,如"'cl'未識別為內部或外部命令、可操作程式或批處理檔"、"錯誤 C1034"或錯誤 LNK1104,則開發人員命令提示符設置不正確。 有關如何解決此問題的資訊,請造訪 **「打開開發人員命令提示符」** 部分。

   > [!NOTE]
   > 如果收到其他編譯器或連結器錯誤或警告,請查看原始程式碼以更正任何錯誤,然後保存它並再次運行編譯器。 有關特定錯誤的資訊,請使用此 MSDN 頁面上的搜尋框查找錯誤編號。

1. 若要執行 hello.exe 程式，請在命令提示字元下，輸入 `hello`。

   程式會顯示下列文字並結束：

   ```Output
   Hello, world, from Visual C++!
   ```

   恭喜您,您已經使用命令列工具編譯並運行了C++程式。

## <a name="next-steps"></a>後續步驟

這個"你好,世界"的例子就像一個C++程式可以得到的一樣簡單。 現實世界中的程式通常具有標頭檔、更多的源檔和指向庫的連結。

您可以使用本演練中的步驟構建您自己的C++代碼,而不是鍵入顯示的範例代碼。 這些步驟還允許您構建許多C++代碼示例程式,這些程式是您在其他位置找到的。 您可以將原始碼並建置應用到任何可寫入的目錄中。 預設情況下,Visual Studio IDE 會在使用者資料夾中、*\\源存儲庫*子資料夾中創建專案。 較舊版本可能會將專案放在*\\文檔 可\<視化工作室\\版本>* 專案* 資料夾中。

要編譯具有其他原始碼檔案的程式,請在命令列中全部輸入它們,例如:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

命令`/EHsc`行選項指示編譯器啟用標準C++異常處理行為。 如果沒有它,引發的異常可能會導致未銷毀的對象和資源洩漏。 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](reference/eh-exception-handling-model.md)。

當您提供其他源檔時,編譯器使用第一個輸入檔案創建程式名稱。 在這種情況下,它輸出一個程式稱為 file1.exe。 要將名稱更改為程式1.exe,加入[/out](reference/out-output-file-name.md)連結器選項:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

為了自動捕捉更多的程式設計錯誤,我們建議您使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告等級選項進行編譯:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

編譯器,cl.exe,還有更多的選項。 您可以應用它們來生成、優化、除錯和分析代碼。 有關快速清單,`cl /?`請輸入開發人員命令提示符。 您還可以單獨編譯和連結,並在更複雜的生成方案中應用連結器選項。 有關編譯器和連結器選項和使用方式的詳細資訊,請參閱[C/C++建築參考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和製作檔、MSBuild 和專案檔(CMake)在命令列上配置和構建更複雜的專案。 有關使用這些工具的詳細資訊,請參閱 Visual Studio 中的[NMAKE 參考](reference/nmake-reference.md)[、MSBuild](msbuild-visual-cpp.md)和[CMake 專案](cmake-projects-in-visual-studio.md)。

C 和C++語言相似,但不同。 MSVC 編譯器使用一個簡單的規則來確定在編譯代碼時要使用的語言。 默認情況下,MSVC 編譯器將結*`.c`* 尾 的檔視為C原始程式碼,並將*`.cpp`* 結束的文件視為C++原始碼。 要強制編譯器將所有檔視為獨立於檔名擴展名C++,請使用[/TP](reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。

MSVC 編譯器包括符合 ISO C99 標準的 C 運行時庫 (CRT),但有一些小例外。 便攜式代碼通常按預期編譯和運行。 MSVC 編譯器將棄用某些過時的庫函數和幾個 POSIX 函數名稱。 支援函數,但首選名稱已更改。 有關詳細資訊,請參閱 CRT 和[編譯器警告 (級別 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)[中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)<br/>
[專案和建置系統](projects-and-build-systems-cpp.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
