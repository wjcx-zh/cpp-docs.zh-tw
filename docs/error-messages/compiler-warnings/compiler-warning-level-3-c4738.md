---
title: "編譯器警告 (層級 3) C4738 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4738"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4738"
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 3) C4738
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在記憶體中儲存 32 位元浮點結果，可能會損失效能  
  
 C4738 是警告指派、轉型、傳遞引數，或其他運算的結果可能需要進行捨入，否則該運算可能會耗盡暫存器而需要使用記憶體 \(溢出\)。  這樣可能會造成效能損失。  
  
 若要解除這項警告並避免捨入，請用 [\/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md) 編譯，或使用 `double` 代替 `float`。  
  
 若要解除這項警告並避免耗盡暫存器，請變更計算順序，並修改您的內嵌使用情形。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 範例  
 下列範例會產生 C4738：  
  
```  
// C4738.cpp  
// compile with: /c /fp:precise /O2 /W3  
// processor: x86  
#include <stdio.h>  
  
#pragma warning(default : 4738)  
  
float func(float f)  
{  
    return f;  
}  
  
int main()  
{  
    extern float f, f1, f2;  
    double d = 0.0;  
  
    f1 = func(d);  
    f2 = (float) d;  
    f = f1 + f2;   // C4738  
    printf_s("%f\n", f);  
}  
```