---
title: "編譯器警告 (層級 3) C4290 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4290"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4290"
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器警告 (層級 3) C4290
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

略過 C\+\+ 例外狀況規格，除非將函式標示為非 \_\_declspec\(nothrow\)  
  
 函式是用 Visual C\+\+ 接受但未實作的例外狀況規格宣告的。  如果程式碼的例外狀況規格在編譯過程中被忽略了，那麼該程式碼可能必須重新編譯及連結，以便在新版的支援例外狀況規格中重複利用。  
  
 如需詳細資訊，請參閱[例外狀況規格 \(throw\)](../../cpp/exception-specifications-throw-cpp.md)。  
  
 您可以用 [warning](../../preprocessor/warning.md) Pragma 來避免此警告：  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 下列程式碼範例會產生 C4290：  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```