---
title: 指派
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: f1697a8de3dff6c46de01db6bbff5447c03b6282
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190699"
---
# <a name="assignment"></a>指派

指派運算子（ **=** ）是嚴格的說，這是二元運算子。 它的宣告與任何其他二元運算子相同，但有下列例外狀況：

- 它必須為非靜態成員函式。 No **operator =** 可以宣告為非成員函式。
- 衍生類別不會進行繼承。
- 預設的**operator = 函**式可以由編譯器針對類別類型產生（如果沒有的話）。

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

提供的引數是運算式的右側。 運算子會傳回物件以保留指派運算子的行為，而該運算子會在指派完成後傳回左方的值。 這可允許指派的連結，例如：

```cpp
pt1 = pt2 = pt3;
```

複製指派運算子不會與複製的處理函式混淆。 從現有物件的結構中，會呼叫後者：

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> 建議遵循[三個規則](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))，定義複製指派運算子的類別也應該明確地定義複製的「程式」、「析構函式」和「從 c + + 11 開始」、「移動程式」和「移動指派運算子」。

## <a name="see-also"></a>另請參閱

- [運算子多載](../cpp/operator-overloading.md)
- [複製建構函式和複製指派運算子 (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
