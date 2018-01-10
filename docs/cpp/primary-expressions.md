---
title: "主要運算式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a6e811e1fe074ce488b09fca29926989bc7f355
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="primary-expressions"></a>主要運算式
主要運算式為更複雜運算式的建置組塊。 它們是常值、名稱，以及範圍解析運算子 (`::`) 所限定的名稱。  主要運算式可以具有下列任何形式：  
  
```  
  
      literal  
      this  
:: namename( expression )  
```  
  
 A*常值*是常數主要運算式。 它的類型取決於其規格形式。 請參閱[常值](../cpp/numeric-boolean-and-pointer-literals-cpp.md)有關指定常值的完整資訊。  
  
 **這**關鍵字是類別物件的指標。 它可在非靜態成員函式中使用，並且指向針對其叫用函式的類別執行個體。 **這**關鍵字不能用在類別成員函式主體之外。  
  
 型別**這**指標`type`  **\*const** (其中`type`是類別名稱) 未特別修改函式內**此**指標。 下列範例會示範成員函式宣告和類型的**這**:  
  
```  
// expre_Primary_Expressions.cpp  
// compile with: /LD  
class Example  
{  
public:  
    void Func();          //  * const this  
    void Func() const;    //  const * const this  
    void Func() volatile; //  volatile * const this  
};  
```  
  
 請參閱[this 指標](this-pointer.md)如需有關修改的類型**這**指標。  
  
 後面接的名稱的範圍解析運算子 (`::`) 會構成主要運算式。  這類名稱必須是全域範圍的名稱，而不是成員名稱。  這個運算式的類型是由名稱的宣告所決定。 如果宣告名稱是左值，它就是左值 (也就是說，它可以出現在指派運算子運算式左邊)。 範圍解析運算子允許參考全域名稱，即使該名稱在目前範圍中為隱藏狀態。 請參閱[範圍](../cpp/scope-visual-cpp.md)如需如何使用範圍解析運算子的範例。  
  
 以括號括住的運算式為主要運算式，其類型和值與未以括號括住之運算式的類型和值相同。 如果未以括號括住的運算式為左值，它就是左值。  
  
 主要運算式語法，上面所列的內容中*名稱*表示任何項目中所述的語法[名稱](http://msdn.microsoft.com/en-us/1c49cc24-08d5-4884-b170-ba8ed42d80db)，不過，當使用名稱型別名稱前面的範圍解析運算子只能在類別中不允許。  這類名稱包括使用者定義的轉換函式名稱和解構函式名稱。  
  
 主要運算式的範例包括：  
  
```  
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 下列範例會將被視為*名稱*，並因此為主要運算式中各種形式：  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## <a name="see-also"></a>請參閱  
 [運算式的類型](../cpp/types-of-expressions.md)