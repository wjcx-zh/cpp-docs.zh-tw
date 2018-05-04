---
title: 邏輯 AND 運算子： &amp; &amp; |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- C++
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f683b7ff17a1dd3945f5cb554a7440ab47fad454
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="logical-and-operator-ampamp"></a>邏輯 AND 運算子： &amp;&amp;
## <a name="syntax"></a>語法  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## <a name="remarks"></a>備註  
 邏輯 AND 運算子 (**&&**) 傳回布林值**true**如果這兩個運算元都是**true**並傳回**false**否則為。 運算元會在求值之前隱含轉換成 `bool` 類型，而且結果是 `bool` 類型。 邏輯 AND 具有由左至右的順序關聯性。  
  
 邏輯 AND 運算子的運算元不需要屬於相同類型，不過必須屬於整數類資料類型或指標類型。 運算元通常是關聯或相等運算式。  
  
 第一個運算元會經過完整評估，並且會在所有副作用完成之後，才繼續評估邏輯 AND 運算式。  
  
 只有在第一個運算元判斷值為 true (非零) 時，才會評估第二個運算元。 這項評估在邏輯 AND 運算式為 false 時，就可以不必評估第二個運算元。 您可以使用這個最少運算評估來預防 null 指標取值，如下列範例所示：  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 如果 `pch` 是 null (0)，則永遠不會評估運算式的右邊。 因此，您無法透過 null 指標來進行指派。  
  
## <a name="operator-keyword-for-"></a>&& 的運算子關鍵字  
 **和**運算子相當於文字的**&&**。 有兩種方式來存取**和**您程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。  
  
## <a name="example"></a>範例  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 內建運算子優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md) [c + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 邏輯運算子](../c-language/c-logical-operators.md)