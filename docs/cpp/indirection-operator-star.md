---
title: '間接取值運算子: * |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80fdbe14539c5b32c2da80a5de75fbe0a2b64241
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409123"
---
# <a name="indirection-operator-"></a>間接取值運算子：*
## <a name="syntax"></a>語法  
  
```  
* cast-expression  
```  
  
## <a name="remarks"></a>備註  
 一元間接運算子 (**\***) 會取值指標; 也就是說，它將指標值轉換為左值。 間接運算子的運算元必須是類型指標。 間接運算式的結果是類型，指標類型即衍生自此。 使用**\*** 運算子，在此內容中的是不同運算子為二元運算子，後者是乘法。  
  
 如果運算元指向某個函式，則結果為函式指示項。 如果運算元指向某個儲存位置，則結果為指定儲存位置的左值。  
  
 間接運算子可以累計用於將指標取值成為指標。 例如:   
  
```cpp 
// expre_Indirection_Operator.cpp  
// compile with: /EHsc  
// Demonstrate indirection operator  
#include <iostream>  
using namespace std;  
int main() {  
   int n = 5;  
   int *pn = &n;  
   int **ppn = &pn;  
  
   cout  << "Value of n:\n"  
         << "direct value: " << n << endl  
         << "indirect value: " << *pn << endl  
         << "doubly indirect value: " << **ppn << endl  
         << "address of n: " << pn << endl  
         << "address of n via indirection: " << *ppn << endl;  
}  
```  
  
 如果指標值無效，則結果會是未定義的。 下列清單包含最常見的一些使指標值無效的情況。  
  
-   指標是一個 null 指標。  
  
-   指標指定了在參考時不可見的本機項目位址。  
  
-   指標指定的位址與物件指向的類型並不一致。  
  
-   指標指定了執行中程式未使用的位址。  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [傳址運算子: （& s)](../cpp/address-of-operator-amp.md)   
 [間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)