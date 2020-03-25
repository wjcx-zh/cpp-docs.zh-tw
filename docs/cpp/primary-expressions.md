---
title: 主要運算式
ms.date: 11/04/2016
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: 03f0d0d04ad8ef2b052b9303d15437c53369a003
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177621"
---
# <a name="primary-expressions"></a>主要運算式

主要運算式為更複雜運算式的建置組塊。 它們是常值、名稱，以及範圍解析運算子 (`::`) 所限定的名稱。  主要運算式可以具有下列任何形式：

```
literal
this
name
::name ( expression )
```

常*值是*常數主要運算式。 它的類型取決於其規格形式。 如需指定常值的完整資訊，請參閱[常](../cpp/numeric-boolean-and-pointer-literals-cpp.md)值。

**This**關鍵字是類別物件的指標。 它可在非靜態成員函式中使用，並且指向針對其叫用函式的類別執行個體。 **這個**關鍵字不能在類別成員函式的主體之外使用。

**這個**指標的類型是在函式中未特別修改**this**指標 `type` **\*const** （其中 `type` 是類別名稱）。 下列範例會顯示成員函式宣告和**這個**的類型：

```cpp
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

如需修改**this**指標類型的詳細資訊，請參閱[此指標](this-pointer.md)。

後面接的名稱的範圍解析運算子 (`::`) 會構成主要運算式。  這類名稱必須是全域範圍的名稱，而不是成員名稱。  這個運算式的類型是由名稱的宣告所決定。 如果宣告名稱是左值，它就是左值 (也就是說，它可以出現在指派運算子運算式左邊)。 範圍解析運算子允許參考全域名稱，即使該名稱在目前範圍中為隱藏狀態。 如需如何使用範圍解析運算子的範例，請參閱[範圍](../cpp/scope-visual-cpp.md)。

以括號括住的運算式為主要運算式，其類型和值與未以括號括住之運算式的類型和值相同。 如果未以括號括住的運算式為左值，它就是左值。

主要運算式的範例包括：

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

下列範例全都視為各種形式的*名稱*，因此是主要運算式：

```cpp
MyClass // a identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>另請參閱

[運算式的類型](../cpp/types-of-expressions.md)
