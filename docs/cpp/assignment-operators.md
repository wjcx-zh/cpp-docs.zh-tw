---
title: 指派運算子
description: C + + 標準語言指派運算子語法和使用。
ms.date: 07/24/2020
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
ms.openlocfilehash: 91346d06c6fab4f3cd83c5318c88e738daf8d249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229216"
---
# <a name="assignment-operators"></a>指派運算子

## <a name="syntax"></a>語法

*運算式**指派-運算子**運算式*

*assignment-operator*：下列其中一個<br/>
&emsp;**`=`**&emsp;**`*=`**&emsp;**`/=`**&emsp;**`%=`**&emsp;**`+=`**&emsp;**`-=`**&emsp;**`<<=`**&emsp;**`>>=`**&emsp;**`&=`**&emsp;**`^=`**&emsp;**`|=`**

## <a name="remarks"></a>備註

指派運算子會將值儲存在左運算元所指定的物件中。 指派作業有兩種：

- *簡單指派*，第二個運算元的值會儲存在第一個運算元所指定的物件中。

- *複合指派*，在儲存結果之前，會先執行算術、移位或位運算。

下表中的所有指派運算子（ **`=`** 運算子除外）都是複合指派運算子。

### <a name="assignment-operators-table"></a>指派運算子資料表

| 運算子 | 意義 |
|--|--|
| **`=`** | 將第二個運算元的值儲存在第一個運算元所指定的物件 (簡單指派)。 |
| **`*=`** | 將第一個運算元的值乘以第二個運算元的值；將結果儲存在第一個運算元所指定的物件。 |
| **`/=`** | 將第一個運算元的值除以第二個運算元的值；將結果儲存在第一個運算元所指定的物件。 |
| **`%=`** | 將第一個運算元以第二個運算元的值取模數；將結果儲存在第一個運算元所指定的物件。 |
| **`+=`** | 將第二個運算元的值加至第一個運算元的值；將結果儲存在第一個運算元所指定的物件。 |
| **`-=`** | 將第一個運算元的值減去第二個運算元的值；將結果儲存在第一個運算元所指定的物件。 |
| **`<<=`** | 將第一個運算元的值往左移位由第二個運算元的值所指定的位元數；將結果儲存在第一個運算元所指定的物件。 |
| **`>>=`** | 將第一個運算元的值往右移位由第二個運算元的值所指定的位元數；將結果儲存在第一個運算元所指定的物件。 |
| **`&=`** | 取得第一和第二個運算元的位元 AND；將結果儲存在第一個運算元所指定的物件。 |
| **`^=`** | 取得第一和第二個運算元的位元排除 OR；將結果儲存在第一個運算元所指定的物件。 |
| **`|=`** | 取得第一和第二個運算元的位元包含 OR；將結果儲存在第一個運算元所指定的物件。 |

### <a name="operator-keywords"></a>運算子關鍵字

有三個複合指派運算子具有關鍵詞對應專案。 其中包括：

| 運算子 | 對等用法 |
|--|--|
| **`&=`** | **`and_eq`** |
| **`|=`** | **`or_eq`** |
| **`^=`** | **`xor_eq`** |

C + + 會針對複合指派運算子，將這些運算子關鍵字指定為替代的拼寫。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="example"></a>範例

```cpp
// expre_Assignment_Operators.cpp
// compile with: /EHsc
// Demonstrate assignment operators
#include <iostream>
using namespace std;
int main() {
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;

   a += b;      // a is 9
   b %= a;      // b is 6
   c >>= 1;      // c is 5
   d |= e;      // Bitwise--d is 0xFFFF

   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl
         << "a += b yields " << a << endl
         << "b %= a yields " << b << endl
         << "c >>= 1 yields " << c << endl
         << "d |= e yields " << hex << d << endl;
}
```

## <a name="simple-assignment"></a>單一指派

簡單指派運算子（ **`=`** ）會導致第二個運算元的值儲存在第一個運算元所指定的物件中。 如果這兩個物件都是算術類型，則在儲存值之前，右運算元會轉換成左側的類型。

**`const`** 和類型的物件 **`volatile`** 可以指派給只有或不是或的類型的左值 **`volatile`** **`const`** **`volatile`** 。

指派給類別類型（ **`struct`** 、 **`union`** 和 **`class`** 類型）的物件是由名為的函式所執行 `operator=` 。 這個運算子函式的預設行為是執行位元複製；不過可以使用多載運算子修改此行為  如需詳細資訊，請參閱[運算子多載](../cpp/operator-overloading.md)。 類別類型也可以有*複製指派*和*移動指派*運算子。 如需詳細資訊，請參閱[複製函數和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)和移動函式和[移動指派運算子](move-constructors-and-move-assignment-operators-cpp.md)。

只要物件是從指定基底類別明確衍生的任何類別，就可以指派給該基底類別的物件。 相反的，因為有從衍生類別到基類的隱含轉換，而不是從基類到衍生類別。 例如：

```cpp
// expre_SimpleAssignment.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
class ABase
{
public:
    ABase() { cout << "constructing ABase\n"; }
};

class ADerived : public ABase
{
public:
    ADerived() { cout << "constructing ADerived\n"; }
};

int main()
{
    ABase aBase;
    ADerived aDerived;

    aBase = aDerived; // OK
    aDerived = aBase; // C2679
}
```

參考類別的指派作用就像指派參考所指向的物件。

對於類別類型的物件而言，指派與初始化不同。 為說明指派與初始化的不同之處，假設下列程式碼

```cpp
UserType1 A;
UserType2 B = A;
```

上述程式碼示範初始化設定式；它會呼叫建構函式 `UserType2`，此建構函式接受屬於類型 `UserType1` 的引數。 假設下列程式碼

```cpp
UserType1 A;
UserType2 B;

B = A;
```

指派陳述式

```cpp
B = A;
```

可能會有下列其中一項作用：

- 呼叫的函式，並提供 `operator=` `UserType2` `operator=` `UserType1` 引數給。

- 如果 `UserType1::operator UserType2` 函式存在，呼叫這類明確轉換函式。

- 呼叫建構函式 `UserType2::UserType2`，前提是這類建構函式存在，而且接受 `UserType1` 引數並複製結果。

## <a name="compound-assignment"></a>複合指派

複合指派運算子會顯示在[指派運算子資料表](#assignment-operators-table)中。 這些運算子的形式為*e1* *op* =  *e2*，其中*e1*是不可修改的 **`const`** 左值，而*e2*是：

- 算術類型

- 如果*op*為或，則為指標 **`+`****`-`**

*E1* *op* =  *e2*表單的行為是*e1* **`=`** *e1* *op* *e2*，但是*e1*只會評估一次。

對列舉類型的複合指派會產生錯誤訊息。 如果左運算元是指標類型，則右運算元必須是指標類型，或者必須是判斷值為0的常數運算式。 當左運算元是整數類資料類型時，右運算元必須不是指標類型。

## <a name="result-of-assignment-operators"></a>指派運算子的結果

指派運算子會在指派之後傳回左運算元所指定的物件值。 結果的類型會是左運算元的類型。 指派運算式的結果一律是左值。 這些運算子具有由右到左的順序關聯性。 左運算元必須是可修改的左值。

在 ANSI C 中，指派運算式的結果不是左值。 這表示 `(a += b) += c` c 中不允許使用合法的 c + + 運算式。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C + + 內建運算子、優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 指派運算子](../c-language/c-assignment-operators.md)
