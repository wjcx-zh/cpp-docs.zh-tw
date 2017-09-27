---
title: "等號比較運算子: = = 和 ！ = |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator, syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: 7
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
ms.openlocfilehash: 5412869204f088e321d2a41da407026f9447eb82
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="equality-operators--and-"></a>等號比較運算子：== 和 !=
## <a name="syntax"></a>語法  
  
```  
expression == expression  
expression != expression  
```  
  
## <a name="remarks"></a>備註  
 二進位相等運算子會比較其運算元，以進行嚴格的相等或不等比較。  
  
 相等運算子等於 (`==`) 和不等於 (`!=`) 的優先順序低於關係運算子，但是它們的行為類似。 這些運算子的結果類型為 `bool`。  
  
 等於運算子 (`==`) 傳回**true** (1) 如果這兩個運算元有相同的值; 否則它會傳回**false** (0)。 不等於運算子 (`!=`) 傳回**true**如果運算元不需要相同的值; 否則它會傳回**false**。  
  
## <a name="operator-keyword-for-"></a>!= 的運算子關鍵字  
 `not_eq` 運算子是 `!=` 的文字對等用法。 有兩種方式來存取`not_eq`您程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。  
  
## <a name="example"></a>範例  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 相等運算子可以比較相同類型成員的指標。 在這類比較時，會執行成員指標轉換。 成員指標也可以與判斷值為 0 的常數運算式進行比較。  
  
## <a name="see-also"></a>另請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)
