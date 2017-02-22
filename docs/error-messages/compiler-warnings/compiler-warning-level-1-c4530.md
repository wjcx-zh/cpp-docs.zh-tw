---
title: "編譯器警告 (層級 1) C4530 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4530"
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已使用 C\+\+ 例外狀況處理常式，但沒有啟用回溯語意 \(Unwind Semantics\)。請指定 \/EHsc  
  
 已使用 C\+\+ 例外狀況處理，但未選擇 [\/EHsc](../../build/reference/eh-exception-handling-model.md)。  
  
 當沒有啟用 \/EHsc 選項時，框架 \(Frame\) 中位於函式擲出與捕捉擲出之間的自動儲存物件不會被終結。  然而，建立於 **try** 或 **catch** 區段的自動儲存物件會被終結。  
  
 下列範例會產生 C4530：  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 以 \/EHsc 編譯範例，以解除警告。