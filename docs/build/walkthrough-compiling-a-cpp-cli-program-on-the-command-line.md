---
title: "逐步解說：在命令列上編譯 C++/CLI 程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
caps.latest.revision: 11
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：在命令列上編譯 C++/CLI 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立以通用語言執行階段 \(CLR\) 為目標且使用 .NET Framework 的 Visual C\+\+ 程式，並在命令列上建置它們。  Visual C\+\+ 支援 C\+\+\/CLI 程式設計語言，其具有其他類型及運算子，以將 .NET 程式設計模型設定為目標。  如需 C\+\+\/CLI 語言的簡介，請參閱 [Pure C\+\+：Hello, C\+\+\/CLI](http://msdn.microsoft.com/magazine/cc163681.aspx) \(英文\)。  如需一般資訊，請參閱 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
 在此逐步解說中，您可以使用文字編輯器來建立基本的 C\+\+\/CLI 程式，然後在命令列上進行編譯。  \(您可以使用自己的 C\+\+\/CLI 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C\+\+\/CLI 程式碼範例。  這項技術對於建置和測試不包含 UI 項目的小模組非常有用\)。  
  
> [!NOTE]
>  您還可以使用 Visual Studio IDE，來編譯 C\+\+\/CLI 程式。  如需詳細資訊，請參閱[逐步解說：編譯針對 Visual Studio 中 CLR 的 C\+\+ 程式](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md)。  
  
## 必要條件  
 您必須了解 C\+\+ 語言的基本概念。  
  
## 編譯 C\+\+\/CLI 程式  
 下列步驟顯示如何編譯使用 .NET Framework 類別的 C\+\+\/CLI 主控台應用程式。  
  
 若要啟用 C\+\+\/CLI 的編譯，您必須使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項。  Visual C\+\+ 編譯器會產生包含 MSIL 程式碼或混合的 MSIL 和機器碼的 .exe 檔案，並會連結至所需的 .NET Framework 程式庫。  
  
#### 在命令列上編譯 C\+\+\/CLI 應用程式  
  
1.  開啟 \[開發人員命令提示字元\] 視窗   \(在 \[開始\] 視窗上，開啟 \[應用程式\]。  開啟您 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本下的 \[Visual Studio Tools\] 資料夾，然後選擇 \[開發人員命令提示字元\] 捷徑\)。如需如何開啟 \[命令提示字元\] 視窗的詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
     若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。  若要以系統管理員身分執行 \[命令提示字元\] 視窗，請開啟 \[開發人員命令提示字元\]  的捷徑功能表，然後選擇 \[以系統管理員身分執行\]。  
  
2.  在命令提示字元處，輸入 **notepad basicclr.cpp**。  
  
     當系統提示您建立檔案時，選擇 \[是\]。  
  
3.  在 \[記事本\] 中，輸入下列行：  
  
    ```  
    int main()  
    {  
        System::Console::WriteLine("This is a C++/CLI program.");  
    }  
    ```  
  
4.  在功能表列上，選擇 \[檔案\]、\[儲存\]。  
  
     您即已建立 Visual C\+\+ 原始程式檔，其使用 <xref:System> 命名空間中的 .NET Framework 類別 \(<xref:System.Console>\)。  
  
5.  在命令提示字元處，輸入 **cl \/clr basicclr.cpp**。  cl.exe 編譯器會將原始程式碼編譯為包含 MSIL 的 .obj 檔案，然後執行連結器，以產生名為 basicclr.exe 的可執行程式  
  
6.  若要執行 basicclr.exe 程式，請在命令提示字元下，輸入 **basicclr**。  
  
     程式會顯示下列文字並結束：  
  
  **這是 C\+\+\/CLI 程式。**  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)   
 [編譯器選項](../build/reference/compiler-options.md)