---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
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
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: 9abecfa6e0bbdf74514e2b7162d1d22a84fa01b2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502410"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

此樣板類別描述一個物件，該物件可控制具有隨機存取之元素的不同長度序列。 您可以使用容器 `vector` ，將一連串的元素管理為連續的儲存區塊。 區塊會實作為隨需成長的陣列。

在下列描述中，與 `GValue` *值* 相同，除非後者是 ref 型別，在這種情況下就是 `Value^` 。

## <a name="syntax"></a>語法

```cpp
template<typename Value>
    ref class vector
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IVector<GValue>
    { ..... };
```

### <a name="parameters"></a>參數

*值*<br/>
受控制序列中項目的類型。

## <a name="requirements"></a>需求

**標頭：**\<cliext/vector>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[vector::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[vector::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[vector::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|容器之泛型介面的反覆運算器類型。|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面之反向反覆運算器的類型。|
|[vector::generic_value (STL/CLR)](#generic_value)|容器之泛型介面的元素類型。|
|[vector::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[vector::reference (STL/CLR)](#reference)|項目的參考類型。|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[vector::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|
|[vector::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|取代所有項目。|
|[vector::at (STL/CLR)](#at)|存取指定位置的項目。|
|[vector::back (STL/CLR)](#back)|存取最後一個項目。|
|[vector::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[vector::capacity (STL/CLR)](#capacity)|報告容器配置儲存區的大小。|
|[vector::clear (STL/CLR)](#clear)|移除所有項目。|
|[vector::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[vector::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[vector::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|
|[vector::front (STL/CLR)](#front)|存取第一個項目。|
|[vector::insert (STL/CLR)](#insert)|將專案加入至指定的位置。|
|[vector::pop_back (STL/CLR)](#pop_back)|移除最後一個元素。|
|[vector::push_back (STL/CLR)](#push_back)|加入新的最後一個元素。|
|[vector::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[vector::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[vector::reserve (STL/CLR)](#reserve)|確保容器的成長容量下限。|
|[vector::resize (STL/CLR)](#resize)|變更項目的數目。|
|[vector::size (STL/CLR)](#size)|計算元素的數目。|
|[vector::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[vector::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|
|[vector::vector (STL/CLR)](#vector)|建構容器物件。|

|屬性|描述|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|存取最後一個項目。|
|[vector::front_item (STL/CLR)](#front_item)|存取第一個項目。|

|運算子|描述|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[vector::operator (STL/CLR)](#op)|存取指定位置的項目。|
|[operator！ = (vector)  (STL/CLR) ](#op_neq)|判斷物件是否 `vector` 不等於另一個 `vector` 物件。|
|[運算子< (vector)  (STL/CLR) ](#op_lt)|判斷 `vector` 物件是否小於另一個 `vector` 物件。|
|[operator<= (向量)  (STL/CLR) ](#op_lteq)|判斷 `vector` 物件是否小於或等於另一個 `vector` 物件。|
|[operator = = (vector)  (STL/CLR) ](#op_eq)|判斷 `vector` 物件是否等於另一個 `vector` 物件。|
|[operator> (vector) (STL/CLR)](#op_gt)|判斷 `vector` 物件是否大於另一個 `vector` 物件。|
|[operator>= (向量)  (STL/CLR) ](#op_gteq)|判斷 `vector` 物件是否大於或等於另一個 `vector` 物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|排序元素。|
|<xref:System.Collections.ICollection>|維護元素群組。|
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的元素排序。|
|<xref:System.Collections.Generic.ICollection%601>|維護具類型的元素群組。|
|<xref:System.Collections.Generic.IList%601>|維護具類型專案的已排序群組。|
|IVector<值\>|維護泛型容器。|

## <a name="remarks"></a>備註

物件會透過儲存的 *值* 元素陣列，配置並釋放它所控制之序列的儲存體，而這些專案會隨需求成長。 成長的發生方式，是將新元素附加的成本分攤為固定的時間。 換句話說，在最後新增專案的成本不會增加，因為受控制序列的長度會變大。 因此，向量是樣板類別 [堆疊 (STL/CLR) ](../dotnet/stack-stl-clr.md)的基礎容器的絕佳候選。

`vector`支援隨機存取反覆運算器，這表示您可以直接參考專案的數值位置，從零算起的第一個 (front) 元素，直到 `size() - 1` 最後一個 (的) 專案為止。 這也表示向量是樣板類別 [priority_queue (STL/CLR) ](../dotnet/priority-queue-stl-clr.md)的基礎容器的絕佳候選。

向量反覆運算器會將控制碼儲存至其相關聯的向量物件，以及它所指定之元素的偏差。 您只能使用反覆運算器與其相關聯的容器物件。 Vector 元素的偏差與其位置相同。

插入或清除元素可以變更儲存在指定位置的專案值，因此 iterator 所指定的值也可以變更。  (容器可能必須將專案向上或向下複製，以在插入或在清除後填滿洞之前建立洞。 ) 不過，只要向量反覆運算器在範圍內，就會維持 `[0, size()]` 有效。 此外，有效的 iterator 仍維持 dereferencable--您可以使用它來存取或修改它所指定的元素值，只要其偏差不等於 `size()` 。

清除或移除專案會呼叫其預存值的函式。 終結容器會清除所有元素。 因此，其元素類型為 ref 類別的容器可確保沒有任何專案存留時間容器。 不過請注意，控制碼的容器不會摧毀其元素。

## <a name="members"></a>成員

## <a name="vectorassign-stlclr"></a><a name="assign"></a> vector：： assign (STL/CLR) 

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

*對*<br/>
要插入的列舉。

*瓦爾*<br/>
要插入的元素值。

### <a name="remarks"></a>備註

第一個成員函式會以值*val*的*count*元素重複來取代受控制的序列。 您可以使用它來填滿具有相同值之元素的容器。

如果 `InIt` 是整數類型，則第二個成員函式的行為會與相同 `assign((size_type)first, (value_type)last)` 。 否則，它會以順序 [，) 取代受控制的序列 `first` `last` 。 您可以使用它來讓受控制序列的複製另一個序列。

第三個成員函式會將受控制序列取代為列舉值 *右邊*所指定的序列。 您可以使用它來讓受控制的序列成為列舉值所描述之序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
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

## <a name="vectorat-stlclr"></a><a name="at"></a> vector：： at (STL/CLR) 

存取指定位置的項目。

### <a name="syntax"></a>語法

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>參數

*pos*<br/>
要存取的項目的位置。

### <a name="remarks"></a>備註

成員函式會傳回位置 *pos*之受控制序列之元素的參考。您可以使用它來讀取或寫入您知道其位置的元素。

### <a name="example"></a>範例

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorback-stlclr"></a><a name="back"></a> vector：： back (STL/CLR) 

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
reference back();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列之最後一個元素的參考，其必須為非空白。 當您知道最後一個元素存在時，您可以使用它來存取最後一個專案。

### <a name="example"></a>範例

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a> vector：： back_item (STL/CLR) 

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>備註

屬性會存取受控制序列的最後一個專案，其必須為非空白。 當您知道最後一個元素存在時，您可以使用它來讀取或寫入最後一個專案。

### <a name="example"></a>範例

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorbegin-stlclr"></a><a name="begin"></a> vector：： begin (STL/CLR) 

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

成員函式會傳回隨機存取反覆運算器，此反覆運算器會指定受控制序列的第一個專案，或在空序列結尾以外的第一個元素。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a> vector：：容量 (STL/CLR) 

報告容器配置儲存區的大小。

### <a name="syntax"></a>語法

```cpp
size_type capacity();
```

### <a name="remarks"></a>備註

成員函式會傳回目前配置用來保存受控制序列的儲存體，此值至少與[vector：： size (STL/CLR) ](#size)相同 `()` 。 您可以使用它來判斷容器在必須為受控制序列重新配置儲存體之前，可成長的程度。

### <a name="example"></a>範例

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorclear-stlclr"></a><a name="clear"></a> vector：： clear (STL/CLR) 

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函式會有效地呼叫[vector：： erase (stl/clr) ](#erase) `(` [vector：： begin (stl/clr) ](#begin) `(),` [vector：： end (STL/clr) ](#end) `())` 。 您可以使用它來確保受控制的序列是空的。

### <a name="example"></a>範例

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a> vector：： const_iterator (STL/CLR) 

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T2` ，可作為受控制序列的常數隨機存取反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a> vector：： const_reference (STL/CLR) 

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

型別描述元素的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> vector：： const_reverse_iterator (STL/CLR) 

受控制序列的常數反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T4` ，可作為受控制序列的常數反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a> vector：:d ifference_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型會描述已簽署的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorempty-stlclr"></a><a name="empty"></a> vector：： empty (STL/CLR) 

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[vector：： size (STL/CLR) ](#size) `() == 0` 。 您可以使用它來測試向量是否為空白。

### <a name="example"></a>範例

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorend-stlclr"></a><a name="end"></a> vector：： end (STL/CLR) 

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

成員函式會傳回隨機存取反覆運算器，其指向受控制序列的結尾以外的位置。 您會用它來取得指定受控制序列之 `current` 結尾的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorerase-stlclr"></a><a name="erase"></a> vector：： erase (STL/CLR) 

移除位於指定位置的項目。

### <a name="syntax"></a>語法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>參數

*first*<br/>
要清除的範圍開頭。

*last*<br/>
要清除的範圍結尾。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>備註

第一個成員函式會移除由 *where*所指向之受控制序列的元素。 您可以使用它來移除單一專案。

第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 您可以使用它來移除零個或多個連續元素。

這兩個成員函式會傳回反覆運算器，此反覆運算器會指定任何移除的元素之外的第一個元素，如果沒有這類專案存在，則[vector：： end (STL/CLR) ](#end) `()` 。

清除專案時，專案複本的數目會是抹除結尾和序列最接近端之間的元素數目的線性。  (清除序列結尾的一或多個元素時，不會複製任何元素。 ) 

### <a name="example"></a>範例

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorfront-stlclr"></a><a name="front"></a> vector：： front (STL/CLR) 

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
reference front();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的第一個元素的參考，而該專案必須為非空白。 當您知道第一個元素存在時，您可以使用它來讀取或寫入第一個專案。

### <a name="example"></a>範例

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a> vector：： front_item (STL/CLR) 

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>備註

屬性會存取受控制序列的第一個專案，其必須為非空白。 當您知道第一個元素存在時，您可以使用它來讀取或寫入第一個專案。

### <a name="example"></a>範例

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a> vector：： generic_container (STL/CLR) 

容器的泛型介面型別。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> vector：： generic_iterator (STL/CLR) 

反覆運算器的類型，用於容器的泛型介面。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>備註

此類型描述可搭配此樣板容器類別的泛型介面使用的泛型反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> vector：： generic_reverse_iterator (STL/CLR) 

反向反覆運算器的類型，用於容器的泛型介面。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述可搭配此樣板容器類別的泛型介面使用的泛型反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a> vector：： generic_value (STL/CLR) 

要搭配容器的泛型介面使用的元素類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

型別描述型別的物件，此物件 `GValue` 描述與這個樣板容器類別的泛型介面搭配使用的預存專案值。

### <a name="example"></a>範例

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorinsert-stlclr"></a><a name="insert"></a> vector：： insert (STL/CLR) 

將專案加入至指定的位置。

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

*對*<br/>
要插入的列舉。

*瓦爾*<br/>
要插入的元素值。

*where*<br/>
在容器中要插入的位置。

### <a name="remarks"></a>備註

每個成員函式會在受控制序列中的 *位置* 所指向的專案之前，插入由其餘運算元所指定的序列。

第一個成員函式會插入具有值 *val* 的元素，並傳回指定新插入之元素的反覆運算器。 您可以使用它，在反覆運算器所指定的位置之前插入單一元素。

第二個成員函式會插入值*val*的*count*元素重複。 您可以使用它來插入零個或多個連續的元素，這些都是相同值的所有複本。

如果 `InIt` 是整數類型，第三個成員函式的行為即與 `insert(where, (size_type)first, (value_type)last)` 相同。 否則，它會插入順序 [ `first` ， `last`) 。 您可以使用它來插入零個或多個從另一個序列複製的連續元素。

第四個成員函式會插入 *右邊*指定的順序。 您可以使用它來插入列舉值所描述的序列。

插入單一專案時，專案複本的數目是在插入點與序列最接近端之間的專案數中的線性。  (在序列的任一結尾插入一或多個專案時，不會複製任何專案。 ) 如果 `InIt` 是輸入反覆運算器，則第三個成員函式會針對序列中的每個元素，有效地執行單一插入。 否則，插入專案時 `N` ，專案複本的數目會是線性， `N` 加上插入點與序列最接近端之間的元素數目。

### <a name="example"></a>範例

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
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

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a> vector：： iterator (STL/CLR) 

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T1` ，可作為受控制序列的隨機存取反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a> vector：： operator = (STL/CLR) 

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子會將 *右移* 至物件，然後傳回 **`*this`** 。 您可以使用它，將受控制序列取代為 *right*中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="vectoroperatorstlclr"></a><a name="op"></a> vector：： operator (STL/CLR) 

存取指定位置的項目。

### <a name="syntax"></a>語法

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>參數

*pos*<br/>
要存取的項目的位置。

### <a name="remarks"></a>備註

成員運算子會將 referene 傳回至位置 *pos*的元素。您可以使用它來存取您知道其位置的元素。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a> vector：:p op_back (STL/CLR) 

移除最後一個元素。

### <a name="syntax"></a>語法

```cpp
void pop_back();
```

### <a name="remarks"></a>備註

成員函式會移除受控制序列的最後一個專案，其必須為非空白。 您可以使用它來將向量減少一個元素的後面。

### <a name="example"></a>範例

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a> vector：:p ush_back (STL/CLR) 

加入新的最後一個元素。

### <a name="syntax"></a>語法

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>備註

成員函式會 `val` 在受控制序列的結尾插入具有值的元素。 您可以使用它來將另一個元素附加至向量。

### <a name="example"></a>範例

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a> vector：： rbegin (STL/CLR) 

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

成員函式會傳回反向反覆運算器，此反覆運算器會指定受控制序列的最後一個專案，或在空白序列的開頭之外。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorreference-stlclr"></a><a name="reference"></a> vector：： reference (STL/CLR) 

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

型別描述對元素的參考。

### <a name="example"></a>範例

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

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

## <a name="vectorrend-stlclr"></a><a name="rend"></a> vector：： rend (STL/CLR) 

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

成員函式會傳回指向受控制序列開頭以外的反向反覆運算器。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a> vector：： reserve (STL/CLR) 

確保容器的成長容量下限。

### <a name="syntax"></a>語法

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>參數

*計數*<br/>
容器的新最小容量。

### <a name="remarks"></a>備註

成員函式可確保 `capacity()` 因而需要至少會傳回 *計數*。 您可以使用它來確保容器不需要重新配置受控制序列的儲存體，直到其成長到指定的大小。

### <a name="example"></a>範例

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorresize-stlclr"></a><a name="resize"></a> vector：： resize (STL/CLR) 

變更項目的數目。

### <a name="syntax"></a>語法

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>參數

*new_size*<br/>
受控制序列的新大小。

*瓦爾*<br/>
填補元素的值。

### <a name="remarks"></a>備註

成員函式可確保[vector：： size (STL/CLR) ](#size) `()` 因而需要會傳回*new_size*。 如果它必須讓受控制序列的時間變長，第一個成員函式會附加具有值的元素 `value_type()` ，而第二個成員函式會附加具有值 *val*的元素。 為了讓受控制的序列變得更短，這兩個成員函式會有效地清除最後一個元素[vector：： size (STL/CLR) ](#size) `() -` `new_size` 時間。 您可以使用它來確保受控制序列的大小 *new_size*，方法是修剪或填補目前的受控制序列。

### <a name="example"></a>範例

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
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

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> vector：： reverse_iterator (STL/CLR) 

受控制序列的反向迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorsize-stlclr"></a><a name="size"></a> vector：： size (STL/CLR) 

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[vector：： empty (STL/CLR) ](#empty) `()` 。

### <a name="example"></a>範例

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a> vector：： size_type (STL/CLR) 

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

型別描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="vectorswap-stlclr"></a><a name="swap"></a> vector：： swap (STL/CLR) 

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函式會交換和右邊的受控制序列 **`*this`** 。 *right* 它會以常數時間來執行，且不會擲回任何例外狀況。 您可以使用它來快速交換兩個容器的內容。

### <a name="example"></a>範例

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
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

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a> vector：： to_array (STL/CLR) 

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

成員函式會傳回陣列，其中包含受控制的序列。 您可以使用它，以陣列形式取得受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a> vector：： value_type (STL/CLR) 

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *值*同義。

### <a name="example"></a>範例

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorvector-stlclr"></a><a name="vector"></a> vector：： vector (STL/CLR) 

建構容器物件。

### <a name="syntax"></a>語法

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>參數

*計數*<br/>
要插入的元素數目。

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*對*<br/>
要插入的物件或範圍。

*瓦爾*<br/>
要插入的元素值。

### <a name="remarks"></a>備註

函數：

`vector();`

使用沒有元素的方式，初始化受控制的序列。 您可以使用它來指定空的初始受控制序列。

函數：

`vector(vector<Value>% right);`

使用序列 [，) 初始化受控制的序列 `right.begin()` `right.end()` 。 您可以使用它來指定初始受控制序列，這是由 vector 物件 *右邊*所控制之序列的複本。

函數：

`vector(vector<Value>^ right);`

使用序列 [，) 初始化受控制的序列 `right->begin()` `right->end()` 。 您可以使用它來指定初始受控制序列，其為控制碼 *正確*的向量物件所控制的序列複本。

函數：

`explicit vector(size_type count);`

使用 *count* 元素（具有值）初始化受控制的序列 `value_type()` 。 您可以使用它來填滿具有預設值的元素的容器。

函數：

`vector(size_type count, value_type val);`

使用具有值*val*的*count*元素，初始化受控制的序列。 您可以使用它來填滿具有相同值之元素的容器。

函數：

`template<typename InIt>`

`vector(InIt first, InIt last);`

使用序列 [，) 初始化受控制的序列 `first` `last` 。 您可以使用它來讓受控制的序列成為另一個序列的複本。

函數：

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

使用列舉值 *右邊*指定的順序，初始化受控制的序列。 您可以使用它來讓受控制的序列成為列舉值所描述之另一個序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
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

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a> operator！ = (vector)  (STL/CLR) 

向量不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left == right)` 。 您可以使用它來測試兩個向量是依元素進行比較時， *左邊* 是否未以 *正確* 的順序排序。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a> 運算子 &lt; (vector)  (STL/CLR) 

向量小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

如果是，運算子函式會傳回 true，如果是，則對 `i` `!(right[i] < left[i])` 而言也是 true `left[i] < right[i]` 。 否則，它會傳回 `left->size() < right->size()` 您使用它來測試當兩個向量*right*是依元素進行比較時，是否要將*左方*排序。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a> operator &lt; = (vector)  (STL/CLR) 

向量小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(right < left)` 。 您可以使用它來測試當兩個向量是依元素進行*比較時，* *左邊*是否未排序。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a> operator = = (vector)  (STL/CLR) 

向量相等比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

只有在由左至右控制的*序列和每*個位置都有相同的長度和時，運算子函*式*才會傳回 true `i` `left[i] ==` `right[i]` 。 您可以使用它來測試當兩個向量是依元素進行比較時， *左邊* 是否 *以相同的* 順序排序。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a> 運算子 &gt; (vector)  (STL/CLR) 

向量大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `right` `<` `left` 。 您可以使用它來測試當兩個向量是依元素進行*比較時，* 是否要將*左方*排序。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a> operator &gt; = (vector)  (STL/CLR) 

向量大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left < right)` 。 您可以使用它來*測試當兩*個向量是依專案進行比較時，*左邊*是否未排序。

### <a name="example"></a>範例

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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
