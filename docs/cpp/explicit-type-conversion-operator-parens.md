---
title: 明確類型轉換運算子：()
ms.date: 11/04/2016
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
ms.openlocfilehash: c168653a82b4d4c5023de1f76a1e6269625c74d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354866"
---
# <a name="explicit-type-conversion-operator-"></a>明確類型轉換運算子：()

C++ 允許使用類似函式呼叫的語法進行明確的類型轉換。

## <a name="syntax"></a>語法

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>備註

*簡單類型名稱*後跟括弧中包含的*運算式清單*使用指定的運算式建構指定類型的物件。 下列範例顯示將類型明確地轉換為類型 int：

```cpp
int i = int( d );
```

下面的示例顯示了一個`Point`類。

## <a name="example"></a>範例

```cpp
// expre_Explicit_Type_Conversion_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
public:
    // Define default constructor.
    Point() { _x = _y = 0; }
    // Define another constructor.
    Point( int X, int Y ) { _x = X; _y = Y; }

    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
    void Show()   { cout << "x = " << _x << ", "
                         << "y = " << _y << "\n"; }
private:
    unsigned _x;
    unsigned _y;
};

int main()
{
    Point Point1, Point2;

    // Assign Point1 the explicit conversion
    //  of ( 10, 10 ).
    Point1 = Point( 10, 10 );

    // Use x() as an l-value by assigning an explicit
    //  conversion of 20 to type unsigned.
    Point1.x() = unsigned( 20 );
    Point1.Show();

    // Assign Point2 the default Point object.
    Point2 = Point();
    Point2.Show();
}
```

## <a name="output"></a>輸出

```Output
x = 20, y = 10
x = 0, y = 0
```

雖然上述範例示範的是使用常數進行明確類型轉換，相同的技巧也可以在物件上進行這些轉換。 下列程式碼片段示範這項功能：

```cpp
int i = 7;
float d;

d = float( i );
```

使用「轉換」語法也可以指定明確類型轉換。 上述範例若是使用轉換語法重新撰寫則會如下所示：

```cpp
d = (float)i;
```

從單一值進行轉換時，轉換和函式樣式轉換的結果相同。 不過，在函式樣式語法中，您可以在轉換時指定一個以上的引數。 這項差異對於使用者定義的類型而言是很重要的。 請考慮 `Point` 類別及其轉換：

```cpp
struct Point
{
    Point( short x, short y ) { _x = x; _y = y; }
    ...
    short _x, _y;
};
...
Point pt = Point( 3, 10 );
```

前面的範例使用函式樣式轉換,示範如何將兩個值(一個用於*x*和一個用於*y)* 轉換為`Point`使用者定義的類型 。

> [!CAUTION]
> 由於其中覆寫了 C++ 編譯器的內建類型檢查，因此請小心使用明確類型轉換。

[強制轉換](../cpp/cast-operator-parens.md)記號必須用於轉換為沒有*簡單類型名稱*的類型(例如指標或引用類型)。 轉換為可以使用*簡單類型名稱*表示的類型可以以任一形式編寫。

在轉換中定義類型是不合法。

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
