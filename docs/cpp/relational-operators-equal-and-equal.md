---
title: 關係運算子： &lt;， &gt;， &lt;=、 和&gt;= |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- <
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56372764c70498aec4ccf7b23fc7d074d1df179e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942859"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>關係運算子： &lt;， &gt;， &lt;=、 和 &gt;=
## <a name="syntax"></a>語法  
  
```  
expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## <a name="remarks"></a>備註  
 二元關係運算子決定下列關聯性：  
  
-   小於 (**\<**)  
  
-   大於 (**>**)  
  
-   小於或等於 (**\<=**)  
  
-   大於或等於 (**>=**)  
  
 關係運算子具有由左到右的順序關聯性。 關係運算子的兩個運算元都必須是算術或指標類型。 會產生值的型別**bool**。 傳回的值是**假**(0) 如果在運算式中的關聯性是 false，否則傳回的值是 **，則為 true** (1)。  
  
## <a name="example"></a>範例  
  
```cpp 
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 在上述範例中的運算式必須以括號括住，因為資料流插入運算子 (**<<**) 的優先順序高於關係運算子。 因此，不加括弧的第一個運算式會評估為：  
  
```cpp 
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 中涵蓋的一般算術轉換[標準轉換](standard-conversions.md)適用於算術類型的運算元。  
  
## <a name="comparing-pointers"></a>比較指標  
 比較相同類型的兩個物件指標時，結果是取決於程式的位址空間中所指向的物件位置。 指標也可以與判斷值為 0 的常數運算式或 void * 類型的指標進行比較。 如果指標的比較對類型的指標 void \*，另一個指標會隱含地轉換至類型 void \*。 然後才進行比較。  
  
 兩個不同類型的指標無法進行比較，除非：  
  
-   其中一個類型是衍生自另一個類型的類別類型。  
  
-   至少有一個指標已明確轉換 (轉型) 為 void * 類型  (另一個指標會隱含地轉換至類型 void\*轉換。)  
  
 相同類型且指向相同物件之兩個指標的比較結果一定為相等。 如果將物件的兩個非靜態成員指標相互比較，則適用下列規則：  
  
-   如果類別型別不是等位，而且如果以不分隔的兩個成員*存取規範*，例如 public、 protected 或 private，宣告的成員指標上次比較結果會大於宣告的成員指標稍早。  
  
-   如果兩個成員之間隔開*存取規範*，結果便未定義。  
  
-   如果類別類型是等位，則該等位中不同資料成員的指標比較結果為相等。  
  
 如果兩個指標指向相同陣列的元素，或指向超出陣列結尾的元素一，則具有較高註標的物件指標比較結果會較高。 只有在指標參考相同陣列中的物件或超出陣列結尾的位置一時，才能保證指標比較有效。  
  
## <a name="see-also"></a>另請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)