---
title: "傳址運算子：&amp; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "address-of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 運算子"
  - "& 運算子, 傳址運算子"
  - "傳址運算子 (&)"
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 傳址運算子：&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
& cast-expression  
```  
  
## 備註  
 一元傳址運算子 \(**&**\) 可接受其運算元的位址。  傳址運算子的運算元可以是函式指示項或左值，此左值指定的物件不是位元欄位，並且不使用 **register** 儲存類別規範宣告。  
  
 傳址運算子僅適用於基本、結構、類別或等位類型是在檔案範圍層級宣告的變數，或是註標的陣列參考。  在這些運算式中，未包含傳址運算子的常數運算式可以在傳址運算式中進行加法或減法運算。  
  
 套用至函式或左值時，運算式的結果會是衍生自運算元類型的指標類型 \(右值\)。  例如，如果運算元為 `char` 類型，則運算式的結果為指向 `char` 的類型指標。  套用至 **const** 或 `volatile` 物件的傳址運算子會求出 **const** `type` \* 的值或 `volatile` `type` \* 的值，其中 `type` 為原始物件的類型。  
  
 傳址運算子套用至[限定名稱](http://msdn.microsoft.com/zh-tw/3fefb16d-8120-4627-8b3f-3d90fbdcd1df)時，其結果取決於 *qualified\-name* 是否指定靜態成員。  如果是，則結果為成員宣告中所指定類型的指標。  如果成員不是靜態的，則結果為 *qualified\-class\-name* 所表示類別之成員 *name* 的指標。\(如需深入了解 *qualified\-class\-name*，請參閱[主要運算式](../cpp/primary-expressions.md)\)。下列程式碼片段將示範成員是否為靜態的結果差異：  
  
```  
// expre_Address_Of_Operator.cpp  
// C2440 expected  
class PTM {  
public:  
           int   iValue;  
    static float fValue;  
};  
  
int main() {  
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static  
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static  
   float *spfValue     = &PTM::fValue;  // OK  
}  
```  
  
 在這個範例中，因為 `fValue` 是靜態成員，所以運算式 `&PTM::fValue` 會產生 `float *` 類型而不是 `float PTM::*` 類型。  
  
 只有在清楚知道所參考的函式版本時，才會採用多載函式的位址。  如需如何取得特定多載函式之位址的詳細資訊，請參閱[多載函式的位址](../misc/address-of-overloaded-functions.md)。  
  
 將傳址運算子套用至參考類型所產生的結果，與將運算子套用至參考繫結所在的物件產生的結果相同。  例如：  
  
## 範例  
  
```  
// expre_Address_Of_Operator2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   double d;        // Define an object of type double.  
   double& rd = d;  // Define a reference to the object.  
  
   // Obtain and compare their addresses  
   if( &d == &rd )  
      cout << "&d equals &rd" << endl;  
}  
```  
  
## Output  
  
```  
&d equals &rd  
```  
  
 下列範例會使用傳址運算子將指標引數傳遞至函式：  
  
```  
// expre_Address_Of_Operator3.cpp  
// compile with: /EHsc  
// Demonstrate address-of operator &  
  
#include <iostream>  
using namespace std;  
  
// Function argument is pointer to type int  
int square( int *n ) {  
   return (*n) * (*n);  
}  
  
int main() {  
   int mynum = 5;  
   cout << square( &mynum ) << endl;   // pass address of int  
}  
```  
  
## Output  
  
```  
25  
```  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md)   
 [間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)