---
title: "編譯器警告 (層級 1) C4730 | Microsoft Docs"
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
  - "C4730"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4730"
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4730
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'main' : 混合 \_m64 和浮點運算式可能導致不正確的程式碼  
  
 函式使用 [\_\_m64](../../cpp/m64.md) 和 **float**\/**double** 型別。  由於 MMX 和浮點暫存器共用相同的實體暫存器空間 \(無法同時使用\)，若在同一個函式中使用 `__m64` 和 **float**\/**double** 型別會造成資料損毀，可能會引起例外狀況。  
  
 若要安全地在同一個函式中使用 `__m64` 型別和浮點數型別，每一個使用其中一個型別的指令都應該以 **\_m\_empty\(\)** \(供 MMX 使用\) 或 **\_m\_femms\(\)** \(供 3DNow\!\) 內建分隔。  
  
 下列範例會產生 C4730：  
  
```  
// C4730.cpp  
// compile with: /W1  
// processor: x86  
#include "mmintrin.h"  
  
void func(double)  
{  
}  
  
int main(__m64 a, __m64 b)  
{  
   __m64 m;  
   double f;  
   f = 1.0;  
   m = _m_paddb(a, b);  
   // uncomment the next line to resolve C4730  
   // _m_empty();  
   func(f * 3.0);   // C4730  
}  
```