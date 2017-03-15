---
title: "編譯器警告 (層級 1) C4556 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "xml"
  - "C4556"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4556"
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4556
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

內建函式直接引數 'value' 的值超出範圍 'lowerbound \- upperbound'  
  
 內建符合硬體指令。  硬體指令有固定的位元數，用來為常數編碼。  如果 ***value*** 超出範圍，就無法正確地編碼。  編譯器會截斷多餘的位元。  
  
 下列範例會產生 C4556：  
  
```  
// C4556.cpp  
// compile with: /W1  
// processor: x86 IPF  
#include <xmmintrin.h>  
void test()  
{  
   __m64 m;  
   _m_pextrw(m, 5);   // C4556  
}  
int main()  
{  
}  
```