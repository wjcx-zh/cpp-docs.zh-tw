---
title: list (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: 6c8fdab696960b0f3bfbe26ab91b1e1493204e9b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446253"
---
# <a name="list-stlclr"></a>list (STL/CLR)

此樣板類別所描述的物件可控制具有雙向存取之元素的變動長度序列。 您可以使用容器 `list` 來管理一連串的專案，作為雙向連結的節點清單，每個專案都儲存一個元素。

在下面的描述中，`GValue` 與*值*相同，除非後者是 ref 類型，在此情況下會 `Value^`。

## <a name="syntax"></a>語法

```cpp
template<typename Value>
    ref class list
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        Microsoft::VisualC::StlClr::IList<GValue>
    { ..... };
```

### <a name="parameters"></a>參數

*ReplTest1*<br/>
受控制序列中項目的類型。

## <a name="requirements"></a>需求

**標頭：** \<cliext/list >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[list::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[list::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[list::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[list::generic_container (STL/CLR)](#generic_container)|容器的泛型介面類別型。|
|[list::generic_iterator (STL/CLR)](#generic_iterator)|容器之泛型介面的反覆運算器類型。|
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面之反向反覆運算器的類型。|
|[list::generic_value (STL/CLR)](#generic_value)|容器之泛型介面的元素類型。|
|[list::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[list::reference (STL/CLR)](#reference)|項目的參考類型。|
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[list::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[list::value_type (STL/CLR)](#value_type)|元素類型。|

|成員函式|描述|
|---------------------|-----------------|
|[list::assign (STL/CLR)](#assign)|取代所有項目。|
|[list::back (STL/CLR)](#back)|存取最後一個項目。|
|[list::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[list::clear (STL/CLR)](#clear)|移除所有項目。|
|[list::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[list::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[list::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|
|[list::front (STL/CLR)](#front)|存取第一個項目。|
|[list::insert (STL/CLR)](#insert)|在指定的位置加入專案。|
|[list::list (STL/CLR)](#list)|建構容器物件。|
|[list::merge (STL/CLR)](#merge)|合併兩個已排序的受控制序列。|
|[list::pop_back (STL/CLR)](#pop_back)|移除最後一個元素。|
|[list::pop_front (STL/CLR)](#pop_front)|移除第一個元素。|
|[list::push_back (STL/CLR)](#push_back)|加入新的最後一個元素。|
|[list::push_front (STL/CLR)](#push_front)|加入新的第一個元素。|
|[list::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[list::remove (STL/CLR)](#remove)|移除具有指定值的元素。|
|[list::remove_if (STL/CLR)](#remove_if)|移除通過指定測試的元素。|
|[list::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[list::resize (STL/CLR)](#resize)|變更項目的數目。|
|[list::reverse (STL/CLR)](#reverse)|反轉受控制的序列。|
|[list::size (STL/CLR)](#size)|計算元素的數目。|
|[list::sort (STL/CLR)](#sort)|排序受控制序列。|
|[list::splice (STL/CLR)](#splice)|重新拼接節點之間的連結。|
|[list::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[list::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|
|[list::unique (STL/CLR)](#unique)|移除通過指定測試的相鄰項目。|

|屬性|描述|
|--------------|-----------------|
|[list::back_item (STL/CLR)](#back_item)|存取最後一個項目。|
|[list::front_item (STL/CLR)](#front_item)|存取第一個項目。|

|運算子|描述|
|--------------|-----------------|
|[list::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[operator!= (list) (STL/CLR)](#op_neq)|判斷 `list` 物件是否不等於另一個 `list` 物件。|
|[operator< (list) (STL/CLR)](#op_lt)|判斷 `list` 物件是否小於另一個 `list` 物件。|
|[operator<= (list) (STL/CLR)](#op_lteq)|判斷 `list` 物件是否小於或等於另一個 `list` 物件。|
|[operator== (list) (STL/CLR)](#op_eq)|判斷 `list` 物件是否等於另一個 `list` 物件。|
|[operator> (list) (STL/CLR)](#op_gt)|判斷 `list` 物件是否大於另一個 `list` 物件。|
|[operator>= (list) (STL/CLR)](#op_gteq)|判斷 `list` 物件是否大於或等於另一個 `list` 物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|透過元素進行序列。|
|<xref:System.Collections.ICollection>|維護元素群組。|
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的專案進行序列。|
|<xref:System.Collections.Generic.ICollection%601>|維護具類型的元素群組。|
|IList\<值 >|維護一般容器。|

## <a name="remarks"></a>備註

物件會在雙向連結清單中，為它所控制的序列配置並釋出儲存區作為個別節點。 它會改變節點間的連結來重新排列元素，而不會將一個節點的內容複寫到另一個節點。 這表示您可以自由地插入和移除專案，而不會干擾其餘元素。 因此，清單是適用于樣板類別[佇列（stl/clr）](../dotnet/queue-stl-clr.md)或樣板類別[堆疊（STL/clr）](../dotnet/stack-stl-clr.md)之基礎容器的理想候選。

`list` 物件支援雙向反覆運算器，這表示您可以逐步執行指定受控制序列中之專案的反覆運算器，以進入連續的元素。 特殊的前端節點對應至[list：： end （STL/CLR）](../dotnet/list-end-stl-clr.md)`()`所傳回的反覆運算器。 您可以遞減這個反覆運算器，使其到達受控制序列中的最後一個元素（如果有的話）。 您可以遞增清單反覆運算器來到達前端節點，然後再比較是否等於 `end()`。 但是，您無法對 `end()`所傳回的反覆運算器進行取值。

請注意，您無法直接指定其數值位置（需要隨機存取反覆運算器）的清單元素。 因此，清單*無法*當做樣板類別[priority_queue （STL/CLR）](../dotnet/priority-queue-stl-clr.md)的基礎容器使用。

清單反覆運算器會儲存其相關聯清單節點的控制碼，然後再將控制碼儲存至其相關聯的容器。 您只能將反覆運算器與相關聯的容器物件搭配使用。 清單反覆運算器會保持有效，只要其相關聯的清單節點與某個清單相關聯。 此外，有效的反覆運算器也是 dereferencable--您可以使用它來存取或更改所指定的元素值，只要它不等於 `end()`。

清除或移除元素會呼叫其預存值的析構函式。 終結容器會清除所有元素。 因此，其元素類型為 ref 類別的容器，可確保沒有任何元素 outlive 容器。 不過要注意的是，控制碼容器並*不*會摧毀其元素。

## <a name="members"></a>成員

## <a name="assign"></a>list：： assign （STL/CLR）

取代所有項目。

### <a name="syntax"></a>語法

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>參數

*計數*<br/>
要插入的元素數目。

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*right*<br/>
要插入的列舉。

*val*<br/>
要插入之元素的值。

### <a name="remarks"></a>備註

第一個成員函式會將受控制的序列取代為值*val*的*count*元素的重複。 您可以使用它來填滿具有相同值的所有專案容器。

如果 `InIt` 是整數類型，第二個成員函式的行為會與 `assign((size_type)first, (value_type)last)`相同。 否則，它會將受控制序列取代為序列 [`first`，`last`）。 您可以使用它讓受控制的序列成為另一個序列的複本。

第三個成員函式會將受控制序列取代為列舉值*右邊*所指定的序列。 您可以使用它，讓受控制的序列成為列舉值所描述之序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="back"></a>list：： back （STL/CLR）

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
reference back();
```

### <a name="remarks"></a>備註

此成員函式會傳回受控制序列之最後一個元素的參考，該專案必須為非空白。 當您知道它是否存在時，您可以使用它來存取最後一個元素。

### <a name="example"></a>範例

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

    // alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="back_item"></a>list：： back_item （STL/CLR）

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>備註

屬性會存取受控制序列中的最後一個專案，其必須為非空白。 當您知道最後一個元素存在時，就可以使用它來讀取或寫入它。

### <a name="example"></a>範例

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

    // alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="begin"></a>list：： begin （STL/CLR）

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

此成員函式會傳回隨機存取反覆運算器，指定受控制序列的第一個元素，或在空序列結尾以外的專案。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="clear"></a>list：： clear （STL/CLR）

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

此成員函式會有效地呼叫[list：： erase （stl/clr）](../dotnet/list-erase-stl-clr.md)`(` [list：： begin （stl/clr）](../dotnet/list-begin-stl-clr.md)`(),` [LIST：： end （stl/clr）](../dotnet/list-end-stl-clr.md)`())`。 您可以使用它來確保受控制的序列是空的。

### <a name="example"></a>範例

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

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

## <a name="const_iterator"></a>list：： const_iterator （STL/CLR）

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T2` 的物件，可做為受控制序列的常數隨機存取反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a>list：： const_reference （STL/CLR）

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

此類型描述專案的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a>list：： const_reverse_iterator （STL/CLR）

受控制序列的常數反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T4` 的物件，可做為受控制序列的常數反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="difference_type"></a>list：:d ifference_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述帶正負號的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a>list：： empty （STL/CLR）

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[list：： size （STL/CLR）](../dotnet/list-size-stl-clr.md)`() == 0`。 您可以使用它來測試清單是否為空的。

### <a name="example"></a>範例

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

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

## <a name="end"></a>list：： end （STL/CLR）

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

此成員函式會傳回指向受控制序列結尾之外的隨機存取反覆運算器。 您可以使用它來取得反覆運算器，以指定受控制序列的結尾;如果受控制序列的長度變更，其狀態不會變更。

### <a name="example"></a>範例

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="erase"></a>list：： erase （STL/CLR）

移除位於指定位置的項目。

### <a name="syntax"></a>語法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>參數

*first*<br/>
要清除之範圍的開頭。

*last*<br/>
要清除的範圍結尾。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>備註

第一個成員函式會移除*中*所指向之受控制序列的元素。 您可以使用它來移除單一元素。

第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 您可以使用它來移除零個或多個連續元素。

這兩個成員函式會傳回反覆運算器，指定任何移除的元素之後剩餘的第一個元素，如果沒有這類元素，則會`()` [list：： end （STL/CLR）](../dotnet/list-end-stl-clr.md) 。

清除元素時，元素複本的數目是抹除結尾和序列最接近端之間的元素數目的線性。 （清除序列任一結尾的一個或多個專案時，不會複製任何專案）。

### <a name="example"></a>範例

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="front"></a>list：： front （STL/CLR）

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
reference front();
```

### <a name="remarks"></a>備註

此成員函式會傳回受控制序列中第一個專案的參考，該專案必須為非空白。 當您知道它是否存在時，您可以使用它來讀取或寫入第一個元素。

### <a name="example"></a>範例

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

    // alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="front_item"></a>list：： front_item （STL/CLR）

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>備註

屬性會存取受控制序列的第一個元素，其必須為非空白。 當您知道它是否存在時，您可以使用它來讀取或寫入第一個元素。

### <a name="example"></a>範例

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

    // alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="generic_container"></a>list：： generic_container （STL/CLR）

容器的泛型介面類別型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
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

## <a name="generic_iterator"></a>list：： generic_iterator （STL/CLR）

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
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="generic_reverse_iterator"></a>list：： generic_reverse_iterator （STL/CLR）

要與容器的泛型介面搭配使用的反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述的泛型反向反覆運算器可與此樣板容器類別的泛型介面搭配使用。

### <a name="example"></a>範例

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="generic_value"></a>list：： generic_value （STL/CLR）

要與容器的泛型介面搭配使用之元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

此類型描述類型為 `GValue` 的物件，描述要與這個樣板容器類別的泛型介面搭配使用的預存專案值。

### <a name="example"></a>範例

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="insert"></a>list：： insert （STL/CLR）

在指定的位置加入專案。

### <a name="syntax"></a>語法

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>參數

*計數*<br/>
要插入的元素數目。

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*right*<br/>
要插入的列舉。

*val*<br/>
要插入之元素的值。

*where*<br/>
在容器中要插入的位置。

### <a name="remarks"></a>備註

每個成員函式*都會在受控制序列中的*專案（由由其餘運算元所指定的序列）之前，插入所指向的元素之前。

第一個成員函式會插入具有值*val*的元素，並傳回反覆運算器，指定新插入的專案。 您可以使用它，在反覆運算器所指定的位置之前插入單一元素。

第二個成員函式會插入 value *val*的*count*元素的重複專案。 您可以使用它來插入零個或多個連續元素，這些都是相同值的所有複本。

如果 `InIt` 是整數類型，第三個成員函式的行為即與 `insert(where, (size_type)first, (value_type)last)` 相同。 否則，它會插入序列 [`first`，`last`）。 您可以使用它來插入從另一個序列複製的零個或多個連續元素。

第四個成員函式會插入*右邊*指定的序列。 您可以使用它來插入列舉值所描述的序列。

當插入單一專案時，元素複本的數目是插入點和序列最接近端之間的元素數目的線性。 （在序列的任一端插入一或多個專案時，不會複製任何元素）。如果 `InIt` 是輸入反覆運算器，則第三個成員函式會針對序列中的每個元素，有效地執行單一插入。 否則，在插入 `N` 專案時，元素複本的數目會是線性，`N` 加上插入點和序列最接近端之間的元素數目。

### <a name="example"></a>範例

```cpp
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="iterator"></a>list：： iterator （STL/CLR）

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T1` 的物件，可做為受控制序列的隨機存取反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

    // alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="list"></a>list：： list （STL/CLR）

建構容器物件。

### <a name="syntax"></a>語法

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>參數

*計數*<br/>
要插入的元素數目。

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*right*<br/>
要插入的物件或範圍。

*val*<br/>
要插入之元素的值。

### <a name="remarks"></a>備註

此構造函式：

`list();`

以沒有專案的方式，初始化受控制的序列。 您可以使用它來指定空的初始受控制序列。

此構造函式：

`list(list<Value>% right);`

使用序列 [`right.begin()`，`right.end()`），初始化受控制的序列。 您可以使用它來指定初始受控制序列，這是清單物件*許可權*所控制之序列的複本。

此構造函式：

`list(list<Value>^ right);`

使用序列 [`right->begin()`，`right->end()`），初始化受控制的序列。 您可以使用它來指定初始受控制序列，這是由其控制碼為*右邊*的清單物件所控制的序列複本。

此構造函式：

`explicit list(size_type count);`

使用值 `value_type()`，初始化具有*count*個元素的受控制序列。 您可以使用它來填滿具有預設值之專案的容器。

此構造函式：

`list(size_type count, value_type val);`

使用具有值*val*的*count*元素，初始化受控制的序列。 您可以使用它來填滿具有相同值的所有專案容器。

此構造函式：

`template<typename InIt>`

`list(InIt first, InIt last);`

使用序列 [`first`，`last`），初始化受控制的序列。 您可以使用它，讓受控制的序列成為另一個序列的複本。

此構造函式：

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

使用列舉值*許可權*所指定的順序，初始化受控制的序列。 您可以使用它，讓受控制的序列成為列舉值所描述之另一個序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="merge"></a>list：： merge （STL/CLR）

合併兩個已排序的受控制序列。

### <a name="syntax"></a>語法

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>參數

*pred*<br/>
元素配對的比較子。

*right*<br/>
要合併的容器。

### <a name="remarks"></a>備註

第一個成員函式會從*right*所控制的序列中移除所有專案，並將其插入受控制的序列中。 這兩個序列之前都必須依 `operator<` 排序--元素在您透過任一序列進行的過程中，都不能減少值。 產生的序列也會依 `operator<`排序。 您可以使用此成員函式，將值增加的兩個序列合併為同時增加值的序列。

第二個成員函式的行為與第一個相同，不同之處在于順序是依據 `pred` -- `pred(X, Y)` 針對序列中專案 `Y` 後面的任何元素 `X`，其必須為 false。 您可以使用它來合併兩個序列，由您指定的述詞函式或委派進行排序。

這兩個函式都會執行穩定的合併--在產生的受控制序列中，任何一個原始受控制序列中的元素都不會有任何配對。 此外，如果在產生的受控制序列中 `X` 和 `Y` 的成對專案具有對等的順序--`!(X < Y) && !(X < Y)`--原始受控制序列中的元素會出現在*right*所控制序列中的專案之前。

### <a name="example"></a>範例

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="op_as"></a>list：： operator = （STL/CLR）

取代受控制的序列。

### <a name="syntax"></a>語法

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子會將*許可權*複製到物件，然後傳回 `*this`。 您可以使用它，將受控制序列取代為*右邊*的受控制序列複本。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="pop_back"></a>list：:p op_back （STL/CLR）

移除最後一個元素。

### <a name="syntax"></a>語法

```cpp
void pop_back();
```

### <a name="remarks"></a>備註

此成員函式會移除受控制序列中的最後一個專案，此專案必須為非空白。 您可以用它來將清單中的一個元素縮短一次。

### <a name="example"></a>範例

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="pop_front"></a>list：:p op_front （STL/CLR）

移除第一個元素。

### <a name="syntax"></a>語法

```cpp
void pop_front();
```

### <a name="remarks"></a>備註

此成員函式會移除受控制序列中的第一個元素，此專案必須為非空白。 您可以用它來將清單縮短為前端的一個元素。

### <a name="example"></a>範例

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="push_back"></a>list：:p ush_back （STL/CLR）

加入新的最後一個元素。

### <a name="syntax"></a>語法

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>備註

成員函式會在受控制序列的結尾插入具有值 `val` 的元素。 您可以使用它將另一個元素附加至清單。

### <a name="example"></a>範例

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="push_front"></a>list：:p ush_front （STL/CLR）

加入新的第一個元素。

### <a name="syntax"></a>語法

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>備註

成員函式會在受控制序列的開頭插入具有值 `val` 的元素。 您可以使用它，在清單前面加上另一個元素。

### <a name="example"></a>範例

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="rbegin"></a>list：： rbegin （STL/CLR）

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

此成員函式會傳回反向反覆運算器，指定受控制序列的最後一個元素，或只在空白序列開頭以外的專案。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="reference"></a>list：： reference （STL/CLR）

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

此類型描述專案的參考。

### <a name="example"></a>範例

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="remove"></a>list：： remove （STL/CLR）

移除具有指定值的元素。

### <a name="syntax"></a>語法

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>參數

*val*<br/>
要移除之元素的值。

### <a name="remarks"></a>備註

成員函式會移除受控制序列中的元素，其中 `((System::Object^)val)->Equals((System::Object^)x)` 為 true （如果有的話）。 您可以使用它來清除具有指定值的任意元素。

### <a name="example"></a>範例

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="remove_if"></a>list：： remove_if （STL/CLR）

移除通過指定測試的元素。

### <a name="syntax"></a>語法

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>參數

*pred*<br/>
測試要移除的元素。

### <a name="remarks"></a>備註

成員函式會從受控制序列中移除（清除）每個元素 `X`，`pred(X)` 為 true。 您可以使用它來移除符合您指定為函式或委派之條件的所有元素。

### <a name="example"></a>範例

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="rend"></a>list：： rend （STL/CLR）

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

此成員函式會傳回指向受控制序列開頭以外的反向反覆運算器。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="resize"></a>list：： resize （STL/CLR）

變更項目的數目。

### <a name="syntax"></a>語法

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>參數

*new_size*<br/>
受控制序列的新大小。

*val*<br/>
填補元素的值。

### <a name="remarks"></a>備註

成員函式可確保[list：： size （STL/CLR）](../dotnet/list-size-stl-clr.md)`()` 因而需要會傳回*new_size*。 如果它必須讓受控制的序列變長，第一個成員函式會附加具有值 `value_type()`的元素，而第二個成員函式會附加具有值*val*的元素。 為了讓受控制的序列更短，這兩個成員函式會有效地清除最後一個元素[list：： size （STL/CLR）](../dotnet/list-size-stl-clr.md)`() -` `new_size` 時間。 您可以使用它來確保受控制的序列具有大小*new_size*，方法是修剪或填補目前受控制的序列。

### <a name="example"></a>範例

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

    // resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="reverse"></a>list：： reverse （STL/CLR）

反轉受控制的序列。

### <a name="syntax"></a>語法

```cpp
void reverse();
```

### <a name="remarks"></a>備註

成員函式會反轉受控制序列中所有元素的順序。 您可以使用它來反映元素的清單。

### <a name="example"></a>範例

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="reverse_iterator"></a>list：： reverse_iterator （STL/CLR）

受控制序列的反向迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

    // alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="size"></a>list：： size （STL/CLR）

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[list：： empty （STL/CLR）](../dotnet/list-empty-stl-clr.md)`()`。

### <a name="example"></a>範例

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
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

## <a name="size_type"></a>list：： size_type （STL/CLR）

兩個元素之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

此類型描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="sort"></a>list：： sort （STL/CLR）

排序受控制序列。

### <a name="syntax"></a>語法

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>參數

*pred*<br/>
元素配對的比較子。

### <a name="remarks"></a>備註

第一個成員函式會重新排列受控制序列中的專案，使其依 `operator<` 排序--專案在序列中進行時不會在值中降低。 您可以使用這個成員函式，依遞增順序排序序列。

第二個成員函式的行為與第一個相同，不同之處在于順序是依據 `pred``pred(X, Y)`  -- 排序，而在結果序列中的專案 `Y` 後面的任何元素 `X` 都是 false。 您可以使用它，依照述詞函式或委派所指定的順序來排序序列。

這兩個函式都會執行穩定的排序--原始受控制序列中的元素不成對，會在產生的受控制序列中反轉。

### <a name="example"></a>範例

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="splice"></a>list：： splice （STL/CLR）

Restitch-節點之間的連結。

### <a name="syntax"></a>語法

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>參數

*first*<br/>
要拼接的範圍開頭。

*last*<br/>
要拼接的範圍結尾。

*right*<br/>
要做為拼接來源的容器。

*where*<br/>
在 [容器] 中要在何處拼接的位置。

### <a name="remarks"></a>備註

第一個成員函式會在所指向受控制序列中的元素*之前，插入*由*右*所控制的序列。 它也會從*右方*移除所有元素。 （`%right` 不能等於 `this`。）您可以用它來將一個清單全部拼接到另一個。

第二個成員函式會*先*在*right*所控制的序列中移除所指的專案，然後將它插入至所指向*之受控制*序列中的元素前面。 （如果 `where` `==` `first` `||` `where` `== ++first`，則不會發生任何變更）。您可以使用它將一個清單的單一專案拼接成另一個。

第三個成員函式會將 [`first`，`last`）指定的子範圍，從由*右*所控制的序列中的專案，插入在*其中*所指向之受控制序列中的元素。 它也會從*right*所控制的序列中移除原始的子範圍。 （如果 `right` `==` `this`，範圍 [`first`，`last`）不能包含在*其中*所指向的元素。）您可以使用它將零個或多個專案的子序列，從一個清單拼接到另一個。

### <a name="example"></a>範例

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="swap"></a>list：： swap （STL/CLR）

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>參數

*right*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函式會在 `*this` 和*右方*之間交換受控制的序列。 它會以常數時間執行，而且不會擲回任何例外狀況。 您可以用它來快速交換兩個容器的內容。

### <a name="example"></a>範例

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
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

## <a name="to_array"></a>list：： to_array （STL/CLR）

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

此成員函式會傳回陣列，其中包含受控制的序列。 您可以用它來取得陣列表單中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
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

## <a name="unique"></a>list：： unique （STL/CLR）

移除通過指定測試的相鄰項目。

### <a name="syntax"></a>語法

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>參數

*pred*<br/>
元素配對的比較子。

### <a name="remarks"></a>備註

第一個成員函式會從受控制的序列（清除）中移除比較等於其前一個專案的每個專案--如果元素 `X` 在元素 `Y` 和 `X == Y`的前面，成員函式會移除 `Y`。 您可以使用它來移除每個子序列的相鄰元素（比較相等的）的所有複本。 請注意，如果已排序受控制的序列，例如藉由呼叫[list：： sort （STL/CLR）](../dotnet/list-sort-stl-clr.md)`()`，則成員函式只會保留具有唯一值的元素。 (也因此才名為終端方法)。

第二個成員函式的行為與第一個相同，不同之處在于它會移除每個元素，`Y` 在 `pred(X, Y)`的元素 `X` 後面。 您可以使用它來移除相鄰專案的每個子序列的所有，但符合您指定之述詞函式或委派的所有複本。 請注意，如果已排序受控制的序列（例如藉由呼叫 `sort(pred)`），則成員函式只會將沒有對等順序的專案保留給任何其他元素。

### <a name="example"></a>範例

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="value_type"></a>list：： value_type （STL/CLR）

元素類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數*值*同義。

### <a name="example"></a>範例

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a>operator！ = （list）（STL/CLR）

清單不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left == right)`。 您可以使用它來測試當兩個清單是以元素進行比較時，是否要將*left*與*right*排序。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_lt"></a>operator&lt; （list）（STL/CLR）

清單小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

如果 `i` 的最低位置 `!(right[i] < left[i])` 也是 `left[i] < right[i]`，則運算子函數會傳回 true。 否則，它會傳回 `left->size() < right->size()` 您用它來測試當兩個清單是以元素進行比較時 *，是否要*在*右邊*排序。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_lteq"></a>operator&lt;= （list）（STL/CLR）

列出小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(right < left)`。 您可以使用它來測試當兩個清單是以元素進行比較時，*左側*是否未按*右*排序。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_eq"></a>operator = = （list）（STL/CLR）

列出相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

只有當*left*和*right*控制的序列具有相同的長度，且每個位置 `i``left[i] ==` `right[i]`時，運算子函數才會傳回 true。 您可以使用它來測試當兩個清單是以元素進行比較時，*左側*是否與*右*排序相同。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_gt"></a>operator&gt; （list）（STL/CLR）

清單大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `right` `<` `left`。 您可以使用它來測試當兩個清單是以元素進行比較時，是否要*向* *右*排序。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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

## <a name="op_gteq"></a>operator&gt;= （list）（STL/CLR）

列出大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>參數

*left*<br/>
要比較的左容器。

*right*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left` `<` `right)`。 您可以使用它來*測試當兩*個清單是以元素進行比較時，*左側*是否未排序。

### <a name="example"></a>範例

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

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