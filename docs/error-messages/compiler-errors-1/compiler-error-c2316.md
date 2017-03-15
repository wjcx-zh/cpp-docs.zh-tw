---
title: "編譯器錯誤 C2316 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2316"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2316"
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C2316
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'exception': 無法攔截，因為無法存取解構函式及\/或複製建構函式  
  
 以傳值方式或以傳址方式攔截到例外狀況，但是複製建構函式及\/或指派運算子都無法存取。  
  
 舊版本的編譯器接受此程式碼，但是現在卻產生錯誤。  
  
## 範例  
 下列範例會產生 C2316：  
  
```  
// C2316.cpp // compile with: /EHsc #include <stdio.h> extern "C" int printf_s(const char*, ...); struct B { public: B() {} // Delete the following line to resolve. private: // copy constructor B(const B&) { } }; void f(const B&) { } int main() { try { B aB; f(aB); } catch (B b) {   // C2316 printf_s("Caught an exception!\n"); } }  
```