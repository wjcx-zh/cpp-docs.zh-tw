---
title: 指派運算子
ms.date: 03/05/2018
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
ms.openlocfilehash: 44211e43a0449c8a50ff03cac31eeed1fcc49a28
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328470"
---
# <a name="assignment-operators"></a>指派運算子

## <a name="syntax"></a>語法

*運算式**指派運算子**運算式*

*指派運算子*： 其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>=&nbsp;&nbsp;&nbsp;*=&nbsp;&nbsp;&nbsp;/=&nbsp;&nbsp;&nbsp;%=&nbsp;&nbsp;&nbsp;+=&nbsp;&nbsp;&nbsp;-=&nbsp;&nbsp;&nbsp;\<\<=&nbsp;&nbsp;&nbsp;>>=&nbsp;&nbsp;&nbsp;&=&nbsp;&nbsp;&nbsp;^=&nbsp;&nbsp;&nbsp;\|=</strong>

## <a name="remarks"></a>備註

指派運算子會將值儲存在左運算元所指定的物件。 有兩種類型的指派作業：

1. *簡單指派*，在第二個運算元的值儲存在第一個運算元所指定的物件。

1. *複合指派*，在其中的算術、 移位或位元運算在儲存結果之前執行。

下表中除了 = 運算子以外的所有指派運算子都是複合指派運算子。

### <a name="assignment-operators"></a>指派運算子

|運算子|意義|
|--------------|-------------|
|**=**|將第二個運算元的值儲存在第一個運算元所指定的物件 (簡單指派)。|
|**\*=**|將第一個運算元的值乘以第二個運算元的值；將結果儲存在第一個運算元所指定的物件。|
|**/=**|將第一個運算元的值除以第二個運算元的值；將結果儲存在第一個運算元所指定的物件。|
|**%=**|將第一個運算元以第二個運算元的值取模數；將結果儲存在第一個運算元所指定的物件。|
|**+=**|將第二個運算元的值加至第一個運算元的值；將結果儲存在第一個運算元所指定的物件。|
|**-=**|將第一個運算元的值減去第二個運算元的值；將結果儲存在第一個運算元所指定的物件。|
|**<\<=**|將第一個運算元的值往左移位由第二個運算元的值所指定的位元數；將結果儲存在第一個運算元所指定的物件。|
|**>>=**|將第一個運算元的值往右移位由第二個運算元的值所指定的位元數；將結果儲存在第一個運算元所指定的物件。|
|**&=**|取得第一和第二個運算元的位元 AND；將結果儲存在第一個運算元所指定的物件。|
|**^=**|取得第一和第二個運算元的位元排除 OR；將結果儲存在第一個運算元所指定的物件。|
|**\|=**|取得第一和第二個運算元的位元包含 OR；將結果儲存在第一個運算元所指定的物件。|

**運算子關鍵字**

三個複合指派運算子有文字對等用法。 包括：

|運算子|對等項目|
|--------------|----------------|
|**&=**|`and_eq`|
|**\|=**|`or_eq`|
|**^=**|`xor_eq`|

有兩種方式來存取您程式中的這些運算子關鍵字： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。

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

簡單指派運算子 (**=**) 會導致儲存在第一個運算元所指定之物件中的第二個運算元的值。 如果兩個物件都是算術類型，右運算元會在儲存值之前轉換成左運算元的類型。

物件的**const**並**volatile**為左值的型別只可指派類型**volatile**或兩者皆非**const**也不**volatile**。

指派給類別類型 （結構、 等位和類別類型） 的物件由名為函式執行`operator=`。 這個運算子函式的預設行為是執行位元複製；不過可以使用多載運算子修改此行為  請參閱[運算子多載](../cpp/operator-overloading.md)如需詳細資訊。 此外，類別型別可以有*複製指派*並*移動指派*運算子。 如需詳細資訊，請參閱 <<c0> [ 複製建構函式和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)並[移動建構函式和移動指派運算子](move-constructors-and-move-assignment-operators-cpp.md)。

只要物件是從指定基底類別明確衍生的任何類別，就可以指派給該基底類別的物件。 反向則不成立，因為可從衍生類別隱含轉換為基底類別，但無法從基底類別轉換為衍生類別。 例如: 

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

- 呼叫函式`operator=`for`UserType2`提供`operator=`隨附`UserType1`引數。

- 如果 `UserType1::operator UserType2` 函式存在，呼叫這類明確轉換函式。

- 呼叫建構函式 `UserType2::UserType2`，前提是這類建構函式存在，而且接受 `UserType1` 引數並複製結果。

## <a name="compound-assignment"></a>複合指派

複合指派運算子，表中所示[指派運算子](#assignment-operators)，在表單中指定*e1* *op*= *e2*，其中*e1*是可修改左值不是**const**型別和*e2*是下列其中之一：

- 算術類型

- 指標，如果*op*是**+** 或 **-**

*E1* *op*= *e2*表單行為會如同*e1* **=** *e1* *op* *e2*，但是*e1*只評估一次。

對列舉類型的複合指派會產生錯誤訊息。 如果左運算元為指標類型，則右運算元必須是指標類型，或者必須是判斷值為 0 的常數運算式。 如果左運算元為整數類資料類型，則右運算元不能是指標類型。

## <a name="result-of-assignment-operators"></a>指派運算子的結果

指派運算子會在指派之後傳回左運算元所指定的物件值。 結果的類型會是左運算元的類型。 指派運算式的結果一律是左值。 這些運算子具有由右到左的順序關聯性。 左運算元必須是可修改的左值。

在 ANSI C 中，指派運算式的結果不是左值。 因此，合法的 C++ 運算式 `(a += b) += c` 在 C 中是不合法的。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 指派運算子](../c-language/c-assignment-operators.md)
