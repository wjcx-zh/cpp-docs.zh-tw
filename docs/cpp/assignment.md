---
title: 指派
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603423"
---
# <a name="assignment"></a>指派

指派運算子 (**=**) 嚴格來說，是二元運算子。 它的宣告與任何其他二元運算子相同，但有下列例外狀況：

- 它必須為非靜態成員函式。 否**運算子 =** 可以宣告為非成員函式。
- 衍生類別不會進行繼承。
- 預設值**運算子 =** 可以針對類別類型，編譯器所產生函式，如果不存在。

下列範例說明如何宣告指派運算子：

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

提供的引數是運算式的右側。 運算子會傳回物件以保留指派運算子的行為，而該運算子會在指派完成後傳回左方的值。 這可讓鏈結的指派，例如：

```cpp
pt1 = pt2 = pt3;
```

複製指派運算子並不會複製建構函式與混淆。 後者會呼叫新的物件建構期間從現有：

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> 建議您最好遵循[三個規則](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))，定義複製指派運算子的類別應該明確地定義複製建構函式，解構函式，和，開始使用 C + + 11，移動建構函式和移動指派運算子。

## <a name="see-also"></a>另請參閱

- [運算子多載](../cpp/operator-overloading.md)
- [複製建構函式和複製指派運算子 (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)