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
ms.openlocfilehash: c6a001797e90bd7381358abb16612926442e8d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371827"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

樣本類描述控制具有隨機存取的不同長度元素序列的物件。 使用容器`vector`將一系列元素作為連續存儲塊進行管理。 塊作為按需增長的陣組實現。

在下面的描述中,`GValue`與*Value*相同,除非後者是 ref 類型,`Value^`在這種情況下,它是 。

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

*ReplTest1*<br/>
受控制序列中項目的類型。

## <a name="requirements"></a>需求

**標題**\<:cliext/向量>

**命名空間**:cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[vector::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[vector::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[vector::generic_container (STL/CLR)](#generic_container)|容器的泛型介面的類型。|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型介面的反覆運算器的類型。|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面的反向反覆運算器的類型。|
|[vector::generic_value (STL/CLR)](#generic_value)|容器的泛型介面的元素的類型。|
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
|[vector::insert (STL/CLR)](#insert)|在指定位置添加元素。|
|[vector::pop_back (STL/CLR)](#pop_back)|刪除最後一個元素。|
|[vector::push_back (STL/CLR)](#push_back)|添加新的最後一個元素。|
|[vector::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[vector::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[vector::reserve (STL/CLR)](#reserve)|確保容器的最低增長能力。|
|[vector::resize (STL/CLR)](#resize)|變更項目的數目。|
|[vector::size (STL/CLR)](#size)|計算元素的數目。|
|[vector::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[vector::to_array (STL/CLR)](#to_array)|將受控序列複製到新陣列。|
|[vector::vector (STL/CLR)](#vector)|建構容器物件。|

|屬性|描述|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|存取最後一個項目。|
|[vector::front_item (STL/CLR)](#front_item)|存取第一個項目。|

|運算子|描述|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[vector::operator (STL/CLR)](#op)|存取指定位置的項目。|
|[運算子!* (向量) (STL/CLR)](#op_neq)|確定物件`vector`是否不等於`vector`其他 物件。|
|[運算符<(向量)(STL/CLR)](#op_lt)|確定`vector`物件是否小於`vector`其他 物件。|
|[運算子<= (向量) (STL/CLR)](#op_lteq)|確定物件是否`vector`小於或等於另一`vector`個 物件。|
|[運算子* (向量) (STL/CLR)](#op_eq)|確定物件是否`vector`等於另一`vector`個 物件。|
|[operator> (vector) (STL/CLR)](#op_gt)|確定物件是否`vector`大於另一個`vector`物件。|
|[運算子>= (向量) (STL/CLR)](#op_gteq)|確定物件是否`vector`大於或等於另一個`vector`物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|通過元素排序。|
|<xref:System.Collections.ICollection>|維護元素組。|
|<xref:System.Collections.Generic.IEnumerable%601>|通過類型化元素進行排序。|
|<xref:System.Collections.Generic.ICollection%601>|維護類型化元素組。|
|<xref:System.Collections.Generic.IList%601>|維護有序的鍵入元素組。|
|IVector<值\>|維護通用容器。|

## <a name="remarks"></a>備註

對象通過存儲*的值*元素陣列為其控制的順序分配和釋放存儲,該陣列按需增長。 增長的方式是附加新元素的成本是攤銷恆定時間。 換句話說,在末尾添加元素的成本不會隨著受控序列的長度變大而增加。 因此,向量是範本類[堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)的基礎容器的良好候選項。

支援`vector`隨機存取反覆運算器,這意味著您可以直接引用給定其數值位置的元素,從第一個(正面)元素的零計`size() - 1`數到最後一個(背面)元素。 這也意味著向量是範本類[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)的基礎容器的良好候選項。

向量反覆運算器將句柄存儲到其關聯的向量物件,以及它指定的元素的偏差。 只能將反覆運算器與其關聯的容器物件一起使用。 向量元素的偏置與其位置相同。

插入或刪除元素可以更改儲存在給定位置的元素值,因此反覆運算器指定的值也可以更改。 (容器可能必須向上或向下複製元素,才能在插入之前創建孔,或在擦除後填充孔。然而,只要向量反覆運算器的偏置在範圍內`[0, size()]`,它仍然有效。 此外,有效的反覆運算器仍然可引用 - 只要其偏差不等於 ,就可以使用它來存取或更改它`size()`指定的元素值 。

刪除或刪除元素將調用析構函數的儲存值。 銷毀容器會擦除所有元素。 因此,元素類型為 ref 類的容器可確保沒有元素比容器壽命大。 但是請注意,句柄的容器不會破壞其元素。

## <a name="members"></a>成員

## <a name="vectorassign-stlclr"></a><a name="assign"></a>向量:配置(STL/CLR)

取代所有項目。

### <a name="syntax"></a>語法

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>參數

*count*<br/>
要插入的元素數目。

*第一*<br/>
要插入的範圍的開始。

*最後*<br/>
要插入的範圍結束。

*對*<br/>
要插入的枚舉。

*瓦爾*<br/>
要插入的元素的值。

### <a name="remarks"></a>備註

第一個成員函數用值*val*的*計數*元素的重複替換受控序列。 使用它填充容器的元素都具有相同的值。

如果是`InIt`整數類型,則第二個成員函數的表示與`assign((size_type)first, (value_type)last)`相同 。 否則,它會受控序列取代為序列`first`* `last` 。 使用它使受控序列成為另一個序列的副本。

第三個成員函數將受控序列替換為枚舉器*右側*指定的序列。 使用它使受控序列成為枚舉器描述序列的副本。

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

## <a name="vectorat-stlclr"></a><a name="at"></a>向量:在 (STL/CLR)

存取指定位置的項目。

### <a name="syntax"></a>語法

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>參數

*Pos*<br/>
要存取的項目的位置。

### <a name="remarks"></a>備註

成員函數返回對位置*位置*處受控序列元素的引用。您可以使用它讀取或寫入您知道其位置的元素。

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

## <a name="vectorback-stlclr"></a><a name="back"></a>向量:回(STL/CLR)

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
reference back();
```

### <a name="remarks"></a>備註

成員函數返回對受控序列的最後一個元素的引用,該元素必須為非空。 當您知道它存在時,可以使用它訪問最後一個元素。

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

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a>向量:back_item(STL/CLR)

存取最後一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type back_item;
```

### <a name="remarks"></a>備註

屬性訪問受控序列的最後一個元素,該元素必須為非空。 當您知道它存在時,可以使用它讀取或寫入最後一個元素。

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

## <a name="vectorbegin-stlclr"></a><a name="begin"></a>向量:開始(STL/CLR)

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

成員函數返回一個隨機存取反覆運算器,該反覆運算器指定受控序列的第一個元素,或剛剛超出空序列的末尾。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

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

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a>向量:容量(STL/CLR)

報告容器配置儲存區的大小。

### <a name="syntax"></a>語法

```cpp
size_type capacity();
```

### <a name="remarks"></a>備註

成員函數返回當前為保存受控序列而分配的存儲,該值至少與[向量::大小 (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`一樣大。 使用它來確定容器在必須為受控序列重新分配存儲之前可以增長多少。

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

## <a name="vectorclear-stlclr"></a><a name="clear"></a>向量:清除(STL/CLR)

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函數有效地調用[向量::擦除 (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(`[向量:開始(STL/CLR)](../dotnet/vector-begin-stl-clr.md)`(),`[向量::結束 (STL/CLR)](../dotnet/vector-end-stl-clr.md)`())`。 使用它來確保受控序列為空。

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

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a>向量:const_iterator(STL/CLR)

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

類型描述未指定類型`T2`的物件,該物件可用作受控序列的恆定隨機存取反覆運算器。

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

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a>向量:const_reference(STL/CLR)

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

類型描述對元素的常量引用。

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

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>向量:const_reverse_iterator(STL/CLR)

受控序列的常量反向反覆運算器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型描述未指定類型`T4`的物件,該物件可用作受控序列的恆定反向反覆運算器。

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

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a>向量::d)類型(STL/CLR)

兩個元素之間簽名距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

類型描述已簽名的元素計數。

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

## <a name="vectorempty-stlclr"></a><a name="empty"></a>向量:空(STL/CLR)

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它等效於[向量:大小 (STL/CLR)。](../dotnet/vector-size-stl-clr.md) `() == 0` 使用它來測試向量是否為空。

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

## <a name="vectorend-stlclr"></a><a name="end"></a>向量:結束(STL/CLR)

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

成員函數返回一個隨機存取反覆運算器,該反覆運算器的點位於受控序列的末尾之外。 您會用它來取得指定受控制序列之 `current` 結尾的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

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

## <a name="vectorerase-stlclr"></a><a name="erase"></a>向量:擦除(STL/CLR)

移除位於指定位置的項目。

### <a name="syntax"></a>語法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>參數

*第一*<br/>
要擦除的範圍的開始。

*最後*<br/>
要擦除的範圍結束。

*其中*<br/>
要擦除的元素。

### <a name="remarks"></a>備註

第一個成員函數刪除由*何處*指向的受控序列的元素。 使用它刪除單個元素。

第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 使用它刪除零個或多個連續元素。

這兩個成員函數返回一個反覆運算器,該反覆運算器指定除刪除的任何元素之外剩餘的第一個元素,或者如果不存在此類元素[,則向量::end (STL/CLR)。](../dotnet/vector-end-stl-clr.md) `()`

擦除元素時,元素副本的數量在擦除結束和序列近端之間的元素數中是線性的。 (在序列的任意一端執行一個或多個元素時,不會發生元素副本。

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

## <a name="vectorfront-stlclr"></a><a name="front"></a>向量:前(STL/CLR)

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
reference front();
```

### <a name="remarks"></a>備註

成員函數返回對受控序列的第一個元素的引用,該元素必須為非空。 當您知道它存在時,可以使用它讀取或寫入第一個元素。

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

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a>向量::front_item(STL/CLR)

存取第一個項目。

### <a name="syntax"></a>語法

```cpp
property value_type front_item;
```

### <a name="remarks"></a>備註

屬性訪問受控序列的第一個元素,該元素必須為非空。 當您知道它存在時,可以使用它讀取或寫入第一個元素。

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

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a>向量:generic_container(STL/CLR)

容器的泛型介面的類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>備註

類型描述此範本容器類的泛型介面。

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

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>向量:generic_iterator(STL/CLR)

用於容器的泛型介面的反覆運算器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>備註

該類型描述了一個泛型反覆運算器,該反覆運算器可與此範本容器類的泛型介面一起使用。

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

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>向量:generic_reverse_iterator(STL/CLR)

用於容器的泛型介面的反向反覆運算器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>備註

該類型描述了一個通用反向反覆運算器,該反覆運算器可與此範本容器類的泛型介面一起使用。

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

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a>向量:generic_value(STL/CLR)

用於容器的泛型介面的元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

類型描述類型`GValue`物件,該物件描述存儲的元素值,以便與此範本容器類的泛型介面一起使用。

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

## <a name="vectorinsert-stlclr"></a><a name="insert"></a>向量:插入(STL/CLR)

在指定位置添加元素。

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

*count*<br/>
要插入的元素數目。

*第一*<br/>
要插入的範圍的開始。

*最後*<br/>
要插入的範圍結束。

*對*<br/>
要插入的枚舉。

*瓦爾*<br/>
要插入的元素的值。

*其中*<br/>
以前在容器中插入的位置。

### <a name="remarks"></a>備註

每個成員函數在元素指向受控序列中*的位置*之前插入由其餘操作數指定的序列。

第一個成員函數插入值*val*的元素,並返回指定新插入的元素的反覆運算器。 使用它在反覆運算器指定的位置之前插入單個元素。

第二個成員函數插入值*val*的*計數*元素的重複。 使用它插入零個或多個連續元素,這些元素都是相同值的副本。

如果 `InIt` 是整數類型，第三個成員函式的行為即與 `insert(where, (size_type)first, (value_type)last)` 相同。 否則,它將插入序列`first`* `last` 。 使用它插入從其他序列複製的零個或多個連續元素。

第四個成員函數插入*右側*指定的序列。 使用它插入枚舉器描述的序列。

插入單個元素時,元素複本的數量在插入點和序列的近端之間的元素數中是線性的。 (在序列的任意一端插入一個或多個元素時,不會發生元素副本。如果是`InIt`輸入反覆運算器,則第三個成員函數可有效地對序列中的每個元素執行單個插入。 否則,插入`N`元素時,元素複本的數量是線性的,`N`加上插入點和序列近端之間的元素數。

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

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a>向量:反覆發代器 (STL/CLR)

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

類型描述未指定類型`T1`的物件,該物件可用作受控序列的隨機存取反覆運算器。

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

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a>向量:運算符*(STL/CLR)

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子*將右邊*複製到物件,`*this`然後傳回 。 使用它將受控序列替換為*右側*受控序列的副本。

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

## <a name="vectoroperatorstlclr"></a><a name="op"></a>向量:運算子(STL/CLR)

存取指定位置的項目。

### <a name="syntax"></a>語法

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>參數

*Pos*<br/>
要存取的項目的位置。

### <a name="remarks"></a>備註

成員運算符返回位置*位置*的元素的引用。您可以使用它存取您知道其位置的元素。

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

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a>向量::pop_back(STL/CLR)

刪除最後一個元素。

### <a name="syntax"></a>語法

```cpp
void pop_back();
```

### <a name="remarks"></a>備註

成員函數刪除受控序列的最後一個元素,該元素必須為非空。 使用它將向量縮短到背面的一個元素。

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

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a>向量::push_back(STL/CLR)

添加新的最後一個元素。

### <a name="syntax"></a>語法

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>備註

成員函數在受控序列的末尾插入具有`val`值的元素。 使用它將另一個元素追加到向量中。

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

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a>向量:rbegin(STL/CLR)

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

成員函數返回一個反向反覆運算器,該反覆運算器指定受控序列的最後一個元素,或剛剛超出空序列的開頭。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

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

## <a name="vectorreference-stlclr"></a><a name="reference"></a>向量:參考(STL/CLR)

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

類型描述對元素的引用。

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

## <a name="vectorrend-stlclr"></a><a name="rend"></a>向量:rend(STL/CLR)

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

成員函數返回一個反向反覆運算器,該反覆運算器的點位於受控序列的開頭之外。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

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

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a>向量:保留(STL/CLR)

確保容器的最低增長能力。

### <a name="syntax"></a>語法

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>參數

*count*<br/>
容器的新最小容量。

### <a name="remarks"></a>備註

成員函數確保`capacity()`從此傳回至少*計數*。 使用它可確保容器在增長到指定大小之前無需重新分配受控序列的存儲。

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

## <a name="vectorresize-stlclr"></a><a name="resize"></a>向量:調整大小(STL/CLR)

變更項目的數目。

### <a name="syntax"></a>語法

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>參數

*new_size*<br/>
受控序列的新大小。

*瓦爾*<br/>
填充元素的值。

### <a name="remarks"></a>備註

成員函數都確保從今以後[向量::大小(STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`傳回*new_size*。 如果必須延長受控序列,則第一個成員函數將值`value_type()`追加元素,而第二個成員函數則追加值為*val*的元素。 為了使受控序列變短,兩個成員函數都有效地擦除最後一個元素[向量::大小 (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() -``new_size`時間。 使用它透過修剪或填充當前受控序列來確保受控序列*的大小new_size。*

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

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>向量:reverse_iterator(STL/CLR)

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

## <a name="vectorsize-stlclr"></a><a name="size"></a>向量:大小(STL/CLR)

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 使用它來確定當前受控序列中的元素數。 如果您關心的只是序列是否具有非零大小,請參閱[向量:空 (STL/CLR)。](../dotnet/vector-empty-stl-clr.md) `()`

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

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a>向量::size_type(STL/CLR)

兩個項目之間帶正負號距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

類型描述非負元素計數。

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

## <a name="vectorswap-stlclr"></a><a name="swap"></a>向量:交換(STL/CLR)

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函數交換*和*之間的`*this`受控序列。 它在恆定時間內這樣做,並且不會引發任何異常。 使用它作為交換兩個容器內容的快速方法。

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

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a>向量::to_array(STL/CLR)

將受控序列複製到新陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>備註

成員函數返回包含受控序列的陣列。 使用它以陣列形式獲取受控序列的副本。

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

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a>向量:value_type(STL/CLR)

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>備註

類型是範本參數*值*的同義詞。

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

## <a name="vectorvector-stlclr"></a><a name="vector"></a>向量:向量(STL/CLR)

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

*count*<br/>
要插入的元素數目。

*第一*<br/>
要插入的範圍的開始。

*最後*<br/>
要插入的範圍結束。

*對*<br/>
要插入的物件或範圍。

*瓦爾*<br/>
要插入的元素的值。

### <a name="remarks"></a>備註

建構函數:

`vector();`

初始化受控序列,無元素。 使用它指定空的初始控制序列。

建構函數:

`vector(vector<Value>% right);`

使用序列的`right.begin()`* 初始化受`right.end()`控序 。 使用它指定初始受控序列,該序列是向量對象*右側*控制序列的副本。

建構函數:

`vector(vector<Value>^ right);`

使用序列的`right->begin()`* 初始化受`right->end()`控序 。 使用它指定初始受控序列,該序列是由句柄*正確的*向量物件控制的序列的副本。

建構函數:

`explicit vector(size_type count);`

用計數元素為每個具有值`value_type()`的*計數*元素初始化受控序列。 使用它填充容器的元素都具有預設值。

建構函數:

`vector(size_type count, value_type val);`

用值*val*的*計數*元素初始化受控序列。 使用它填充容器的元素都具有相同的值。

建構函數:

`template<typename InIt>`

`vector(InIt first, InIt last);`

使用序列的`first`* 初始化受`last`控序 。 使用它使受控序列成為另一個序列的副本。

建構函數:

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

使用枚舉器*右側*指定的序列初始化受控序列。 使用它使受控序列成為枚舉器描述的另一個序列的副本。

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

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a>運算子!* (向量) (STL/CLR)

向量不相等比較。

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

運算子函數傳回`!(left == right)`。 使用它來測試當按元素比較兩個向量時,*左的*排序是否與*右側*相同。

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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a>運算子&lt;(向量) (STL/CLR)

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

如果 對於最低`i``!(right[i] < left[i])`位置 ,運算子傳回`left[i] < right[i]`true, 如果 。 否則,它返回`left->size() < right->size()`「使用它」來測試在按元素比較兩個向量之前是否*對**左*排序。

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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a>運算子&lt;= (向量) (STL/CLR)

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

運算子函數傳回`!(right < left)`。 使用它來測試在按元素比較兩個向量時,*是否*未*在右後右*排序。

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

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a>運算子* (向量) (STL/CLR)

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

僅當*由左右*控制的順序長度*right*相同 且`i``left[i] ==``right[i]`每個位置 具有相同的長度時,運算符函數才會返回 true。 使用它來測試當按元素比較兩個向量時,*左的*排序是否與*右側*相同。

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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a>運算子&gt;(向量) (STL/CLR)

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

運算子函數傳回`right``<``left`。 使用它來測試在按元素比較兩個向量時 *,左是否*按*右*順序排列。

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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a>運算子&gt;= (向量) (STL/CLR)

向量大於或相等的比較。

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

運算子函數傳回`!(left < right)`。 使用它來測試在按元素比較兩個向量*之前是否*未對*左側*進行排序。

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
