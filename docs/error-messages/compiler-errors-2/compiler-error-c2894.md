---
title: "編譯器錯誤 C2894 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2894"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2894"
ms.assetid: 4e250579-2b59-4993-a6f4-49273e7ecf06
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2894
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不可以宣告樣板擁有 'C' 連結  
  
 這項錯誤可能是因為 `extern` "C" 區塊之中所定義的樣板而產生。  
  
 下列範例會產生 C2894：  
  
```  
// C2894.cpp  
extern "C" {  
   template<class T> class stack {};   // C2894 fail  
  
   template<class T> void f(const T &aT) {}   // C2894  
}  
```  
  
 下列範例會產生 C2894：  
  
```  
// C2894b.cpp  
// compile with: /c  
extern "C" template<class T> void f(const T &aT) {}   // C2894  
  
template<class T> void f2(const T &aT) {}   // OK  
```