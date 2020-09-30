---
title: map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
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
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
ms.openlocfilehash: 31d696c1bf85cdcb1d662474042c82524abdfcf1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508592"
---
# <a name="map-stlclr"></a>map (STL/CLR)

此樣板類別描述一個物件，該物件可控制具有雙向存取之元素的不同長度序列。 您可以使用容器 `map` 來管理一連串的專案，做為 (近) 的節點數目，每個節點都會儲存一個元素。 專案是由索引鍵（用來排序序列）和對應值所組成。

在下列描述中，與 `GValue` 相同：

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

其中：

`GKey` 與索引 *鍵* 相同，除非後者是 ref 型別，在這種情況下，它是 `Key^`

`GMapped` 與 *對應* 相同，除非後者是 ref 型別，在這種情況下，它是 `Mapped^`

## <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    ref class map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>參數

*索引鍵*<br/>
受控制序列中項目的主要元件型別。

*映射*<br/>
受控制序列中元素的其他元件類型。

## <a name="requirements"></a>需求

**標頭：**\<cliext/map>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[map::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[map::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[map::difference_type (STL/CLR)](#difference_type)| (的類型可能簽署兩個專案之間的) 距離。|
|[map::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|
|[map::generic_iterator (STL/CLR)](#generic_iterator)|容器之泛型介面的反覆運算器類型。|
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面之反向反覆運算器的類型。|
|[map::generic_value (STL/CLR)](#generic_value)|容器之泛型介面的元素類型。|
|[map::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[map::key_compare (STL/CLR)](#key_compare)|兩個索引鍵的排序委派。|
|[map::key_type (STL/CLR)](#key_type)|排序索引鍵的類型。|
|[map::mapped_type (STL/CLR)](#mapped_type)|與每個索引鍵相關聯之對應值的型別。|
|[map::reference (STL/CLR)](#reference)|項目的參考類型。|
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[map::size_type (STL/CLR)](#size_type)|兩個元素之間 (非負) 距離的型別。|
|[map::value_compare (STL/CLR)](#value_compare)|兩個元素值的排序委派。|
|[map::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[map::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[map::clear (STL/CLR)](#clear)|移除所有項目。|
|[map::count (STL/CLR)](#count)|計算符合指定索引鍵的元素。|
|[map::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[map::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[map::equal_range (STL/CLR)](#equal_range)|尋找符合指定之索引鍵的範圍。|
|[map::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|
|[map::find (STL/CLR)](#find)|尋找符合指定之索引鍵的元素。|
|[map::insert (STL/CLR)](#insert)|加入項目。|
|[map::key_comp (STL/CLR)](#key_comp)|複製兩個索引鍵的排序委派。|
|[map::lower_bound (STL/CLR)](#lower_bound)|尋找符合指定索引鍵的範圍開頭。|
|[map::make_value (STL/CLR)](#make_value)|結構值物件。|
|[map::map (STL/CLR)](#map)|建構容器物件。|
|[map::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[map::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[map::size (STL/CLR)](#size)|計算元素的數目。|
|[map::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[map::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|
|[map::upper_bound (STL/CLR)](#upper_bound)|尋找符合指定索引鍵的範圍結尾。|
|[map::value_comp (STL/CLR)](#value_comp)|針對兩個元素值複製順序委派。|

|運算子|描述|
|--------------|-----------------|
|[map::operator= (STL/CLR)](#op_as)|取代受控制的序列。|
|[map::operator (STL/CLR)](#op)|將索引鍵對應至其相關聯的對應值。|
|[operator！ = (map)  (STL/CLR) ](#op_neq)|判斷物件是否 `map` 不等於另一個 `map` 物件。|
|[operator< (map)  (STL/CLR) ](#op_lt)|判斷 `map` 物件是否小於另一個 `map` 物件。|
|[operator<= (map) (STL/CLR)](#op_lteq)|判斷 `map` 物件是否小於或等於另一個 `map` 物件。|
|[operator = = (map)  (STL/CLR) ](#op_eq)|判斷 `map` 物件是否等於另一個 `map` 物件。|
|[operator> (map)  (STL/CLR) ](#op_gt)|判斷 `map` 物件是否大於另一個 `map` 物件。|
|[operator>= (map)  (STL/CLR) ](#op_gteq)|判斷 `map` 物件是否大於或等於另一個 `map` 物件。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|排序元素。|
|<xref:System.Collections.ICollection>|維護元素群組。|
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的元素排序。|
|<xref:System.Collections.Generic.ICollection%601>|維護具類型的元素群組。|
|<xref:System.Collections.Generic.IDictionary%602>|維護 {key，value} 組的群組。|
|ITree<索引鍵，值>|維護泛型容器。|

## <a name="remarks"></a>備註

物件會針對其控制為個別節點的序列，配置和釋出儲存體。 它會將元素插入 (近) 平衡的樹狀結構中，藉由變更節點之間的連結，而不是藉由將節點的內容複寫到另一個節點的方式來保持排序。 這表示您可以自由插入和移除專案，而不會干擾其餘的元素。

物件會藉由呼叫 map：： key_compare 類型的預存委派物件來排序它所控制的序列， [ (STL/CLR) ](#key_compare)。 當您建立對應時，可以指定預存的委派物件。如果您未指定委派物件，預設值就是比較 `operator<(key_type, key_type)` 。 您可以藉由呼叫成員函式[map：： key_comp (STL/CLR) ](#key_comp)來存取這個儲存的物件 `()` 。

這類委派物件必須在類型 [map：： key_type (STL/CLR) ](#key_type)的索引鍵上強制執行嚴格弱式排序。 這表示，針對任何兩個金鑰， `X` 以及 `Y` ：

`key_comp()(X, Y)` 每次呼叫時，都會傳回相同的布林值結果。

如果 `key_comp()(X, Y)` 是 true，則 `key_comp()(Y, X)` 必須為 false。

如果 `key_comp()(X, Y)` 是 true，則 `X` 會被視為之前的排序 `Y` 。

如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 是 true，則 `X` 和 `Y` 也稱為具有對等的排序。

若為 `X` `Y` 受控制序列中的任何元素， `key_comp()(Y, X)` 則為 false。  (預設的委派物件，索引鍵的值永遠不會減少。 ) 與範本類別 [對應](../dotnet/map-stl-clr.md)不同，樣板類別的物件不需要所有專案的索引 `map` 鍵都是唯一的。  (兩個以上的索引鍵可以有對等的順序。 ) 

每個元素都包含個別的索引鍵和對應的值。 序列的表示方式，可讓您查閱、插入和移除具有許多作業的任意元素，並以序列中專案數目的對數為比例， (對數時間) 。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。

地圖支援雙向反覆運算器，這表示您可以逐步執行指定受控制序列中專案的反覆運算器，以逐步執行連續的元素。 特殊前端節點對應于[map：： end (STL/CLR) ](#end)所傳回的反覆運算器 `()` 。 您可以遞減此反覆運算器，以到達受控制序列中的最後一個元素（如果有的話）。 您可以將地圖反覆運算器遞增以連接到前端節點，然後比較是否等於 `end()` 。 但是，您無法取值傳回的反覆運算器 `end()` 。

請注意，您不能直接參考其數位位置（需要隨機存取反覆運算器）的對應元素。

地圖反覆運算器會將控制碼儲存至其相關聯的地圖節點，然後再將控制碼儲存至其相關聯的容器。 您只能使用反覆運算器與其相關聯的容器物件。 Map iterator 會維持有效，只要其相關聯的對應節點與某個對應相關聯。 此外，有效的 iterator 是 dereferencable--您可以使用它來存取或修改它所指定的元素值，只要它不等於就可以了 `end()` 。

清除或移除專案會呼叫其預存值的函式。 終結容器會清除所有元素。 因此，其元素類型為 ref 類別的容器可確保沒有任何專案存留時間容器。 不過請注意，控制碼的 *容器不會摧毀其* 元素。

## <a name="members"></a>成員

## <a name="mapbegin-stlclr"></a><a name="begin"></a> map：： begin (STL/CLR) 

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

成員函式會傳回雙向反覆運算器，其指定受控制序列的第一個專案，或空白序列結尾以外的第一個元素。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_map_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymap::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="mapclear-stlclr"></a><a name="clear"></a> map：： clear (STL/CLR) 

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函式會有效地呼叫[map：： erase (stl/clr) ](#erase) `(` [map：： begin (stl/clr) ](#begin) `(),` [map：： end (STL/clr) ](#end) `())` 。 您可以使用它來確保受控制的序列是空的。

### <a name="example"></a>範例

```cpp
// cliext_map_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="mapconst_iterator-stlclr"></a><a name="const_iterator"></a> map：： const_iterator (STL/CLR) 

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T2` ，可作為受控制序列的常數雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_map_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reference-stlclr"></a><a name="const_reference"></a> map：： const_reference (STL/CLR) 

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

型別描述元素的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_map_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> map：： const_reverse_iterator (STL/CLR) 

受控制序列的常數反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T4` ，可作為受控制序列的常數反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapcount-stlclr"></a><a name="count"></a> map：： count (STL/CLR) 

尋找符合指定索引鍵的項目數目。

### <a name="syntax"></a>語法

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回受控制序列中的專案數目，其具有與索引 *鍵*相等的排序。 您會用它來判斷目前在受控制序列中，符合指定之索引鍵的項目數目。

### <a name="example"></a>範例

```cpp
// cliext_map_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="mapdifference_type-stlclr"></a><a name="difference_type"></a> map：:d ifference_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能的負元素計數。

### <a name="example"></a>範例

```cpp
// cliext_map_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="mapempty-stlclr"></a><a name="empty"></a> map：： empty (STL/CLR) 

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[map：： size (STL/CLR) ](#size) `() == 0` 。 您可以使用它來測試地圖是否為空的。

### <a name="example"></a>範例

```cpp
// cliext_map_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="mapend-stlclr"></a><a name="end"></a> map：： end (STL/CLR) 

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

成員函式會傳回雙向反覆運算器，指向受控制序列的結尾以外的位置。 您可以使用它來取得反覆運算器，以指定受控制序列的結尾。如果受控制序列的長度變更，其狀態不會變更。

### <a name="example"></a>範例

```cpp
// cliext_map_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymap::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

## <a name="mapequal_range-stlclr"></a><a name="equal_range"></a> map：： equal_range (STL/CLR) 

尋找符合指定之索引鍵的範圍。

### <a name="syntax"></a>語法

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回一對反覆運算器 `cliext::pair<iterator, iterator>(` [map：： lower_bound (stl/clr) ](#lower_bound) `(key),` [map：： upper_bound (stl/clr) ](#upper_bound) `(key))` 。 您可以使用它來判斷目前在受控制序列中，符合指定索引鍵的元素範圍。

### <a name="example"></a>範例

```cpp
// cliext_map_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_iter Pairii;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="maperase-stlclr"></a><a name="erase"></a> map：： erase (STL/CLR) 

移除位於指定位置的項目。

### <a name="syntax"></a>語法

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>參數

*first*<br/>
要清除的範圍開頭。

*key*<br/>
要清除的索引鍵值。

*last*<br/>
要清除的範圍結尾。

*where*<br/>
要清除的元素。

### <a name="remarks"></a>備註

第一個成員函式會移除由*where*所指向之受控制序列的專案，並傳回反覆運算器，指定移除專案之後的第一個元素，或[map：： end (STL/CLR) ](#end) （ `()` 如果沒有這樣的元素的話）。 您可以使用它來移除單一專案。

第二個成員函式會移除範圍 [，) 中受控制序列的元素， `first` `last` 並傳回反覆運算器，此反覆運算器會指定移除任何專案之後剩餘的第一個元素，或 `end()` 如果沒有這類專案存在，則為。 您可以使用它來移除零個或多個連續元素。

第三個成員函式會移除其索引鍵對索引 *鍵*具有對等排序之受控制序列的任何元素，並傳回已移除的元素數目計數。 您可以使用它來移除和計算所有符合指定索引鍵的元素。

每個專案清除都會花費時間與受控制序列中專案數目的對數成正比。

### <a name="example"></a>範例

```cpp
// cliext_map_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    cliext::map<wchar_t, int> c1;
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="mapfind-stlclr"></a><a name="find"></a> map：： find (STL/CLR) 

尋找符合指定之索引鍵的元素。

### <a name="syntax"></a>語法

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

如果受控制序列中至少有一個專案具有與索引*鍵*相等的排序，則成員函式會傳回反覆運算器，指定其中一個元素;否則，它會傳回[map：： end (STL/CLR) ](#end) `()` 。 您可以使用它來找出目前在受控制序列中且符合指定索引鍵的元素。

### <a name="example"></a>範例

```cpp
// cliext_map_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymap::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="mapgeneric_container-stlclr"></a><a name="generic_container"></a> map：： generic_container (STL/CLR) 

容器的泛型介面型別。

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
// cliext_map_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymap::make_value(L'e', 5));
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="mapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> map：： generic_iterator (STL/CLR) 

反覆運算器的類型，用於容器的泛型介面。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>備註

此類型描述可搭配此樣板容器類別的泛型介面使用的泛型反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="mapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> map：： generic_reverse_iterator (STL/CLR) 

反向反覆運算器的類型，用於容器的泛型介面。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述可搭配此樣板容器類別的泛型介面使用的泛型反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="mapgeneric_value-stlclr"></a><a name="generic_value"></a> map：： generic_value (STL/CLR) 

要搭配容器的泛型介面使用的元素類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

型別描述型別的物件，此物件 `GValue` 描述與這個樣板容器類別的泛型介面搭配使用的預存專案值。

### <a name="example"></a>範例

```cpp
// cliext_map_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="mapinsert-stlclr"></a><a name="insert"></a> map：： insert (STL/CLR) 

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

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*對*<br/>
要插入的列舉。

*瓦爾*<br/>
要插入的索引鍵值。

*where*<br/>
在容器中插入 (提示僅) 。

### <a name="remarks"></a>備註

每個成員函式都會插入其餘運算元所指定的序列。

第一個成員函式會致力於插入具有值 *val*的元素，並傳回一對值 `X` 。 如果 `X.second` 為 true，會 `X.first` 指定新插入的專案，否則會 `X.first` 指定具有對等順序的專案，而該專案已存在，且不會插入新的元素。 您可以使用它來插入單一元素。

第二個成員函式會插入具有值 *val*的元素，並使用 *where* 作為提示 (來改善效能) ，並傳回反覆運算器，以指定新插入的元素。 您可以使用它來插入單一元素，這可能與您知道的元素相鄰。

第三個成員函式會將序列 [ `first` ， `last`) 插入。 您可以使用它來插入從另一個序列複製的零或多個元素。

第四個成員函式會插入 *右邊*指定的順序。 您可以使用它來插入列舉值所描述的序列。

每個插入的專案都需要時間與受控制序列中專案數目的對數成正比。 但是，如果指定的提示指定插入點連續的元素，則可能會在分攤的常數時間內進行插入。

### <a name="example"></a>範例

```cpp
// cliext_map_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_bool Pairib;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
// insert a single value, success and failure
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Mymap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Mymap::iterator it =
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymap::value_type>^)%c1);
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [[x 24] True]
insert([L'b' 2]) = [[b 2] False]
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="mapiterator-stlclr"></a><a name="iterator"></a> map：： iterator (STL/CLR) 

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T1` ，可作為受控制序列的雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_map_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapkey_comp-stlclr"></a><a name="key_comp"></a> map：： key_comp (STL/CLR) 

複製兩個索引鍵的排序委派。

### <a name="syntax"></a>語法

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>備註

成員函式會傳回排序委派，用來排序受控制的序列。 您會用它來比較兩個索引鍵。

### <a name="example"></a>範例

```cpp
// cliext_map_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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

## <a name="mapkey_compare-stlclr"></a><a name="key_compare"></a> map：： key_compare (STL/CLR) 

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
// cliext_map_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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

## <a name="mapkey_type-stlclr"></a><a name="key_type"></a> map：： key_type (STL/CLR) 

排序索引鍵的類型。

### <a name="syntax"></a>語法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數索引 *鍵*的同義字。

### <a name="example"></a>範例

```cpp
// cliext_map_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="maplower_bound-stlclr"></a><a name="lower_bound"></a> map：： lower_bound (STL/CLR) 

尋找符合指定索引鍵的範圍開頭。

### <a name="syntax"></a>語法

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會決定受控制序列中的第一個專案，其對索引 `X` *鍵*具有對等的排序。 如果沒有這類元素，則會傳回[map：： end (STL/CLR) ](#end) `()` ; 否則會傳回指定的 iterator `X` 。 您可以使用它來找出目前在受控制序列中，符合指定索引鍵的一連串元素。

### <a name="example"></a>範例

```cpp
// cliext_map_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymap::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="mapmake_value-stlclr"></a><a name="make_value"></a> map：： make_value (STL/CLR) 

結構值物件。

### <a name="syntax"></a>語法

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>參數

*key*<br/>
要使用的索引鍵值。

*已對應*<br/>
要搜尋的對應值。

### <a name="remarks"></a>備註

成員函式會傳回 `value_type` 其索引鍵為 *索引鍵* 且對應值為 *對應*的物件。 您可以使用它來撰寫一個適合與其他數個成員函式搭配使用的物件。

### <a name="example"></a>範例

```cpp
// cliext_map_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapmap-stlclr"></a><a name="map"></a> map：： map (STL/CLR) 

建構容器物件。

### <a name="syntax"></a>語法

```cpp
map();
explicit map(key_compare^ pred);
map(map<Key, Mapped>% right);
map(map<Key, Mapped>^ right);
template<typename InIter>
    mapmap(InIter first, InIter last);
template<typename InIter>
    map(InIter first, InIter last,
        key_compare^ pred);
map(System::Collections::Generic::IEnumerable<GValue>^ right);
map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>參數

*first*<br/>
要插入的範圍開頭。

*last*<br/>
要插入的範圍結尾。

*Pred*<br/>
受控制序列的順序述詞。

*對*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

函數：

`map();`

使用預設順序述詞，初始化沒有元素的受控制序列 `key_compare()` 。 您可以使用它來指定空的初始受控制序列，以及預設順序述詞。

函數：

`explicit map(key_compare^ pred);`

使用順序述詞 *pred*，初始化沒有元素的受控制序列。 您可以使用它來指定空的初始受控制序列，以及指定的順序述詞。

函數：

`map(map<Key, Mapped>% right);`

使用順序 [ `right.begin()` ， `right.end()`) ，以預設順序述詞初始化受控制的序列。 您可以使用它來指定初始受控制序列，這是由 map 物件 *許可權*所控制之序列的複本，以及預設順序述詞。

函數：

`map(map<Key, Mapped>^ right);`

使用順序 [ `right->begin()` ， `right->end()`) ，以預設順序述詞初始化受控制的序列。 您可以使用它來指定初始受控制序列，這是由 map 物件 *許可權*所控制之序列的複本，以及預設順序述詞。

函數：

`template<typename InIter> map(InIter first, InIter last);`

使用順序 [ `first` ， `last`) ，以預設順序述詞初始化受控制的序列。 您可以使用它，以預設順序述詞，讓受控制的序列成為另一個序列的複本。

函數：

`template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`

使用序列 [ `first` ， `last`) ，以順序述詞 *pred*初始化受控制的序列。 您可以使用它，利用指定的順序述詞，讓受控制的序列成為另一個序列的複本。

函數：

`map(System::Collections::Generic::IEnumerable<Key>^ right);`

以列舉值 *右邊*指定的順序，使用預設順序述詞，初始化受控制的序列。 您可以使用它來讓受控制的序列成為列舉值所描述之另一個順序的複本，以及預設順序述詞。

函數：

`map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

使用由列舉值 *右邊*指定的序列，並搭配順序述詞 *pred*，初始化受控制的序列。 您可以使用它，透過指定的順序述詞，讓受控制的序列成為列舉值所描述之另一個序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_map_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
// construct an empty container
    Mymap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymap c3(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3);
    for each (Mymap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymap c7(c4);
    for each (Mymap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymap c8(%c3);
    for each (Mymap::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
```

## <a name="mapmapped_type-stlclr"></a><a name="mapped_type"></a> map：： mapped_type (STL/CLR) 

與每個索引鍵關聯的對應值類型。

### <a name="syntax"></a>語法

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>備註

此類型與 *對應*的範本參數同義。

### <a name="example"></a>範例

```cpp
// cliext_map_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="mapoperator-stlclr"></a><a name="op_as"></a> map：： operator = (STL/CLR) 

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
map<Key, Mapped>% operator=(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子會將 *右移* 至物件，然後傳回 **`*this`** 。 您可以使用它，將受控制序列取代為 *right*中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2 = c1;
    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="mapoperatorstlclr"></a><a name="op"></a> map：： operator (STL/CLR) 

將索引鍵對應至其相關聯的對應值。

### <a name="syntax"></a>語法

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會致力於尋找對索引 *鍵*具有對等排序的元素。 如果找到一個，就會傳回相關聯的對應值;否則，它會插入 `value_type(key, mapped_type())` 並傳回關聯的 (預設) 對應值。 您可以使用它來查詢對應的值，並指定其相關聯的索引鍵，或者，如果找不到任何索引鍵，則確定該索引鍵的專案是否存在。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_sub.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[A 0] [a 1] [b 2] [c 3]
[A 10] [a 1] [b 2] [c 13]
```

## <a name="maprbegin-stlclr"></a><a name="rbegin"></a> map：： rbegin (STL/CLR) 

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

成員函式會傳回反向反覆運算器，此反覆運算器會指定受控制序列的最後一個專案，或在空白序列的開頭之外。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_map_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="mapreference-stlclr"></a><a name="reference"></a> map：： reference (STL/CLR) 

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

型別描述對元素的參考。

### <a name="example"></a>範例

```cpp
// cliext_map_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="maprend-stlclr"></a><a name="rend"></a> map：： rend (STL/CLR) 

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

成員函式會傳回指向受控制序列開頭以外的反向反覆運算器。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_map_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="mapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> map：： reverse_iterator (STL/CLR) 

受控制序列的反向迭代器類型。

### <a name="syntax"></a>語法

```
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// cliext_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapsize-stlclr"></a><a name="size"></a> map：： size (STL/CLR) 

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[map：： empty (STL/CLR) ](#empty) `()` 。

### <a name="example"></a>範例

```cpp
// cliext_map_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymap::make_value(L'd', 4));
    c1.insert(Mymap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="mapsize_type-stlclr"></a><a name="size_type"></a> map：： size_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

型別描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_map_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::size_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="mapswap-stlclr"></a><a name="swap"></a> map：： swap (STL/CLR) 

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函式會交換和右邊的受控制序列 **`this`** 。 *right* 它會以常數時間來執行，且不會擲回任何例外狀況。 您可以使用它來快速交換兩個容器的內容。

### <a name="example"></a>範例

```cpp
// cliext_map_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymap c2;
    c2.insert(Mymap::make_value(L'd', 4));
    c2.insert(Mymap::make_value(L'e', 5));
    c2.insert(Mymap::make_value(L'f', 6));
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="mapto_array-stlclr"></a><a name="to_array"></a> map：： to_array (STL/CLR) 

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>備註

成員函式會傳回陣列，其中包含受控制的序列。 您可以使用它，以陣列形式取得受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_map_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="mapupper_bound-stlclr"></a><a name="upper_bound"></a> map：： upper_bound (STL/CLR) 

尋找符合指定索引鍵的範圍結尾。

### <a name="syntax"></a>語法

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會決定受控制序列中的最後一個專案，其對索引 `X` *鍵*具有對等的順序。 如果不存在這類專案，或 `X` 為受控制序列中的最後一個專案，則會傳回[map：： END (STL/CLR) ](#end) `()` ; 否則會傳回指定第一個元素的反覆運算器 `X` 。 您可以使用它來找出目前在受控制序列中，符合指定索引鍵的專案序列結尾。

### <a name="example"></a>範例

```cpp
// cliext_map_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymap::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="mapvalue_comp-stlclr"></a><a name="value_comp"></a> map：： value_comp (STL/CLR) 

針對兩個元素值複製順序委派。

### <a name="syntax"></a>語法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>備註

成員函式會傳回排序委派，用來排序受控制的序列。 您可以使用它來比較兩個元素值。

### <a name="example"></a>範例

```cpp
// cliext_map_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_compare-stlclr"></a><a name="value_compare"></a> map：： value_compare (STL/CLR) 

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
// cliext_map_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_type-stlclr"></a><a name="value_type"></a> map：： value_type (STL/CLR) 

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>備註

這個類型與 `generic_value`同義。

### <a name="example"></a>範例

```cpp
// cliext_map_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="operator-map-stlclr"></a><a name="op_neq"></a> operator！ = (map)  (STL/CLR) 

清單不等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left == right)` 。 您可以使用它來測試當兩個地圖依元素進行比較時， *左邊* 是否未以 *正確* 的順序排序。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-map-stlclr"></a><a name="op_lt"></a> operator &lt; (map)  (STL/CLR) 

清單小於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

如果是，運算子函式會傳回 true，如果是，則對 `i` `!(right[i] < left[i])` 而言也是 true `left[i] < right[i]` 。 否則，它會傳回 `left->size() < right->size()` 您使用它來測試當兩個地圖*right*是依元素進行比較時，是否要將*左方*排序。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-map-stlclr"></a><a name="op_lteq"></a> operator &lt; = (map)  (STL/CLR) 

清單小於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(right < left)` 。 您可以使用它來測試當兩個地圖是依專案進行*比較時，* 是否不會排序*左*。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-map-stlclr"></a><a name="op_eq"></a> operator = = (map)  (STL/CLR) 

列出相等的比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

只有在由左至右控制的*序列和每*個位置都有相同的長度和時，運算子函*式*才會傳回 true `i` `left[i] ==` `right[i]` 。 您可以使用它來測試當兩個地圖依元素進行比較時， *左邊* 是否 *以相同的* 順序排序。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-map-stlclr"></a><a name="op_gt"></a> operator &gt; (map)  (STL/CLR) 

清單大於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `right` `<` `left` 。 您可以使用它來測試當兩個地圖依元素進行*比較時，* 是否要將*左方*排序。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-map-stlclr"></a><a name="op_gteq"></a> operator &gt; = (map)  (STL/CLR) 

列出大於或等於比較。

### <a name="syntax"></a>語法

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>參數

*離開*<br/>
要比較的左容器。

*對*<br/>
要比較的右容器。

### <a name="remarks"></a>備註

Operator 函數會傳回 `!(left` `<` `right)` 。 您可以使用它來測試當兩個地圖是依專案進行比較時，是否要將 *left* 排在 *右邊* 。

### <a name="example"></a>範例

```cpp
// cliext_map_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
