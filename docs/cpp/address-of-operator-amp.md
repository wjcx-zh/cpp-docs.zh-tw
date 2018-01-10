---
title: "傳址運算子： &amp; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&'
dev_langs: C++
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 814b21839ac851e942aaee34ed28fd43facb418a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="address-of-operator-amp"></a>傳址運算子：&amp;
## <a name="syntax"></a>語法  
  
```  
& cast-expression  
```  
  
## <a name="remarks"></a>備註  
 一元傳址運算子 (**&**) 會採用其運算元的位址。 傳址運算子的運算元可以是函式指示項或左值，它們必須能指定的物件不是位元欄位，並且不是使用 **register** 儲存類別指定名稱進行宣告。  
  
 傳址運算子僅適用於基本、結構、類別或等位型別是在檔案範圍層級宣告的變數，或是註標的陣列參考。 在這些運算式中，未包含傳址運算子的常數運算式可以在傳址運算式中進行加法或減法運算。  
  
 套用至函式或左值時，運算式的結果會是衍生自運算元類型的指標類型 (右值)。 例如，如果運算元為 `char` 類型，則運算式的結果為指向 `char` 的類型指標。 傳址運算子套用至**const**或`volatile`物件，會評估為**const** `type`  **\*** 或`volatile` `type` **\*** ，其中`type`是原始物件的類型。  
  
 傳址運算子套用至時[限定的名稱](http://msdn.microsoft.com/en-us/3fefb16d-8120-4627-8b3f-3d90fbdcd1df)，結果會取決於是否*限定名稱*指定靜態成員。 如果是，則結果為成員宣告中所指定類型的指標。 如果成員不是靜態的結果是成員的指標*名稱*類別所表示的*限定類別名稱*。 (請參閱[主要運算式](../cpp/primary-expressions.md)如需詳細資訊*限定類別名稱*。)下列程式碼片段將示範成員是否為靜態的結果差異：  
  
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
  
 在這個範例中，因為 `&PTM::fValue` 是靜態成員，所以運算式 `float *` 會產生 `float PTM::*` 類型而不是 `fValue` 類型。  
  
 只有在清楚知道所參考的函式版本時，才會採用多載函式的位址。 請參閱[函式多載](function-overloading.md)濆爧髍孮特定位址的相關資訊的多載函式。  
  
 將傳址運算子套用至參考類型所產生的結果，與將運算子套用至參考繫結所在的物件產生的結果相同。 例如:   
  
## <a name="example"></a>範例  
  
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
  
## <a name="output"></a>輸出  
  
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
  
## <a name="output"></a>輸出  
  
```  
25  
```  
  
## <a name="see-also"></a>請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [左值參考宣告子： &](../cpp/lvalue-reference-declarator-amp.md)   
 [間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)
