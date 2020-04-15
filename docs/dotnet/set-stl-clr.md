---
title: set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
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
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
ms.openlocfilehash: 38b0a3278efd10ef5cc989a5fc900bf82d377eae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320312"
---
# <a name="set-stlclr"></a>set (STL/CLR)

範本類描述控制具有雙向存取許可權的不同長度元素序列的物件。 您可以使用容器`set`將一系列元素作為(幾乎)平衡有序的節點樹進行管理,每個節點存儲一個元素。

在下面的描述中,`GValue`它與`GKey`相同 ,後者又與*Key*相同,除非後者是 ref 型`Key^`態,在這種情況下,它是 。

## <a name="syntax"></a>語法

```cpp
template<typename Key>
    ref class set
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

*關鍵*<br/>
受控制序列中項目的主要元件型別。

## <a name="requirements"></a>需求

**標題**\<:cliext/set>

**命名空間**:cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[set::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[set::difference_type (STL/CLR)](#difference_type)|兩個元素之間的距離的類型(可能已簽名)。|
|[set::generic_container (STL/CLR)](#generic_container)|容器的泛型介面的類型。|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型介面的反覆運算器的類型。|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面的反向反覆運算器的類型。|
|[set::generic_value (STL/CLR)](#generic_value)|容器的泛型介面的元素的類型。|
|[set::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[set::key_compare (STL/CLR)](#key_compare)|兩個鍵的排序委託。|
|[set::key_type (STL/CLR)](#key_type)|排序索引鍵的類型。|
|[set::reference (STL/CLR)](#reference)|項目的參考類型。|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[set::size_type (STL/CLR)](#size_type)|兩個元素之間的(非負)距離的類型。|
|[set::value_compare (STL/CLR)](#value_compare)|兩個元素值的排序委託。|
|[set::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[set::clear (STL/CLR)](#clear)|移除所有項目。|
|[set::count (STL/CLR)](#count)|計算與指定鍵匹配的元素。|
|[set::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[set::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[set::equal_range (STL/CLR)](#equal_range)|尋找符合指定之索引鍵的範圍。|
|[set::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|
|[set::find (STL/CLR)](#find)|尋找符合指定之索引鍵的元素。|
|[set::insert (STL/CLR)](#insert)|加入項目。|
|[set::key_comp (STL/CLR)](#key_comp)|複製兩個鍵的排序委託。|
|[set::lower_bound (STL/CLR)](#lower_bound)|尋找與指定鍵匹配的範圍的開頭。|
|[set::make_value (STL/CLR)](#make_value)|構造值物件。|
|[set::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[set::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[set::set (STL/CLR)](#set)|建構容器物件。|
|[set::size (STL/CLR)](#size)|計算元素的數目。|
|[set::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[set::to_array (STL/CLR)](#to_array)|將受控序列複製到新陣列。|
|[set::upper_bound (STL/CLR)](#upper_bound)|尋找與指定鍵匹配的範圍的末尾。|
|[set::value_comp (STL/CLR)](#value_comp)|複製兩個元素值的排序委託。|

|運算子|描述|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[運算元!*(設置)(STL/CLR)](#op_neq)|確定物件`set`是否不等於`set`其他 物件。|
|[運算子<(設定)(STL/CLR)](#op_lt)|確定`set`物件是否小於`set`其他 物件。|
|[運算子<= (設定) (STL/CLR)](#op_lteq)|確定物件是否`set`小於或等於另一`set`個 物件。|
|[operator== (set) (STL/CLR)](#op_eq)|確定物件是否`set`等於另一`set`個 物件。|
|[運算子>(設定)(STL/CLR)](#op_gt)|確定物件是否`set`大於另一個`set`物件。|
|[運算子>= (設定) (STL/CLR)](#op_gteq)|確定物件是否`set`大於或等於另一個`set`物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|通過元素排序。|
|<xref:System.Collections.ICollection>|維護元素組。|
|<xref:System.Collections.Generic.IEnumerable%601>|通過類型化元素進行排序。|
|<xref:System.Collections.Generic.ICollection%601>|維護類型化元素組。|
|ITree\<鍵,值>|維護通用容器。|

## <a name="remarks"></a>備註

物件為其控制為單個節點控制的順序分配和釋放存儲。 它將元素插入到(幾乎)平衡的樹中,它通過更改節點之間的連結(從不通過將一個節點的內容複製到另一個節點)來保持順序。 這意味著您可以自由插入和刪除元素,而不會干擾其餘元素。

對象通過調用[類型集:::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)的存儲委託物件來命令其控制的順序。 您可以在構造集時指定存儲的委託物件;但是,在構造集時,可以指定存儲的委託物件。如果指定沒有委託物件,則預設值為比較`operator<(key_type, key_type)`。 通過調用成員函數[集::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`來訪問此存儲的物件。

此類委託物件必須對類型[集:::key_type (STL/CLR) 的](../dotnet/set-key-type-stl-clr.md)鍵施加嚴格的弱排序。 這意味著,對於任何兩個鍵`X``Y`和 :

`key_comp()(X, Y)`在每個調用上返回相同的布爾結果。

如果`key_comp()(X, Y)`為 true,`key_comp()(Y, X)`則必須為 false。

如果`key_comp()(X, Y)`為 true,`X`則表示之前已`Y`訂購 。

如果`!key_comp()(X, Y) && !key_comp()(Y, X)`為`X`true, 則`Y`表示具有等效排序。

對於受控序列`X``Y`中前面的任何元素`key_comp()(Y, X)`, 都是 false。 (對於預設委託物件,鍵的值永遠不會減少。與範本類[集](../dotnet/set-stl-clr.md)不同,範`set`本類的物件不要求所有元素的鍵都是唯一的。 (兩個或多個金鑰可以具有等效排序。

每個元素同時充當 ey 和值。 序列的表示方式允許查找、插入和刪除任意元素,其操作數量與序列中元素數(對數時間)的對數成正比。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。

集支援雙向反覆運算器,這意味著您可以步進到相鄰元素,給定一個反覆運算器,該反覆運算器在受控序列中指定元素。 特殊頭節點對應於按[set:end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`傳回的反覆運算器。 可以遞減此反覆運算器以到達受控序列中的最後一個元素(如果存在)。 您可以增量一個集疊代器以到達頭節點,然後它將比較等於`end()`。 但是,您不能取消引用返回的`end()`反覆運算器。

請注意,您不能直接引用給定其數值位置的集元素,該元素需要隨機存取反覆運算器。

集反覆運算器將句柄存儲到其關聯的集節點,而該節點又將句柄存儲到其關聯的容器。 只能將反覆運算器與其關聯的容器物件一起使用。 只要集反覆運算器的關聯集節點與某個集相關聯,則其反覆運算器仍然有效。 此外,有效的反覆運算器是可引用的 -- 只要它不`end()`等於 , 就可以使用它來訪問或更改它指定的元素值。

刪除或刪除元素將調用析構函數的儲存值。 銷毀容器會擦除所有元素。 因此,元素類型為 ref 類的容器可確保沒有元素比容器壽命大。 但是請注意,句柄的容器*不會*破壞其元素。

## <a name="members"></a>成員

## <a name="setbegin-stlclr"></a><a name="begin"></a>設定:開始(STL/CLR)

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

成員函數返回一個雙向反覆運算器,該反覆運算器指定受控序列的第一個元素,或剛剛超出空序列的末尾。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_set_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::iterator it = c1.begin();
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

## <a name="setclear-stlclr"></a><a name="clear"></a>設定:清除(STL/CLR)

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函數有效地調用[集::擦除 (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(`[集:開始(STL/CLR)](../dotnet/set-begin-stl-clr.md)`(),`[集::結束(STL/CLR)](../dotnet/set-end-stl-clr.md)`())`。 使用它來確保受控序列為空。

### <a name="example"></a>範例

```cpp
// cliext_set_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setconst_iterator-stlclr"></a><a name="const_iterator"></a>集::const_iterator(STL/CLR)

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

類型描述未指定類型`T2`的物件,該物件可用作受控序列的恆定雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_set_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setconst_reference-stlclr"></a><a name="const_reference"></a>設定::const_reference(STL/CLR)

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

類型描述對元素的常量引用。

### <a name="example"></a>範例

```cpp
// cliext_set_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>設定::const_reverse_iterator(STL/CLR)

受控序列的常量反向反覆運算器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

類型描述未指定類型`T4`的物件,該物件可用作受控序列的恆定反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="setcount-stlclr"></a><a name="count"></a>設定:計數(STL/CLR)

尋找符合指定索引鍵的項目數目。

### <a name="syntax"></a>語法

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函數返回具有與*鍵*等效排序的受控序列中的元素數。 您會用它來判斷目前在受控制序列中，符合指定之索引鍵的項目數目。

### <a name="example"></a>範例

```cpp
// cliext_set_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setdifference_type-stlclr"></a><a name="difference_type"></a>設定::d)類型 (STL/ CLR)

兩個元素之間簽名距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

類型描述可能為負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_set_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="setempty-stlclr"></a><a name="empty"></a>集::空(STL/CLR)

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它等效於[設置:大小 (STL/CLR)。](../dotnet/set-size-stl-clr.md) `() == 0` 使用它來測試該集是否為空。

### <a name="example"></a>範例

```cpp
// cliext_set_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setend-stlclr"></a><a name="end"></a>設定:結束(STL/CLR)

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

成員函數返回一個雙向反覆運算器,該反覆運算器的點位於受控序列的末尾之外。 使用它來獲取指定受控序列結束的反覆運算器;如果受控序列的長度發生更改,其狀態不會更改。

### <a name="example"></a>範例

```cpp
// cliext_set_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    Myset::iterator it = c1.end();
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

## <a name="setequal_range-stlclr"></a><a name="equal_range"></a>集::equal_range(STL/CLR)

尋找符合指定之索引鍵的範圍。

### <a name="syntax"></a>語法

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函數返回一對反覆運算器`cliext::pair<iterator, iterator>(`[集:lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [集::upper_bound (STL/CLR)。](../dotnet/set-upper-bound-stl-clr.md) `(key))` 使用它來確定當前在受控序列中與指定鍵匹配的元素範圍。

### <a name="example"></a>範例

```cpp
// cliext_set_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_iter Pairii;
int main()
    {
    Myset c1;
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

## <a name="seterase-stlclr"></a><a name="erase"></a>設定:擦除(STL/CLR)

移除位於指定位置的項目。

### <a name="syntax"></a>語法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>參數

*第一*<br/>
要擦除的範圍的開始。

*關鍵*<br/>
要擦除的關鍵值。

*最後*<br/>
要擦除的範圍結束。

*其中*<br/>
要擦除的元素。

### <a name="remarks"></a>備註

第一個成員函數刪除由*何處*指向的受控序列的元素,並返回一個反覆運算器,該反覆運算器指定刪除的元素之外的第一個元素,如果不存在此類元素,[則設置:end (STL/CLR)。](../dotnet/set-end-stl-clr.md) `()` 使用它刪除單個元素。

第二個成員函數刪除範圍`first``last`* 中的受控序列的元素,並返回一個反覆運算器,該反覆運算器指定超出刪除的任何元素之外的第一個元素,`end()`或者如果 不存在此類元素。 使用它刪除零個或多個連續元素。

第三個成員函數刪除鍵與*鍵*的等效排序的受控序列的任何元素,並返回刪除的元素數的計數。 使用它刪除和計數與指定鍵匹配的所有元素。

每個元素擦除所需的時間與受控序列中元素數的對數成正比。

### <a name="example"></a>範例

```cpp
// cliext_set_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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
    Myset::iterator it = c1.end();
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

## <a name="setfind-stlclr"></a><a name="find"></a>設定:尋找(STL/CLR)

尋找符合指定之索引鍵的元素。

### <a name="syntax"></a>語法

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

如果受控序列中至少有一個元素具有與*鍵*等效排序,則成員函數將返回指定其中一個元素的反覆運算器;否則它將返回[集::結束 (STL/CLR)。](../dotnet/set-end-stl-clr.md) `()` 使用它來尋找當前與指定鍵匹配的受控序列中的元素。

### <a name="example"></a>範例

```cpp
// cliext_set_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setgeneric_container-stlclr"></a><a name="generic_container"></a>設定::generic_container(STL/CLR)

容器的泛型介面的類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>備註

類型描述此範本容器類的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_set_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
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

## <a name="setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>設定::generic_iterator(STL/CLR)

用於容器的泛型介面的反覆運算器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>備註

該類型描述了一個泛型反覆運算器,該反覆運算器可與此範本容器類的泛型介面一起使用。

### <a name="example"></a>範例

```cpp
// cliext_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>套::generic_reverse_iterator(STL/CLR)

用於容器的泛型介面的反向反覆運算器的類型。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>備註

該類型描述了一個通用反向反覆運算器,該反覆運算器可與此範本容器類的泛型介面一起使用。

### <a name="example"></a>範例

```cpp
// cliext_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_reverse_iterator gcit = gc1->rbegin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="setgeneric_value-stlclr"></a><a name="generic_value"></a>設定::generic_value(STL/CLR)

用於容器的泛型介面的元素的類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

類型描述類型`GValue`物件,該物件描述存儲的元素值,以便與此範本容器類的泛型介面一起使用。

### <a name="example"></a>範例

```cpp
// cliext_set_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="setinsert-stlclr"></a><a name="insert"></a>設定:插入(STL/CLR)

加入項目。

### <a name="syntax"></a>語法

```cpp
cliext::pair<iterator, bool> insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>參數

*第一*<br/>
要插入的範圍的開始。

*最後*<br/>
要插入的範圍結束。

*對*<br/>
要插入的枚舉。

*瓦爾*<br/>
要插入的鍵值。

*其中*<br/>
容器中要插入的位置(僅限提示)。

### <a name="remarks"></a>備註

每個成員函數插入由其餘操作數指定的序列。

第一個成員函數嘗試插入值*為 val*的元素,並傳`X`回一對值 。 如果`X.second`為 true,則指定新插入的元素;如果為`X.first`true, 則指定新插入的元素。否則`X.first`指定具有已存在的等效排序且未插入新元素的元素。 使用它插入單個元素。

第二個成員函數插入值*為 val*的元素,使用*其中*用作提示(以提高性能),並返回指定新插入的元素的反覆運算器。 使用它插入一個可能與您知道的元素相鄰的單個元素。

第三個成員函數插入序列`first`* `last` 。 使用它插入從其他序列複製的零個或多個元素。

第四個成員函數插入*右側*指定的序列。 使用它插入枚舉器描述的序列。

每個元素插入所需的時間與受控序列中元素數的對數成正比。 但是,給定指定插入點附近的元素的提示,可以在攤銷常量時間內進行插入。

### <a name="example"></a>範例

```cpp
// cliext_set_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_bool Pairib;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value, unique and duplicate
    Pairib pair1 = c1.insert(L'x');
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",
        *pair1.first, pair1.second);

    pair1 = c1.insert(L'b');
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",
        *pair1.first, pair1.second);

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
    Myset c2;
    Myset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    Myset c3;
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
insert(L'x') = [x True]
insert(L'b') = [b False]
a b c x
insert(begin(), L'y') = y
a b c x y
a b c x
a b c x y
```

## <a name="setiterator-stlclr"></a><a name="iterator"></a>集:反覆運算器 (STL/ CLR)

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

類型描述一個未指定類型`T1`的物件,該物件可用作受控序列的雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_set_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setkey_comp-stlclr"></a><a name="key_comp"></a>設定:key_comp(STL/CLR)

複製兩個鍵的排序委託。

### <a name="syntax"></a>語法

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>備註

成員函數返回用於排序受控序列的排序委託。 您會用它來比較兩個索引鍵。

### <a name="example"></a>範例

```cpp
// cliext_set_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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

## <a name="setkey_compare-stlclr"></a><a name="key_compare"></a>設定::key_compare(STL/CLR)

兩個鍵的排序委託。

### <a name="syntax"></a>語法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>備註

類型是委託的同義詞,用於確定其鍵參數的順序。

### <a name="example"></a>範例

```cpp
// cliext_set_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
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

## <a name="setkey_type-stlclr"></a><a name="key_type"></a>設定:key_type(STL/CLR)

排序索引鍵的類型。

### <a name="syntax"></a>語法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

類型是範本參數*Key*的同義詞。

### <a name="example"></a>範例

```cpp
// cliext_set_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using key_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setlower_bound-stlclr"></a><a name="lower_bound"></a>設定:lower_bound(STL/CLR)

尋找與指定鍵匹配的範圍的開頭。

### <a name="syntax"></a>語法

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函數確定受控序列中與`X`*鍵*具有等效排序的第一個元素。 如果不存在此類元素,它將返回[集::結束(STL/CLR);](../dotnet/set-end-stl-clr.md) `()`否則,它將返回指定的`X`反覆運算器。 使用它來定位當前在受控序列中匹配指定鍵的元素序列的開頭。

### <a name="example"></a>範例

```cpp
// cliext_set_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setmake_value-stlclr"></a><a name="make_value"></a>設定:make_value(STL/CLR)

構造值物件。

### <a name="syntax"></a>語法

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
要使用的鍵值。

### <a name="remarks"></a>備註

成員函數返回其鍵`value_type`為*鍵*的物件。 使用它來組合一個適合與其他幾個成員函數一起使用的物件。

### <a name="example"></a>範例

```cpp
// cliext_set_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(Myset::make_value(L'a'));
    c1.insert(Myset::make_value(L'b'));
    c1.insert(Myset::make_value(L'c'));

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setoperator-stlclr"></a><a name="op_as"></a>設定::運算子* (STL/CLR)

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子*將右邊*複製到物件,`*this`然後傳回 。 使用它將受控序列替換為*右側*受控序列的副本。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="setrbegin-stlclr"></a><a name="rbegin"></a>設定:rbegin(STL/CLR)

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

成員函數返回一個反向反覆運算器,該反覆運算器指定受控序列的最後一個元素,或剛剛超出空序列的開頭。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_set_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    Myset::reverse_iterator rit = c1.rbegin();
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

## <a name="setreference-stlclr"></a><a name="reference"></a>設定:參考(STL/CLR)

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

類型描述對元素的引用。

### <a name="example"></a>範例

```cpp
// cliext_set_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setrend-stlclr"></a><a name="rend"></a>設定:rend (STL/CLR)

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

成員函數返回一個反向反覆運算器,該反覆運算器的點位於受控序列的開頭之外。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_set_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::reverse_iterator rit = c1.rend();
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

## <a name="setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>設定:reverse_iterator(STL/CLR)

受控制序列的反向迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// cliext_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="setset-stlclr"></a><a name="set"></a>設定:設定(STL/CLR)

建構容器物件。

### <a name="syntax"></a>語法

```cpp
set();
explicit set(key_compare^ pred);
set(set<Key>% right);
set(set<Key>^ right);
template<typename InIter>
    setset(InIter first, InIter last);
template<typename InIter>
    set(InIter first, InIter last,
        key_compare^ pred);
set(System::Collections::Generic::IEnumerable<GValue>^ right);
set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>參數

*第一*<br/>
要插入的範圍的開始。

*最後*<br/>
要插入的範圍結束。

*Pred*<br/>
對受控序列的謂詞進行排序。

*對*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

建構函數:

`set();`

初始化沒有元素的受控序列,預設排序謂詞`key_compare()`。 使用它指定一個空的初始控制序列,使用預設排序謂詞。

建構函數:

`explicit set(key_compare^ pred);`

初始化沒有元素的受控序列,順序謂字*預置*。 使用它指定一個空的初始控制序列,以及指定的排序謂詞。

建構函數:

`set(set<Key>% right);`

使用預設排序謂詞使用序列`right.begin()`*`right.end()`初始 化受控序列。 使用它指定初始受控序列,該序列是設置物件*右側*控制序列的副本,具有預設排序謂詞。

建構函數:

`set(set<Key>^ right);`

使用預設排序謂詞使用序列`right->begin()`*`right->end()`初始 化受控序列。 使用它指定初始受控序列,該序列是設置物件*右側*控制序列的副本,具有預設排序謂詞。

建構函數:

`template<typename InIter> set(InIter first, InIter last);`

使用預設排序謂詞使用序列`first`*`last`初始 化受控序列。 使用它使受控序列成為另一個序列的副本,預設排序謂詞。

建構函數:

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

使用序列 # 初始化受`first`控`last`序 , 使用排序的預設 *。* 使用它使受控序列成為另一個序列的副本,並帶有指定的排序謂詞。

建構函數:

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

使用枚舉器*右側*指定的序列初始化受控序列,使用預設排序謂詞。 使用它使受控序列成為枚舉器描述的另一個序列的副本,並帶有預設排序謂詞。

建構函數:

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

使用枚舉器*右方*指定的序列初始化受控序列,並*預用*排序謂詞 。 使用它使受控序列成為枚舉器描述的另一個序列的副本,並帶有指定的排序謂詞。

### <a name="example"></a>範例

```cpp
// cliext_set_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
// construct an empty container
    Myset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an ordering rule
    Myset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    Myset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range and an ordering rule
    Myset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    Myset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration and an ordering rule
    Myset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct from a generic container
    Myset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myset c8(%c3);
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

## <a name="setsize-stlclr"></a><a name="size"></a>設定:大小(STL/CLR)

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 使用它來確定當前受控序列中的元素數。 如果您關心的只是序列是否具有非零大小,請參閱[設置:空 (STL/CLR)。](../dotnet/set-empty-stl-clr.md) `()`

### <a name="example"></a>範例

```cpp
// cliext_set_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setsize_type-stlclr"></a><a name="size_type"></a>設定:size_type(STL/CLR)

兩個元素之間的簽名距離的類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

類型描述非負元素計數。

### <a name="example"></a>範例

```cpp
// cliext_set_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::size_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="setswap-stlclr"></a><a name="swap"></a>集::交換(STL/CLR)

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函數交換*和*之間的`this`受控序列。 它在恆定時間內這樣做,並且不會引發任何異常。 使用它作為交換兩個容器內容的快速方法。

### <a name="example"></a>範例

```cpp
// cliext_set_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    Myset c2;
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

## <a name="setto_array-stlclr"></a><a name="to_array"></a>設定:to_array (STL/ CLR)

將受控序列複製到新陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>備註

成員函數返回包含受控序列的陣列。 使用它以陣列形式獲取受控序列的副本。

### <a name="example"></a>範例

```cpp
// cliext_set_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setupper_bound-stlclr"></a><a name="upper_bound"></a>設定::upper_bound(STL/CLR)

尋找與指定鍵匹配的範圍的末尾。

### <a name="syntax"></a>語法

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函數確定受控序列中與`X`*鍵*具有等效排序的最後一個元素。 如果不存在此類元素,或者`X`是受控序列中的最後一個元素,則返回[集::end (STL/CLR);](../dotnet/set-end-stl-clr.md) `()`否則,它將返回一個反覆運算器,該反覆運算器指定超出`X`的第一個元素。 使用它來定位當前在受控序列中匹配指定鍵的元素序列的末尾。

### <a name="example"></a>範例

```cpp
// cliext_set_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
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

## <a name="setvalue_comp-stlclr"></a><a name="value_comp"></a>設定::value_comp(STL/CLR)

複製兩個元素值的排序委託。

### <a name="syntax"></a>語法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>備註

成員函數返回用於排序受控序列的排序委託。 使用它比較兩個元素值。

### <a name="example"></a>範例

```cpp
// cliext_set_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

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

## <a name="setvalue_compare-stlclr"></a><a name="value_compare"></a>集::value_compare(STL/CLR)

兩個元素值的排序委託。

### <a name="syntax"></a>語法

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>備註

類型是委託的同義詞,用於確定其值參數的順序。

### <a name="example"></a>範例

```cpp
// cliext_set_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

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

## <a name="setvalue_type-stlclr"></a><a name="value_type"></a>集::value_type(STL/CLR)

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>備註

這個類型與 `generic_value`同義。

### <a name="example"></a>範例

```cpp
// cliext_set_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using value_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-set-stlclr"></a><a name="op_neq"></a>運算元!*(設置)(STL/CLR)

列出不相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函數傳回`!(left == right)`。 使用它來測試在按元素比較兩個集時 *,左的*排序是否與*右側*相同。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorlt-set-stlclr"></a><a name="op_lt"></a>運算子&lt;(設定)(STL/CLR)

清單小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

如果 對於最低`i``!(right[i] < left[i])`位置 ,運算子傳回`left[i] < right[i]`true, 如果 。 否則,它返回`left->size() < right->size()`「使用它」來測試在按元素比較兩個集之前是否*對**左側*進行排序。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorlt-set-stlclr"></a><a name="op_lteq"></a>運算子&lt;= (設定) (STL/CLR)

列出小於或相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函數傳回`!(right < left)`。 使用此項目測試在按元素比較兩個集時,*是否*未*在右後右*排序。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operator-set-stlclr"></a><a name="op_eq"></a>運算子* (設定) (STL/CLR)

列出相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

僅當*由左右*控制的順序長度*right*相同 且`i``left[i] ==``right[i]`每個位置 具有相同的長度時,運算符函數才會返回 true。 使用它來測試在按元素比較兩個集時 *,左的*排序是否與*右側*相同。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorgt-set-stlclr"></a><a name="op_gt"></a>運算子&gt;(設定)(STL/CLR)

清單大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函數傳回`right``<``left`。 使用它來測試在按元素比較兩個集時 *,左是否*按*右*順序排列。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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

## <a name="operatorgt-set-stlclr"></a><a name="op_gteq"></a>運算子&gt;= (設定) (STL/CLR)

列出大於或相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

運算子函數傳回`!(left < right)`。 使用它來測試在按元素比較兩個集之前是否未*對**左側*進行排序。

### <a name="example"></a>範例

```cpp
// cliext_set_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
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
