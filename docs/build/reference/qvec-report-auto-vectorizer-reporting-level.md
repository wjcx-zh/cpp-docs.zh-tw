---
title: "/Qvec-report (自動向量化工具報告層級) | Microsoft Docs"
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
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qvec-report (自動向量化工具報告層級)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用編譯器 [自動 Vectorizer](../../parallel/auto-parallelization-and-auto-vectorization.md) 的報告功能，並指定資訊訊息在編譯期間輸出的層級。  
  
## 語法  
  
```  
/Qvec-report:{1}{2}  
```  
  
## 備註  
 **\/Qvec\-report:1**  
 輸出向量化迴圈的資訊訊息。  
  
 **\/Qvec\-report:2**  
 與原因程式碼一起輸出向量化迴圈以及未向量化的 for 迴圈的資訊訊息。  
  
 如需更多錯誤代碼和訊息的詳細資訊，請參閱 [向量化工具和平行化工具訊息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
### 若要在 Visual Studio 中設定 \/Qvec\-report 編譯器選項  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[**屬性頁**\] 對話方塊，請在 \[**C\/C\+\+**\] 底下，選取 \[**命令列**\]。  
  
3.  在 \[**其他選項。**\] 方塊中輸入 `/Qvec-report: 1` 或 `/Qvec-report: 2`。  
  
### 若要以程式方式設定 \/Qvec\-report 編譯器選項  
  
-   請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [機器碼中的平行程式設計](http://go.microsoft.com/fwlink/?LinkId=263662)