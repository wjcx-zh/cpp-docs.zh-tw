---
title: "逐步解說：在命令列上編譯 C++/CX 程式 | Microsoft Docs"
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
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：在命令列上編譯 C++/CX 程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立以 Windows 執行階段為目標的 Visual C\+\+ 程式，並在命令列上建置它們。  Visual C\+\+ 支援 Visual C\+\+ 元件擴充功能 \(C\+\+\/CX\)，其具有以 WinRT 執行階段程式設計模型為目標的其他類型及運算子。  您可以使用 C\+\+\/CX，以建置 Windows Phone 8.1、Windows 市集及 Windows 桌面的應用程式。  如需相關資訊，請參閱 [C\+\+\/CX 導覽](http://msdn.microsoft.com/magazine/dn166929.aspx)及[Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)。  
  
 在此逐步解說中，您可以使用文字編輯器來建立基本的 C\+\+\/CX 程式，然後在命令列上進行編譯。  \(您可以使用自己的 C\+\+\/CX 程式，而不是輸入所顯示的程式，或者您可以使用其他說明文章中的 C\+\+\/CX 程式碼範例。  這項技術對於建置和測試不包含 UI 項目的小模組非常有用\)。  
  
> [!NOTE]
>  您還可以使用 Visual Studio IDE，來編譯 C\+\+\/CX 程式。  因為這個 IDE 包括設計、偵錯、模擬以及在命令列上無法使用的部署支援，我們建議您使用 IDE 建置 Windows 市集應用程式。  如需詳細資訊，請參閱[Create a basic C\+\+ Store app](http://msdn.microsoft.com/library/windows/apps/dn263168)。  
  
## 必要條件  
 您必須了解 C\+\+ 語言的基本概念。  
  
## 編譯 C\+\+\/CX 程式  
 若要啟用 C\+\+\/CX 的編譯，您必須使用 [\/ZW](../build/reference/zw-windows-runtime-compilation.md) 編譯器選項。  Visual C\+\+ 編譯器會產生以 Windows 執行階段為目標的 .exe 檔案，並會連結至所需的程式庫。  
  
#### 在命令列上編譯 C\+\+\/CX 應用程式  
  
1.  開啟 \[開發人員命令提示字元\] 視窗   \(在 \[開始\] 視窗上，開啟 \[應用程式\]。  開啟您 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本下的 \[Visual Studio Tools\] 資料夾，然後選擇 \[開發人員命令提示字元\] 捷徑\)。如需如何開啟 \[命令提示字元\] 視窗的詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
     若要成功編譯程式碼，需要系統管理員認證，具體取決於電腦的作業系統及組態。  若要以系統管理員身分執行 \[命令提示字元\] 視窗，請開啟 \[開發人員命令提示字元\]  的捷徑功能表，然後選擇 \[以系統管理員身分執行\]。  
  
2.  在命令提示字元處，輸入 **notepad basiccx.cpp**。  
  
     當系統提示您建立檔案時，選擇 \[是\]。  
  
3.  在 \[記事本\] 中，輸入下列行：  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  在功能表列上，選擇 \[檔案\]、\[儲存\]。  
  
     您已建立使用 Windows 執行階段[Platform 命名空間](../Topic/Platform%20namespace%20\(C++-CX\).md)命名空間的 Visual C\+\+ 原始檔。  
  
5.  在命令提示字元處，輸入 **cl \/EHsc \/ZW basiccx.cpp \/link \/SUBSYSTEM:CONSOLE**。  cl.exe 編譯器會將原始程式碼編譯為 .obj 檔案，然後執行連結器，以產生名為 basiccx.exe 的可執行程式   \([\/EHsc](../build/reference/eh-exception-handling-model.md) 編譯器選項會指定 C\+\+ 例外狀況處理模型，而 [\/link](../build/reference/link-pass-options-to-linker.md) 旗標會指定主控台應用程式\)。  
  
6.  若要執行 basiccx.exe 程式，請在命令提示字元下，輸入 **basiccx**。  
  
     程式會顯示下列文字並結束：  
  
  **這是 C\+\+\/CX 程式。**  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C\/C\+\+ 程式](../build/building-c-cpp-programs.md)   
 [編譯器選項](../build/reference/compiler-options.md)