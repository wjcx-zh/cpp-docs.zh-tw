---
title: hash_multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
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
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
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
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
ms.openlocfilehash: b5aae5830437309e95f808567a2d3a7ea093c8f8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507161"
---
# <a name="hash_multiset-stlclr"></a>hash_multiset (STL/CLR)

此樣板類別描述一個物件，該物件可控制具有雙向存取之元素的不同長度序列。 您可以使用容器 `hash_multiset` 來管理一連串的專案做為雜湊表、每個資料表專案儲存雙向連結的節點清單，以及每個節點儲存一個元素。 每個元素的值會用來做為排序次序的索引鍵。

在下列描述中，與 `GValue` 相同 `GKey` ，除非後者是 ref 型別，否則它就會與索引 *鍵* 相同，在這種情況下，則為 `Key^` 。

## <a name="syntax"></a>語法

```cpp
template<typename Key>
    ref class hash_multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>參數

*索引鍵*<br/>
受控制序列中項目的主要元件型別。

## <a name="requirements"></a>需求

**標頭：**\<cliext/hash_set>

**命名空間：** cliext

## <a name="declarations"></a>宣告

|類型定義|描述|
|---------------------|-----------------|
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|
|[hash_multiset::difference_type (STL/CLR)](#difference_type)| (的類型可能簽署兩個專案之間的) 距離。|
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|容器之泛型介面的反覆運算器類型。|
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面之反向反覆運算器的類型。|
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|容器之泛型介面的元素類型。|
|[hash_multiset::hasher (STL/CLR)](#hasher)|索引鍵的雜湊委派。|
|[hash_multiset::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|兩個索引鍵的排序委派。|
|[hash_multiset::key_type (STL/CLR)](#key_type)|排序索引鍵的類型。|
|[hash_multiset::reference (STL/CLR)](#reference)|項目的參考類型。|
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|
|[hash_multiset::size_type (STL/CLR)](#size_type)|兩個元素之間 (非負) 距離的型別。|
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|兩個元素值的排序委派。|
|[hash_multiset::value_type (STL/CLR)](#value_type)|項目的類型。|

|成員函式|描述|
|---------------------|-----------------|
|[hash_multiset::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|計算值區的數目。|
|[hash_multiset::clear (STL/CLR)](#clear)|移除所有項目。|
|[hash_multiset::count (STL/CLR)](#count)|計算符合指定索引鍵的元素。|
|[hash_multiset::empty (STL/CLR)](#empty)|測試項目是否不存在。|
|[hash_multiset::end (STL/CLR)](#end)|指定受控制序列的結尾。|
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|尋找符合指定之索引鍵的範圍。|
|[hash_multiset::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|
|[hash_multiset::find (STL/CLR)](#find)|尋找符合指定之索引鍵的元素。|
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|複製索引鍵的雜湊委派。|
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|建構容器物件。|
|[hash_multiset::insert (STL/CLR)](#insert)|加入項目。|
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|複製兩個索引鍵的排序委派。|
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|計算每個值區的平均項目數。|
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|尋找符合指定索引鍵的範圍開頭。|
|[hash_multiset::make_value (STL/CLR)](#make_value)|結構值物件。|
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|取得或設定每個 Bucket 最大項目數。|
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|
|[hash_multiset::rehash (STL/CLR)](#rehash)|重建雜湊資料表。|
|[hash_multiset::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|
|[hash_multiset::size (STL/CLR)](#size)|計算元素的數目。|
|[hash_multiset::swap (STL/CLR)](#swap)|交換兩個容器的內容。|
|[hash_multiset::to_array (STL/CLR)](#to_array)|將受控制序列複製到新的陣列。|
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|尋找符合指定索引鍵的範圍結尾。|
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|針對兩個元素值複製順序委派。|

|運算子|描述|
|--------------|-----------------|
|[hash_multiset::operator= (STL/CLR)](#op)|取代受控制的序列。|

## <a name="interfaces"></a>介面

|介面|描述|
|---------------|-----------------|
|<xref:System.ICloneable>|複製物件。|
|<xref:System.Collections.IEnumerable>|排序元素。|
|<xref:System.Collections.ICollection>|維護元素群組。|
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的元素排序。|
|<xref:System.Collections.Generic.ICollection%601>|維護具類型的元素群組。|
|IHash\<Key, Value>|維護泛型容器。|

## <a name="remarks"></a>備註

物件會在雙向連結清單中，配置並釋放它所控制之序列的儲存體，以作為個別節點。 為了加速存取，物件也會在雜湊表) 的清單中維護不同長度的指標陣列， (雜湊表，有效地將整個清單視為清單子或值區的序列來管理。 它會藉由變更節點之間的連結，而不是藉由將節點的內容複寫到另一個節點的方式，將專案插入至值區，以保持排序。 這表示您可以自由插入和移除專案，而不會干擾其餘的元素。

物件會藉由呼叫 hash_set：： key_compare 類型的預存委派物件來排序每個值區， [ (STL/CLR) ](./hash-set-stl-clr.md#key_compare)。 當您建立 hash_set 時，可以指定預存的委派物件。如果您未指定委派物件，預設值就是比較 `operator<=(key_type, key_type)` 。

您可以藉由呼叫成員函式[hash_set：： key_comp (STL/CLR) ](./hash-set-stl-clr.md#key_comp)來存取儲存的委派物件 `()` 。 這類委派物件必須在 [hash_set：： key_type (STL/CLR) ](./hash-set-stl-clr.md#key_type)類型的索引鍵之間定義對等順序。 這表示，針對任何兩個金鑰， `X` 以及 `Y` ：

`key_comp()(X, Y)` 每次呼叫時，都會傳回相同的布林值結果。

如果 `key_comp()(X, Y) && key_comp()(Y, X)` 是 true，則 `X` 和 `Y` 也稱為具有對等的排序。

任何行為類似 `operator<=(key_type, key_type)` `operator>=(key_type, key_type)` 或 `operator==(key_type, key_type)` 定義 eqivalent 順序的排序規則。

請注意，容器只會確保其索引鍵具有對等順序的專案 (，以及相同整數值) 的雜湊在值區中相鄰。 不同于樣板類別 [hash_set (STL/CLR) ](../dotnet/hash-set-stl-clr.md)，範本類別的物件不 `hash_multiset` 需要所有元素的索引鍵都是唯一的。  (兩個以上的索引鍵可以有對等的順序。 ) 

物件會藉由呼叫 [hash_set：： hasher (STL/CLR) ](./hash-set-stl-clr.md#hasher)類型的預存委派物件，判斷哪些值區應包含指定的排序索引鍵。 您可以藉由呼叫成員函式[hash_set：： hash_delegate (STL/CLR) ](./hash-set-stl-clr.md#hash_delegate) `()` 取得相依于索引鍵值的整數值，來存取這個儲存的物件。 當您建立 hash_set 時，可以指定預存的委派物件。如果您未指定委派物件，則預設值為函數 `System::Object::hash_value(key_type)` 。 這表示對於任何金鑰 `X` 和 `Y` ：

`hash_delegate()(X)` 每次呼叫時，都會傳回相同的整數結果。

如果 `X` 和 `Y` 具有對等順序，則應該傳回與 `hash_delegate()(X)` 相同的整數結果 `hash_delegate()(Y)` 。

每個元素都可作為索引鍵和值。 順序的表示方式，可讓您查閱、插入和移除任意專案，而這些作業與序列中的專案數目無關， (常數時間) --至少在案例中的最大值。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。

但是，如果雜湊值未一致地散發，雜湊表就可以進行退化。 在最極端的情況下，雜湊函數一律會傳回相同的值（查閱、插入和移除），與序列中的專案數目成正比 (線性時間) 。 容器會致力於選擇合理的雜湊函式、平均值區大小，以及雜湊表大小 (值區的總數) ，但您可以覆寫任何或所有的選項。 例如，請參閱函式 [hash_set：： max_load_factor (stl/clr) ](./hash-set-stl-clr.md#max_load_factor) 和 [hash_set：： rehash (stl/clr) ](./hash-set-stl-clr.md#rehash)。

Hash_multiset 支援雙向反覆運算器，這表示您可以使用反覆運算器逐步執行連續的元素，以指定受控制序列中的元素。 特殊的前端節點對應至[hash_multiset：： end (STL/CLR) ](#end)所傳回的反覆運算器 `()` 。 您可以遞減此反覆運算器，以到達受控制序列中的最後一個元素（如果有的話）。 您可以將 hash_multiset 反覆運算器遞增以到達前端節點，然後再比較是否等於 `end()` 。 但是，您無法取值傳回的反覆運算器 `end()` 。

請注意，您不能直接參考指定其數位位置的 hash_multiset 專案，這需要隨機存取反覆運算器。

Hash_multiset 反覆運算器會將控制碼儲存至其相關聯的 hash_multiset 節點，然後再將控制碼儲存至其相關聯的容器。 您只能使用反覆運算器與其相關聯的容器物件。 Hash_multiset 反覆運算器會維持有效，只要其相關聯的 hash_multiset 節點與某些 hash_multiset 相關聯。 此外，有效的 iterator 是 dereferencable--您可以使用它來存取或修改它所指定的元素值，只要它不等於就可以了 `end()` 。

清除或移除專案會呼叫其預存值的函式。 終結容器會清除所有元素。 因此，其元素類型為 ref 類別的容器可確保沒有任何專案存留時間容器。 不過請注意，控制碼的 *容器不會摧毀其* 元素。

## <a name="members"></a>成員

## <a name="hash_multisetbegin-stlclr"></a><a name="begin"></a> hash_multiset：： begin (STL/CLR) 

指定受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
iterator begin();
```

### <a name="remarks"></a>備註

成員函式會傳回雙向反覆運算器，其指定受控制序列的第一個專案，或空白序列結尾以外的第一個元素。 您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::iterator it = c1.begin();
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

## <a name="hash_multisetbucket_count-stlclr"></a><a name="bucket_count"></a> hash_multiset：： bucket_count (STL/CLR) 

計算值區的數目。

### <a name="syntax"></a>語法

```cpp
int bucket_count();
```

### <a name="remarks"></a>備註

成員函式會傳回目前的 bucket 數目。 您可以使用它來判斷雜湊表的大小。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetclear-stlclr"></a><a name="clear"></a> hash_multiset：： clear (STL/CLR) 

移除所有項目。

### <a name="syntax"></a>語法

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函式會有效地呼叫[hash_multiset：： erase (stl/clr) ](#erase) `(` [hash_multiset：： begin (stl/clr) ](#begin) `(),` [hash_multiset：： end (stl/clr) ](#end) `())` 。 您可以使用它來確保受控制的序列是空的。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetconst_iterator-stlclr"></a><a name="const_iterator"></a> hash_multiset：： const_iterator (STL/CLR) 

用於受控制序列的常數迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T2` ，可作為受控制序列的常數雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetconst_reference-stlclr"></a><a name="const_reference"></a> hash_multiset：： const_reference (STL/CLR) 

項目的常數參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>備註

型別描述元素的常數參考。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_multiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> hash_multiset：： const_reverse_iterator (STL/CLR) 

受控制序列的常數反向反覆運算器類型。

### <a name="syntax"></a>語法

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T4` ，可作為受控制序列的常數反向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_multisetcount-stlclr"></a><a name="count"></a> hash_multiset：： count (STL/CLR) 

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
// cliext_hash_multiset_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetdifference_type-stlclr"></a><a name="difference_type"></a> hash_multiset：:d ifference_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>備註

此類型描述可能的負元素計數。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::difference_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="hash_multisetempty-stlclr"></a><a name="empty"></a> hash_multiset：： empty (STL/CLR) 

測試項目是否不存在。

### <a name="syntax"></a>語法

```cpp
bool empty();
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。 它相當於[hash_multiset：： size (STL/CLR) ](#size) `() == 0` 。 您可以使用它來測試 hash_multiset 是否為空白。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetend-stlclr"></a><a name="end"></a> hash_multiset：： end (STL/CLR) 

指定受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
iterator end();
```

### <a name="remarks"></a>備註

成員函式會傳回雙向反覆運算器，指向受控制序列的結尾以外的位置。 您可以使用它來取得反覆運算器，以指定受控制序列的結尾。如果受控制序列的長度變更，其狀態不會變更。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_multiset::iterator it = c1.end();
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

## <a name="hash_multisetequal_range-stlclr"></a><a name="equal_range"></a> hash_multiset：： equal_range (STL/CLR) 

尋找符合指定之索引鍵的範圍。

### <a name="syntax"></a>語法

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回一對反覆運算器 `cliext::pair<iterator, iterator>(` [hash_multiset：： lower_bound (stl/clr) ](#lower_bound) `(key),` [hash_multiset：： upper_bound (stl/clr) ](#upper_bound) `(key))` 。 您可以使用它來判斷目前在受控制序列中，符合指定索引鍵的元素範圍。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
typedef Myhash_multiset::pair_iter_iter Pairii;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multiseterase-stlclr"></a><a name="erase"></a> hash_multiset：： erase (STL/CLR) 

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

第一個成員函式會移除由*where*所指向之受控制序列的元素，並傳回反覆運算器，指定移除專案之後的第一個元素，或[hash_multiset：： end (STL/CLR) ](#end) （ `()` 如果沒有這類專案存在）。 您可以使用它來移除單一專案。

第二個成員函式會移除範圍 [，) 中受控制序列的元素， `first` `last` 並傳回反覆運算器，此反覆運算器會指定移除任何專案之後剩餘的第一個元素，或 `end()` 如果沒有這類專案存在，則為。 您可以使用它來移除零個或多個連續元素。

第三個成員函式會移除其索引鍵對索引 *鍵*具有對等排序之受控制序列的任何元素，並傳回已移除的元素數目計數。 您可以使用它來移除和計算所有符合指定索引鍵的元素。

每個專案清除都會花費時間與受控制序列中專案數目的對數成正比。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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
    Myhash_multiset::iterator it = c1.end();
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

## <a name="hash_multisetfind-stlclr"></a><a name="find"></a> hash_multiset：： find (STL/CLR) 

尋找符合指定之索引鍵的元素。

### <a name="syntax"></a>語法

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

如果受控制序列中至少有一個專案具有與索引*鍵*相等的排序，則成員函式會傳回反覆運算器，指定其中一個元素;否則，它會傳回[hash_multiset：： end (STL/CLR) ](#end) `()` 。 您可以使用它來找出目前在受控制序列中且符合指定索引鍵的元素。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetgeneric_container-stlclr"></a><a name="generic_container"></a> hash_multiset：： generic_container (STL/CLR) 

容器的泛型介面型別。

### <a name="syntax"></a>語法

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>備註

此類型描述此範本容器類別的泛型介面。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
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

## <a name="hash_multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> hash_multiset：： generic_iterator (STL/CLR) 

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
// cliext_hash_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> hash_multiset：： generic_reverse_iterator (STL/CLR) 

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
// cliext_hash_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="hash_multisetgeneric_value-stlclr"></a><a name="generic_value"></a> hash_multiset：： generic_value (STL/CLR) 

要搭配容器的泛型介面使用的元素類型。

### <a name="syntax"></a>語法

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>備註

型別描述型別的物件，此物件 `GValue` 描述與這個樣板容器類別的泛型介面搭配使用的預存專案值。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_multisethash_delegate-stlclr"></a><a name="hash_delegate"></a> hash_multiset：： hash_delegate (STL/CLR) 

尋找符合指定之索引鍵的元素。

### <a name="syntax"></a>語法

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>備註

成員函式會傳回用來將索引鍵值轉換為整數的委派。 您可以使用它來雜湊索引鍵。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multisethash_multiset-stlclr"></a><a name="hash_multiset"></a> hash_multiset：： hash_multiset (STL/CLR) 

建構容器物件。

### <a name="syntax"></a>語法

```cpp
hash_multiset();
explicit hash_multiset(key_compare^ pred);
hash_multiset(key_compare^ pred, hasher^ hashfn);
hash_multiset(hash_multiset<Key>% right);
hash_multiset(hash_multiset<Key>^ right);
template<typename InIter>
    hash_multiset(InIter first, InIter last);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>參數

*first*<br/>
要插入的範圍開頭。

*hashfn*<br/>
將索引鍵對應至值區的雜湊函數。

*last*<br/>
要插入的範圍結尾。

*Pred*<br/>
受控制序列的順序述詞。

*對*<br/>
要插入的物件或範圍。

### <a name="remarks"></a>備註

函數：

`hash_multiset();`

使用預設的順序述詞 `key_compare()` 和預設雜湊函式，初始化受控制的序列，但不含任何元素。 您可以使用它來指定空的初始受控制序列，以及預設順序述詞和雜湊函數。

函數：

`explicit hash_multiset(key_compare^ pred);`

使用順序述詞 *pred*和預設雜湊函式，初始化受控制的序列，但不含任何元素。 您可以使用它來指定空的初始受控制序列，以及指定的順序述詞和預設雜湊函數。

函數：

`hash_multiset(key_compare^ pred, hasher^ hashfn);`

使用順序述詞 *pred*，以及雜湊函數 *hashfn*，初始化受控制的序列。 您可以使用它來指定空的初始受控制序列，以及指定的順序述詞和雜湊函數。

函數：

`hash_multiset(hash_multiset<Key>% right);`

使用序列 [ `right.begin()` 、 `right.end()`) 、預設排序述詞和預設雜湊函數，初始化受控制的序列。 您可以使用它來指定初始受控制序列，這是由 hash_multiset 物件 *許可權*所控制之序列的複本，以及預設排序述詞和雜湊函數。

函數：

`hash_multiset(hash_multiset<Key>^ right);`

使用序列 [ `right->begin()` 、 `right->end()`) 、預設排序述詞和預設雜湊函數，初始化受控制的序列。 您可以使用它來指定初始受控制序列，這是由 hash_multiset 物件 *許可權*所控制之序列的複本，以及預設排序述詞和雜湊函數。

函數：

`template<typename InIter> hash_multiset(InIter first, InIter last);`

使用序列 [ `first` 、 `last`) 、預設排序述詞和預設雜湊函數，初始化受控制的序列。 您可以使用它，將受控制的序列設為另一個序列的複本，並使用預設順序述詞和雜湊函數。

函數：

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`

使用) 順序述詞 `first` `last` *pred*和預設雜湊函數，初始化受控制的序列。 您可以使用它，以指定的順序述詞和預設雜湊函數，讓受控制的序列成為另一個序列的複本。

函數：

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

使用) 順序述詞 `first` `last` *pred*和雜湊函數 *hashfn*，初始化受控制的序列。 您可以使用它，以指定的順序述詞和雜湊函式，讓受控制的序列成為另一個序列的複本。

函數：

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

使用列舉值 *右邊*指定的序列、預設順序述詞和預設雜湊函數，初始化受控制的序列。 您可以使用它來讓受控制的序列成為列舉值所描述之另一個順序的複本，以及預設排序述詞和雜湊函數。

函數：

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

使用列舉值 *右邊*所指定的序列、順序述詞 *pred*和預設雜湊函數，初始化受控制的序列。 您可以使用它來讓受控制的序列成為列舉值所描述之另一個順序的複本，以及指定的順序述詞和預設雜湊函數。

函數：

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

使用列舉值 *右邊*所指定的序列、順序述詞 *pred*，以及雜湊函數 *hashfn*，初始化受控制的序列。 您可以使用它來讓受控制的序列成為列舉值所描述之另一個順序的複本，以及指定的順序述詞和雜湊函數。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
// construct an empty container
    Myhash_multiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_multiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_multiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_multiset c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_multiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_multiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_multiset c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_multiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_multiset c8(%c3);
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
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hash_multisethasher-stlclr"></a><a name="hasher"></a> hash_multiset：： hasher (STL/CLR) 

索引鍵的雜湊委派。

### <a name="syntax"></a>語法

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>備註

此類型說明將索引鍵值轉換為整數的委派。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multisetinsert-stlclr"></a><a name="insert"></a> hash_multiset：： insert (STL/CLR) 

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

*對*<br/>
要插入的列舉。

*瓦爾*<br/>
要插入的索引鍵值。

*where*<br/>
在容器中插入 (提示僅) 。

### <a name="remarks"></a>備註

每個成員函式都會插入其餘運算元所指定的序列。

第一個成員函式會插入具有值 *val*的元素，並傳回指定新插入之元素的反覆運算器。 您可以使用它來插入單一元素。

第二個成員函式會插入具有值 *val*的元素，並使用 *where* 作為提示 (來改善效能) ，並傳回反覆運算器，以指定新插入的元素。 您可以使用它來插入單一元素，這可能與您知道的元素相鄰。

第三個成員函式會將序列 [ `first` ， `last`) 插入。 您可以使用它來插入從另一個序列複製的零或多個元素。

第四個成員函式會插入 *右邊*指定的順序。 您可以使用它來插入列舉值所描述的序列。

每個插入的專案都需要時間與受控制序列中專案數目的對數成正比。 但是，如果指定的提示指定插入點連續的元素，則可能會在分攤的常數時間內進行插入。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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
    Myhash_multiset c2;
    Myhash_multiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_multiset c3;
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

## <a name="hash_multisetiterator-stlclr"></a><a name="iterator"></a> hash_multiset：： iterator (STL/CLR) 

受控制序列之迭代器的類型。

### <a name="syntax"></a>語法

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>備註

型別描述未指定類型的物件 `T1` ，可作為受控制序列的雙向反覆運算器。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetkey_comp-stlclr"></a><a name="key_comp"></a> hash_multiset：： key_comp (STL/CLR) 

複製兩個索引鍵的排序委派。

### <a name="syntax"></a>語法

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>備註

成員函式會傳回排序委派，用來排序受控制的序列。 您會用它來比較兩個索引鍵。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_multisetkey_compare-stlclr"></a><a name="key_compare"></a> hash_multiset：： key_compare (STL/CLR) 

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
// cliext_hash_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_multisetkey_type-stlclr"></a><a name="key_type"></a> hash_multiset：： key_type (STL/CLR) 

排序索引鍵的類型。

### <a name="syntax"></a>語法

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數索引 *鍵*的同義字。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_multiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetload_factor-stlclr"></a><a name="load_factor"></a> hash_multiset：： load_factor (STL/CLR) 

計算每個值區的平均項目數。

### <a name="syntax"></a>語法

```cpp
float load_factor();
```

### <a name="remarks"></a>備註

成員函式會傳回 `(float)` [hash_multiset：： size (stl/clr) ](#size) `() /` [hash_multiset：： bucket_count (stl/clr) ](#count) `()` 。 您可以使用它來判斷平均 bucket 大小。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetlower_bound-stlclr"></a><a name="lower_bound"></a> hash_multiset：： lower_bound (STL/CLR) 

尋找符合指定索引鍵的範圍開頭。

### <a name="syntax"></a>語法

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會決定受控制序列中的第一個專案，此專案 `X` 會雜湊到與索引 *鍵* 相同的值區，並對索引 *鍵*具有對等的排序 如果沒有這類專案存在，則會傳回[hash_multiset：： end (STL/CLR) ](#end) `()` ; 否則會傳回指定的 iterator `X` 。 您可以使用它來找出目前在受控制序列中，符合指定索引鍵的一連串元素。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetmake_value-stlclr"></a><a name="make_value"></a> hash_multiset：： make_value (STL/CLR) 

結構值物件。

### <a name="syntax"></a>語法

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要使用的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回 `value_type` 其索引鍵為 *索引鍵的*物件。 您可以使用它來撰寫一個適合與其他數個成員函式搭配使用的物件。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(Myhash_multiset::make_value(L'a'));
    c1.insert(Myhash_multiset::make_value(L'b'));
    c1.insert(Myhash_multiset::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetmax_load_factor-stlclr"></a><a name="max_load_factor"></a> hash_multiset：： max_load_factor (STL/CLR) 

取得或設定每個 Bucket 最大項目數。

### <a name="syntax"></a>語法

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>參數

*new_factor*<br/>
要儲存的新最大載入因數。

### <a name="remarks"></a>備註

第一個成員函式會傳回目前儲存的最大載入因數。 您可以使用它來判斷平均 bucket 大小上限。

第二個成員函式會以 *new_factor*取代儲存區的最大載入因數。 在後續的插入之前，不會發生自動重新雜湊。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetoperator-stlclr"></a><a name="op"></a> hash_multiset：： operator = (STL/CLR) 

取代受控制的序列。

### <a name="syntax"></a>語法

```cpp
hash_multiset<Key>% operator=(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要複製的容器。

### <a name="remarks"></a>備註

成員運算子會將 *右移* 至物件，然後傳回 **`*this`** 。 您可以使用它，將受控制序列取代為 *right*中受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_multiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_multiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="hash_multisetrbegin-stlclr"></a><a name="rbegin"></a> hash_multiset：： rbegin (STL/CLR) 

指定反向受控制序列的開頭。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>備註

成員函式會傳回反向反覆運算器，此反覆運算器會指定受控制序列的最後一個專案，或在空白序列的開頭之外。 因此，它會指定反向序列的 `beginning`。 您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
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

## <a name="hash_multisetreference-stlclr"></a><a name="reference"></a> hash_multiset：： reference (STL/CLR) 

項目的參考類型。

### <a name="syntax"></a>語法

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>備註

型別描述對元素的參考。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_multiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetrehash-stlclr"></a><a name="rehash"></a> hash_multiset：： rehash (STL/CLR) 

重建雜湊資料表。

### <a name="syntax"></a>語法

```cpp
void rehash();
```

### <a name="remarks"></a>備註

成員函式會重建雜湊表，以確保[hash_multiset：： load_factor (stl/clr) ](#load_factor) `() <=` [hash_multiset：： max_load_factor (stl/clr) ](#max_load_factor)。 否則，雜湊表只會在插入之後視需要增加大小。  (不會自動縮減大小。 ) 您使用它來調整雜湊表的大小。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetrend-stlclr"></a><a name="rend"></a> hash_multiset：： rend (STL/CLR) 

指定反向受控制序列的結尾。

### <a name="syntax"></a>語法

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>備註

成員函式會傳回指向受控制序列開頭以外的反向反覆運算器。 因此，它會指定反向序列的 `end`。 您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::reverse_iterator rit = c1.rend();
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

## <a name="hash_multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> hash_multiset：： reverse_iterator (STL/CLR) 

受控制序列的反向迭代器類型。

### <a name="syntax"></a>語法

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>備註

此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_multisetsize-stlclr"></a><a name="size"></a> hash_multiset：： size (STL/CLR) 

計算元素的數目。

### <a name="syntax"></a>語法

```cpp
size_type size();
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的元素數目。 如果您只在意順序是否有非零的大小，請參閱[hash_multiset：： empty (STL/CLR) ](#empty) `()` 。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetsize_type-stlclr"></a><a name="size_type"></a> hash_multiset：： size_type (STL/CLR) 

兩個元素之間的帶正負號距離類型。

### <a name="syntax"></a>語法

```cpp
typedef int size_type;
```

### <a name="remarks"></a>備註

型別描述非負的元素計數。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::size_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="hash_multisetswap-stlclr"></a><a name="swap"></a> hash_multiset：： swap (STL/CLR) 

交換兩個容器的內容。

### <a name="syntax"></a>語法

```cpp
void swap(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>參數

*對*<br/>
要交換內容的容器。

### <a name="remarks"></a>備註

成員函式會交換和右邊的受控制序列 **`this`** 。 *right* 它會以常數時間來執行，且不會擲回任何例外狀況。 您可以使用它來快速交換兩個容器的內容。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_multiset c2;
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

## <a name="hash_multisetto_array-stlclr"></a><a name="to_array"></a> hash_multiset：： to_array (STL/CLR) 

將受控制序列複製到新的陣列。

### <a name="syntax"></a>語法

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>備註

成員函式會傳回陣列，其中包含受控制的序列。 您可以使用它，以陣列形式取得受控制序列的複本。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetupper_bound-stlclr"></a><a name="upper_bound"></a> hash_multiset：： upper_bound (STL/CLR) 

尋找符合指定索引鍵的範圍結尾。

### <a name="syntax"></a>語法

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會決定受控制序列中的最後一個專案，此專案 `X` 會雜湊到與索引 *鍵* 相同的值區，並對索引 *鍵*具有對等的排序 如果沒有這類專案，或 `X` 為受控制序列中的最後一個專案，則會傳回[hash_multiset：： END (STL/CLR) ](#end) `()` ; 否則會傳回反覆運算器，指定超過的第一個元素 `X` 。 您可以使用它來找出目前在受控制序列中，符合指定索引鍵的專案序列結尾。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetvalue_comp-stlclr"></a><a name="value_comp"></a> hash_multiset：： value_comp (STL/CLR) 

針對兩個元素值複製順序委派。

### <a name="syntax"></a>語法

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>備註

成員函式會傳回排序委派，用來排序受控制的序列。 您可以使用它來比較兩個元素值。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_multisetvalue_compare-stlclr"></a><a name="value_compare"></a> hash_multiset：： value_compare (STL/CLR) 

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
// cliext_hash_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_multisetvalue_type-stlclr"></a><a name="value_type"></a> hash_multiset：： value_type (STL/CLR) 

項目的類型。

### <a name="syntax"></a>語法

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>備註

這個類型與 `generic_value`同義。

### <a name="example"></a>範例

```cpp
// cliext_hash_multiset_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_multiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```
