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
ms.openlocfilehash: 6d025230abcff42e367a231e616a13f0f8c684f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320301"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

包括用於定義範本類`<cliext/utility>``pair`的 STL/CLR 標頭以及多個支援範本函數。

## <a name="syntax"></a>語法

```cpp
#include <utility>
```

## <a name="requirements"></a>需求

**標題**\<:cliext/實用程式>

**命名空間**:cliext

## <a name="declarations"></a>宣告

|類別|描述|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|包裝一對元素。|

|運算子|描述|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|對相等的比較。|
|[運算子!* (對) (STL/CLR)](#op_neq)|對不相等的比較。|
|[運算子<(對)(STL/CLR)](#op_lt)|對小於比較。|
|[運算子\<= (對) (STL/CLR)](#op_lteq)|對小於或相等的比較。|
|[運算子>(對)(STL/CLR)](#op_gt)|對大於比較。|
|[運算子>= (對) (STL/CLR)](#op_gteq)|大於或等於比較的對。|

|函式|描述|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|從一對值製作一對。|

## <a name="members"></a>成員

## <a name="pair-stlclr"></a><a name="pair"></a>對(STL/CLR)

範本類描述環繞一對值的物件。

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
|[pair::first (STL/CLR)](#first)|第一個存儲值。|
|[pair::second (STL/CLR)](#second)|第二個記憶體值。|

|成員函式|描述|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|構造對物件。|
|[pair::swap (STL/CLR)](#swap)|交換兩對的內容。|

|運算子|描述|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|替換存儲的值對。|

## <a name="remarks"></a>備註

物件存儲一對值。 使用此範本類將兩個值合併到單個物件中。 此外,物件(`cliext::pair`此處描述)僅儲存託管類型;因此,該物件(此處描述)僅儲存託管類型。以存儲一對非託管類型使用`std::pair`,在中`<utility>`聲明。

## <a name="pairfirst-stlclr"></a><a name="first"></a>對:第一(STL/CLR)

第一個包裝值。

### <a name="syntax"></a>語法

```cpp
Value1 first;
```

### <a name="remarks"></a>備註

物件存儲第一個包裝值。

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a>對::first_type(STL/CLR)

第一個包裝值的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>備註

類型是範本參數*Value1*的同義詞。

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a>對::運算符*(STL/CLR)

替換存儲的值對。

### <a name="syntax"></a>語法

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的配對。

### <a name="remarks"></a>備註

成員運算子*將右邊*複製到物件,`*this`然後傳回 。 使用它將存儲的值對替換為*右側*存儲的值對的副本。

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a>對::p航空(STL/CLR)

構造對物件。

### <a name="syntax"></a>語法

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>參數

*對*<br/>
要存儲的對。

*val1*<br/>
要存儲的第一個值。

*瓦爾2*<br/>
要存儲的第二個值。

### <a name="remarks"></a>備註

建構函數:

`pair();`

使用預設構造值初始化存儲的對。

建構函數:

`pair(pair<Value1, Value2>% right);`

初始化存儲的對與`right.`[對::第一(STL/CLR)](../dotnet/pair-first-stl-clr.md)和`right.`[對:秒(STL/CLR)。](../dotnet/pair-second-stl-clr.md)

`pair(pair<Value1, Value2>^ right);`

初始化存儲的對與`right->`[對::第一(STL/CLR)](../dotnet/pair-first-stl-clr.md)和`right>`[對:秒(STL/CLR)。](../dotnet/pair-second-stl-clr.md)

建構函數:

`pair(Value1 val1, Value2 val2);`

用*val1*和*val2*初始化存儲的對。

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

## <a name="pairsecond-stlclr"></a><a name="second"></a>對:秒(STL/CLR)

第二個包裝值。

### <a name="syntax"></a>語法

```cpp
Value2 second;
```

### <a name="remarks"></a>備註

物件存儲第二個包裝值。

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a>對::second_type(STL/CLR)

第二個包裝值的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>備註

類型是範本參數*Value2*的同義詞。

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

## <a name="pairswap-stlclr"></a><a name="swap"></a>對:交換(STL/CLR)

交換兩對的內容。

### <a name="syntax"></a>語法

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
配對以交換內容。

### <a name="remarks"></a>備註

成員函數交換*與*之間的`*this`儲存的值對 。

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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a>make_pair(STL/CLR)

從一`pair`對值製作 。

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

*第一*<br/>
要換行的第一個值。

*第二*<br/>
要換行的第二個值。

### <a name="remarks"></a>備註

此範本函式會傳回 `pair<Value1, Value2>(first, second)`。 使用它從一`pair<Value1, Value2>`對值構造物件。

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a>運算子!* (對) (STL/CLR)

對不相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左對。

*對*<br/>
要比較的右對。

### <a name="remarks"></a>備註

運算子函數傳回`!(left == right)`。 使用它來測試當按元素比較兩對時,*左的*排序是否與*右側*相同。

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a>運算子&lt;(對)(STL/CLR)

對小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左對。

*對*<br/>
要比較的右對。

### <a name="remarks"></a>備註

運算子函數`left.first <``right.first || !(right.first <``left.first &&``left.second <`傳回`right.second`。 使用它來測試當按元素比較兩對時,*左是否*按*右前*排列。

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a>運算子&lt;= (對) (STL/CLR)

對小於或相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左對。

*對*<br/>
要比較的右對。

### <a name="remarks"></a>備註

運算子函數傳回`!(right < left)`。 使用它來測試在按元素比較兩對時,*是否*未*在右後右*排序。

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a>運算子* (對) (STL/CLR)

對相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左對。

*對*<br/>
要比較的右對。

### <a name="remarks"></a>備註

運算`left.first ==``right.first &&``left.second ==`子`right.second`函數傳回 。 使用它來測試當按元素比較兩對時,*左的*排序是否與*右側*相同。

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a>運算子&gt;(對)(STL/CLR)

對大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左對。

*對*<br/>
要比較的右對。

### <a name="remarks"></a>備註

運算子函數傳回`right``<``left`。 使用它來測試在按元素比較兩對時 *,左是否*按*右*順序排列。

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a>運算子&gt;= (對) (STL/CLR)

大於或等於比較的對。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左對。

*對*<br/>
要比較的右對。

### <a name="remarks"></a>備註

運算子函數傳回`!(left < right)`。 使用它來測試在按元素比較兩*對之前是否*未對*左側*進行排序。

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
