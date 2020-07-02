---
title: span 類別（c + + 標準程式庫） |Microsoft Docs
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: e77f57bc56a75406745349e19d03bc26edc5470d
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813505"
---
# <a name="span-class-c-standard-library"></a>span 類別（c + + 標準程式庫）

提供連續物件序列的輕量視圖。 Span 提供了一種安全的方式，可以反復執行並編制索引至記憶體中的物件，例如在內建陣列中儲存的物件、 `std::array` 或 `std::vector` 。

如果您通常會使用指標和索引來存取一連串的後端物件， `span` 則會是更安全、輕量的替代方法。

`span`可以在編譯時期設定的大小，方法是將它指定為樣板引數，或指定在執行時間 `dynamic_extent` 。

## <a name="syntax"></a>語法

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>範本參數

|參數|描述|
|-|-|
|`T`| 範圍中元素的類型。 |
|`Extent`| 如果在編譯時期指定，則為範圍中的元素數目。 否則 `std::dynamic_extent` ，如果要在執行時間指定元素的數目，則為。 |

[推算指南](#deduction_guides)

## <a name="members"></a>成員

| **類型定義** | **描述** |
|-|-|
| [const_pointer](#pointer) | 元素之指標的類型 `const` 。 |
| [const_reference](#reference) | 專案的參考型別 `const` 。 |
| [difference_type](#difference_type) | 兩個項目之間帶正負號距離的類型。 |
| [element_type](#element_type) | Span 元素的類型。 |
| [定位](#iterator) | 範圍的反覆運算器類型。 |
| [滑鼠](#pointer) | 項目的指標類型。 |
| [reference](#reference) | 項目的參考類型。 |
| [reverse_iterator](#reverse_iterator) | 範圍的反向反覆運算器類型。 |
| [size_type](#size_type) | 範圍中兩個元素之間不帶正負號距離的類型。 |
| [value_type](#value_type) | 元素的類型，不含 `const` 或 `volatile` 限定。 |
| **建構函式** | **描述** |
|[跨](#span)| 結構 `span` 。|
| **反覆運算器支援** | **描述** |
|[起點](#begin) | 取得指向範圍中第一個元素的反覆運算器。|
|[成品](#end) | 取得指向範圍結尾的反覆運算器。 |
|[rbegin](#rbegin) | 取得反向反覆運算器，指向範圍的最後一個元素;也就是反轉範圍的開頭。|
|[rend](#rend) | 取得指向範圍前端的反向反覆運算器;也就是反轉範圍的結尾。|
| **Access 元素**| **描述** |
|[返回](#back) | 取得範圍中的最後一個元素。|
|[資料](#data) | 取得範圍中第一個元素的位址。|
|[前端](#front) | 取得範圍中的第一個元素。|
|[操作\[\]](#op_at) | 存取指定位置的元素。|
| **觀察者** | **描述** |
|[empty](#empty)| 測試 span 是否為空白。|
|[size](#size) | 取得範圍中的元素數目。|
|[size_bytes](#size_bytes) | 取得範圍的大小（以位元組為單位）。|
| **子檢視** | **描述**|
| [first](#first_view) | 從範圍前端取得 subspan。|
| [last](#last_view) | 從範圍的背面取得 subspan。|
| [subspan](#sub_view) | 從範圍中的任何位置取得 subspan。|
| **運算子** | **描述** |
|[span：： operator =](#op_eq)| 取代範圍。|
|[span：：運算子\[\]](#op_at)| 取得位於指定位置的元素。 |

## <a name="remarks"></a>備註

所有 `span` 成員函式都有常數時間複雜性。

不同 `array` `vector` 于或，span 不會「擁有」它內部的元素。 Span 不會為其中的專案釋放任何儲存體，因為它不會擁有這些物件的儲存空間。

## <a name="requirements"></a>需求

**標頭：**\<span>

**命名空間：** std

**編譯器選項：** /std： c + + 最新版本

## <a name="spanback"></a><a name="back"></a> `span::back`

取得範圍中的最後一個元素。

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>傳回值

範圍中最後一個元素的參考。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

取得指向範圍中第一個元素的反覆運算器。

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>傳回值

指向範圍中第一個元素的反覆運算器。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

取得範圍資料開頭的指標。

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>傳回值

範圍中儲存之第一個專案的指標。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

範圍中兩個專案之間的元素數目。

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

範圍中元素的類型。

```cpp
using element_type = T;
```

### <a name="remarks"></a>備註

建立範圍時，會從範本參數取得類型 `T` 。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

Span 是否包含元素。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>傳回值

`true`如果為 `this->size() == 0` ，則傳回。 否則為 `false`。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

取得範圍結尾的反覆運算器。

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>傳回值

指向超出範圍結尾的反覆運算器。

### <a name="remarks"></a>備註

`end` 用來測試迭代器是否已超過其範圍結尾。

不要取值此反覆運算器所傳回的值。 使用它來識別反覆運算器是否已到達超出範圍中的最後一個元素。

### <a name="example"></a>範例

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

從這個範圍的前方取得 subspan。

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>參數

*計數*\
要放入 subspan 的這個範圍前端的元素數目。  
元素的數目會指定為範本的參數或函式，如下所示。

### <a name="return-value"></a>傳回值

包含 `count` 來自此範圍前端之元素的範圍。

### <a name="remarks"></a>備註

如果可能的話，請使用此函式的範本版本 `count` ，在編譯時期驗證，並保留範圍的相關資訊，因為它會傳回固定範圍的範圍。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }

    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

取得範圍中的第一個元素。

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>傳回值

範圍中第一個元素的參考。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

跨範圍元素的反覆運算器類型。

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>備註

這個型別可做為範圍中元素的反覆運算器。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

取得 subspan，取自此範圍的結尾。

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>參數

*計數*\
從這個範圍結尾到要放入 subspan 的元素數目。
此數位可指定為範本的參數或函式，如下所示。

### <a name="return-value"></a>傳回值

包含 `count` 此範圍中最後一個元素的範圍。

### <a name="remarks"></a>備註

如果可能的話，請使用此函式的範本版本 `count` ，在編譯時期驗證，並保留範圍的相關資訊，因為它會傳回固定範圍的範圍。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }

    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

取得位於指定位置之範圍中的元素。

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>參數

*投影*\
要存取的範圍中以零為基底的元素。

### <a name="return-value"></a>傳回值

位置*位移*上的專案參考。 如果位置無效，則行為是未定義的。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

將另一個範圍指派給這個。

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>參數

*另一方面*\
要指派給這個的範圍。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

指派會執行資料指標和大小的淺層複製。 淺層複製是安全的，因為 `span` 不會為它所包含的元素配置記憶體。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

指標的類型，以及指向 `const` span 元素的指標。

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];

    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

取得反向反覆運算器，指向這個範圍的最後一個元素。

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

指向反轉範圍開頭的反覆運算器。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

參考的型別，以及 `const` 指向 span 元素的參考。

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

取得隨機存取反覆運算器，指向反轉範圍結尾之外的位置。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>傳回值

反向反覆運算器，指向反轉範圍中最後一個元素後面的預留位置;也就是未反轉範圍中第一個元素之前的預留位置。

### <a name="remarks"></a>備註

`rend`會與反轉範圍搭配使用，就如同[span：： end](#end)是與 span 搭配使用一樣。 使用它來測試反向反覆運算器是否已到達其範圍的結尾。

傳回的值 `rend` 不應該取值。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

範圍的反向反覆運算器類型。

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

取得範圍中的元素數目。

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>傳回值

範圍中的元素數目。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

取得範圍中的元素大小（以位元組為單位）。

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>傳回值

Span 中所有元素佔用的位元組數目;也就是 `sizeof(element_type)` 乘以範圍中的專案數。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

不帶正負號的類型，適合用來儲存範圍中的專案數。

```cpp
using size_type = size_t;
```

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span`構造.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>參數

*arr*\
從陣列中建立範圍。

*計數*\
要在範圍中的元素數目。

*頭*\
反覆運算器至範圍中的第一個元素。

*次*\
反覆運算器至範圍中最後一個元素的正上方。

*位*\
要在範圍中的元素數目。

*另一方面*\
建立此範圍的複本。

*r*\
從這個範圍中建造一個範圍。

### <a name="remarks"></a>備註

Span 不會針對範圍內的專案釋放儲存區，因為它不會擁有其中物件的儲存空間。

|建構函式  | 描述  |
|---------|---------|
|`span()` | 建立空的範圍。 只有在範本參數為或時，才會在多載解析期間考慮 `Extent` `0` `dynamic_extent` 。|
|`span(It first, size_type count)` | 從 iterator 的第一個專案中，建立範圍 `count` `first` 。  只有在樣板參數不是時，才會在多載解析時考慮 `Extent` `dynamic_extent` 。 |
|`span(It first, End last)` | 在反覆運算器中從專案建立範圍， `first` 直到到達結束為止 `last` 。 只有在樣板參數不是時，才會在多載解析時考慮 `Extent` `dynamic_extent` 。 `It`必須是 `contiguous_iterator` 。  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  從指定陣列的元素中，建立範圍 `N` 。 只有在樣板參數 `Extent` 為或等於時，才會在多載解析時考慮 `dynamic_extent` `N` 。 |
|`span(R&& r)` |  從範圍內建立範圍。 只有在樣板參數不是時才會參與多載解析 `Extent` `dynamic_extent` 。|
|`span(const span& other)` |  編譯器產生的複製函數。 資料指標的淺層複本是安全的，因為 span 不會配置記憶體來保存元素。 |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | 轉換函式：從另一個範圍中建造一個範圍。 只有在範本參數 `Extent` 為 `dynamic_extent` 、或 `N` 為或 equals 時， `dynamic_extent` `Extent` 才會參與多載解析。|

### <a name="example"></a>範例

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;

    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }

    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

取得此範圍的 subspan。

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>參數

*計數*\
要放入 subspan 中的元素數目。 如果 `count` 為 `dynamic_extent` （預設值），則會將 subspan 從 `offset` 到這個範圍的結尾。

*投影*\
此範圍中用來啟動 subspan 的位置。

### <a name="return-value"></a>傳回值

從這個範圍開始的範圍 `offset` 。 包含 `count` 元素。

### <a name="remarks"></a>備註

此函式的範本版本可在編譯時期檢查計數，藉由傳回固定範圍的範圍來保留範圍的相關資訊。

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

範圍中元素的類型，不含 `const` 或 `volatile` 限定。

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a>推算指南

以下是針對 span 提供的推斷指南。

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>另請參閱

[\<span>](../standard-library/span.md)  
[如何使用類別樣板引數推斷](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
