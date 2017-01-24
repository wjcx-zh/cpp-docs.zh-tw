---
title: "C/C++ 建置參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "組建 [C++], 其他資訊"
  - "cl.exe 編譯器 [C++], 建置程式"
  - "編譯原始程式碼 [C++], 其他資訊"
  - "連結器 [C++], 建置參考"
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C/C++ 建置參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供了兩種建置 C\/C\+\+ 程式的方式，  最簡單也最常見的方式是[在 Visual C\+\+ 開發環境內建置](../../ide/building-cpp-projects-in-visual-studio.md)。  另一種則是[使用命令列工具從命令提示字元建置](../../build/building-on-the-command-line.md)。  無論選擇哪一種方式，您都可以使用 Visual C\+\+ 原始檔編輯器或是您慣用的協力廠商編輯器來建立原始程式檔 \(Source File\)。  
  
 如果您的程式是使用 Makefile 而非 .vcxproj 檔案，您仍然可以在開發環境中將之建立為[外部專案](../../ide/building-external-projects.md)。  
  
## 在本節中  
 [編譯 C\/C\+\+ 程式](../../build/reference/compiling-a-c-cpp-program.md)  
 說明編譯器會建立一個含有機器碼 \(Machine Code\)、連結器 \(Linker\) 指示詞、區段、外部參考及函式\/資料名稱的目的檔 \(Object File\)。  
  
 [連結](../../build/reference/linking.md)  
 說明連結器的功能，包括組合由編譯器建立的目的檔和靜態連結程式庫的程式碼、解析名稱參考，以及建立可執行檔。  
  
 [發行的組建](../../build/reference/release-builds.md)  
 提出由偵錯組建變更為發行的組建 \(Release Build\) 的原因及時機資訊，同時也探討進行這項變更時可能會面臨的問題。  
  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)  
 提供討論最佳化程式碼之機制的主題連結。  
  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)  
 提供下列命令列工具，用來檢視或操作建置輸出。  
  
 [C\/C\+\+ 建置錯誤](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 介紹目錄中的建置錯誤章節。  
  
## 相關章節  
 [C\/C\+\+ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)  
 討論前置處理器 \(Preprocessor\) 會藉由轉譯巨集、運算子和指示詞來為編譯器準備原始程式檔。  
  
 [瞭解自訂建置步驟和建置事件](../../ide/understanding-custom-build-steps-and-build-events.md)  
 討論自訂建置程序。  
  
 [建置 C\/C\+\+ 程式](../../build/building-c-cpp-programs.md)  
 提供主題連結，這些主題將描述如何從命令列或從 Visual Studio 整合式開發環境建置程式。  
  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)  
 說明在開發環境或在命令列上設定編譯器選項。  
  
 [編譯器選項](../../build/reference/compiler-options.md)  
 提供討論使用編譯器選項的主題連結。  
  
 [設定連結器選項](../../build/reference/setting-linker-options.md)  
 說明在整合式開發環境內部或外部設定連結器選項。  
  
 [連結器選項](../../build/reference/linker-options.md)  
 提供討論使用連結器選項的主題連結。  
  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)  
 說明 Microsoft Browse Information Maintenance Utility \(BSCMAKE.EXE\) 可根據編譯期間建立之 .sbr 檔，建置瀏覽資訊檔 \(Browse Information File，.bsc\)。  
  
 [LIB 參考](../../build/reference/lib-reference.md)  
 說明 Microsoft Library Manager \(LIB.exe\)，它可建立並管理通用物件檔案格式 \(Common Object File Format，COFF\) 目的檔的程式庫。  
  
 [EDITBIN 參考](../../build/reference/editbin-reference.md)  
 說明 Microsoft COFF 二進位檔案編輯器 \(EDITBIN.EXE\)，它可修改通用物件檔案格式 \(COFF\) 的二進位檔案。  
  
 [DUMPBIN 參考](../../build/reference/dumpbin-reference.md)  
 說明 Microsoft COFF 二進位檔案傾印工具 \(DUMPBIN.EXE\)，它可顯示關於通用物件檔案格式 \(COFF\) 二進位檔案的資訊。  
  
 [NMAKE 參考](../../build/nmake-reference.md)  
 說明 Microsoft Program Maintenance Utility \(NMAKE.EXE\)，它是會根據包含在描述檔中的命令來建置專案的工具。