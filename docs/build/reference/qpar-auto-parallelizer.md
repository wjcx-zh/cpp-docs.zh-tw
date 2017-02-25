---
title: "/Qpar (自動平行化工具) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration"
dev_langs: 
  - "C++"
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Qpar (自動平行化工具)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使編譯器的 [自動 Parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md) 功能會在自己的程式碼自動平行迴圈。  
  
## 語法  
  
```  
/Qpar  
```  
  
## 備註  
 當編譯器自動平行迴圈程式碼時，它會散佈多處理器核心的計算。  只有編譯器判斷是合法的做法，且平行處理會改善效能時，迴圈會平行處理。  
  
 `#pragma loop()` 指示詞可以協助最佳化程式平行處理特定的迴圈。  如需詳細資訊，請參閱[迴圈](../../preprocessor/loop.md)。  
  
 如需關於自動 parallelizer 允許輸出訊息的方式的詳細資訊，請參閱 [\/Qpar\-report \(自動平行化工具報告層級\)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)。  
  
### 若要在 Visual Studio 中設定 \/Qpar 編譯器選項  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[**屬性頁**\] 對話方塊，請在 \[**C\/C\+\+**\] 底下，選取 \[**命令列**\]。  
  
3.  在 \[**其他選項。**\] 方塊中，輸入 `/Qpar`。  
  
### 若要以程式方式設定 \/Qpar 編譯器選項  
  
-   請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [\/Qpar\-report \(自動平行化工具報告層級\)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\#pragma loop\(\)](../../preprocessor/loop.md)   
 [機器碼中的平行程式設計](http://go.microsoft.com/fwlink/?LinkId=263662)