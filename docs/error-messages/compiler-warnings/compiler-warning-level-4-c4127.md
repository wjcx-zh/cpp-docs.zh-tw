---
title: "編譯器警告 （層級 4） C4127 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 6197f0018ebb6f23b4608e376282b32cd030ba30
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4127"></a>編譯器警告 (層級 4) C4127
條件運算式是常數  
  
 `if` 陳述式或 `while` 迴圈的控制運算式會評估為常數。 因為其常見慣用語，一般的常數，例如 1 或`true`不會觸發警告，除非它們是在運算式中作業的結果。 如果的控制運算式的`while`迴圈是一個常數，因為迴圈結束，中間，請考慮更換`while`迴圈與`for`迴圈。 您可以略過初始化，結束測試並迴圈的遞增`for`迴圈，會導致無限的就像迴圈`while(1)`，，您可以結束迴圈的主體`for`陳述式。  
  
 下列範例會示範兩種方式 C4127 產生，並示範如何使用 for 迴圈來避免警告︰  
  
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
