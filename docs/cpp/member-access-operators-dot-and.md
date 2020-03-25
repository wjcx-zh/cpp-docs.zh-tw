---
title: 成員存取運算子：。 和-&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 05bab55e1646783e0f8ab9b414d608c912f60a0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178011"
---
# <a name="member-access-operators--and--gt"></a>成員存取運算子：。 和-&gt;

## <a name="syntax"></a>語法

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>備註

成員存取運算子 **。** 和 **->** 是用來參考結構、等位和類別的成員。 成員存取運算式具有選定成員的值和類型。

成員存取運算式有兩種形式：

1. 在第一個表單中，後置*運算式*代表 struct、class 或 union 類型的值，而*name*則是指定的結構、等位或類別的成員。 如果後置*運算式*是左值，則作業的值是*名稱*的，而且是左值。

1. 在第二種形式中，後置運算式代表結構、等*位*或類別的指標，而*名稱*則是指定的結構、等位或類別的成員。 值為*名稱*，而且是左值。 **->** 運算子會將指標取值。 因此，`e->member` 和 `(*e).member` （其中*e*代表指標）的運算式會產生相同的結果（除非 **->** 或<strong>\*</strong>的運算子超載）。

## <a name="example"></a>範例

下列範例示範成員存取運算子的兩種形式。

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[類別和結構](../cpp/classes-and-structs-cpp.md)<br/>
[結構和等位成員](../c-language/structure-and-union-members.md)
