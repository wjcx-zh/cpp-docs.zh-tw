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
ms.openlocfilehash: 271bc01f5c8fd9dd07bfa03035ae3d0204ebd8e7
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500587"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

包含 STL/CLR 標頭 `<cliext/utility>` 來定義範本類別 `pair` 以及數個支援的範本函數。

## <a name="syntax"></a>Syntax

```cpp
#include <utility>
```

## <a name="requirements"></a>需求

**標頭：**\<cliext/utility>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類別|描述|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|包裝成對的元素。|

|運算子|描述|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|配對相等比較。|
|[operator！ = (配對)  (STL/CLR) ](#op_neq)|配對不等於比較。|
|[運算子< (組)  (STL/CLR) ](#op_lt)|配對小於比較。|
|[operator \< = (對)  (STL/CLR) ](#op_lteq)|配對小於或等於比較。|
|[運算子> (組)  (STL/CLR) ](#op_gt)|配對大於比較。|
|[operator>= (組)  (STL/CLR) ](#op_gteq)|配對大於或等於比較。|

|函式|描述|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|從一對值進行配對。|

## <a name="members"></a>成員

## <a name="pair-stlclr"></a><a name="pair"></a> (STL/CLR) 的配對

此範本類別描述包裝一組值的物件。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>參數

*Value1*<br/>
第一個包裝值的型別。

*Value2*<br/>
第二個包裝值的型別。

## <a name="members"></a>成員

|類型定義|描述|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|第一個包裝值的型別。|
|[pair::second_type (STL/CLR)](#second_type)|第二個包裝值的型別。|

|Member 物件|描述|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|第一個儲存的值。|
|[pair::second (STL/CLR)](#second)|第二個儲存的值。|

|成員函式|描述|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|建立成對的物件。|
|[pair::swap (STL/CLR)](#swap)|交換兩組的內容。|

|運算子|描述|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|取代預存值的配對。|

## <a name="remarks"></a>備註

物件會儲存一組值。 您可以使用此範本類別將兩個值合併成單一物件。 此外， `cliext::pair` 此處所述的物件 () 只會儲存 managed 類型; 若要儲存一組非受控型別 `std::pair` ，請使用在中宣告的類型 `<utility>` 。

## <a name="pairfirst-stlclr"></a><a name="first"></a> 配對：： first (STL/CLR) 

第一個包裝的值。

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

## <a name="pairfirst_type-stlclr"></a><a name="first_type"></a> 配對：： first_type (STL/CLR) 

第一個包裝值的型別。

### <a name="syntax"></a>語法

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *Value1*同義。

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

## <a name="pairoperator-stlclr"></a><a name="op_as"></a> 配對：： operator = (STL/CLR) 

取代預存值的配對。

### <a name="syntax"></a>語法

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的配對。

### <a name="remarks"></a>備註

成員運算子會將 *右移* 至物件，然後傳回 **`*this`** 。 您可以使用它來取代預存值的配對，並在 *右邊*儲存一組值的複本。

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

## <a name="pairpair-stlclr"></a><a name="pair_pair"></a> 配對：:p air (STL/CLR) 

建立成對的物件。

### <a name="syntax"></a>語法

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>參數

*對*<br/>
要儲存的配對。

*val1*<br/>
要儲存的第一個值。

*val2*<br/>
要儲存的第二個值。

### <a name="remarks"></a>備註

函數：

`pair();`

使用預設的結構值，初始化預存的配對。

函數：

`pair(pair<Value1, Value2>% right);`

使用 `right.` [對：： FIRST (STL/clr) ](#first)和組 `right.` [：： second (stl/clr) ](#second)，初始化預存的配對。

`pair(pair<Value1, Value2>^ right);`

使用 `right->` [對：： FIRST (STL/clr) ](#first)和組 `right>` [：： second (stl/clr) ](#second)，初始化預存的配對。

函數：

`pair(Value1 val1, Value2 val2);`

使用 *val1* 和 *val2*，初始化預存配對。

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

## <a name="pairsecond-stlclr"></a><a name="second"></a> 成對：： second (STL/CLR) 

第二個包裝值。

### <a name="syntax"></a>語法

```cpp
Value2 second;
```

### <a name="remarks"></a>備註

物件會儲存第二個包裝值。

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

## <a name="pairsecond_type-stlclr"></a><a name="second_type"></a> 配對：： second_type (STL/CLR) 

第二個包裝值的型別。

### <a name="syntax"></a>語法

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 *Value2*的同義字。

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

## <a name="pairswap-stlclr"></a><a name="swap"></a> 配對：： swap (STL/CLR) 

交換兩組的內容。

### <a name="syntax"></a>語法

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
與交換內容的配對。

### <a name="remarks"></a>備註

成員函式會將預存值的成對值 **`*this`** 與 *右*值交換。

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

## <a name="make_pair-stlclr"></a><a name="make_pair"></a> make_pair (STL/CLR) 

`pair`從一對值進行。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>參數

*Value1*<br/>
第一個包裝值的型別。

*Value2*<br/>
第二個包裝值的型別。

*first*<br/>
要換行的第一個值。

*second*<br/>
要換行的第二個值。

### <a name="remarks"></a>備註

此範本函式會傳回 `pair<Value1, Value2>(first, second)`。 您可以使用它來 `pair<Value1, Value2>` 從一對值中建立物件。

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

## <a name="operator-pair-stlclr"></a><a name="op_neq"></a> operator！ = (配對)  (STL/CLR) 

配對不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左配對。

*對*<br/>
要比較的右側配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left == right)` 。 您可以使用它來測試當兩個配對是依元素進行比較時， *左邊* 是否未以 *正確* 的順序排序。

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lt"></a> 運算子 &lt; (配對)  (STL/CLR) 

配對小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左配對。

*對*<br/>
要比較的右側配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second` 。 您可以使用它來測試 *是否要* 在兩個配對是依專案進行比較時，于 *右邊* 排序。

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

## <a name="operatorlt-pair-stlclr"></a><a name="op_lteq"></a> operator &lt; = (對)  (STL/CLR) 

配對小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左配對。

*對*<br/>
要比較的右側配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(right < left)` 。 您可以使用它來測試當兩個配對是依元素進行*比較時，* 是否不會排序*left* 。

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

## <a name="operator-pair-stlclr"></a><a name="op_eq"></a> operator = = (對)  (STL/CLR) 

配對相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左配對。

*對*<br/>
要比較的右側配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `left.first ==` `right.first &&` `left.second ==` `right.second` 。 您可以使用它來測試當兩個配對是依元素進行比較時，是否將 *左* 的順序與 *右方* 相同。

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gt"></a> 運算子 &gt; (配對)  (STL/CLR) 

配對大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左配對。

*對*<br/>
要比較的右側配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `right` `<` `left` 。 您可以使用它來測試當兩個配對是依元素進行*比較時，* 是否要將*左方*排序。

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

## <a name="operatorgt-pair-stlclr"></a><a name="op_gteq"></a> operator &gt; = (對)  (STL/CLR) 

配對大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左配對。

*對*<br/>
要比較的右側配對。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left < right)` 。 您可以使用它來*測試當兩*個配對是依專案進行比較時，是否要將*左方*排序。

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
