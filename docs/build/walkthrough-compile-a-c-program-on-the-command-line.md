---
title: "逐步解說：在命令列上編譯 C 程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C 程式編譯 [C++]"
  - "命令列應用程式 [C++], C 程式"
  - "編譯程式 [C++]"
  - "Visual C, 編譯"
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
caps.latest.revision: 46
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：在命令列上編譯 C 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 包含 C 編譯器，可讓您用來建立任何程式，從基本的主控台程式到 Windows 桌面應用程式都沒有問題。  
  
 此逐步解說顯示如何使用文字編輯器來建立基本的 C 程式，然後在命令列上進行編譯。  
  
 您可以使用自己的 C 程式，而不需要輸入本逐步解說中顯示的範例程式。  您也可以使用在說明主題中包含的任何 C 程式碼範例程式。  
  
 根據預設，Visual C\+\+ 編譯器會將以 .c 結尾的所有檔案都視為 C 原始程式碼，並會將以 .cpp 結尾的所有檔案都視為 C\+\+ 原始程式碼。  若要強制編譯器忽視副檔名，而將所有檔案都視為 C，請使用 [\/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 編譯器選項。  
  
## 必要條件  
 您必須了解 C 語言的基本概念。  
  
### 若要建立 C 原始程式檔並在命令列中進行編譯  
  
1.  開啟開發人員命令提示字元。  在 Windows 8 的 \[**開始**\] 畫面上，開啟 \[**Visual Studio Tools**\] 資料夾，然後選擇 \[**開發人員命令提示字元**\] 捷徑。  在舊版 Windows 中，選擇 \[開始\] 按鈕，依序展開 \[所有程式\]、\[Microsoft Visual Studio\] 和 \[Visual Studio Tools\]，然後選擇 \[開發人員命令提示字元\]。  
  
     根據電腦上的 Windows 版本和系統安全性組態，您可能需要開啟 \[**開發人員命令提示字元**\] 的捷徑功能表，然後再選擇 \[**以系統管理員身分執行**\]，才能成功建置並執行以下列步驟建立的應用程式。  
  
    > [!NOTE]
    >  \[**開發人員命令提示字元**\] 會自動設定 C 編譯器及所有必要程式庫的正確路徑。  請使用此命令提示字元，而非一般的命令提示字元視窗。  如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
2.  在命令提示字元，建立原始程式檔的目錄，並將其設定為目前工作目錄。  例如，輸入 **md c:\\simple** 並按下 Enter，建立名為 simple 的目錄，然後輸入 **cd c:\\simple** 並按下 Enter，變更至該目錄。  
  
3.  在命令提示字元輸入 **notepad** 並按下 Enter。  
  
4.  在 \[記事本\] 中，輸入下列程式碼行。  
  
     [!code-cpp[NVC_Walkthrough_Compile_C#100](../build/codesnippet/CPP/walkthrough-compile-a-c-program-on-the-command-line_1.c)]  
  
5.  在功能表列上，選擇 \[**檔案**\]、\[**儲存檔案**\]，開啟 \[**另存新檔**\] 對話方塊。  巡覽至您已建立的目錄。  在 \[**檔案名稱**\] 方塊中，輸入原始程式檔的名稱 \(例如 simple.c\)，然後選取 \[**存檔類型**\] 下拉式清單中的 \[**所有檔案 \(\*.\*\)**\]。  選擇 \[**存檔**\] 按鈕，即可在工作目錄中建立 C 原始程式檔。  
  
6.  在命令提示字元輸入 **dir** 並按下 Enter。  您應該會看到所建立的原始程式檔：  
  
  **C:\\simple \> dir**  
 **Volume in drive C has no label. \(磁碟機 C 內的磁碟區沒有標籤。\)  Volume Serial Number is CC62\-6545 \(磁碟區序號為 CC62\-6545\)**  
 **Directory of C:\\simple \(C:\\simple 的目錄\)**  
**10\/02\/2012  03:46 PM    \<DIR\>          .  10\/02\/2012  03:46 PM    \<DIR\>          ..  10\/02\/2012  03:36 PM               102 simple.c**  
 **1 File\(s\)            102 bytes \(1 個檔案 102 個位元組\)**  
 **2 Dir\(s\)  514,900,566,016 bytes free \(2 個目錄 514,900,566,016 位元組的可用空間\)**      您電腦上顯示的詳細資料會略有不同。  如果您沒有看到您的原始程式碼檔案，請確定您已變更為所建立的目錄，並確定已將原始程式檔儲存在此目錄中。  
  
7.  在命令提示字元，一起指定 **cl** 命令和原始程式檔名稱 \(例如 **cl simple.c**\)，再按下 Enter 編譯程式。  cl.exe 編譯器會產生包含已編譯程式碼的 .obj 檔案，然後執行連結器，以建置可執行程式，其具有原始程式檔的名稱，但副檔名為 .exe，例如 simple.exe。  
  
     您可以在編譯器所顯示的輸出資訊行中看到可執行程式的名稱。  
  
     **輸出**  
  
  **Microsoft \(R\) C\/C\+\+ Optimizing Compiler Version 17.00.50727.1 for x86**  
**Copyright \(C\) Microsoft Corporation.  著作權所有，並保留一切權利。  simple.c**  
**Microsoft \(R\) Incremental Linker Version 11.00.50727.1**  
**Copyright \(C\) Microsoft Corporation.  著作權所有，並保留一切權利。  \/out:simple.exe**  
**simple.obj**      工具的版本號碼取決於 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本，以及您已安裝的任何更新。  
  
    > [!NOTE]
    >  如果發生類似「'cl' 不是內部或外部命令、可執行的程式或批次檔」的錯誤、錯誤 C1034 或錯誤 LNK1104，您必須設定適用於編譯器和工具的環境。  如需詳細資訊，請檢閱步驟 1。  
    >   
    >  如果發生編譯器錯誤或警告，請檢閱原始程式碼有無錯誤、儲存原始程式碼後再次執行編譯器。  如需有關特定錯誤的詳細資訊，請使用此頁面上的搜尋方塊。  
  
8.  若要執行程式，請輸入其名稱 \(不含副檔名，例如 **simple**\)，然後按下 Enter。  
  
     程式會顯示下列文字並結束：  
  
     `This is a native C program.`  
  
## 請參閱  
 [逐步解說：建立 Win32 主控台程式 \(C\+\+\)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [C 語言參考](../c-language/c-language-reference.md)   
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)   
 [相容性](../c-runtime-library/compatibility.md)