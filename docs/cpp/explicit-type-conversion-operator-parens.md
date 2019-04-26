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
ms.openlocfilehash: 9dc9440db9ea1ff7285ff9b682f6be9900c2a1ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184309"
---
# <a name="explicit-type-conversion-operator-"></a>明確類型轉換運算子：()

C++ 允許使用類似函式呼叫的語法進行明確的類型轉換。

## <a name="syntax"></a>語法

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>備註

A*簡單類型名稱*後面*運算式清單*括在括號建構使用指定的運算式指定之型別的物件。 下列範例顯示將類型明確地轉換為類型 int：

```cpp
int i = int( d );
```

下列範例所示`Point`類別。

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

## <a name="output"></a>Output

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

上述範例中，使用函式樣式轉換，其中示範如何將兩個值 (一個用於*x* ，另一個用於*y*) 使用者定義型別`Point`。

> [!CAUTION]
>  由於其中覆寫了 C++ 編譯器的內建類型檢查，因此請小心使用明確類型轉換。

[Cast](../cpp/cast-operator-parens.md)轉換為不需要的類型，必須使用標記法*簡單類型名稱*（比方說，指標或參考類型）。 可以表示的類型轉換*簡單類型名稱*以任一形式。

在轉換中定義類型是不合法。

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)