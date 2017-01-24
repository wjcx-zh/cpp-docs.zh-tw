---
title: "編譯器錯誤 C2085 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2085"
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 不在型式參數清單中  
  
 識別項宣告於函式定義中，但未出現在型式參數清單 \(Formal Parameter\) 內 \(僅適用於 ANSI C\)。  
  
 下列範例會產生 C2085：  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 可能的解決方案：  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 如果遺漏分號，`func1()` 看起來就像一個函式定義，而非原型 \(Prototype\)，因此將 `main` 定義在 `func1()`，將會產生識別項 `main` 的錯誤 C2085。