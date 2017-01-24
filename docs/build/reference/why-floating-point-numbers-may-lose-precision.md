---
title: "浮點數會失去精確度的原因 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DBL_EPSILON 常數"
  - "浮點數, 精確度"
  - "FLT_EPSILON 常數"
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 浮點數會失去精確度的原因
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一般而言，十進位浮點數值並沒有精確的二進位表示式。  這是 CPU 表示浮點資料方式的副作用 \(Side Effect\)。  因為這個原因，可能會失去一些精確度，且某些浮點作業可能產生未預期的結果。  
  
 下列其中一項因素造成這種行為：  
  
-   十進位數字的二進位表示式可能不精確  
  
-   使用的數字之間出現型別不符的情形，\(例如，混用浮點數 \(Float\) 和雙精度浮點數 \(Double\)。  
  
 為了解決這種行為，大部分的程式設計人員可能會確保此值大於或小於其所需的值，或是取得並使用 BCD \(Binary Coded Decimal\) 程式庫來保持精確度。  
  
 浮點值的二進位表示會影響浮點計算的精確度和正確性。  Microsoft Visual C\+\+ 使用 [IEEE 浮點格式](../../build/reference/ieee-floating-point-representation.md)。  
  
## 範例  
  
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
  
  **它們並不相等！  c 的值為 2.4679999352 或 2.468000**    
## 註解  
 若為 EPSILON，您可使用常數 FLT\_EPSILON \(其被定義為浮點 1.192092896e\-07F\) 或 DBL\_EPSILON \(其被定義雙精度 2.2204460492503131e\-016\)；  您必須對這些常數併入 float.h。  這些常數被定義為最小的正數 x，而 x\+1.0 不等於 1.0。  由於這是一個非常小的數字，因此在涉及極大數字的計算時，應採用使用者定義的容錯度。  
  
## 請參閱  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)