---
title: "編譯器警告 (層級 1) C4313 | Microsoft Docs"
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
  - "C4313"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4313"
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4313
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 格式字串中的 'format specifier' 與引數數目 \(屬於類型 'type'\) 衝突  
  
 指定的格式與您所傳遞的值之間沒有衝突。  例如，您傳遞 64 位元的參數至未限定的 %d 格式規範，但其預期的是 32 位元的整數參數。  當程式碼是針對 64 位元目標編譯時，這個警告才有效。  
  
## 範例  
 使用 64 位元目標編譯時，下列程式碼範例會產生 C4313。  
  
```  
// C4313.cpp  
// Compile by using: cl /W1 C4313.cpp  
#include <stdio.h>  
int main() {  
   int * pI = 0;  
   printf("%d", pI);   // C4313 on 64-bit platform code  
   // Try one of the following lines instead:  
   // printf("%p\n", pI);  
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information  
}  
```