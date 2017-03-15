---
title: "編譯器警告 (層級 3) C4197 | Microsoft Docs"
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
  - "C4197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4197"
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 略過型別轉換中最上層的 volatile 型別  
  
 編譯器偵測到使用 [volatile](../../cpp/volatile-cpp.md) 限定的 r\-value 型別轉換，或偵測到將 r\-value 型別轉換成某些使用 volatile 限定的型別。  根據 C 標準 \(6.5.3\)，與限定型別有關的屬性只對 l\-value 運算式有意義。  
  
 下列範例會產生 C4197：  
  
```  
// C4197.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <signal.h>  
#include <stdlib.h>  
  
void sigproc(int);  
struct S  
{  
   int i;  
} s;  
  
int main()  
{  
   signal(SIGINT, sigproc);  
   s.i = 1;  
   S *pS = &s;  
   for ( ; (volatile int)pS->i ; )   // C4197  
      break;  
   // for ( ; *(volatile int *)&pS->i ; )   // OK  
   //    break;  
}  
  
void sigproc(int) // ctrl-C  
{  
   signal(SIGINT, sigproc);  
   s.i = 0;  
}  
  
```