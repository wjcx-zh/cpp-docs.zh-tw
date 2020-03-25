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
ms.openlocfilehash: 079a3390df56ba55bd4d71a320faa249266abb54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189009"
---
# <a name="explicit-type-conversion-operator-"></a>明確類型轉換運算子：()

C++ 允許使用類似函式呼叫的語法進行明確的類型轉換。

## <a name="syntax"></a>語法

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>備註

後面接著以括弧括住的*運算式清單*的簡單型別*名稱*，會使用指定的運算式來構造指定型別的物件。 下列範例顯示將類型明確地轉換為類型 int：

```cpp
int i = int( d );
```

下列範例顯示 `Point` 類別。

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

雖然上述範例示範的是使用常數進行明確類型轉換，相同的技巧也可以在物件上進行這些轉換。 下列程式碼片段示範如何進行：

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

上述範例會使用函式樣式轉換，示範如何將兩個值（一個用於*x* ，另一個用於*y*）轉換成使用者定義型別 `Point`。

> [!CAUTION]
>  由於其中覆寫了 C++ 編譯器的內建類型檢查，因此請小心使用明確類型轉換。

[轉換](../cpp/cast-operator-parens.md)標記法必須用於轉換成不具有*簡單類型名稱*的類型（例如指標或參考型別）。 轉換成可以用*簡單類型名稱*表示的類型，可以使用任一形式來撰寫。

在轉換中定義類型是不合法。

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
