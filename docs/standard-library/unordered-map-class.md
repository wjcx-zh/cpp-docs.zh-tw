---
title: unordered_map 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
dev_langs:
- C++
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f8f74a2aa1eb47d9de4705941bd7367e313e7bd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863065"
---
# <a name="unorderedmap-class"></a>unordered_map 類別

此樣板類別描述控制不同長度的 `std::pair<const Key, Ty>` 類型項目序列的物件。 序列由雜湊函式弱式排序，將序列分割為子序列的已排序集合，稱為 Bucket。 在每個 Bucket 中，比較函式判斷是否有任何一對項目具有對等順序。 每個項目儲存兩個物件：排序鍵和值。 序列表示允許以一些作業查閱、插入和移除任意項目，這些作業可以獨立於序列中的項目數目 (常數時間)，至少當所有 Bucket 長度大約相等時。 在最壞的情況下，當所有項目都在一個 Bucket 時，作業數目與序列中的項目數目成正比 (線性時間)。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。

## <a name="syntax"></a>語法

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`Key`|索引鍵類型。|
|`Ty`|對應的類型。|
|`Hash`|雜湊函式物件類型。|
|`Pred`|相等比較函式物件類型。|
|`Alloc`|配置器類別。|

## <a name="members"></a>成員

|類型定義|描述|
|-|-|
|[allocator_type](#allocator_type)|管理儲存體的配置器類型。|
|[const_iterator](#const_iterator)|用於受控制序列的常數迭代器類型。|
|[const_local_iterator](#const_local_iterator)|用於受控制序列的常數 Bucket 迭代器類型。|
|[const_pointer](#const_pointer)|項目的常數指標類型。|
|[const_reference](#const_reference)|項目的常數參考類型。|
|[difference_type](#difference_type)|兩個項目之間帶正負號距離的類型。|
|[hasher](#hasher)|雜湊函式的類型。|
|[iterator](#iterator)|受控制序列之迭代器的類型。|
|[key_equal](#key_equal)|比較函式的類型。|
|[key_type](#key_type)|排序索引鍵的類型。|
|[local_iterator](#local_iterator)|用於受控制序列的 Bucket 迭代器類型。|
|[mapped_type](#mapped_type)|與每個索引鍵關聯的對應值類型。|
|[pointer](#pointer)|項目的指標類型。|
|[reference](#reference)|項目的參考類型。|
|[size_type](#size_type)|兩個項目之間不帶正負號距離的類型。|
|[value_type](#value_type)|元素的類型。|

|成員函式|描述|
|-|-|
|[at](#at)|尋找具有指定之索引鍵的項目。|
|[begin](#begin)|指定受控制序列的開頭。|
|[bucket](#bucket)|取得索引鍵值的值區數目。|
|[bucket_count](#bucket_count)|取得 Bucket 的數目。|
|[bucket_size](#bucket_size)|取得 Bucket 大小。|
|[cbegin](#cbegin)|指定受控制序列的開頭。|
|[cend](#cend)|指定受控制序列的結尾。|
|[clear](#clear)|移除所有項目。|
|[count](#count)|尋找符合指定索引鍵的項目數目。|
|[emplace](#emplace)|加入就地建構的項目。|
|[emplace_hint](#emplace_hint)|加入就地建構的項目，含提示。|
|[empty](#empty)|測試項目是否不存在。|
|[end](#end)|指定受控制序列的結尾。|
|[equal_range](#equal_range)|尋找符合指定之索引鍵的範圍。|
|[erase](#erase)|移除位於指定位置的項目。|
|[find](#find)|尋找符合指定之索引鍵的元素。|
|[get_allocator](#get_allocator)|取得已儲存的配置器物件。|
|[hash_function](#hash)|取得儲存的雜湊函式物件。|
|[insert](#insert)|加入項目。|
|[key_eq](#key_eq)|取得儲存的比較函式物件。|
|[load_factor](#load_factor)|計算每個值區的平均項目數。|
|[max_bucket_count](#max_bucket_count)|取得 Bucket 最大數目。|
|[max_load_factor](#max_load_factor)|取得或設定每個 Bucket 最大項目數。|
|[max_size](#max_size)|取得受控制序列的大小上限。|
|[rehash](#rehash)|重建雜湊資料表。|
|[size](#size)|計算元素的數目。|
|[swap](#swap)|交換兩個容器的內容。|
|[unordered_map](#unordered_map)|建構容器物件。|

|運算子|描述|
|-|-|
|[unordered_map::operator[]](#op_at)|尋找或插入具有指定索引鍵的項目。|
|[unordered_map::operator=](#op_eq)|複製雜湊資料表。|

## <a name="remarks"></a>備註

物件會排列它所控制序列的順序，方式是呼叫兩個預存物件，一個是 [unordered_map::key_equal](#key_equal) 類型的比較函式物件，一個是 [unordered_map::hasher](#hasher) 類型的雜湊函式物件。 您可以透過呼叫成員函式 [unordered_map::key_eq](#key_eq)`()` 存取第一個預存物件；透過呼叫成員函式 [unordered_map::hash_function](#hash)`()` 存取第二個預存物件。 具體來說，只有在兩個引數值具有對等順序，對於 `X` 類型的所有值 `Y` 和 `Key`，呼叫 `key_eq()(X, Y)` 才會傳回 true，呼叫 `hash_function()(keyval)` 會產生 `size_t` 類型值的分佈。 不同於樣板類別 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)，樣板類別 `unordered_map` 的物件可保證 `key_eq()(X, Y)` 針對受控制序列的任何兩個元素永遠是 false。 (索引鍵是唯一的)。

物件也會儲存最大載入因數，指定每個 Bucket 所需的項目平均數目上限。 如果插入元素會使 [unordered_map::load_factor](#load_factor)`()` 超出最大的載入因數，容器會增加值區的數目並視需要重建雜湊資料表。

受控制序列中實際的項目順序取決於雜湊函式、比較函式、插入順序、最大載入因數和 Bucket 目前數目。 一般來說，您無法預測受控制序列中的項目順序。 不過，您永遠可以確保，有對等順序的任何項目子集在受控制序列中為相鄰。

物件會透過 [unordered_map::allocator_type](#allocator_type) 類型的預存配置器物件，配置並釋放它所控制之序列的儲存體。 這種配置器物件必須具有和 `allocator` 樣板類別物件相同的外部介面。 請注意，如果已指定容器物件，儲存的配置器物件不會複製。

## <a name="requirements"></a>需求

**標頭：** \<unordered_map>

**命名空間：** std

## <a name="allocator_type"></a>  unordered_map::allocator_type

管理儲存體的配置器類型。

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Alloc`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}

```

```Output
al == std::allocator() is true
```

## <a name="at"></a>  unordered_map::at

在 unordered_map 中尋找具有指定索引鍵值的項目。

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`key`|要尋找的索引鍵值。|

### <a name="return-value"></a>傳回值

所找到項目之資料值的參考。

### <a name="remarks"></a>備註

如果找不到引數索引鍵值，則函式會擲回 `out_of_range`類別的物件。

### <a name="example"></a>範例

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}
```

## <a name="begin"></a>  unordered_map::begin

指定受控制序列或值區的開頭。

```cpp
iterator begin();
const_iterator begin() const;
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`nbucket`|Bucket 編號。|

### <a name="remarks"></a>備註

最前面兩個成員函式傳回的正向迭代器，指向序列的第一個項目 (或在空序列結尾以外的位置)。 最後面兩個成員函式傳回的正向迭代器，指向值區 `nbucket` 的第一個項目 (或在空值區結尾以外的位置)。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

#typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="bucket"></a>  unordered_map::bucket

取得索引鍵值的值區數目。

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>參數

`keyval` 要對應的索引鍵的值。

### <a name="remarks"></a>備註

此成員函式會傳回目前對應至索引鍵值 `keyval`的值區數目。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
 [c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a>  unordered_map::bucket_count

取得 Bucket 的數目。

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>備註

成員函式會傳回目前的 Bucket 數目。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3][b, 2][a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="bucket_size"></a>  unordered_map::bucket_size

取得 Bucket 大小

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>參數

`nbucket` Bucket 編號。

### <a name="remarks"></a>備註

成員函式會傳回 Bucket 編號 `nbucket`的大小。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
 [c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a>  unordered_map::cbegin

傳回 `const` 迭代器，為範圍中的第一個項目定址。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

`const` 正向存取迭代器，指向範圍的第一個項目，或指向空白範圍結尾 (空白範圍 `cbegin() == cend()`) 之外的位置。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮將 `Container` 視為支援 `begin()` 和 `cbegin()` 的各種可修改 (非 `const`) 容器。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  unordered_map::cend

傳回 `const` 迭代器，為範圍中最後一個項目之外的位置定址。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

指向範圍結尾之外的 `const` 正向存取迭代器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮將 `Container` 視為任何支援 `end()` 和 `cend()` 且可修改 (非 `const`) 的容器類型。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="clear"></a>  unordered_map::clear

移除所有項目。

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函式呼叫 [unordered_map::erase](#erase)`(` [unordered_map::begin](#begin)`(),` [unordered_map::end](#end)`())`。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}

```

```Output
 [c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="const_iterator"></a>  unordered_map::const_iterator

用於受控制序列的常數迭代器類型。

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>備註

此類型說明可做為受控制序列之常數正向迭代器的物件。 在此將其描述為已定義實作之 `T1`類型的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="const_local_iterator"></a>  unordered_map::const_local_iterator

用於受控制序列的常數 Bucket 迭代器類型。

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>備註

此類型說明可作為值區之常數正向迭代器的物件。 在此將其描述為已定義實作之 `T5`類型的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="const_pointer"></a>  unordered_map::const_pointer

項目的常數指標類型。

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之項目的常數指標。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="const_reference"></a>  unordered_map::const_reference

項目的常數參考類型。

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>備註

此類型所說明的物件可作為受控制序列之元素的常數參考。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="count"></a>  unordered_map::count

尋找符合指定索引鍵的項目數目。

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>參數

`keyval` 若要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式傳回由 [unordered_map::equal_range](#equal_range)`(keyval)` 分隔之範圍中的元素數。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}

```

```Output
 [c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a>  unordered_map::difference_type

兩個項目之間帶正負號距離的類型。

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>備註

此帶正負號的整數類型所描述的物件可代表受控制序列中任何兩個項目位址之間的差距。 在此將其描述為已定義實作之 `T3`類型的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
 [c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="emplace"></a>  unordered_map::emplace

將就地建構元素 (沒有執行複製或移動作業) 插入到 unordered_map。

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`args`|轉送以建構插入 unordered_map 之元素的引數，除非它已經包含一個值以同等方式排序的元素。|

### <a name="return-value"></a>傳回值

如果已插入，`pair` 的 `bool` 元件就會傳回 true，如果 `unordered_map` 已經包含元素，其中該元素的索引鍵具有對等的排序值，且其迭代器元件傳回插入新元件或該元素已在的位址，則會傳回 false。

若要存取此成員函式所傳回的配對 `pr` 迭代器元件，請使用 `pr.first`，若要取其值，請使用 `*(pr.first)`。 若要存取此成員函式所傳回之配對 `pr` 的 `bool` 元件，請使用 `pr.second`。

### <a name="remarks"></a>備註

此函式不會使任何迭代器或參考無效。

在插入期間，如果擲回例外狀況，但不是發生在容器的雜湊函式中，則不會修改容器。 若雜湊函式中擲回例外狀況，則結果為未定義。

如需程式碼範例，請參閱 [map::emplace](../standard-library/map-class.md#emplace)。

## <a name="emplace_hint"></a>  unordered_map::emplace_hint

將就地建構 (未執行任何複製或移動作業) 的項目連同位置提示一起插入。

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`args`|轉送以建構插入 unordered_map 之元素的引數，除非該 unordered_map 中已經包含該元素，或廣義而言，除非它已經包含索引鍵以同等方式排序的元素。|
|`where`|有關要從何處開始搜尋正確插入點的提示。|

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

如果插入因為項目已經存在而失敗，則會將迭代器傳回現有的項目。

### <a name="remarks"></a>備註

此函式不會使任何參考無效。

在插入期間，如果擲回例外狀況，但不是發生在容器的雜湊函式中，則不會修改容器。 若雜湊函式中擲回例外狀況，則結果為未定義。

元素的 [value_type](../standard-library/map-class.md#value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

如需程式碼範例，請參閱 [map::emplace_hint](../standard-library/map-class.md#emplace_hint)。

## <a name="empty"></a>  unordered_map::empty

測試項目是否不存在。

```cpp
bool empty() const;
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="end"></a>  unordered_map::end

指定受控制序列的結尾。

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`nbucket`|Bucket 編號。|

### <a name="remarks"></a>備註

前兩個成員函式會傳回指向序列結尾之外的正向迭代器。 最後兩個成員函式會傳回指向值區 `nbucket`結尾之外的正向迭代器。

## <a name="equal_range"></a>  unordered_map::equal_range

尋找符合指定之索引鍵的範圍。

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>參數

`keyval` 若要搜尋的索引鍵值。

### <a name="remarks"></a>備註

此成員函式會傳回一組迭代器 `X` ，使 `[X.first, X.second)` 僅分隔與 `keyval`具有相同順序之受控制序列的項目。 如果沒有這類項目存在，則兩個迭代器皆為 `end()`。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
 [c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="erase"></a>  unordered_map::erase

從指定的位置移除 unordered_map 中的元素或元素範圍，或移除符合指定索引鍵的元素。

```cpp
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
```

### <a name="parameters"></a>參數

`Where` 要移除之項目的位置。

`First` 要移除的第一個元素的位置。

`Last` 要移除的最後一個元素之後的位置。

`Key` 要移除之項目的索引鍵值。

### <a name="return-value"></a>傳回值

針對前兩個成員函式，會傳回雙向迭代器，其中指定任何移除之元素後剩餘的第一個元素，或如果沒有這類元素，則傳回 map 結尾的元素。

在第三個成員函式中，傳回已從 unordered_map 移除的元素數。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [map::erase](../standard-library/map-class.md#erase)。

## <a name="find"></a>  unordered_map::find

尋找符合指定之索引鍵的元素。

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>參數

`keyval` 若要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式傳回 [unordered_map::equal_range](#equal_range)`(keyval).first`。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}

```

```Output
 [c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="get_allocator"></a>  unordered_map::get_allocator

取得已儲存的配置器物件。

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>備註

這個成員函式會傳回儲存的配置器物件。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}

```

```Output
al == std::allocator() is true
```

## <a name="hash"></a>  unordered_map::hash_function

取得儲存的雜湊函式物件。

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回儲存的雜湊函式物件。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}

```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a>  unordered_map::hasher

雜湊函式的類型。

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Hash`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}

```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a>  unordered_map::insert

將某個項目或項目範圍插入 unordered_map 中。

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);


// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);


// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);


// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);


// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);


// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`Val`|除非其中包含了索引鍵已經過對等地排序的項目，否則為要插入 unordered_map 中的項目值。|
|`Where`|要開始搜尋正確的插入點的地方。|
|`ValTy`|範本參數，指定 unordered_map 可用於建構 [value_type](../standard-library/map-class.md#value_type) 之元素的引數類型，並將 `Val` 作為引數完美轉送。|
|`First`|要複製之第一個元素的位置。|
|`Last`|要複製之最一個元素後方的位置。|
|`InputIterator`|符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#value_type) 物件的類型。|
|`IList`|要從中複製項目的 [initializer_list](../standard-library/initializer-list.md)。|

### <a name="return-value"></a>傳回值

單一元素成員函式 (1) 和 (2) 會傳回 [pair](../standard-library/pair-structure.md)，其中其中若已執行插入則 `bool` 元件為 true，若 unordered_map 已包含其中索引鍵具有依順序排列的對等值的元素，則為 false。 若 `bool` 元件為 True，傳回值組的迭代器元件會指向最新插入的元素；若 `bool` 元件為 False，則會指向現有元素。

具有提示的單一項目成員函式 (3) 及 (4) 會傳回指向位置的迭代器，該位置是新項目插入 unordered_map 中的位置，或者，若對等索引鍵已存在，則指向現有項目。

### <a name="remarks"></a>備註

此函式不會使任何迭代器、指標或參考無效。

在只插入一個項目的期間，若擲出例外狀況，但沒有發生在容器的雜湊函式中，則不會修改容器的狀態。 若雜湊函式中擲回例外狀況，則結果為未定義。 在插入多個項目期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。

若要存取 `pair` `pr` 的迭代器元件 (由單一元素成員函式傳回)，請使用 `pr.first`；若要對傳回的 pair 中的迭代器取值，請使用 `*pr.first` (提供您元素)。 若要存取 `bool` 元件，請使用 `pr.second`。 例如，請參閱本文中稍後的範例程式碼。

容器的 [value_type](../standard-library/map-class.md#value_type) 是屬於容器的 typedef，而就 map 而言，`map<K, V>::value_type` 是 `pair<const K, V>`。 元素的值是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。

範圍成員函式 (5) 會將項目值的序列插入對應至每個項目的 unordered_map，而這些項目是由範圍 `[First, Last)` 中的迭代器指定；因此不會插入 `Last`。 容器成員函式 `end()` 會參考容器中最後一個項目之後的位置。例如陳述式 `m.insert(v.begin(), v.end());` 嘗試將 `v` 的所有項目插入 `m`。 只會插入具有範圍中唯一值的元素；若重複則會忽略。 若要觀察哪些元素會遭到拒絕，請使用單一元素版本的 `insert`。

初始設定式清單成員函式 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 unordered_map。

針對插入就地建構的元素 (也就是沒有執行複製或移動作業)，請參閱 [unordered_map::emplace](#emplace) 和 [unordered_map::emplace_hint](#emplace_hint)。

如需程式碼範例，請參閱 [map::insert](../standard-library/map-class.md#insert)。

## <a name="iterator"></a>  unordered_map::iterator

受控制序列之迭代器的類型。

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>備註

此類型說明可作為受控制序列之正向迭代器的物件。 在此將其說明為實作定義類型 `T0`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="key_eq"></a>  unordered_map::key_eq

取得儲存的比較函式物件。

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回儲存的比較函式物件

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }

```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_equal"></a>  unordered_map::key_equal

比較函式的類型。

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Pred`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }

```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_type"></a>  unordered_map::key_type

排序索引鍵的類型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Key`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="load_factor"></a>  unordered_map::load_factor

計算每個值區的平均項目數。

```cpp
float load_factor() const;
```

### <a name="remarks"></a>備註

成員函式傳回 `(float)`[unordered_map::size](#size)`() / (float)`[unordered_map::bucket_count](#bucket_count)`()`，亦即每個值區的平均元素數。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }

```

```Output
 [c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="local_iterator"></a>  unordered_map::local_iterator

值區迭代器的類型。

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>備註

此類型說明可做為值區之正向迭代器的物件。 在此將其描述為已定義實作之 `T4`類型的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="mapped_type"></a>  unordered_map::mapped_type

與每個索引鍵關聯的對應值類型。

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Ty`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="max_bucket_count"></a>  unordered_map::max_bucket_count

取得 Bucket 最大數目。

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回目前允許的最大值區數目。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }

```

```Output
 [c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="max_load_factor"></a>  unordered_map::max_load_factor

取得或設定每個 Bucket 最大項目數。

```cpp
float max_load_factor() const;


void max_load_factor(float factor);
```

### <a name="parameters"></a>參數

`factor` 新的最大載入因數。

### <a name="remarks"></a>備註

第一個成員函式會傳回儲存的最大載入因數。 第二個成員函式會以 `factor`取代儲存的最大載入因數。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }

```

```Output
 [c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="max_size"></a>  unordered_map::max_size

取得受控制序列的大小上限。

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回物件可以控制之最長序列的長度。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }

```

```Output
max_size() == 536870911
```

## <a name="op_at"></a>  unordered_map::operator[]

尋找或插入具有指定索引鍵的項目。

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`Keyval`|要尋找或插入的索引鍵值。|

### <a name="return-value"></a>傳回值

所插入項目之資料值的參考。

### <a name="remarks"></a>備註

如果找不到引數索引鍵值，則將它與資料類型的預設值一起插入。

`operator[]` 可用來將元素插入使用 *m*[_ *Key*] = `DataValue` 的對應 *m* 中，其中 `DataValue` 是具有索引鍵值 \_ *Key* 之元素的 `mapped_type` 值。

當使用 `operator[]` 插入項目時，傳回的參考不會指出插入是變更預先存在的項目，還是建立新的項目。 成員函式 [find](../standard-library/map-class.md#find) 和 [insert](../standard-library/map-class.md#insert) 可用來判斷具有指定索引鍵的元素在插入之前是否已經存在。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }

```

```Output
 [c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
 [c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>備註

成員函式會將迭代器 `where` 判斷為 [unordered_map::insert](#insert)`(` [unordered_map::value_type](#value_type)`(keyval, Ty())` 的傳回值。 (如果沒有此類項目存在，它會插入具有指定之索引鍵的項目)。然後傳回 `(*where).second` 的參考。

## <a name="op_eq"></a>  unordered_map::operator=

使用來自另一個 unordered_map 的項目來取代這個 unordered_map 的項目。

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`right`|此運算子函式從中指派內容的 unordered_map。|

### <a name="remarks"></a>備註

第一個版本會將 `right` 中的所有元素複製到這個 unordered_map。

第二個版本會將 `right` 中的所有元素移至這個 unordered_map。

這個 unordered_map 中 `operator`= executes 之前的所有項目都會被捨棄。

### <a name="example"></a>範例

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  unordered_map::pointer

項目的指標類型。

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之項目的指標。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="reference"></a>  unordered_map::reference

項目的參考類型。

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之元素的參考。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="rehash"></a>  unordered_map::rehash

重建雜湊資料表。

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>參數

`nbuckets` 要求的貯體數目。

### <a name="remarks"></a>備註

此成員函式會將值區數目改變為至少 `nbuckets` ，並視需要重建雜湊資料表。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
    }

```

```Output
 [c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="size"></a>  unordered_map::size

計算元素的數目。

```cpp
size_type size() const;
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }

```

```Output
 [c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="size_type"></a>  unordered_map::size_type

兩個項目之間不帶正負號距離的類型。

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>備註

此不帶正負號的整數類型所描述的物件可代表任何受控制序列的長度。 在此將其描述為已定義實作之 `T2`類型的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }

```

```Output
size == 0
```

## <a name="swap"></a>  unordered_map::swap

交換兩個容器的內容。

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>參數

`right` 要交換的容器。

### <a name="remarks"></a>備註

成員函式會交換 `*this` 和 `right` 之間受控制的序列。 如果是 [unordered_map::get_allocator](#get_allocator)`() == right.get_allocator()`，它會以常數時間來執行，只會在結果是複製類型 `Tr` 預存特性物件時擲回例外狀況，並且不會使指定此兩個受控制序列中元素的任何參考、指標或迭代器失效。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_map"></a>  unordered_map::unordered_map

建構容器物件。

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
 InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>參數

|參數|描述|
|-|-|
|`Al`|要儲存的配置器物件。|
|`Comp`|要儲存的比較函式物件。|
|`Hash`|要儲存的雜湊函式物件。|
|`Bucket_count`|Bucket 最小數目。|
|`Right`|要複製的容器。|
|`First`||
|`Last`||
|`IList`|包含要複製之項目的 initializer_list。|

### <a name="remarks"></a>備註

第一個建構函式指定由 `right` 控制之序列的複本。 第二個建構函式會指定空白的受控制序列。 第三個建構函式會插入項目值序列 `[first, last)`。 第四個建構函式透過移動 `right` 來指定序列的複本。

所有建構函式也會初始化數個儲存值。 對於複製建構函式，其值是從 `Right` 取得。 否則就是：

Bucket 的最小數目為引數 `Bucket_count` (如果存在)；否則其為本文所述的預設值，即由實作所定義的值 `N0`。

雜湊函式物件是引數 `Hash` (如果存在)；否則為 `Hash()`。

比對函式物件是引數 `Comp` (如果存在)；否則為 `Pred()`。

配置器物件是引數 `Al` (如果存在)；否則為 `Alloc()`。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
 [a, 1] [b, 2] [c, 3]
 [d, 4] [e, 5] [f, 6]
 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
 [a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]
 ```

## <a name="value_type"></a>  unordered_map::value_type

元素的類型。

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>備註

此類型描述受控制序列的項目。

### <a name="example"></a>範例

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>另請參閱

[<unordered_map>](../standard-library/unordered-map.md)<br/>
[容器](../cpp/containers-modern-cpp.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
