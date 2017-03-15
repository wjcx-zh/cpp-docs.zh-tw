---
title: "/arch (x64) | Microsoft Docs"
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
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /arch (x64)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 x64 上，為程式碼產生指定架構。  另請參閱 [\/arch \(x86\)](../../build/reference/arch-x86.md) 和 [\/arch \(ARM\)](../../build/reference/arch-arm.md)。  
  
## 語法  
  
```  
/arch:[AVX|AVX2]  
```  
  
## 引數  
 **\/arch:AVX**  
 啟用 Intel Advanced Vector Extensions 指令的使用。  
  
 **\/arch:AVX2**  
 啟用 Intel Advanced Vector Extensions 2 指令的使用。  
  
## 備註  
 **\/arch** 僅會影響原生函式的程式碼產生。  當您使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，**\/arch** 不會對 Managed 函式的程式碼產生有任何影響。  
  
 指定 `__AVX__` 編譯器選項時，會定義 **\/arch:AVX** 前置處理器符號。  指定 `__AVX2__` 編譯器選項時，會定義 **\/arch:AVX2** 前置處理器符號。  如需詳細資訊，請參閱[預先定義的巨集](../../preprocessor/predefined-macros.md)。  **\/arch:AVX2** 選項已引入 Visual Studio 2013 Update 2 12.0.34567.1 版。  
  
### 在 Visual Studio 中設定 \/arch:AVX 或 \/arch:AVX2 編譯器選項  
  
1.  開啟專案的 \[屬性頁\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[配置屬性\]、\[C\/C\+\+\] 資料夾。  
  
3.  選取 \[**程式碼產生**\] 屬性頁。  
  
4.  在 \[啟用進階指令集\] 下拉式方塊中，選擇 \[Advanced Vector Extensions \(\/arch:AVX\)\] 或 \[Advanced Vector Extensions 2 \(\/arch:\/AVX2\)\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## 請參閱  
 [\/arch \(最小 CPU 架構\)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)