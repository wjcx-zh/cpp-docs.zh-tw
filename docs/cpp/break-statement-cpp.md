---
title: break 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 3dda0b19fffaaf725ab363a0c4fe70d2ca54e3f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267711"
---
# <a name="break-statement-c"></a>break 陳述式 (C++)

**中斷**陳述式會結束執行的最接近的封閉式迴圈或條件出現的陳述式。 控制會傳遞至陳述式結尾之後的陳述式 (如果有的話)。

## <a name="syntax"></a>語法

```
break;
```

## <a name="remarks"></a>備註

**中斷**陳述式搭配條件式[切換](../cpp/switch-statement-cpp.md)陳述式與[請勿](../cpp/do-while-statement-cpp.md)，[如](../cpp/for-statement-cpp.md)，和[時](../cpp/while-statement-cpp.md)迴圈陳述式。

在 **切換**陳述式**中斷**陳述式會執行下一個陳述式外部程式**切換**陳述式。 不含**中斷**陳述式中，每個陳述式，從相符**案例**結尾標籤**切換**陳述式，包括**預設**子句，會執行。

在迴圈中，**中斷**陳述式會結束執行的最接近的封閉式**不要**，**如**，或**雖然**陳述式。 控制會傳遞到已結束之陳述式的下一個陳述式 (如果有的話)。

在巢狀陳述式中，**中斷**陳述式只會結束**進行**，**如**，**切換**，或**時**立即將它關閉的陳述式。 您可以使用**會傳回**或是**goto**陳述式將控制項從更深的巢狀結構。

## <a name="example"></a>範例

下列程式碼示範如何使用**中斷**中的陳述式**如**迴圈。

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

下列程式碼示範如何使用**中斷**中**雖然**迴圈並**執行**迴圈。

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

下列程式碼示範如何使用**中斷**switch 陳述式中。 您必須使用**中斷**在所有情況下，如果您要個別; 處理每個案例中，如果您不使用**中斷**，執行程式碼便會略過下一個案例。

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