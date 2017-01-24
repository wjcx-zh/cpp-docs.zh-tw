---
title: "編譯器錯誤 C2164 | Microsoft Docs"
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
  - "C2164"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2164"
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2164
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 內建函式未宣告  
  
 `intrinsic` Pragma 使用了未宣告的函式 \(僅發生於使用**\/Oi** 時\)。  或是，使用了一個編譯器內建函式，但未包含其標頭檔 \(Header File\)。  
  
 下列範例會產生 C2164：  
  
```  
// C2164.c  
// compile with: /c  
// processor: x86  
// Uncomment the following line to resolve.  
// #include "xmmintrin.h"  
void b(float *p) {  
   _mm_load_ss(p);   // C2164  
}  
```