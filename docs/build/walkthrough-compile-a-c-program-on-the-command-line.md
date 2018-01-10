---
title: "逐步解說： 編譯 C 程式命令列上的 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
caps.latest.revision: "46"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7520e2d78c924ee21c489d2e8327c4bda9b973aa
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>逐步解說： 編譯 C 程式命令列上
Visual c + + 包含 C 編譯器可讓您建立的所有項目從基本的主控台程式到完整 Windows 桌面應用程式、 行動應用程式，以及更多。  
  
 本逐步解說示範如何建立基本，"Hello，World"為樣式 C 程式中，使用文字編輯器 中，，然後在命令列進行編譯。 如果您就不必在 c + + 命令列上，請參閱[逐步解說： 編譯原生 c + + 程式命令列上](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果您想要再試一次 Visual Studio IDE，而不是使用命令列，請參閱[逐步解說： 使用專案和方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成此逐步解說，您必須已安裝 Visual Studio 和選擇性的 Visual c + + 元件或 Microsoft Visual c + + 建置工具。  
  
 Visual Studio 為許多語言和平台支援全功能的編輯器，資源管理員，、 偵錯工具和編譯器的功能強大的整合式的開發環境。 如需這些功能，以及如何下載並安裝 Visual Studio，包括免費的 Visual Studio Community 版本，請參閱[VisualStudio.com](https://www.visualstudio.com/)。  
  
 只有命令列編譯器、 工具和您要建立 C 和 c + + 程式庫，則會安裝 Visual Studio 建置工具。 它非常適合組建實驗室或教室會執行，並會安裝相當快速。 若要只安裝命令列工具，下載[Visual Studio 建置工具](https://go.microsoft.com/fwlink/p/?linkid=840931)並執行安裝程式。 如需詳細資訊，請參閱[Visual c + + 建置工具](http://landinghub.visualstudio.com/visual-cpp-build-tools)。  
  
 您可以在命令列上建置 C 或 c + + 程式之前，您必須確認確認已安裝的工具，以及您可以從命令列存取它們。 Visual c + + 為了尋找工具、 標頭和程式庫，它會使用具有複雜的命令列環境的需求。 **您無法使用 Visual c + + 中的純文字的命令提示字元視窗**。 您需要*開發人員命令提示字元*視窗中，這可能會擁有所有必要的環境變數設定的一般的命令提示字元視窗。 幸運的是，Visual c + + 會安裝為您啟動已設定為命令列組建環境的開發人員命令提示字元捷徑。 不幸的是，開發人員命令提示字元 捷徑，和它們的所在位置的名稱是幾乎每個版本的 Visual c + +，並在不同版本的 Windows 中。 您的第一個逐步解說工作是尋找正確的捷徑使用。  
  
> [!NOTE]
>  開發人員命令提示字元捷徑會自動設定編譯器和工具，以及任何必要的標頭和程式庫的正確路徑。 這些值有些不同，每個組建組態。 您必須設定這些環境值自行如果您不使用其中一個捷徑。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。 因為在建置環境很複雜，我們強烈建議您使用而不是建立您自己的開發人員命令提示字元捷徑。  
  
## <a name="open-a-developer-command-prompt"></a>開啟開發人員命令提示字元  
  
1.  如果您已安裝 Visual Studio 2017 Windows 10 上，開啟 [開始] 功能表，然後再向下捲動並開啟**Visual Studio 2017**資料夾 （不 Visual Studio 2017 應用程式）。 選擇**VS 2017 的開發人員命令提示字元**以開啟命令提示字元視窗。  
  
     如果您已安裝 Microsoft Visual c + + 建置工具 2015 Windows 10 上，開啟**啟動**功能表，然後向下的捲動並開啟**Visual c + + 建置工具**資料夾。 選擇**Visual c + + 2015 x86 Native Tools 命令提示字元**以開啟命令提示字元視窗。  
  
     如果您使用不同版本的 Visual Studio，或是執行不同版本的 Windows，尋找您的 開始 功能表中，或啟動 Visual Studio 工具 資料夾，其中包含開發人員命令提示字元捷徑的頁面。 您也可以使用 Windows search 函數來搜尋 」 開發人員命令提示字元，然後選擇符合您的 Visual Studio 安裝的版本。 使用捷徑來開啟 [命令提示字元] 視窗。  
  
2.  接下來，確認 Visual c + + 開發人員命令提示字元已正確設定。 在命令提示字元 視窗中，輸入`cl`並確認輸出看起來像下面這樣：  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>  
    ```  
  
     可能會有差異，在目前的目錄或版本號碼，視 Visual c + + 和安裝任何更新的版本而定。 如果這是類似您所看到的內容，則您必須準備好要建置 C 或 c + + 程式，在命令列。  
  
    > [!NOTE]
    >  如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，當您執行**cl**命令時，則可能您不使用開發人員命令提示字元，或有問題的 Visual c + + 安裝。 您必須先修正此問題，然後才能繼續。  
  
     如果您找不到開發人員命令提示字元 捷徑，或如果您收到錯誤訊息，當您輸入`cl`，Visual c + + 安裝可能會有問題。 請嘗試重新安裝 Visual c + + 元件，在 Visual Studio 中，或重新安裝 Visual Studio 建置工具。 不要繼續進行下一節之前可以這麼做。 如需安裝和 Visual c + + 疑難排解的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。  
  
    > [!NOTE]
    >  根據電腦等系統安全性設定的 Windows 版本，您可能必須按一下滑鼠右鍵以開啟 開發人員命令提示字元捷徑的捷徑功能表，然後選擇**系統管理員身分執行**至已成功建置並執行您依照本逐步解說建立的程式。  
  
## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>建立 C 原始程式檔和命令列上進行編譯  
  
1.  在 [開發人員命令提示字元] 視窗中，輸入**cd c:\\** 目前工作目錄變更到 c： 磁碟機的根目錄。 接下來，輸入**md c:\simple**建立的目錄，然後輸入**cd c:\simple**變更到該目錄。 這是將包含原始程式檔和編譯的程式的目錄。  
  
2.  輸入**記事本 simple.c**在開發人員命令提示字元。 在快顯的 「 記事本 」 警示的對話方塊，選擇**是**在您的工作目錄中建立新的 simple.c 檔案。  
  
3.  在記事本中，輸入下列程式碼：  
  
    ```C  
    #include <stdio.h>  
  
    int main()  
    {  
        printf("Hello, World! This is a native C program compiled on the command line.\n");  
        return 0;  
    }   
    ```  
  
4.  在 記事本 功能表列上選擇 **檔案**，**儲存**simple.c 儲存您的工作目錄中。  
  
5.  切換回開發人員命令提示字元視窗。 輸入**dir**在命令提示字元中列出 c:\simple 目錄的內容。 您應該會看到類似如下的目錄清單中的來源檔案 simple.c:  
  
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
  
     日期及其他詳細資料會不同於您的電腦。 如果您沒有看到您的原始程式碼檔，simple.c，請確定您已變更至您所建立，c:\simple 目錄，並在 [記事本]，請確定您在此目錄中儲存原始程式檔。 也請確定您使用 .c 檔案的副檔名，不是.txt 副檔名儲存的原始程式碼。  
  
6.  若要編譯您的程式，請輸入**cl simple.c**在開發人員命令提示字元。  
  
     您可以看到可執行的程式名稱，simple.exe，則編譯器會顯示的輸出資訊行中：  
  
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
    >  如果您收到錯誤，例如 「 'cl' 無法辨識為內部或外部命令、 可執行程式或批次檔 」 錯誤、 錯誤 C1034 或錯誤 LNK1104，您的開發人員命令提示字元未正確設定。 如需如何修正此問題的資訊，請回到**開啟開發人員命令提示字元**> 一節。  
  
    > [!NOTE]
    >  如果您收到不同的編譯器或連結器錯誤或警告，請檢閱您的原始程式碼，更正任何錯誤，然後加以儲存，並再次執行編譯器。 如需特定錯誤的資訊，此 MSDN 頁面上使用 [搜尋] 方塊尋找錯誤號碼。  
  
7.  若要執行您的程式，請輸入**簡單**在命令提示字元。  
  
     程式會顯示下列文字並結束：  
  
    ```Output  
    Hello, World! This is a native C program compiled on the command line.  
    ```  
  
     恭喜，您只編譯並執行 C 程式中使用命令列。  
  
## <a name="next-steps"></a>後續步驟  
 這個"Hello，World"範例是大約像簡單 C 程式可以取得。 真實世界的程式有標頭檔和多個原始程式檔，在程式庫，連結，然後執行有用的工作。  
  
 您可以使用在本逐步解說的步驟來建置您自己的 C 程式碼，而不是輸入所顯示的範例程式碼。 您也可以建立許多 C 程式碼的範例程式，您會發現其他位置。 若要編譯的程式有多個原始程式碼檔，請在命令列中，像這樣中輸入：  
  
 `cl file1.c file2.c file3.c`  
  
 編譯器輸出 file1.exe 程式。 若要變更 program1.exe 名稱，加入[/out](../build/reference/out-output-file-name.md)連結器選項：  
  
 `cl file1.c file2.c file3.c /link /out:program1.exe`  
  
 以自動擷取更多的程式設計錯誤，我們建議您編譯使用[/W3](../build/reference/compiler-option-warning-level.md)或[/W4](../build/reference/compiler-option-warning-level.md)警告層級的選項：  
  
 `cl /W4 file1.c file2.c file3.c /link /out:program1.exe`  
  
 編譯器，cl.exe，有許多其他選項，您可以套用建置、 最佳化、 偵錯及分析您的程式碼。 如需快速的清單中，輸入**cl /？** 在開發人員命令提示字元。 您也可以編譯和個別連結，連結器選項建置更複雜的案例中套用。 如需有關編譯器和連結器選項和使用方式的詳細資訊，請參閱[C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)。  
  
 您可以使用 NMAKE makefile 或 MSBuild 和專案檔來設定和在命令列上建置更複雜的專案。 如需有關使用這些工具的詳細資訊，請參閱[NMAKE 參考](../build/nmake-reference.md)和[MSBuild](../build/msbuild-visual-cpp.md)。  
  
 C 和 c + + 語言非常類似，但不是相同。 Visual c + + 編譯器會使用簡單的規則來決定在編譯程式碼時使用的語言。 根據預設，Visual C++ 編譯器會將以 .c 結尾的所有檔案都視為 C 原始程式碼，並會將以 .cpp 結尾的所有檔案都視為 C++ 原始程式碼。 若要強制編譯器忽視副檔名將所有檔案都視為 C，請使用[/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項。  
  
 Visual c + + C 編譯器會通常與 ISO C99 標準相容，但不是完全相容。 在大部分情況下，可移植的 C 程式碼會編譯，並如預期般執行。 Visual c + + 不支援 ISO C11 中大部分的變更。 Visual c + + 編譯器已被取代特定的程式庫函式和 POSIX 函式名稱。 支援的函式，但慣用的名稱已變更。 如需詳細資訊，請參閱[CRT 中安全性功能](../c-runtime-library/security-features-in-the-crt.md)和[編譯器警告 （層級 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說： 建立標準 c + + 程式 （c + +）](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [C 語言參考](../c-language/c-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)   
 [相容性](../c-runtime-library/compatibility.md)