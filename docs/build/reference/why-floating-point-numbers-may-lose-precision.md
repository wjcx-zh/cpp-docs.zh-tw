---
title: "為什麼會失去精確度的浮點數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 371aad5dc573a13ca834d8d6d9667a43bb40324e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>浮點數會失去精確度的原因
浮點十進位值通常不需要實際的二進位表示法。 這是造成副作用的 CPU 如何代表浮動點資料。 基於這個理由，您可能會流失有效位數，以及一些浮點運算可能會產生非預期的結果。  
  
 此行為是下列其中一個動作的結果：  
  
-   可能不精確的十進位數字的二進位表示法。  
  
-   使用的數字 （例如，混合 float 和 double） 之間沒有型別不相符。  
  
 若要解決這個問題，請確定值大於或小於功能所需的大部分的程式設計人員，或者它們取得，並使用 Binary Coded Decimal (BCD) 程式庫可以維護有效位數。  
  
 浮點值的二進位表示法會影響的有效位數和精確度的浮點計算。 Microsoft Visual c + + 使用[IEEE 浮點格式](../../build/reference/ieee-floating-point-representation.md)。  
  
## <a name="example"></a>範例  
  
```  
// Floating-point_number_precision.c  
// Compile options needed: none. Value of c is printed with a decimal   
// point precision of 10 and 6 (printf rounded value by default) to   
// show the difference  
#include <stdio.h>  
  
#define EPSILON 0.0001   // Define your own tolerance  
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))  
  
int main() {  
   float a, b, c;  
  
   a = 1.345f;  
   b = 1.123f;  
   c = a + b;  
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result  
   if (c == 2.468)            // Comment this line for correct result  
      printf_s("They are equal.\n");  
   else  
      printf_s("They are not equal! The value of c is %13.10f "  
                "or %f",c,c);  
}  
```  
  
```Output  
They are not equal! The value of c is  2.4679999352 or 2.468000  
```  
  
## <a name="comments"></a>註解  
 EPSILON，您可以使用常數 FLT_EPSILON，定義為 1.192092896e 浮點數的-07F，或 DBL_EPSILON，定義為 2.2204460492503131e 雙-016。 您需要包含 float.h 這些常數。 這些常數會定義為最小正數 x 數字，這類 x + 1.0 不等於 1.0。 因為這是很小的數目，您應該採用使用者定義計算非常大量的容錯。  
  
## <a name="see-also"></a>請參閱  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)