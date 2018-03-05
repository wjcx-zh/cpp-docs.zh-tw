---
title: "邏輯 OR 運算子: | ||Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '||'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a826b23f94c4eae4a4fdb5379563b015f05dde71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="logical-or-operator-"></a>邏輯 OR 運算子：||
## <a name="syntax"></a>語法  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## <a name="remarks"></a>備註  
 邏輯 OR 運算子 (`||`) 傳回布林值**true**如果任一個或兩個運算元都是**true**並傳回**false**否則。 運算元會在求值之前隱含轉換成 `bool` 類型，而且結果是 `bool` 類型。 邏輯 OR 具有由左至右的順序關聯性。  
  
 邏輯 OR 運算子的運算元不需要屬於相同類型，不過必須屬於整數類資料類型或指標類型。 運算元通常是關聯或相等運算式。  
  
 第一個運算元會經過完整求值，並且會在所有副作用完成之後，才繼續求出邏輯 OR 運算式的值。  
  
 只有在第一個運算元的判斷值為 false (0) 時，才會計算第二個運算元的結果。 這樣在邏輯 OR 運算式為 true 時，就可以不必計算第二個運算元的結果。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在上述範例中，如果 `x` 等於 `w`、`y` 或 `z`，則 `printf` 函式的第二個引數判斷值為 true，並且印出值 1。 否則，它的判斷值為 false，並且印出值 0。 只要其中一項條件的判斷值為 true，求值就會停止。  
  
## <a name="operator-keyword-for-124124"></a>運算子關鍵字 &#124; &#124;  
 **或**運算子相當於文字的`||`。 有兩種方式來存取**或**您程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。  
  
## <a name="example"></a>範例  
  
```  
// expre_Logical_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical OR  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b || b > c yields "  
         << (a < b || b > c) << endl  
         << "The false expression "  
         << "a > b || b > c yields "  
         << (a > b || b > c) << endl;  
}  
```  
  
## <a name="see-also"></a>請參閱  
[C + + 內建運算子優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md) [c + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 邏輯運算子](../c-language/c-logical-operators.md)