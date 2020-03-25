---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: a841c41c8f640dcde2a3d98841f66f6c6dc04602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208282"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

包含 STL/CLR 標頭 `<cliext/utility>` 以定義樣板類別 `pair` 和數個支援的範本函式。

## <a name="syntax"></a>語法

```cpp
#include <utility>
```

## <a name="requirements"></a>需求

**標頭：** \<cliext/公用程式 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類別|描述|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|包裝一對元素。|

|運算子|描述|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|配對相等比較。|
|[operator!= (pair) (STL/CLR)](#op_neq)|配對不等於比較。|
|[operator< (pair) (STL/CLR)](#op_lt)|配對小於比較。|
|[operator\<= （配對）（STL/CLR）](#op_lteq)|配對小於或等於比較。|
|[operator> (pair) (STL/CLR)](#op_gt)|配對大於比較。|
|[operator>= (pair) (STL/CLR)](#op_gteq)|配對大於或等於比較。|

|函式|描述|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|從一對值進行配對。|

## <a name="members"></a>成員

## <a name="pair-stlclr"></a><a name="pair"></a>配對（STL/CLR）
此範本類別描述包裝一對值的物件。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>參數

*Value1*<br/>
第一個包裝值的類型。

*Value2*<br/>
第二個包裝值的類型。

## <a name="members"></a>成員

|類型定義|描述|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|第一個包裝值的類型。|
|[pair::second_type (STL/CLR)](#second_type)|第二個包裝值的類型。|

|成員物件|描述|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|第一個儲存的值。|
|[pair::second (STL/CLR)](#second)|第二個儲存的值。|

|成員函式|描述|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|構造配對物件。|
|[pair::swap (STL/CLR)](#swap)|交換兩組的內容。|

|運算子|描述|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|取代預存值的配對。|

## <a name="remarks"></a>備註

物件會儲存一對值。 您可以使用此範本類別，將兩個值結合成單一物件。 此外，物件 `cliext::pair` （在此描述）只會儲存 managed 類型;若要儲存一對非受控類型，請使用在 `<utility>`中宣告的 `std::pair`。

## <a name="pairfirst-stlclr"></a><a name="first"></a>成對：： first （STL/CLR）

第一個已包裝的值。

### <a name="syntax"></a>語法

```cpp
Value1 first;
```

### <a name="remarks"></a>備註

物件會儲存第一個包裝的值。

### <a name="example"></a>範例

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>成對：： first_type （STL/CLR）

第一個包裝值的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數*Value1*的同義字。

### <a name="example"></a>範例

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>成對：： operator = （STL/CLR）

取代預存值的配對。

### <a name="syntax"></a>語法

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
配對以複製。

### <a name="remarks"></a>備註

成員運算子會將*許可權*複製到物件，然後傳回 `*this`。 您可以使用它，以*右邊*的一組預存值來取代儲存的值配對。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>配對：:p 空中（STL/CLR）

構造配對物件。

### <a name="syntax"></a>語法

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>參數

*right*<br/>
要儲存的配對。

*val1*<br/>
要儲存的第一個值。

*val2*<br/>
要儲存的第二個值。

### <a name="remarks"></a>備註

此構造函式：

`pair();`

使用預設的結構值，初始化預存的配對。

此構造函式：

`pair(pair<Value1, Value2>% right);`

使用 `right.`組[： first （stl/clr）](../dotnet/pair-first-stl-clr.md)和 `right.`組[：： second （stl/clr）](../dotnet/pair-second-stl-clr.md)，初始化預存配對。

`pair(pair<Value1, Value2>^ right);`

使用 `right->`組[： first （stl/clr）](../dotnet/pair-first-stl-clr.md)和 `right>`組[：： second （stl/clr）](../dotnet/pair-second-stl-clr.md)，初始化預存配對。

此構造函式：

`pair(Value1 val1, Value2 val2);`

使用*val1*和*val2*，初始化預存配對。

### <a name="example"></a>範例

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="pairsecond-stlclr"></a><a name="second"></a>成對：： second （STL/CLR）

第二個已包裝的值。

### <a name="syntax"></a>語法

```cpp
Value2 second;
```

### <a name="remarks"></a>備註

物件會儲存第二個已包裝的值。

### <a name="example"></a>範例

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>成對：： second_type （STL/CLR）

第二個包裝值的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數*Value2*的同義字。

### <a name="example"></a>範例

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="pairswap-stlclr"></a><a name="swap"></a>成對：： swap （STL/CLR）

交換兩組的內容。

### <a name="syntax"></a>語法

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
與交換內容的配對。

### <a name="remarks"></a>備註

成員函式會在 `*this` 和*right*之間交換已儲存的值配對。

### <a name="example"></a>範例

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair （STL/CLR）

從一對值進行 `pair`。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>參數

*Value1*<br/>
第一個包裝值的類型。

*Value2*<br/>
第二個包裝值的類型。

*first*<br/>
要包裝的第一個值。

*second*<br/>
要換行的第二個值。

### <a name="remarks"></a>備註

此範本函式會傳回 `pair<Value1, Value2>(first, second)`。 您可以使用它來從一對值中建立 `pair<Value1, Value2>` 物件。

### <a name="example"></a>範例

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>operator！ = （配對）（STL/CLR）

配對不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左邊配對。

*right*<br/>
要比較的右配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left == right)`。 您可以使用它來測試當兩個配對是以元素進行比較時，是否將*left*與*right*排序。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>operator&lt; （配對）（STL/CLR）

配對小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左邊配對。

*right*<br/>
要比較的右配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`。 您可以使用它來*測試當兩*個配對是以元素進行比較時，是否將*left*排序。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>operator&lt;= （配對）（STL/CLR）

配對小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左邊配對。

*right*<br/>
要比較的右配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(right < left)`。 您可以使用它來測試當兩個配對是以元素進行比較時，*左側*是否未按*右*排序。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>operator = = （配對）（STL/CLR）

配對相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左邊配對。

*right*<br/>
要比較的右配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `left.first ==` `right.first &&` `left.second ==` `right.second`。 您可以使用它來測試當兩個配對是以元素進行比較時，*左側*是否與*右*排序相同。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>operator&gt; （配對）（STL/CLR）

配對大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左邊配對。

*right*<br/>
要比較的右配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `right` `<` `left`。 您可以使用它來測試當兩個配對是以元素進行比較時 *，是否要*在*右*向後排序。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>operator&gt;= （配對）（STL/CLR）

配對大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左邊配對。

*right*<br/>
要比較的右配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left < right)`。 您可以使用它來*測試當兩*個配對是以元素進行比較時，*左側*是否未排序。

### <a name="example"></a>範例

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```
