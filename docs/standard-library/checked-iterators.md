---
title: Checked Iterators
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: 2327638208f30908cd3429ae656ce569f5821195
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684899"
---
# <a name="checked-iterators"></a>Checked Iterators

已檢查的迭代器能確保您的容器界限不會被覆寫。 已檢查的迭代器適用於發行組建和偵錯組建。 如需如何在偵錯模式編譯時使用偵錯迭代器的詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。

## <a name="remarks"></a>備註

如需如何停用由已檢查迭代器所產生之警告的資訊，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

您可以使用[ \_ 反覆運算器 \_ DEBUG \_ LEVEL](../standard-library/iterator-debug-level.md)預處理器宏來啟用或停用已檢查的反覆運算器功能。 如果 _ITERATOR_DEBUG_LEVEL 定義為1或2，不安全的反覆運算器使用會導致執行階段錯誤，而且程式會終止。 如果已定義為 0，已檢查的迭代器停用。 根據預設，發行組建的 _ITERATOR_DEBUG_LEVEL 值為0，而針對 DEBUG 組建則為2。

> [!IMPORTANT]
> 舊版文件和原始程式碼可能會參考 [_SECURE_SCL](../standard-library/secure-scl.md) 巨集。 使用 _ITERATOR_DEBUG_LEVEL 來控制 _SECURE_SCL。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

當 _ITERATOR_DEBUG_LEVEL 定義為1或2時，會執行這些反覆運算器檢查：

- 檢查所有標準迭代器 (例如 [vector::iterator](../standard-library/vector-class.md#iterator))。

- 如果輸出迭代器是已檢查的迭代器，呼叫標準程式庫函式 (例如 [std::copy](../standard-library/algorithm-functions.md#copy)) 會取得已檢查的行為。

- 如果輸出迭代器是未檢查的迭代器，呼叫標準程式庫函式會產生編譯器警告。

- 如果在容器界限之外存取，下列函式會產生執行階段錯誤：

:::row:::
   :::column span="":::
      &emsp;&emsp;[`basic_string::operator[]`](../standard-library/basic-string-class.md#op_at)\
      &emsp;&emsp;[`bitset::operator[]`](../standard-library/bitset-class.md#op_at)\
      &emsp;&emsp;[`deque::back`](../standard-library/deque-class.md#back)\
      &emsp;&emsp;[`deque::front`](../standard-library/deque-class.md#front)
   :::column-end:::
   :::column span="":::
      [`deque::operator[]`](../standard-library/deque-class.md#op_at)\
      [`list::back`](../standard-library/list-class.md#back)\
      [`list::front`](../standard-library/list-class.md#front)\
      [`queue::back`](../standard-library/queue-class.md#back)
   :::column-end:::
   :::column span="":::
      [`queue::front`](../standard-library/queue-class.md#front)\
      [`vector::back`](../standard-library/vector-class.md#back)\
      [`vector::front`](../standard-library/vector-class.md#front)\
      [`vector::operator[]`](../standard-library/vector-class.md#op_at)
   :::column-end:::
:::row-end:::

當 _ITERATOR_DEBUG_LEVEL 定義為0時：

- 不會檢查任何標準迭代器。 迭代器可移到容器界限之外，因而導致未定義的行為。

- 如果輸出迭代器是已檢查的迭代器，呼叫標準程式庫函式 (例如 `std::copy`) 會取得已檢查的行為。

- 如果輸出迭代器是未檢查的迭代器，呼叫標準程式庫函式會取得未檢查的行為。

如果您嘗試移動超過容器的界限，已檢查的迭代器會參考呼叫 `invalid_parameter_handler` 的迭代器。 如需 `invalid_parameter_handler` 的詳細資訊，請參閱[參數驗證](../c-runtime-library/parameter-validation.md)。

支援已檢查迭代器的迭代器配接器是 [checked_array_iterator 類別](../standard-library/checked-array-iterator-class.md)和 [unchecked_array_iterator 類別](../standard-library/unchecked-array-iterator-class.md)。

## <a name="examples"></a>範例

當您使用 _ITERATOR_DEBUG_LEVEL 設定為1或2的編譯時，如果您嘗試使用特定類別的索引運算子來存取容器界限之外的專案，就會發生執行階段錯誤。

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

這個程式會列印 "67"，然後快顯具有其他失敗資訊的判斷提示失敗對話方塊。

同樣地，當您使用 _ITERATOR_DEBUG_LEVEL 設定為1或2時，如果您嘗試在 `front` `back` 容器為空白時使用或在容器類別中存取專案，則會發生執行階段錯誤。

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

這個程式會快顯具有其他失敗資訊的判斷提示失敗對話方塊。

下列程式碼示範各種迭代器使用案例，附帶每個使用案例的註解。 根據預設，在偵錯工具組建中，_ITERATOR_DEBUG_LEVEL 設定為2，在零售組建中設定為0。

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

當您使用 `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` 編譯此程式碼時，編譯器會發出警告，但會編譯成可執行檔，而沒有任何錯誤：

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

以命令列執行時，可執行檔會產生以下輸出：

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫總覽](../standard-library/cpp-standard-library-overview.md)\
[Debug Iterator 支援](../standard-library/debug-iterator-support.md)
