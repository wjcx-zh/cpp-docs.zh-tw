---
title: 以範圍為基礎的 for 陳述式 (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 504f177cf68b978642f15ba4799cab8cb517f447
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188346"
---
# <a name="range-based-for-statement-c"></a>以範圍為基礎的 for 陳述式 (C++)

對於 `statement` 中的每個項目，重複且循序地執行 `expression`。

## <a name="syntax"></a>語法

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>備註

使用以範圍為基礎**的 for**語句來建造必須透過「範圍」執行的迴圈，這定義為您可以逐一查看的任何專案（例如 `std::vector`），或是由 `begin()` 和C++ `end()`所定義的任何其他標準程式庫序列。 在 `for-range-declaration` 部分中所宣告的名稱在**for**語句中為 local，而且無法在 `expression` 或 `statement`中重新宣告。 請注意， [auto](../cpp/auto-cpp.md)關鍵字在語句的 `for-range-declaration` 部分中是慣用的。

**Visual Studio 2017 中的新功能：** 以範圍為基礎的 for 迴圈不再需要 begin （）和 end （）傳回相同類型的物件。 這可讓 end() 傳回 sentinel 物件，例如 Ranges-V3 提案中所定義範圍使用的物件。 如需詳細資訊，請參閱 [Generalizing the Range-Based For Loop](https://wg21.link/p0184r0) (一般化範圍架構的 For 迴圈) 和 [range-v3 library on GitHub](https://github.com/ericniebler/range-v3) (GitHub 上的 range-v3 程式庫)。

這段程式碼示範如何使用範圍架構**的 for**迴圈來逐一查看陣列和向量：

```cpp
// range-based-for.cpp
// compile by using: cl /EHsc /nologo /W4
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    // Basic 10-element integer array.
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Range-based for loop to iterate through the array.
    for( int y : x ) { // Access by value using a copy declared as a specific type.
                       // Not preferred.
        cout << y << " ";
    }
    cout << endl;

    // The auto keyword causes type inference to be used. Preferred.

    for( auto y : x ) { // Copy of 'x', almost always undesirable
        cout << y << " ";
    }
    cout << endl;

    for( auto &y : x ) { // Type inference by reference.
        // Observes and/or modifies in-place. Preferred when modify is needed.
        cout << y << " ";
    }
    cout << endl;

    for( const auto &y : x ) { // Type inference by const reference.
        // Observes in-place. Preferred when no modify is needed.
        cout << y << " ";
    }
    cout << endl;
    cout << "end of integer array test" << endl;
    cout << endl;

    // Create a vector object that contains 10 elements.
    vector<double> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i + 0.14159);
    }

    // Range-based for loop to iterate through the vector, observing in-place.
    for( const auto &j : v ) {
        cout << j << " ";
    }
    cout << endl;
    cout << "end of vector test" << endl;
}
```

輸出如下：

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

以範圍為基礎**的 for**迴圈會在 `statement` 中的其中一個執行時終止：在範圍架構**的 for**迴圈外，會[中斷](../cpp/break-statement-cpp.md)、[傳回或移](../cpp/goto-statement-cpp.md)至已[加上卷](../cpp/return-statement-cpp.md)標的語句。 以範圍**為基礎的 for**迴圈中的[continue](../cpp/continue-statement-cpp.md)語句只會終止目前的反復專案。

請記住下列關於範圍型**的**事實：

- 自動辨識陣列。

- 辨識具有 `.begin()` 和 `.end()` 的容器。

- 使用與引數相依的查閱 `begin()` 和 `end()` 以取得任何其他項目。

## <a name="see-also"></a>另請參閱

[auto](../cpp/auto-cpp.md)<br/>
[反覆運算陳述式](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[while 陳述式 (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while 陳述式 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for 陳述式 (C++)](../cpp/for-statement-cpp.md)
