---
title: "乘法類運算子和模數運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb6ad2396b47932f05d9404485e4b32a7e92363b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>乘法類運算子和模數運算子
## <a name="syntax"></a>語法  
  
```  
expression * expression   
expression / expression   
expression % expression  
```  
  
## <a name="remarks"></a>備註  
 乘法類運算子包括：  
  
-   乘法 (**\***)  
  
-   除法 (**/**)  
  
-   模數 (除法的餘數) (`%`)  
  
 這些二進位運算子具有由左至右的順序關聯性。  
  
 乘法類運算子接受算術類型的運算元。 模數運算子 (`%`) 具有較嚴格的要求，其運算元必須為整數類資料類型  (若要取得浮點除法的餘數，請使用執行階段函式[fmod](../c-runtime-library/reference/fmod-fmodf.md)。)中涵蓋的轉換[標準轉換](standard-conversions.md)適用於運算元，結果會是轉換後的類型。  
  
 乘法運算子會產生第一個運算元與第二個運算元相乘的結果。  
  
 除法運算子會產生第一個運算元除以第二個運算元的結果。  
  
 模數運算子會產生下列運算式中，所提供的其餘部分其中*e1*是第一個運算元和*e2*是第二個： *e1* -(*e1* /  *e2*) \* *e2*，其中兩個運算元都是整數類資料類型。  
  
 在除法或模數運算式中除以 0 並未定義，而且會產生執行階段錯誤。 因此，下列運算式會產生未定義的錯誤結果：  
  
```  
i % 0  
f / 0.0  
```  
  
 如果乘法、除法或模數運算式的兩個運算元有相同的正負號，則結果為正數。 否則，結果為負數。 模數運算結果的正負號是由實作所定義。  
  
> [!NOTE]
>  由於乘法類運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果乘法類運算的結果無法以轉換後的運算元類型表示，則資訊可能會遺失。  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
 在 Microsoft C++ 中，模數運算式的結果一律與第一個運算元的正負號相同。  
  
**結束 Microsoft 特定的**  
 如果兩個整數計算的除法不精確，而且只有一個運算元為負數，則結果會是小於除法運算會產生之實際值的最大整數 (範圍內，忽略正負號)。 例如，計算的值的-11 / 3 是-3.666666666。 該整數除法的結果是-3。  
  
 乘法類運算子之間的關聯性由身分識別提供 (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*。  
  
## <a name="example"></a>範例  
 下列程式將示範乘法類運算子。 請注意的任一個運算元`10 / 3`必須明確轉換為類型`float`避免發生截斷，如此這兩個運算元都是類型`float`除法之前。  
  
```  
// expre_Multiplicative_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   int x = 3, y = 6, z = 10;  
   cout  << "3 * 6 is " << x * y << endl  
         << "6 / 3 is " << y / x << endl  
         << "10 % 3 is " << z % x << endl  
         << "10 / 3 is " << (float) z / x << endl;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 乘法類運算子](../c-language/c-multiplicative-operators.md)