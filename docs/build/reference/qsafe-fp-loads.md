---
title: "/Qsafe_fp_loads | Microsoft Docs"
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
ms.assetid: 2b2ce52d-ba57-4bd3-a739-47a7f8bfaba9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qsafe_fp_loads
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

需要浮點值的整數移動指令，並停用特定浮點數負載最佳化。  
  
## 語法  
  
```  
/Qsafe_fp_loads  
```  
  
## 備註  
 **\/Qsafe\_fp\_loads** 僅供以 x86 為目標的編譯器；在針對 x64 或 ARM 的編譯器中無法使用。  
  
 **\/Qsafe\_fp\_loads** 強制編譯器使用整數移動指令而非浮點移動指令來在記憶體和 MMX 暫存器之間移動資料。  這個選項也會停用暫存器可在多個控制項路徑的浮點數值的載入最佳化，當值可能會導致例外狀況載入，例如 NaN 值載入。  
  
 這個選項是由 [\/fp:except](../../build/reference/fp-specify-floating-point-behavior.md)覆寫。  **\/Qsafe\_fp\_loads** 指定由 **\/fp:except**指定的編譯器行為的子集。  
  
 **\/Qsafe\_fp\_loads** 與 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 和 [\/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md)不相容。  如需浮點編譯器選項的詳細資訊，請參閱 [\/fp \(指定浮點數行為\)](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)