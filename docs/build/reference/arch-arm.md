---
title: "/arch (ARM) | Microsoft Docs"
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
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /arch (ARM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為 ARM 上的程式碼產生指定架構。  請參閱 [\/arch \(x86\)](../../build/reference/arch-x86.md) 和 [\/arch \(x64\)](../../build/reference/arch-x64.md)。  
  
## 語法  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## 引數  
 **\/arch:ARMv7VE**  
 啟用 ARMv7VE 虛擬擴充功能指令。  
  
 **\/arch:VFPv4**  
 啟用 ARM VFPv4 指令。  如果未指定此選項，VFPv3 就是預設值。  
  
## 備註  
 `_M_ARM_FP` 巨集 \(僅適用於 ARM\) 指示已使用哪個 **\/arch** 編譯器選項 \(如果有的話\)。  如需詳細資訊，請參閱[預先定義的巨集](../../preprocessor/predefined-macros.md)。  
  
 當您使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，**\/arch** 不會對 Managed 函式的程式碼產生有任何影響。  **\/arch** 僅會影響原生函式的程式碼產生。  
  
### 若要在 Visual Studio 中設定 \/arch:ARMv7VE 或 \/arch:VFPv4 編譯器選項  
  
1.  開啟專案的 \[屬性頁\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[其他選項\] 方塊中，加入 `/arch:ARMv7VE` 或 `/arch:VFPv4`。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。  
  
## 請參閱  
 [\/arch \(最小 CPU 架構\)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)