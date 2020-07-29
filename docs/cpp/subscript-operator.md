---
title: 注標運算子 []
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: a4eb878a18aa38b7047104903d10d96d66cc6720
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231087"
---
# <a name="subscript-operator-"></a>注標運算子 []

## <a name="syntax"></a>語法

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>備註

後置運算式（也可以是主要運算式）後面接著注標運算子 **[]**，指定陣列索引。

如需 c + +/CLI 中 managed 陣列的詳細資訊，請參閱[陣列](../extensions/arrays-cpp-component-extensions.md)。

通常，後置*運算式*所代表的值是指標值，例如陣列識別碼，而*expression*則是整數值（包括列舉類型）。 不過，在語法上需要的是其中一個指標類型的運算式，另一個則是整數類型。 因此，整數值可以在後置*運算式*位置中，而指標值可以在*運算式*或注標位置的括弧中。 請考慮下列程式碼片段：

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

在上述範例中，運算式 `nArray[2]` 與 `2[nArray]` 相同。 原因是注標運算式的結果 `e1[e2]` 是由所提供：

`*((e2) + (e1))`

運算式所產生的位址不是來自位址*e1*的*e2*位元組。 而是會調整位址，以產生陣列*e2*中的下一個物件。 例如：

```cpp
double aDbl[2];
```

和的位址 `aDb[0]` `aDb[1]` 是8個位元組，也就是類型的物件大小 **`double`** 。 這項根據物件類型的調整是由 c + + 語言自動完成，並定義于[加法類運算子](../cpp/additive-operators-plus-and.md)中，其中會討論指標類型運算元的加法和減法。

註標運算式也可以擁有多個註標，如下所示：

*運算式*2 **[** *運算式*2 **] [** *expression3* **]** .。。

註標運算式的關聯是由左至右。 最左邊的注標*運算式（運算式* **1 [** *運算式*2 **]**）會先進行評估。 *expression1* 和 *expression2* 相加所產生的位址會形成指標運算式，然後 *expression3* 會加入這個指標運算式形成新的指標運算式，依此類推，直到加入最後一個註標運算式為止。 <strong>\*</strong>除非最後一個指標值會定址陣列類型，否則間接運算子（）會在評估最後一個下標運算式之後套用。

具有多個註標的運算式會參考多維陣列的元素。 所謂的多維陣列是指其中所包含的元素也是一種陣列。 例如，三維陣列的第一個元素是具有兩個維度的陣列。 下列範例會宣告和初始化一個簡單的二維字元陣列：

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>正數和負數註標

陣列的第一個元素是元素 0。 C + + 陣列的範圍是從*陣列*[0] 到*陣列*[*大小*-1]。 不過，C++ 支援正註標和負註標。 負註標必須在陣列界限內，如果不在界限內，則無法預測結果。 下列程式碼顯示正的和負的陣列註標：

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

最後一行中的負數注標可能會產生執行階段錯誤，因為它指向 **`int`** 記憶體中比陣列來源更低的位址256位置。 指標 `midArray` 會初始化為的中間， `intArray` 因此可能（但危險）在其上使用正和負的陣列索引。 陣列註標錯誤不會產生編譯時間錯誤，但是會產生無法預期的結果。

註標運算子可以交替。 因此，只要注標運算子未多載（請參閱多載[運算子](../cpp/operator-overloading.md)），運算式*陣列*[*索引*] 和*索引*[*陣列*] 就會保證相等。 第一種形式是最常用的程式撰寫作法，但兩種都可以運作。

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[陣列](../cpp/arrays-cpp.md)<br/>
[一維陣列](../c-language/one-dimensional-arrays.md)<br/>
[多維陣列](../c-language/multidimensional-arrays-c.md)<br/>
