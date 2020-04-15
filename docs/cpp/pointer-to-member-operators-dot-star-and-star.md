---
title: 指標到成員運算符:.* 和 -&gt;*
ms.date: 11/04/2016
f1_keywords:
- .*
- ->*
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
ms.openlocfilehash: 2100933bf525f0717978528301049085eaecd4f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320331"
---
# <a name="pointer-to-member-operators--and--gt"></a>指標到成員運算符:.* 和 -&gt;*

## <a name="syntax"></a>語法

```
expression .* expression
expression ->* expression
```

## <a name="remarks"></a>備註

指標到成員運算子 .* 和 ->\*返回運算式左側指定物件的特定類成員的值。  右邊則必須指定類別的成員。  以下範例會示範如何使用這些運算子：

```cpp
// expre_Expressions_with_Pointer_Member_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

class Testpm {
public:
   void m_func1() { cout << "m_func1\n"; }
   int m_num;
};

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
void (Testpm::*pmfn)() = &Testpm::m_func1;
int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

// Access the member function
   (ATestpm.*pmfn)();
   (pTestpm->*pmfn)();   // Parentheses required since * binds
                        // less tightly than the function call.

// Access the member data
   ATestpm.*pmd = 1;
   pTestpm->*pmd = 2;

   cout  << ATestpm.*pmd << endl
         << pTestpm->*pmd << endl;
   delete pTestpm;
}
```

## <a name="output"></a>輸出

```Output
m_func1
m_func1
1
2
```

在上述範例中，成員 `pmfn` 的指標會在叫用成員函式 `m_func1` 時使用。 另一個成員 `pmd` 的指標會在存取 `m_num` 成員時使用。

二元運算子 .* 會將其第一個運算元 (該運算元必須是類別類型的物件) 與其第二個運算元 (該運算元必須是成員指標類型) 結合。

二進位運算符 ->+ 將其第一個操作數(必須是指向類類型物件的指標)與其第二個操作數(必須是指向成員的指標類型)合併。

在包含 .* 運算子的運算式中，第一個運算元必須是第二個運算元中所指定成員指標本身所屬且可存取的類別類型，或是該類別所明確衍生且可存取的類型。

在包含 ->+ 運算符的運算式中,第一個操作數必須是第二個操作數中指定的類型的"指向類類型的指標"類型,或者它必須是明確派生自該類的類型。

## <a name="example"></a>範例

以下列類別和程式碼片段為例：

```cpp
// expre_Expressions_with_Pointer_Member_Operators2.cpp
// C2440 expected
class BaseClass {
public:
   BaseClass(); // Base class constructor.
   void Func1();
};

// Declare a pointer to member function Func1.
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;

class Derived : public BaseClass {
public:
   Derived();  // Derived class constructor.
   void Func2();
};

// Declare a pointer to member function Func2.
void (Derived::*pmfnFunc2)() = &Derived::Func2;

int main() {
   BaseClass ABase;
   Derived ADerived;

   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to
                           // access pointers to members of
                           // derived classes.

   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously
                              // derived from BaseClass.
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.
}
```

.* 或\*->指向成員的指標運算符的結果是指向成員的指標聲明中指定的類型的物件或函數。 因此，在上述範例中，`ADerived.*pmfnFunc1()` 運算式的結果會是傳回 void 的函式指標。 如果第二個運算元是左值，則這個結果會是左值。

> [!NOTE]
> 如果其中一個成員指標運算子的結果是函式，則結果只能做為函式呼叫運算子的運算元使用。

## <a name="see-also"></a>另請參閱

[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
