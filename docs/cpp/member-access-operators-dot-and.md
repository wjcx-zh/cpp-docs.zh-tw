---
title: 成員存取運算子:。 和-&gt;
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
ms.openlocfilehash: 0f370aa04af2e78efd5edfb7836fb71a4c4516a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468740"
---
# <a name="member-access-operators--and--gt"></a>成員存取運算子:。 和-&gt;

## <a name="syntax"></a>語法

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>備註

成員存取運算子 **。** 並**->** 用來參考的結構、 等位和類別成員。 成員存取運算式具有選定成員的值和類型。

成員存取運算式有兩種形式：

1. 在第一個表單中，*後置運算式*代表值的結構、 類別或等位型別，並*名稱*指定的結構、 等位或類別的成員命名。 作業的值是*名稱*和是左值，如果*後置運算式*是左值。

1. 在第二個表單中，*後置運算式*代表結構、 等位或類別的指標並*名稱*指定的結構、 等位或類別的成員命名。 值是*名稱*，而且是左值。 **->** 運算子會取值指標。 因此，運算式`e->member`並`(*e).member`(其中*e*表示的指標) 產生相同的結果 (除非運算子**->** 或 <strong>\*</strong>多載)。

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