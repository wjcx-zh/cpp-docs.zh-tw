---
title: "編譯器警告 （層級 4） C4127 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4127
dev_langs: C++
helpviewer_keywords: C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1a5bbd86b6197907f043478df225dceb79679f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4127"></a>編譯器警告 (層級 4) C4127
條件運算式是常數  
  
 `if` 陳述式或 `while` 迴圈的控制運算式會評估為常數。 因為其常見慣用語，一般的常數，例如 1 或`true`不會觸發警告，除非它們是在運算式中作業的結果。 如果的控制運算式`while`迴圈是一個常數，因為在中間結束迴圈，請考慮更換`while`迴圈`for`迴圈。 您可以省略初始化、 終止測試，並在迴圈的遞增`for`迴圈，而會導致無限的就像迴圈`while(1)`，您可以結束迴圈的主體和`for`陳述式。  
  
 下列範例示範兩種方式會產生 C4127，並示範如何使用 for 迴圈來避免這個警告：  
  
```  
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (1 == 1) {}   // C4127  
   while (42) { break; }   // C4127  
  
   // OK  
   for ( ; ; ) {  
      printf("test\n");  
      break;  
   }  
}  
```