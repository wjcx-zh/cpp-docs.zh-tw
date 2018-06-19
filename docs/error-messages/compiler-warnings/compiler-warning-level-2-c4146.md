---
title: 編譯器警告 （層級 2） C4146 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4146
dev_langs:
- C++
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a94d2aed0b455fda646214f4488c53045b7f6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296685"
---
# <a name="compiler-warning-level-2-c4146"></a>編譯器警告 （層級 2） C4146
一元減號運算子套用至不帶正負號的類型，所得的結果不帶正負號  
  
 不帶正負號的類型可以保有只非負數值，而使一元減號 （負） 通常是毫無意義，當套用至不帶正負號的類型。 運算元和結果都是非負數。  
  
 實際上，這是當程式設計人員想要表示的最小整數值，其為-2147483648。 作為-2147483648 無法寫入此值，因為運算式會處理兩個階段：  
  
1.  數字 2147483648 會加以評估。 因為它大於 2147483647 的最大整數值，2147483648 類型不[int](../../c-language/integer-types.md)，但`unsigned int`。  
  
2.  一元減號會套用到的值，與不帶正負號的結果，也就是 2147483648 也會發生。  
  
 結果的不帶正負號型別可能會導致非預期的行為。 如果在比較時，使用該結果，則不帶正負號的比較可能會使用，例如，當另一個運算元是`int`。 本節將說明為什麼下列的程式範例只會列印一行。  
  
 預期的第二行`1 is greater than the most negative int`，因為未列印`((unsigned int)1) > 2147483648`為 false。  
  
 您可以使用 INT_MIN limits.h，具有類型，以避免 C4146**帶正負號 int**。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4146:  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```