---
title: "邏輯負運算子：! | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '!'
- Not
dev_langs: C++
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd8169d2281f1cbd77063eddc312fa93655b99dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="logical-negation-operator-"></a>邏輯負運算子：!
## <a name="syntax"></a>語法  
  
```  
  
! cast-expression  
```  
  
## <a name="remarks"></a>備註  
 邏輯負運算子 (**！**) 會反轉其運算元的意義。 運算元必須是算術或指標類型 (或判斷值為算術或指標類型的運算式)。 運算元會隱含轉換成 `bool` 類型。 結果是**true**如果轉換的運算元**false**; 結果是**false**如果轉換的運算元**true**。 其結果會是 `bool` 類型。  
  
 運算式*e*，一元運算式**！***e* 相當於運算式**(***e* `==` 0)，除了多載的運算子是與相關。  
  
## <a name="operator-keyword-for-"></a>! 的運算子關鍵字  
 **不**運算子相當於文字的**！**。 有兩種方式來存取**不**您程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。  
  
## <a name="example"></a>範例  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算術運算子](../c-language/unary-arithmetic-operators.md)