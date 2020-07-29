---
title: 以範圍為基礎的 for 陳述式 (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 1197080e2e96e0e5c51bc06e93026567a33c7842
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223612"
---
# <a name="range-based-for-statement-c"></a>以範圍為基礎的 for 陳述式 (C++)

對於 `statement` 中的每個項目，重複且循序地執行 `expression`。

## <a name="syntax"></a>語法

> **`for (`***for 範圍聲明* **`:`***運算式***`)`**\
&emsp;*語句*

## <a name="remarks"></a>備註

使用範圍架構的 **`for`** 語句來建立必須透過*範圍*執行的迴圈，其定義為您可以逐一查看的任何專案（例如）， `std::vector` 或任何其他 c + + 標準程式庫序列，其範圍是由和所定義 `begin()` `end()` 。 在部分中宣告的名稱在 `for-range-declaration` 語句中是本機的 **`for`** ，而且不能在或中重新 `expression` 宣告 `statement` 。 請注意，在 [`auto`](../cpp/auto-cpp.md) 語句的部分中，關鍵字是慣用的 `for-range-declaration` 。

**Visual Studio 2017 中的新功能：** 以範圍為基礎的 **`for`** 迴圈不再需要該 `begin()` 和傳回 `end()` 相同類型的物件。 這可讓傳回 `end()` sentinel 物件，例如範圍-V3 提案中定義的範圍所使用的。 如需詳細資訊，請參閱在 GitHub 上[一般化以範圍為基礎的 `For` 迴圈](https://wg21.link/p0184r0)和[範圍 v3 程式庫](https://github.com/ericniebler/range-v3)。

這段程式碼會示範如何使用以範圍為基礎的 **`for`** 迴圈，逐一查看陣列和向量：

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

**`for`** 當中的其中一個執行時，以範圍為基礎的迴圈 `statement` 會終止： [`break`](../cpp/break-statement-cpp.md) 、 [`return`](../cpp/return-statement-cpp.md) 或 [`goto`](../cpp/goto-statement-cpp.md) 至以範圍為基礎之迴圈以外的標記語句 **`for`** 。 [`continue`](../cpp/continue-statement-cpp.md)以範圍為基礎的迴圈中的語句 **`for`** 只會終止目前的反復專案。

請記住下列有關範圍型的事實 **`for`** ：

- 自動辨識陣列。

- 辨識具有 `.begin()` 和 `.end()` 的容器。

- 使用與引數相依的查閱 `begin()` 和 `end()` 以取得任何其他項目。

## <a name="see-also"></a>另請參閱

[`auto`](../cpp/auto-cpp.md)<br/>
[反覆運算陳述式](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[`while`語句（c + +）](../cpp/while-statement-cpp.md)<br/>
[`do-while`語句（c + +）](../cpp/do-while-statement-cpp.md)<br/>
[`for`語句（c + +）](../cpp/for-statement-cpp.md)
