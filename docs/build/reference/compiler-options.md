---
title: "編譯器選項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器"
  - "編譯器選項, C++"
  - "IPF Visual C++ 編譯器"
  - "Itanium Visual C++ 編譯器"
  - "x64 Visual C++ 編譯器"
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# 編譯器選項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cl.exe 是控制 Microsoft C 和 C\+\+ 編譯器和連結器的工具。cl.exe 在支援 Microsoft Visual Studio 的作業系統上才能執行。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動這個工具。  您不能從系統命令提示字元或從檔案總管來啟動它。  
  
 編譯器會產生通用物件檔案格式 \(Common Object File Format，COFF\) 的目的檔 \(.obj\)。  連結器會產生可執行檔 \(.exe\) 或動態連結程式庫 \(DLL\)。  
  
 請注意，所有編譯器選項都必須區分大小寫。  
  
 若只要編譯而不要連結，請使用 [\/c](../../build/reference/c-compile-without-linking.md)。  
  
## 尋找選項  
 若要尋找特定的編譯器選項，請參閱下列兩種清單：  
  
-   [依字母順序排列的編譯器選項](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)  
  
## 指定選項  
 每一項編譯器選項的主題都會討論如何在開發環境中設定。  如需如何在開發環境外部指定選項的詳細資訊，請參閱：  
  
-   [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)  
  
-   [CL 命令檔](../../build/reference/cl-command-files.md)  
  
-   [CL 環境變數](../../build/reference/cl-environment-variables.md)  
  
## 相關組建工具  
 使用 [NMAKE](../../build/nmake-reference.md) 建置 \(Build\) 您的輸出檔。  
  
 使用 [BSCMAKE](../../build/reference/bscmake-reference.md) 支援類別瀏覽。  
  
 [連結器選項](../../build/reference/linker-options.md)也會影響程式建置的方式。  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [快速編譯](../../build/reference/fast-compilation.md)   
 [CL 叫用連結器](../../build/reference/cl-invokes-the-linker.md)