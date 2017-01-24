---
title: "/favor (專為架構最佳化) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/favor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-favor 編譯器選項 [C++]"
  - "/favor 編譯器選項 [C++]"
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /favor (專為架構最佳化)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生已為特定 **\/favor:**`option` 架構最佳化的程式碼，或為 AMD 和 Intel 架構中微架構特性最佳化的程式碼。  
  
## 語法  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## 備註  
 **\/favor:blend**  
 \(x86 and x64\) 會產生在 AMD 和 Intel 兩種架構中為微架構特性最佳化的程式碼。  雖然 **\/favor:blend** 可能無法在特定處理器上提供可能達到的最佳效能，但它的設計是要在跨一系列廣泛的 x86 及 x64 處理器上提供最佳效能。  **\/favor:blend** 預設為啟用。  
  
 **\/favor:ATOM**  
 \(x86 和 x64\) 會產生 Intel 原子處理器和 Intel Centrino 技術原子處理器技術的特定的最佳化的程式碼。  產生的程式碼使用 **\/favor:ATOM** 也可能會產生 Intel 處理器的 Intel SSSE3、 SSE3、SSE 和 SSE2 指令。  
  
 **\/favor:AMD64**  
 \(x64 only\) 會為 AMD Opteron 及支援 64 位元擴充功能的 Athlon 處理器最佳化所產生的程式碼。  最佳化的程式碼可以在所有 x64 相容平台上執行。  使用 **\/favor:AMD64** 所產生的程式碼，可能會在支援 Intel64 的 Intel 處理器上產生較差的效能。  
  
 **\/favor:INTEL64**  
 \(x64 only\) 最佳化為支援 Intel64 的 Intel 處理器所產生的程式碼，一般來說，會為該平台產生較佳效能。  所產生的程式碼可以在任何 x64 平台上執行。  使用 **\/favor:INTEL64** 所產生的程式碼，可能會在 AMD Opteron 及支援 64 位元擴充功能的 Athlon 處理器上產生較差的效能。  
  
> [!NOTE]
>  Intel64 架構先前稱為延伸記憶體 64 技術，對應的編譯器選項為 **\/favor:EM64T**。  
  
 如需 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 架構程式設計的詳細資訊，請參閱 [x64 軟體慣例](../../build/x64-software-conventions.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)