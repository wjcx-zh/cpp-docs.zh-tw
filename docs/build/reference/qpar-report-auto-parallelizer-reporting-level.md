---
title: "/Qpar-report (自動平行化工具報告層級) | Microsoft Docs"
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
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qpar-report (自動平行化工具報告層級)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用編譯器的 [Auto\-Parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md) 報告功能，並指定在編譯期間輸出的資訊訊息層級。  
  
## 語法  
  
```  
/Qpar-report:{1}{2}  
```  
  
## 備註  
 **\/Qpar\-report:1**  
 輸出已平行化之迴圈的資訊訊息。  
  
 **\/Qpar\-report:2**  
 輸出已平行化之迴圈的資訊訊息，並輸出未平行化之迴圈的資訊訊息連同原因碼。  
  
 訊息會報告至 stdout。  如果未報告資訊訊息，則可能是程式碼不包含迴圈，或是報告層級並未設定成報告未平行化的迴圈。  如需原因碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。  
  
### 在 Visual Studio 中設定 \/Qpar 編譯器選項  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[**屬性頁**\] 對話方塊，選取 \[**C\/C\+\+**\] 底下的 \[**命令列**\]。  
  
3.  在 \[其他選項\] 方塊中，輸入 `/Qpar-report:1` 或 `/Qpar-report:2`。  
  
### 以程式設計方式設定 \/Qpar\-report 編譯器選項  
  
-   請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [使用機器碼的平行程式設計](http://go.microsoft.com/fwlink/?LinkId=263662)