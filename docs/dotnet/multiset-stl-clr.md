---
title: multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multiset
- cliext::multiset::begin
- cliext::multiset::clear
- cliext::multiset::const_iterator
- cliext::multiset::const_reference
- cliext::multiset::const_reverse_iterator
- cliext::multiset::count
- cliext::multiset::difference_type
- cliext::multiset::empty
- cliext::multiset::end
- cliext::multiset::equal_range
- cliext::multiset::erase
- cliext::multiset::find
- cliext::multiset::generic_container
- cliext::multiset::generic_iterator
- cliext::multiset::generic_reverse_iterator
- cliext::multiset::generic_value
- cliext::multiset::insert
- cliext::multiset::iterator
- cliext::multiset::key_comp
- cliext::multiset::key_compare
- cliext::multiset::key_type
- cliext::multiset::lower_bound
- cliext::multiset::make_value
- cliext::multiset::multiset
- cliext::multiset::operator=
- cliext::multiset::rbegin
- cliext::multiset::reference
- cliext::multiset::rend
- cliext::multiset::reverse_iterator
- cliext::multiset::size
- cliext::multiset::size_type
- cliext::multiset::swap
- cliext::multiset::to_array
- cliext::multiset::upper_bound
- cliext::multiset::value_comp
- cliext::multiset::value_compare
- cliext::multiset::value_type
- cliext::multiset::operator!=
- cliext::multiset::operator<
- cliext::multiset::operator<=
- cliext::multiset::operator==
- cliext::multiset::operator>
- cliext::multiset::operator>=
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
ms.openlocfilehash: 4907665c25f65affab0fc2c0bbd37f70d6a3c352
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211039"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)

此樣板類別所描述的物件可控制具有雙向存取之元素的變動長度序列。 您可以使用容器 `multiset` 來管理一連串的專案，當做節點的（幾乎）平衡的已排序樹狀結構，每個專案都儲存一個元素。

在下面的描述中，與相同 `GValue` `GKey` ，除非後者是 ref 型別（在*Key*此情況下為） `Key^` 。

## <a name="syntax"></a>語法

```cpp
template<typename Key>
    ref class multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>參數

*索引鍵*<br/>
受控制序列中項目的主要元件型別。

## <a name="requirements"></a>需求

**標頭：**\<cliext/set>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|說明|
|---------------------|-----------------|
|[multiset::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[multiset::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[multiset::difference_type (STL/CLR)](#difference_type)|兩個元素之間的（可能已簽署）距離的類型。|
|[multiset::generic_container (STL/CLR)](#generic_container)|容器的泛型介面類別型。|
|[multiset::generic_iterator (STL/CLR)](#generic_iterator)|容器之泛型介面的反覆運算器類型。|
|[multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面之反向反覆運算器的類型。|
|[multiset::generic_value (STL/CLR)](#generic_value)|容器之泛型介面的元素類型。|
|[multiset::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[multiset::key_compare (STL/CLR)](#key_compare)|兩個索引鍵的排序委派。|
|[multiset::key_type (STL/CLR)](#key_type)|排序索引鍵的類型。|
|[multiset::reference (STL/CLR)](#reference)|項目的參考類型。|
|[multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[multiset::size_type (STL/CLR)](#size_type)|兩個元素之間的（非負）距離類型。|
|[multiset::value_compare (STL/CLR)](#value_compare)|兩個元素值的排序委派。|
|[multiset::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|說明|
|---------------------|-----------------|
|[multiset::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[multiset::clear (STL/CLR)](#clear)|移除所有項目。|
|[multiset::count (STL/CLR)](#count)|計算符合指定索引鍵的元素。|
|[multiset::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[multiset::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[multiset::equal_range (STL/CLR)](#equal_range)|尋找符合指定之索引鍵的範圍。|
|[multiset::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|
|[multiset::find (STL/CLR)](#find)|尋找符合指定之索引鍵的元素。|
|[multiset::insert (STL/CLR)](#insert)|加入項目。|
|[multiset::key_comp (STL/CLR)](#key_comp)|複製兩個索引鍵的排序委派。|
|[multiset::lower_bound (STL/CLR)](#lower_bound)|尋找符合指定之索引鍵的範圍開頭。|
|[multiset::make_value (STL/CLR)](#make_value)|構造值物件。|
|[multiset::multiset (STL/CLR)](#multiset)|建構容器物件。|
|[multiset::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[multiset::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[multiset::size (STL/CLR)](#size)|計算元素的數目。|
|[multiset::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[multiset::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|
|[multiset::upper_bound (STL/CLR)](#upper_bound)|尋找符合指定之索引鍵的結束範圍。|
|[multiset::value_comp (STL/CLR)](#value_comp)|複製兩個元素值的順序委派。|

|運算子|說明|
|--------------|-----------------|
|[multiset::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[operator！ = （多重集）（STL/CLR）](#op_neq)|判斷物件是否 `multiset` 不等於另一個 `multiset` 物件。|
|[運算子< （多重集）（STL/CLR）](#op_lt)|判斷 `multiset` 物件是否小於另一個 `multiset` 物件。|
|[operator<= （多重集）（STL/CLR）](#op_lteq)|判斷 `multiset` 物件是否小於或等於另一個 `multiset` 物件。|
|[operator = = （多重集）（STL/CLR）](#op_eq)|判斷 `multiset` 物件是否等於另一個 `multiset` 物件。|
|[operator> (multiset) (STL/CLR)](#op_gt)|判斷 `multiset` 物件是否大於另一個 `multiset` 物件。|
|[operator>= （多重集）（STL/CLR）](#op_gteq)|判斷 `multiset` 物件是否大於或等於另一個 `multiset` 物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|透過元素進行序列。|
|<xref:System.Collections.ICollection>|維護元素群組。|
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的專案進行序列。|
|<xref:System.Collections.Generic.ICollection%601>|維護具類型的元素群組。|
|ITree\<Key, Value>|維護一般容器。|

## <a name="remarks"></a>備註

物件會為其所控制的序列配置並釋出儲存體，以作為個別節點。 它會將專案插入（幾乎）平衡的樹狀結構中，藉由改變節點間的連結來保持排序，而不是將某個節點的內容複寫到另一個節點。 這表示您可以自由地插入和移除專案，而不會干擾其餘元素。

物件會藉由呼叫類型為[多重集：： key_compare （STL/CLR）](../dotnet/multiset-key-compare-stl-clr.md)的預存委派物件，來排序它所控制的序列。 當您建立多重集時，可以指定預存的委派物件;如果您沒有指定委派物件，預設值就是比較 `operator<(key_type, key_type)` 。 您可以藉由呼叫成員函式[多重集：： key_comp （STL/CLR）](../dotnet/multiset-key-comp-stl-clr.md)來存取這個儲存的物件 `()` 。

這類委派物件必須對[多重集：： key_type （STL/CLR）](../dotnet/multiset-key-type-stl-clr.md)類型的索引鍵強制執行嚴格弱式排序。 這表示，對於任何兩個索引鍵 `X` 和 `Y` ：

`key_comp()(X, Y)`會在每次呼叫時傳回相同的布林值結果。

如果 `key_comp()(X, Y)` 為 true，則 `key_comp()(Y, X)` 必須為 false。

如果 `key_comp()(X, Y)` 為 true，則 `X` 表示在之前排序過 `Y` 。

如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 為 true，則 `X` 和 `Y` 會被視為具有對等的順序。

針對位於 `X` `Y` 受控制序列中的任何專案， `key_comp()(Y, X)` 為 false。 （對於預設委派物件，索引鍵永遠不會減少值）。不同于樣板類別[集（STL/CLR）](../dotnet/set-stl-clr.md)，樣板類別的物件 `multiset` 不需要所有元素的索引鍵都是唯一的。 （兩個或多個索引鍵可以具有對等的順序）。

每個元素都會同時做為安永和值。 序列的表示方式，允許查閱、插入和移除具有數個作業的任意專案，並與序列中專案數的對數成正比（對數時間）。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。

多重集支援雙向反覆運算器，這表示您可以逐步執行連續的專案，方法是指定以受控制序列中的元素。 特殊的前端節點對應至[多重集：： end （STL/CLR）](../dotnet/multiset-end-stl-clr.md)傳回的反覆運算器 `()` 。 您可以遞減這個反覆運算器，使其到達受控制序列中的最後一個元素（如果有的話）。 您可以遞增多重集反覆運算器，使其到達前端節點，然後再比較是否等於 `end()` 。 但是，您無法對所傳回的反覆運算器進行取值 `end()` 。

請注意，您無法直接參考多重集元素的數值位置（需要隨機存取反覆運算器）。

多重集反覆運算器會儲存其相關聯集節點的控制碼，然後再將控制碼儲存至其相關聯的容器。 您只能將反覆運算器與相關聯的容器物件搭配使用。 多重集反覆運算器會保持有效，只要其相關聯的多重集節點與某些多重集相關聯即可。 此外，有效的反覆運算器也是 dereferencable--您可以使用它來存取或更改其指定的元素值，只要它不等於即可 `end()` 。

清除或移除元素會呼叫其預存值的析構函式。 終結容器會清除所有元素。 因此，其元素類型為 ref 類別的容器，可確保沒有任何元素 outlive 容器。 不過要注意的是，控制碼容器並*不*會摧毀其元素。

## <a name="members"></a>成員

## <a name="multisetbegin-stlclr"></a><a name="begin"></a>多重集：： begin （STL/CLR）

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

此成員函式會傳回雙向反覆運算器，指定受控制序列的第一個元素，或在空序列結尾以外的專案。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_multiset_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="multisetclear-stlclr"></a><a name="clear"></a>多重集：： clear （STL/CLR）

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

此成員函式會有效地呼叫[多重集：： erase （stl/clr）](../dotnet/multiset-erase-stl-clr.md) `(` [多重集：： begin （stl/clr）](../dotnet/multiset-begin-stl-clr.md) `(),` [多重集：： end （stl/clr）](../dotnet/multiset-end-stl-clr.md) `())` 。 您可以使用它來確保受控制的序列是空的。

### <a name="example"></a>範例

```cpp
// cliext_multiset_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="multisetconst_iterator-stlclr"></a><a name="const_iterator"></a>多重集：： const_iterator （STL/CLR）

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型的物件 `T2` ，可做為受控制序列的常數雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reference-stlclr"></a><a name="const_reference"></a>多重集：： const_reference （STL/CLR）

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

此類型描述專案的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>多重集：： const_reverse_iterator （STL/CLR）

受控制序列的常數反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型的物件 `T4` ，可做為受控制序列的常數反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetcount-stlclr"></a><a name="count"></a>多重集：： count （STL/CLR）

尋找符合指定索引鍵的項目數目。

### <a name="syntax"></a>語法

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

此成員函式會傳回受控制序列中具有對等順序與索引*鍵*的元素數目。 您會用它來判斷目前在受控制序列中，符合指定之索引鍵的項目數目。

### <a name="example"></a>範例

```cpp
// cliext_multiset_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="multisetdifference_type-stlclr"></a><a name="difference_type"></a>多重集：:d ifference_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能為負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::difference_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultiset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="multisetempty-stlclr"></a><a name="empty"></a>多重集：： empty （STL/CLR）

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[多重集：： size （STL/CLR）](../dotnet/multiset-size-stl-clr.md) `() == 0` 。 您可以使用它來測試多重集是否為空的。

### <a name="example"></a>範例

```cpp
// cliext_multiset_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="multisetend-stlclr"></a><a name="end"></a>多重集：： end （STL/CLR）

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

此成員函式會傳回指向受控制序列結尾之外的雙向反覆運算器。 您可以使用它來取得反覆運算器，以指定受控制序列的結尾;如果受控制序列的長度變更，其狀態不會變更。

### <a name="example"></a>範例

```cpp
// cliext_multiset_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Mymultiset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="multisetequal_range-stlclr"></a><a name="equal_range"></a>多重集：： equal_range （STL/CLR）

尋找符合指定之索引鍵的範圍。

### <a name="syntax"></a>語法

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

此成員函式會傳回一對反覆運算器 `cliext::pair<iterator, iterator>(` [多重集：： lower_bound （stl/clr）](../dotnet/multiset-lower-bound-stl-clr.md) `(key),` [多重集：： upper_bound （stl/clr）](../dotnet/multiset-upper-bound-stl-clr.md) `(key))` 。 您可以使用它來判斷目前在受控制序列中符合指定索引鍵的元素範圍。

### <a name="example"></a>範例

```cpp
// cliext_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
typedef Mymultiset::pair_iter_iter Pairii;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="multiseterase-stlclr"></a><a name="erase"></a>多重集：： erase （STL/CLR）

移除位於指定位置的項目。

### <a name="syntax"></a>語法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>參數

*first*<br/>
要清除之範圍的開頭。

*key*<br/>
要清除的機碼值。

*last*<br/>
要清除的範圍結尾。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>備註

第一個成員函式會移除所指向之受控制序列的*專案，並*傳回反覆運算器，指定移除的專案之後剩餘的第一個元素，或如果沒有這類元素，則傳回[多重集：： end （STL/CLR）](../dotnet/multiset-end-stl-clr.md) `()` 。 您可以使用它來移除單一元素。

第二個成員函式會移除範圍 [，）中受控制序列的專案 `first` `last` ，並傳回反覆運算器，指定移除任何元素之後剩餘的第一個元素，或 `end()` 如果沒有這類元素存在，則為。 您可以使用它來移除零個或多個連續元素。

第三個成員函式會移除受控制序列中的任何專案，其索引鍵對索引鍵具有對等的*順序，並*傳回已移除的元素數計數。 您可以使用它來移除和計算符合指定索引鍵的所有元素。

每個專案抹除的時間會與受控制序列中專案數的對數成正比。

### <a name="example"></a>範例

```cpp
// cliext_multiset_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Mymultiset::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="multisetfind-stlclr"></a><a name="find"></a>多重集：： find （STL/CLR）

尋找符合指定之索引鍵的元素。

### <a name="syntax"></a>語法

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

如果受控制序列中至少有一個專案具有對*等的順序，則*成員函式會傳回指定其中一個元素的反覆運算器;否則，它會傳回[多重集：： end （STL/CLR）](../dotnet/multiset-end-stl-clr.md) `()` 。 您可以使用它來找出目前在受控制序列中且符合指定索引鍵的元素。

### <a name="example"></a>範例

```cpp
// cliext_multiset_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="multisetgeneric_container-stlclr"></a><a name="generic_container"></a>多重集：： generic_container （STL/CLR）

容器的泛型介面類別型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>多重集：： generic_iterator （STL/CLR）

用於容器之泛型介面的反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>備註

此類型描述的泛型反覆運算器可與此樣板容器類別的泛型介面搭配使用。

### <a name="example"></a>範例

```cpp
// cliext_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>多重集：： generic_reverse_iterator （STL/CLR）

要與容器的泛型介面搭配使用的反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述的泛型反向反覆運算器可與此樣板容器類別的泛型介面搭配使用。

### <a name="example"></a>範例

```cpp
// cliext_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="multisetgeneric_value-stlclr"></a><a name="generic_value"></a>多重集：： generic_value （STL/CLR）

要與容器的泛型介面搭配使用之元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

此類型描述類型的物件 `GValue` ，其描述要與這個樣板容器類別的泛型介面搭配使用的預存元素值。

### <a name="example"></a>範例

```cpp
// cliext_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="multisetinsert-stlclr"></a><a name="insert"></a>多重集：： insert （STL/CLR）

加入項目。

### <a name="syntax"></a>語法

```cpp
iterator insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>參數

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*再*<br/>
要插入的列舉。

*初始值*<br/>
要插入的機碼值。

*where*<br/>
在容器中要插入的位置（僅提示）。

### <a name="remarks"></a>備註

每個成員函式都會插入由其餘運算元所指定的序列。

第一個成員函式會插入具有值*val*的元素，並傳回反覆運算器，指定新插入的專案。 您可以使用它來插入單一元素。

第二個成員函式會插入具有值*val*的元素，並使用*where*做為提示（以改善效能），並傳回反覆運算器，指定新插入的專案。 您可以使用它來插入單一專案，這可能會與您知道的元素相鄰。

第三個成員函式會插入序列 [ `first` ， `last` ）。 您可以使用它來插入從另一個序列複製的零個或多個元素。

第四個成員函式會插入*右邊*指定的序列。 您可以使用它來插入列舉值所描述的序列。

每個專案插入所花的時間，會與受控制序列中專案數的對數成正比。 不過，若指定的提示會指定插入點旁邊的元素，則插入可能會在分攤的常數時間內發生。

### <a name="example"></a>範例

```cpp
// cliext_multiset_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Mymultiset c2;
    Mymultiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultiset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="multisetiterator-stlclr"></a><a name="iterator"></a>多重集：： iterator （STL/CLR）

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型的物件 `T1` ，可做為受控制序列的雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_multiset_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetkey_comp-stlclr"></a><a name="key_comp"></a>多重集：： key_comp （STL/CLR）

複製兩個索引鍵的排序委派。

### <a name="syntax"></a>語法

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>備註

此成員函式會傳回用來排序受控制序列的排序委派。 您會用它來比較兩個索引鍵。

### <a name="example"></a>範例

```cpp
// cliext_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multisetkey_compare-stlclr"></a><a name="key_compare"></a>多重集：： key_compare （STL/CLR）

兩個索引鍵的排序委派。

### <a name="syntax"></a>語法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>備註

此類型是委派的同義字，可決定其索引鍵引數的順序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multisetkey_type-stlclr"></a><a name="key_type"></a>多重集：： key_type （STL/CLR）

排序索引鍵的類型。

### <a name="syntax"></a>語法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數索引*鍵*的同義字。

### <a name="example"></a>範例

```cpp
// cliext_multiset_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetlower_bound-stlclr"></a><a name="lower_bound"></a>多重集：： lower_bound （STL/CLR）

尋找符合指定之索引鍵的範圍開頭。

### <a name="syntax"></a>語法

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式 `X` 會判斷受控制序列中具有對索引*鍵*之對等順序的第一個元素。 如果沒有這類元素存在，則會傳回[多重集：： end （STL/CLR）](../dotnet/multiset-end-stl-clr.md)， `()` 否則會傳回指定的反覆運算器 `X` 。 您可以使用它來尋找目前在受控制序列中符合指定索引鍵之專案序列的開頭。

### <a name="example"></a>範例

```cpp
// cliext_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="multisetmake_value-stlclr"></a><a name="make_value"></a>多重集：： make_value （STL/CLR）

構造值物件。

### <a name="syntax"></a>語法

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要使用的索引鍵值。

### <a name="remarks"></a>備註

此成員函式 `value_type` 會傳回其索引鍵為*key*的物件。 您可以使用它來撰寫適合搭配數個其他成員函式使用的物件。

### <a name="example"></a>範例

```cpp
// cliext_multiset_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(Mymultiset::make_value(L'a'));
    c1.insert(Mymultiset::make_value(L'b'));
    c1.insert(Mymultiset::make_value(L'c'));

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetmultiset-stlclr"></a><a name="multiset"></a>多重集：：多重集（STL/CLR）

建構容器物件。

### <a name="syntax"></a>語法

```cpp
multiset();
explicit multiset(key_compare^ pred);
multiset(multiset<Key>% right);
multiset(multiset<Key>^ right);
template<typename InIter>
    multisetmultiset(InIter first, InIter last);
template<typename InIter>
    multiset(InIter first, InIter last,
        key_compare^ pred);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>參數

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*pred*<br/>
受控制序列的順序述詞。

*再*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

此構造函式：

`multiset();`

使用預設排序述詞，初始化沒有任何專案的受控制序列 `key_compare()` 。 您可以使用它來指定空的初始受控制序列，並使用預設的順序述詞。

此構造函式：

`explicit multiset(key_compare^ pred);`

使用順序述詞*pred*，初始化不含任何專案的受控制序列。 您可以使用它來指定空的初始受控制序列，並指定順序述詞。

此構造函式：

`multiset(multiset<Key>% right);`

使用順序 [，）初始化受控制的序列 `right.begin()` `right.end()` ，並搭配預設的排序述詞。 您可以使用它來指定初始受控制序列，這是由多重集物件*許可權*所控制之序列的複本，並具有預設排序述詞。

此構造函式：

`multiset(multiset<Key>^ right);`

使用順序 [，）初始化受控制的序列 `right->begin()` `right->end()` ，並搭配預設的排序述詞。 您可以使用它來指定初始受控制序列，這是由多重集物件*許可權*所控制之序列的複本，並具有預設排序述詞。

此構造函式：

`template<typename InIter> multiset(InIter first, InIter last);`

使用順序 [，）初始化受控制的序列 `first` `last` ，並搭配預設的排序述詞。 您可以使用它，讓受控制的序列成為另一個序列的複本，並使用預設的順序述詞。

此構造函式：

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

使用順序述詞 pred，初始化具有序列 [，）的受控制序列 `first` `last` 。 *pred* 您可以使用它，讓受控制的序列成為另一個序列的複本，並指定順序述詞。

此構造函式：

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

使用預設排序述詞，以枚舉器*右邊*指定的順序，初始化受控制的序列。 您可以使用它，讓受控制的序列成為枚舉器所描述之另一個序列的複本，並使用預設的排序述詞。

此構造函式：

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

使用排序述詞*pred*，以列舉值*右邊*所指定的順序，初始化受控制的序列。 您可以使用它，透過指定的排序述詞，讓受控制的序列成為枚舉器所描述之另一個序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_multiset_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
// construct an empty container
    Mymultiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mymultiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultiset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="multisetoperator-stlclr"></a><a name="op_as"></a>多重集：： operator = （STL/CLR）

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子會將*許可權*複製到物件，然後傳回 **`*this`** 。 您可以使用它，將受控制序列取代為*右邊*的受控制序列複本。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Mymultiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="multisetrbegin-stlclr"></a><a name="rbegin"></a>多重集：： rbegin （STL/CLR）

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

此成員函式會傳回反向反覆運算器，指定受控制序列的最後一個元素，或只在空白序列開頭以外的專案。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultiset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="multisetreference-stlclr"></a><a name="reference"></a>多重集：： reference （STL/CLR）

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述專案的參考。

### <a name="example"></a>範例

```cpp
// cliext_multiset_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multisetrend-stlclr"></a><a name="rend"></a>多重集：： rend （STL/CLR）

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

此成員函式會傳回指向受控制序列開頭以外的反向反覆運算器。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_multiset_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>多重集：： reverse_iterator （STL/CLR）

受控制序列的反向迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// cliext_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="multisetsize-stlclr"></a><a name="size"></a>多重集：： size （STL/CLR）

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[多重集：： empty （STL/CLR）](../dotnet/multiset-empty-stl-clr.md) `()` 。

### <a name="example"></a>範例

```cpp
// cliext_multiset_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="multisetsize_type-stlclr"></a><a name="size_type"></a>多重集：： size_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_multiset_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::size_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="multisetswap-stlclr"></a><a name="swap"></a>多重集：： swap （STL/CLR）

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*再*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函式會在和 right 之間交換受控制的序列 **`this`** 。 *right* 它會以常數時間執行，而且不會擲回任何例外狀況。 您可以用它來快速交換兩個容器的內容。

### <a name="example"></a>範例

```cpp
// cliext_multiset_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultiset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
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
d e f
d e f
a b c
```

## <a name="multisetto_array-stlclr"></a><a name="to_array"></a>多重集：： to_array （STL/CLR）

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>備註

此成員函式會傳回陣列，其中包含受控制的序列。 您可以用它來取得陣列表單中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_multiset_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="multisetupper_bound-stlclr"></a><a name="upper_bound"></a>多重集：： upper_bound （STL/CLR）

尋找符合指定之索引鍵的結束範圍。

### <a name="syntax"></a>語法

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式 `X` 會判斷受控制序列中，具有對索引*鍵*之對等順序的最後一個元素。 如果沒有這類元素存在，或如果 `X` 是受控制序列中的最後一個專案，則會傳回[多重集：： END （STL/CLR）](../dotnet/multiset-end-stl-clr.md)， `()` 否則會傳回反覆運算器，指定超出的第一個元素 `X` 。 您可以使用它來找出目前在受控制序列中符合指定索引鍵之專案序列的結尾。

### <a name="example"></a>範例

```cpp
// cliext_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="multisetvalue_comp-stlclr"></a><a name="value_comp"></a>多重集：： value_comp （STL/CLR）

複製兩個元素值的順序委派。

### <a name="syntax"></a>語法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>備註

此成員函式會傳回用來排序受控制序列的排序委派。 您可以使用它來比較兩個元素的值。

### <a name="example"></a>範例

```cpp
// cliext_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="multisetvalue_compare-stlclr"></a><a name="value_compare"></a>多重集：： value_compare （STL/CLR）

兩個元素值的排序委派。

### <a name="syntax"></a>語法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>備註

此類型是委派的同義字，可決定其值引數的順序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="multisetvalue_type-stlclr"></a><a name="value_type"></a>多重集：： value_type （STL/CLR）

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>備註

這個類型與 `generic_value`同義。

### <a name="example"></a>範例

```cpp
// cliext_multiset_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-multiset-stlclr"></a><a name="op_neq"></a>operator！ = （多重集）（STL/CLR）

清單不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `!(left == right)` 。 您可以使用它來測試當兩個多重集是以元素進行比較時，是否要將*left*與*right*排序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lt"></a>運算子 &lt; （多重集）（STL/CLR）

清單小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

如果的最低位置也為 true，則運算子函數 `i` 會傳回 true `!(right[i] < left[i])` `left[i] < right[i]` 。 否則，它會傳回 `left->size() < right->size()` 您用它來測試當兩個多重*right*集是以元素進行比較時，*左側*是否已排序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lteq"></a>operator &lt; = （多重集）（STL/CLR）

列出小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `!(right < left)` 。 您可以使用它來測試當兩個多重集是以元素進行比較時，*左側*是否不是靠*右*排序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-multiset-stlclr"></a><a name="op_eq"></a>operator = = （多重集）（STL/CLR）

列出相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

只有當*left*和*right*所控制的序列具有相同的長度，且每個位置都有相同的時，運算子函數才會傳回 true `i` `left[i] ==` `right[i]` 。 您可以使用它來測試當兩個多重集是以元素進行比較時，是否要將*left*排序為*正確*。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gt"></a>運算子 &gt; （多重集）（STL/CLR）

清單大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `right` `<` `left` 。 您可以使用它來測試當兩個多重集是依照元素進行比較時，是否要*向**右*排序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gteq"></a>operator &gt; = （多重集）（STL/CLR）

列出大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*左面*<br/>
要比較的左容器。

*再*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函式會傳回 `!(left < right)` 。 您可以使用它來測試當兩個多重集是以元素進行比較時，*左側*是否未按*右*排序。

### <a name="example"></a>範例

```cpp
// cliext_multiset_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
