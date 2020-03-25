---
title: break 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 23d31e1456106d5f82c4a13079c72c231b8477bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190478"
---
# <a name="break-statement-c"></a>break 陳述式 (C++)

**Break**語句會結束執行最近的封閉迴圈或其出現的條件陳述式。 控制會傳遞至陳述式結尾之後的陳述式 (如果有的話)。

## <a name="syntax"></a>語法

```
break;
```

## <a name="remarks"></a>備註

**Break**語句搭配條件式[switch](../cpp/switch-statement-cpp.md)語句和[do](../cpp/do-while-statement-cpp.md)、 [for](../cpp/for-statement-cpp.md)和[while](../cpp/while-statement-cpp.md)迴圈語句使用。

在**switch**語句中， **break**語句會導致程式在**switch**語句外執行下一個語句。 若沒有**break**語句，則會執行符合的**case**標籤到**switch**語句結尾的每個語句（包括**default**子句）。

在迴圈中， **break**語句會結束執行最接近的封閉式**do**、 **for**或**while**語句。 控制會傳遞到已結束之陳述式的下一個陳述式 (如果有的話)。

在 nested 語句中， **break**語句只會結束立即將它括住的**do**、 **for**、 **switch**或**while**語句。 您可以使用**return**或**goto**語句，從更深層的嵌套結構中轉移控制權。

## <a name="example"></a>範例

下列程式碼顯示如何在**for**迴圈中使用**break**語句。

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

下列程式碼顯示如何在**while**迴圈和**do**迴圈中使用**break** 。

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

下列程式碼顯示如何在 switch 語句中使用**break** 。 如果您想要個別處理每個案例，則必須在每個案例中使用**break** ;如果您未使用**break**，則程式碼執行會落在下一個案例中。

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>另請參閱

[跳躍陳述式](../cpp/jump-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[continue 陳述式](../cpp/continue-statement-cpp.md)
