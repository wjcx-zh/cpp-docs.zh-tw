---
title: "前置遞增和遞減運算子: + + 和-|Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators, syntax
- ++ operator, prefix increment operators
- operators [C++], decrement
- -- operator, prefix decrement operators
- operators [C++], increment
- decrement operators, syntax
- decrement operators
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 22844a2bca61b81dc5cf7c2fc4fffa45a2783078
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="prefix-increment-and-decrement-operators--and---"></a>前置遞增和遞減運算子：++ 和 --
## <a name="syntax"></a>語法  
  
```  
++ unary-expression  
-- unary-expression  
```  
  
## <a name="remarks"></a>備註  
 前置遞增運算子 (`++`) 會將其運算元加一，這個增量值是運算式的結果。 運算元必須是左值的型別不**const**。 結果會是與運算元相同類型的左值。  
  
 前置遞減運算子 (**--**) 相當於前置遞增運算子，不同之處在於，運算元會減一且結果是這個減量值。  

 **Visual Studio 2017 15.3 和更新版本**(適用於[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 遞增或遞減運算子的運算元不可以是型別`bool`。
  
 前置和後置遞增和遞減運算子都會影響其運算元。 它們之間的主要差異在於遞增或遞減在運算式評估中發生的順序 。 (如需詳細資訊，請參閱[後置遞增和遞減運算子](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)。)在前置形式中，遞增或遞減會在運算式評估中使用值之前發生，因此運算式的值會與運算元的值不同。 在後置形式中，遞增或遞減會在運算式評估中使用值之後發生，因此運算式的值會與運算元的值相同。 例如，下列程式會列印 "`++i = 6`"：  
  
```  
// expre_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int i = 5;  
   cout << "++i = " << ++i << endl;  
}  
```  
  
 整數或浮點類型的運算元會以整數值 1 遞增或遞減。 結果的類型與運算元類型相同。 指標類型的運算元會以其定址之物件的大小遞增或遞減。 遞增指標會指向下一個物件，遞減指標則指向上一個物件。  
  
 由於遞增和遞減運算子在使用中的遞增或遞減運算子的運算式有副作用，[前置處理器巨集](../preprocessor/macros-c-cpp.md)可以有非預期的結果。 請考量以下範例：  
  
```  
// expre_Increment_and_Decrement_Operators2.cpp  
#define max(a,b) ((a)<(b))?(b):(a)  
  
int main()  
{  
   int i = 0, j = 0, k;  
   k = max( ++i, j );  
}  
```  
  
 巨集會展開為：  
  
```  
k = ((++i)<(j))?(j):(++i);  
```  
  
 如果 `i` 大於或等於 `j`，或是比 `j` 少 1，則會遞增兩次。  
  
> [!NOTE]
>  在許多情況下，C++ 內嵌函式會比巨集更理想，因為這類函式會排除副作用 (如這裡所述的副作用)，並且可讓語言執行更完整的類型檢查。  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [前置遞增和遞減運算子](../c-language/prefix-increment-and-decrement-operators.md)
