---
title: "逐步解說：在命令列上編譯原生 C++ 程式 | Microsoft Docs"
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
  - "命令列應用程式 [C++], native"
  - "編譯程式 [C++]"
  - "機器碼 [C++]"
  - "Visual C++, 機器碼"
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
caps.latest.revision: 63
caps.handback.revision: 57
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：在命令列上編譯原生 C++ 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 包含命令列的 C\+\+ 編譯器，可讓您建立各式各樣的應用程式，從基本的主控應用程式，到通用 Windows 應用程式、Windows 市集應用程式及 .NET 元件，一應俱全。  
  
 在此逐步解說中，您可以使用文字編輯器來建立基本的 Visual C\+\+ 主控台程式，然後在命令列上進行編譯。  
  
> [!NOTE]
>  您還可以使用 Visual Studio 整合式開發環境 \(IDE\)，來編譯 Visual C\+\+ 程式。 如需詳細資訊，請參閱[逐步解說：使用專案和方案 \(C\+\+\)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)。  
  
 在此逐步解說中，您可以使用自己的 Visual C\+\+ 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 Visual C\+\+ 程式碼範例。  
  
## 必要條件  
 若要完成此逐步解說，您使用的 Visual Studio 版本必須包含 Visual C\+\+ 元件。 這對於了解 C\+\+ 語言的基本概念很有幫助。 這些指示假設您使用 Windows 10 與 Visual Studio 2015，對於其他環境與版本的指示則類似。  
  
### 建立 Visual C\+\+ 原始程式檔並在命令列中進行編譯  
  
1.  首先，請開啟 \[開發人員命令提示字元\]。 Visual C\+\+ 編譯器需要特殊的命令環境才能執行，因此在此逐步解說中，您無法使用一般的命令提示字元。  
  
     在 Windows 的 \[開始\] 功能表中，開啟 \[所有應用程式\]。 捲動以尋找並開啟所用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本的 **Visual Studio** 資料夾，然後選擇 \[開發人員命令提示字元\] 捷徑。  
  
2.  建立新目錄來保存您的程式。 在 \[開發人員命令提示字元\] 視窗中輸入 `cd \` 命令，將目錄變更為磁碟機的根目錄。 輸入 `md examples` 命令，為範例程式碼建立目錄。 輸入 `cd examples` 命令，將該目錄設為目前的工作目錄。 這是您第一個程式的存放位置。  
  
3.  在命令提示字元中，輸入 **notepad basic.cpp**。  
  
     當系統提示您建立檔案時，選擇 \[是\]。 這會開啟空白的 \[記事本\] 視窗，讓您在其中輸入您的程式碼。  
  
4.  在 \[記事本\] 中，輸入下列行：  
  
    ```cpp  
    #include <iostream> using namespace std; void main() { cout << "Hello, world, from Visual C++!" << endl; }  
    ```  
  
     這是非常簡單的程式，會在螢幕上書寫一行文字，然後結束。 若要將錯誤數降至最低，請複製此程式碼，再將其貼到記事本中。  
  
5.  儲存您的工作！ 在 \[記事本\] 的 \[檔案\] 功能表中，選擇 \[儲存\]。  
  
     您即已建立 Visual C\+\+ 原始程式檔。  
  
6.  在命令提示字元中輸入 `cl /EHsc hello.cpp`，以編譯您的程式。  
  
     cl.exe 編譯器會產生內含編譯後之程式碼的 .obj 檔案，然後執行連結器，以建立名為 basic.exe 的可執行程式。 此名稱會出現在編譯器所顯示輸出資訊行中。 編譯器的輸出類似如下：  
  
    ```Output  
    適用於 x86 的 Microsoft (R) C/C++ 最佳化編譯器 19.00.23504 版。Copyright (C) Microsoft Corporation.  著作權所有，並保留一切權利。 hello.cpp Microsoft (R) Incremental Linker 14.00.23504.0 版。Copyright (C) Microsoft Corporation.  著作權所有，並保留一切權利。 /out:hello.exe hello.obj  
    ```  
  
     如有錯誤，請使用 \[記事本\] 檢查您的程式碼，確認其與範例完全相符。 儲存變更後，再次執行編譯器命令。  若找不到 cl 命令，請確認您是使用 \[開發人員命令提示字元\]，而不是一般的命令視窗。 若未安裝，便須安裝 Visual Studio 安裝程式中的 Visual C\+\+ 元件  
  
7.  若要執行 hello.exe 程式，請在命令提示字元下，輸入 `hello`。  
  
     程式會顯示下列文字並結束：  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     恭喜您，您已經使用命令列工具完成程式的建立並編譯。  
  
## 後續步驟  
 如需如何開啟 \[開發人員命令提示字元\] 視窗，以使用命令列工具的資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 若要成功編譯此逐步解說中的程式碼，需要系統管理員認證，具體取決於電腦的作業系統及設定。 若要以系統管理員身分執行 \[開發人員命令提示字元\] 視窗，請按一下滑鼠右鍵開啟 \[開發人員命令提示字元\]  的捷徑功能表，然後選擇 \[以系統管理員身分執行\]。  
  
 **\/EHsc** 命令列選項會指示編譯器啟用 C\+\+ 例外狀況處理。 如需詳細資訊，請參閱[\/EH \(例外狀況處理模型\)](../build/reference/eh-exception-handling-model.md)。  
  
## 請參閱  
 [Visual C\+\+ 導覽](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)   
 [編譯器選項](../build/reference/compiler-options.md)