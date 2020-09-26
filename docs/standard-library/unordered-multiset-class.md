---
title: unordered_multiset 類別
description: C + + 標準程式庫容器類別的 API 參考 `unordered_multiset` ，其描述用於儲存和抓取集合資料的物件，其中包含的專案值不需要是唯一的，而且會當做索引鍵值。 資料不會自動排序。
ms.date: 9/10/2020
f1_keywords:
- unordered_set/std::unordered_multiset
- unordered_set/std::unordered_multiset::allocator_type
- unordered_set/std::unordered_multiset::const_iterator
- unordered_set/std::unordered_multiset::const_local_iterator
- unordered_set/std::unordered_multiset::const_pointer
- unordered_set/std::unordered_multiset::const_reference
- unordered_set/std::unordered_multiset::difference_type
- unordered_set/std::unordered_multiset::hasher
- unordered_set/std::unordered_multiset::iterator
- unordered_set/std::unordered_multiset::key_equal
- unordered_set/std::unordered_multiset::key_type
- unordered_set/std::unordered_multiset::local_iterator
- unordered_set/std::unordered_multiset::pointer
- unordered_set/std::unordered_multiset::reference
- unordered_set/std::unordered_multiset::size_type
- unordered_set/std::unordered_multiset::value_type
- unordered_set/std::unordered_multiset::begin
- unordered_set/std::unordered_multiset::bucket
- unordered_set/std::unordered_multiset::bucket_count
- unordered_set/std::unordered_multiset::bucket_size
- unordered_set/std::unordered_multiset::cbegin
- unordered_set/std::unordered_multiset::cend
- unordered_set/std::unordered_multiset::clear
- unordered_set/std::unordered_multiset::contains
- unordered_set/std::unordered_multiset::count
- unordered_set/std::unordered_multiset::emplace
- unordered_set/std::unordered_multiset::emplace_hint
- unordered_set/std::unordered_multiset::empty
- unordered_set/std::unordered_multiset::end
- unordered_set/std::unordered_multiset::equal_range
- unordered_set/std::unordered_multiset::erase
- unordered_set/std::unordered_multiset::find
- unordered_set/std::unordered_multiset::get_allocator
- unordered_set/std::unordered_multiset::hash
- unordered_set/std::unordered_multiset::insert
- unordered_set/std::unordered_multiset::key_eq
- unordered_set/std::unordered_multiset::load_factor
- unordered_set/std::unordered_multiset::max_bucket_count
- unordered_set/std::unordered_multiset::max_load_factor
- unordered_set/std::unordered_multiset::max_size
- unordered_set/std::unordered_multiset::rehash
- unordered_set/std::unordered_multiset::size
- unordered_set/std::unordered_multiset::swap
- unordered_set/std::unordered_multiset::unordered_multiset
- unordered_set/std::unordered_multiset::operator=
- unordered_set/std::unordered_multiset::hash_function
helpviewer_keywords:
- std::unordered_multiset
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::contains
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
- std::unordered_multiset::unordered_multiset
- std::unordered_multiset::operator=
- std::unordered_multiset::allocator_type
- std::unordered_multiset::const_iterator
- std::unordered_multiset::const_local_iterator
- std::unordered_multiset::const_pointer
- std::unordered_multiset::const_reference
- std::unordered_multiset::difference_type
- std::unordered_multiset::hasher
- std::unordered_multiset::iterator
- std::unordered_multiset::key_equal
- std::unordered_multiset::key_type
- std::unordered_multiset::local_iterator
- std::unordered_multiset::pointer
- std::unordered_multiset::reference
- std::unordered_multiset::size_type
- std::unordered_multiset::value_type
- std::unordered_multiset::begin
- std::unordered_multiset::bucket
- std::unordered_multiset::bucket_count
- std::unordered_multiset::bucket_size
- std::unordered_multiset::cbegin
- std::unordered_multiset::cend
- std::unordered_multiset::clear
- std::unordered_multiset::count
- std::unordered_multiset::emplace
- std::unordered_multiset::emplace_hint
- std::unordered_multiset::empty
- std::unordered_multiset::end
- std::unordered_multiset::equal_range
- std::unordered_multiset::erase
- std::unordered_multiset::find
- std::unordered_multiset::get_allocator
- std::unordered_multiset::hash_function
- std::unordered_multiset::insert
- std::unordered_multiset::key_eq
- std::unordered_multiset::load_factor
- std::unordered_multiset::max_bucket_count
- std::unordered_multiset::max_load_factor
- std::unordered_multiset::max_size
- std::unordered_multiset::rehash
- std::unordered_multiset::size
- std::unordered_multiset::swap
ms.assetid: 70c8dfc5-492a-4af2-84f5-1aa9cb04b71c
ms.openlocfilehash: 0730f4eb6ba8e625c2c40cecddc4f689ec775d17
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352774"
---
# <a name="unordered_multiset-class"></a>unordered_multiset 類別

類別樣板描述的物件可控制型別專案的不同長度序列 `const Key` 。 序列由雜湊函式弱式排序，將序列分割為子序列的已排序集合，稱為 Bucket。 在每個 Bucket 中，比較函式判斷是否有任何一對項目具有對等順序。 每個項目同時做為排序鍵和值。 序列表示允許以一些作業查閱、插入和移除任意項目，這些作業可以獨立於序列中的項目數目 (常數時間)，至少當所有 Bucket 長度大約相等時。 在最壞的情況下，當所有項目都在一個 Bucket 時，作業數目與序列中的項目數目成正比 (線性時間)。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。

## <a name="syntax"></a>語法

```cpp
template <class Key,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<Key>>
class unordered_multiset;
```

### <a name="parameters"></a>參數

*關鍵*\
索引鍵類型。

*散 列*\
雜湊函式物件類型。

*Pred*\
相等比較函式物件類型。

*配置*\
配置器類別。

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
|[迭 代](#iterator)|受控制序列之迭代器的類型。|
|[key_equal](#key_equal)|比較函式的類型。|
|[key_type](#key_type)|排序索引鍵的類型。|
|[local_iterator](#local_iterator)|用於受控制序列的 Bucket 迭代器類型。|
|[指標](#pointer)|項目的指標類型。|
|[reference](#reference)|項目的參考類型。|
|[size_type](#size_type)|兩個項目之間不帶正負號距離的類型。|
|[value_type](#value_type)|項目的類型。|

|成員函式|說明|
|-|-|
|[開始](#begin)|指定受控制序列的開頭。|
|[桶](#bucket)|取得索引鍵值的值區數目。|
|[bucket_count](#bucket_count)|取得 Bucket 的數目。|
|[bucket_size](#bucket_size)|取得 Bucket 大小。|
|[cbegin](#cbegin)|指定受控制序列的開頭。|
|[cend](#cend)|指定受控制序列的結尾。|
|[清除](#clear)|移除所有項目。|
|[包含](#contains)<sup>c + + 20</sup>|檢查是否有具有指定索引鍵的元素。|
|[計數](#count)|尋找符合指定索引鍵的項目數目。|
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
|[重複](#rehash)|重建雜湊資料表。|
|[size](#size)|計算元素的數目。|
|[交換](#swap)|交換兩個容器的內容。|
|[unordered_multiset](#unordered_multiset)|建構容器物件。|

|運算子|說明|
|-|-|
|[unordered_multiset::operator=](#op_eq)|複製雜湊資料表。|

## <a name="remarks"></a>備註

物件會排列它所控制之序列的順序，方式是呼叫兩個預存物件，一個是 [unordered_multiset::key_equal](#key_equal) 類型的比較函式物件，一個是 [unordered_multiset::hasher](#hasher) 類型的雜湊函式物件。 您可以藉由呼叫成員函式[unordered_multiset：： key_eq](#key_eq); 來存取第一個儲存的物件 `()` ，而且您可以藉由呼叫成員函式[unordered_multiset：： hash_function](#hash)來存取第二個儲存的物件 `()` 。 具體來說，只有在兩個引數值具有對等順序，對於 `X` 類型的所有值 `Y` 和 `Key`，呼叫 `key_eq()(X, Y)` 才會傳回 true，呼叫 `hash_function()(keyval)` 會產生 `size_t` 類型值的分佈。 不同于類別樣板 [Unordered_set 類別](../standard-library/unordered-set-class.md)，類型的物件不 `unordered_multiset` 會確定 `key_eq()(X, Y)` 受控制序列的任何兩個元素一律為 false。 (索引鍵不需要是唯一的)。

物件也會儲存最大載入因數，指定每個 Bucket 所需的項目平均數目上限。 如果插入元素會使[unordered_multiset：： load_factor](#load_factor) `()` 超過最大的載入因數，容器會增加值區的數目並視需要重建雜湊資料表。

受控制序列中實際的項目順序取決於雜湊函式、比較函式、插入順序、最大載入因數和 Bucket 目前數目。 一般來說，您無法預測受控制序列中的項目順序。 不過，您永遠可以確保，有對等順序的任何項目子集在受控制序列中為相鄰。

物件會透過 [unordered_multiset::allocator_type](#allocator_type) 類型的預存配置器物件，配置並釋放它所控制之序列的儲存體。 這種配置器物件必須與類型的物件具有相同的外部介面 `allocator` 。 請注意，如果已指定容器物件，儲存的配置器物件不會複製。

## <a name="requirements"></a>需求

**標頭：**\<unordered_set>

**命名空間：** std

## <a name="unordered_multisetallocator_type"></a><a name="allocator_type"></a> unordered_multiset：： allocator_type

管理儲存體的配置器類型。

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Alloc` 的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_allocator_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_multisetbegin"></a><a name="begin"></a> unordered_multiset：： begin

指定受控制序列或值區的開頭。

```cpp
iterator begin();

const_iterator begin() const;

local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>參數

*nbucket*\
值區數目。

### <a name="remarks"></a>備註

最前面兩個成員函式傳回的正向迭代器，指向序列的第一個項目 (或在空序列結尾以外的位置)。 最後兩個成員函式會傳回正向反覆運算器，指向值區 *nbucket* 的第一個元素 (或空白值區結尾) 。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_begin.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect first two items "[c] [b]"
    Myset::iterator it2 = c1.begin();
    std::cout << "[" << *it2 << "] ";
    ++it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[c] [b]
[a]
```

## <a name="unordered_multisetbucket"></a><a name="bucket"></a> unordered_multiset：： bucket

取得索引鍵值的值區數目。

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>參數

*keyval*\
要對應的索引鍵值。

### <a name="remarks"></a>備註

此成員函式會傳回目前對應至索引鍵值 `keyval`的值區數目。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_bucket.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_multisetbucket_count"></a><a name="bucket_count"></a> unordered_multiset：： bucket_count

取得 Bucket 的數目。

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>備註

成員函式會傳回目前的 Bucket 數目。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

    return (0);
}
```

```Output
[c] [b] [a]
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

## <a name="unordered_multisetbucket_size"></a><a name="bucket_size"></a> unordered_multiset：： bucket_size

取得 Bucket 大小

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>參數

*nbucket*\
值區數目。

### <a name="remarks"></a>備註

成員函式會傳回值區編號 *nbucket*的大小。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_bucket_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_multisetcbegin"></a><a name="cbegin"></a> unordered_multiset：： cbegin

傳回 **`const`** 反覆運算器，定址範圍中的第一個元素。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

**`const`** 向前存取反覆運算器，指向範圍的第一個元素，或指向空白範圍結尾以外的位置， (空白範圍， `cbegin() == cend()`) 。

### <a name="remarks"></a>備註

傳回值為 `cbegin` 時，無法修改範圍中的項目。

您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `begin()` `cbegin()` 。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator

auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="unordered_multisetcend"></a><a name="cend"></a> unordered_multiset：： cend

傳回 **`const`** 反覆運算器，定址範圍中最後一個元素之外的位置。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

**`const`** 指向範圍結尾之外的正向存取反覆運算器。

### <a name="remarks"></a>備註

`cend` 用來測試迭代器是否已超過其範圍結尾。

您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮 `Container` 將任何支援和的非) 容器 (不是可修改的 **`const`** `end()` `cend()` 。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator

auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

`cend` 所傳回的值不應該取值。

## <a name="unordered_multisetclear"></a><a name="clear"></a> unordered_multiset：： clear

移除所有項目。

```cpp
void clear();
```

### <a name="remarks"></a>備註

成員函式呼叫 [unordered_multiset::erase](#erase)`(` [unordered_multiset::begin](#begin)`(),` [unordered_multiset::end](#end)`())`。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_clear.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="unordered_multisetconst_iterator"></a><a name="const_iterator"></a> unordered_multiset：： const_iterator

用於受控制序列的常數迭代器類型。

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>備註

此類型說明可做為受控制序列之常數正向迭代器的物件。 在此將其說明為實作定義類型 `T1`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_const_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetconst_local_iterator"></a><a name="const_local_iterator"></a> unordered_multiset：： const_local_iterator

用於受控制序列的常數 Bucket 迭代器類型。

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>備註

此類型說明可作為值區之常數正向迭代器的物件。 在此將其說明為實作定義類型 `T5`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="unordered_multisetconst_pointer"></a><a name="const_pointer"></a> unordered_multiset：： const_pointer

項目的常數指標類型。

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之項目的常數指標。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_const_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::const_pointer p = &*it;
        std::cout << "[" << *p << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetconst_reference"></a><a name="const_reference"></a> unordered_multiset：： const_reference

項目的常數參考類型。

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>備註

此類型所說明的物件可作為受控制序列之元素的常數參考。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_const_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::const_reference ref = *it;
        std::cout << "[" << ref << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetcontains"></a><a name="contains"></a> unordered_multiset：： contains

檢查中是否有具有指定索引鍵的元素 `unordered_multiset` 。

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>參數

*K*\
索引鍵的類型。

*關鍵*\
要尋找之元素的索引鍵值。

### <a name="return-value"></a>傳回值

`true` 如果在容器中找到元素，則為， `false` 否則為。

### <a name="remarks"></a>備註

`contains()` 是 c + + 20 的新功能。 若要使用它，請指定 [/std： c + + 最新](../build/reference/std-specify-language-standard-version.md) 的編譯器選項。

`template<class K> bool contains(const K& key) const` 如果是透明的，則只會參與多載解析 `key_compare` 。

### <a name="example"></a>範例

```cpp
// Requires /std:c++latest
#include <unordered_set>
#include <iostream>

int main()
{
    std::unordered_multiset<int> theUnorderedMultiset = { 1, 2, 3 };

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMultiset.contains(1) << '\n';
    std::cout << theUnorderedMultiset.contains(4) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="unordered_multisetcount"></a><a name="count"></a> unordered_multiset：： count

尋找符合指定索引鍵的項目數目。

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>參數

*keyval*\
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回範圍中以[unordered_multiset：： equal_range](#equal_range)分隔的元素數目 `(keyval)` 。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="unordered_multisetdifference_type"></a><a name="difference_type"></a> unordered_multiset：:d ifference_type

兩個項目之間帶正負號距離的類型。

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>備註

此帶正負號的整數類型所描述的物件可代表受控制序列中任何兩個項目位址之間的差距。 在此將其說明為實作定義類型 `T3`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_difference_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Myset::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
end()-begin() == 3
begin()-end() == -3
```

## <a name="unordered_multisetemplace"></a><a name="emplace"></a> unordered_multiset：： emplace

插入就地建構 (未執行任何複製或移動作業) 的元素。

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>參數

*參數*\
轉送以建構插入 unordered_multiset 之元素的引數。

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

### <a name="remarks"></a>備註

此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。

在插入期間，如果擲回例外狀況，但不是發生在容器的雜湊函式中，則不會修改容器。 若雜湊函式中擲回例外狀況，則結果為未定義。

如需程式碼範例，請參閱 [multiset::emplace](../standard-library/multiset-class.md#emplace)。

## <a name="unordered_multisetemplace_hint"></a><a name="emplace_hint"></a> unordered_multiset：： emplace_hint

將就地建構 (未執行任何複製或移動作業) 的項目連同位置提示一起插入。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>參數

*參數*\
轉送以建構插入 unordered_multiset 之元素的引數。

*：*\
一個有關要從哪裡開始搜尋正確插入點的提示。

### <a name="return-value"></a>傳回值

新插入項目的迭代器。

### <a name="remarks"></a>備註

此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。

在插入期間，如果擲回例外狀況，但不是發生在容器的雜湊函式中，則不會修改容器。 若雜湊函式中擲回例外狀況，則結果為未定義。

如需程式碼範例，請參閱 [set::emplace_hint](../standard-library/set-class.md#emplace_hint)。

## <a name="unordered_multisetempty"></a><a name="empty"></a> unordered_multiset：： empty

測試項目是否不存在。

```cpp
bool empty() const;
```

### <a name="remarks"></a>備註

成員函式會對空的受控制序列傳回 true。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_empty.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="unordered_multisetend"></a><a name="end"></a> unordered_multiset：： end

指定受控制序列的結尾。

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>參數

*nbucket*\
值區數目。

### <a name="remarks"></a>備註

前兩個成員函式會傳回指向序列結尾之外的正向迭代器。 最後兩個成員函式會傳回指向值區 *nbucket*結尾之外的正向反覆運算器。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_end.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect last two items "[a] [b]"
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << "[" << *it2 << "] ";
    --it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a] [b]
[a]
```

## <a name="unordered_multisetequal_range"></a><a name="equal_range"></a> unordered_multiset：： equal_range

尋找符合指定之索引鍵的範圍。

```cpp
std::pair<iterator, iterator>
    equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
    equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>參數

*keyval*\
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回一組反覆運算器 `X` ，其 `[X.first, X.second)` 只會分隔具有對等順序與 *keyval*之受控制序列的元素。 如果沒有這類項目存在，則兩個迭代器皆為 `end()`。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_equal_range.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="unordered_multiseterase"></a><a name="erase"></a> unordered_multiset：： erase

從指定的位置移除 unordered_multiset 中的元素或元素範圍，或移除符合指定索引鍵的元素。

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>參數

*：*\
要移除之項目的位置。

*第一*\
要移除之第一個項目的位置。

*最後*\
緊接在要移除之最後一個元素後面的位置。

*關鍵*\
要移除之項目的索引鍵值。

### <a name="return-value"></a>傳回值

在前兩個成員函式中，會傳回雙向迭代器，其中指定任何移除的元素之外剩餘的第一個元素，或者如果沒有此類元素，則傳回 unordered_multiset 結尾的元素。

在第三個成員函式中，傳回已從 unordered_multiset 移除的元素數。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [set::erase](../standard-library/set-class.md#erase)。

## <a name="unordered_multisetfind"></a><a name="find"></a> unordered_multiset：： find

尋找符合指定之索引鍵的元素。

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>參數

*keyval*\
要搜尋的索引鍵值。

### <a name="remarks"></a>備註

成員函式會傳回[unordered_multiset：： equal_range](#equal_range) `(keyval).first` 。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_find.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << *it << "] " << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="unordered_multisetget_allocator"></a><a name="get_allocator"></a> unordered_multiset：： get_allocator

取得已儲存的配置器物件。

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>備註

這個成員函式會傳回儲存的配置器物件。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_get_allocator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_multisethash_function"></a><a name="hash"></a> unordered_multiset：： hash_function

取得儲存的雜湊函式物件。

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回儲存的雜湊函式物件。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_hash_function.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_multisethasher"></a><a name="hasher"></a> unordered_multiset：： hasher

雜湊函式的類型。

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Hash` 的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_hasher.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_multisetinsert"></a><a name="insert"></a> unordered_multiset：： insert

將某個元素或元素範圍插入 unordered_multiset 中。

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>參數

*瓦爾*\
要插入至 unordered_multiset 的元素值。

*：*\
要開始搜尋正確的插入點的地方

*ValTy*\
範本參數，指定 unordered_multiset 可以用來建立 [value_type](../standard-library/map-class.md#value_type)之元素的引數類型，並將 *Val* 以引數形式完美轉送。

*第一*\
要複製之第一個元素的位置。

*最後*\
要複製之最一個元素後方的位置。

*InputIterator*\
符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#value_type) 物件的類型。

*IList*\
要從中複製元素的 [initializer_list](../standard-library/initializer-list.md) 。

### <a name="return-value"></a>傳回值

單一元素插入成員函式 (1) 和 (2)，會將迭代器傳回至在 unordered_multiset 中插入新元素的位置。

具有提示的單一元素成員函式 (3) 和 (4)，會傳回迭代器，其指向在 unordered_multiset 中插入新元素的位置。

### <a name="remarks"></a>備註

此函式不會使指標或參考無效，但是可能會使容器的所有迭代器無效。

在只插入一個項目的期間，若擲出例外狀況，但沒有發生在容器的雜湊函式中，則不會修改容器的狀態。 若雜湊函式中擲回例外狀況，則結果為未定義。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。

容器的 [value_type](../standard-library/map-class.md#value_type) 是屬於容器的 typedef，而針對 set，`unordered_multiset<V>::value_type` 是 `const V` 類型。

範圍成員函式 (5) 將專案值的序列插入到對應至範圍內反覆運算器定址之每個元素的 unordered_multiset 中 `[First, Last)` ，因此不會插入 *最後一個* 專案。 容器成員函式 `end()` 是指容器中最後一個元素後方的位置；例如，陳述式 `m.insert(v.begin(), v.end());` 會將 `v` 的所有元素插入至 `m`。

初始設定式清單成員函式 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 unordered_multiset。

針對插入就地建構的元素 (也就是沒有執行複製或移動作業)，請參閱 [unordered_multiset::emplace](#emplace) 和 [unordered_multiset::emplace_hint](#emplace_hint)。

如需程式碼範例，請參閱 [multiset::insert](../standard-library/multiset-class.md#insert)。

## <a name="unordered_multisetiterator"></a><a name="iterator"></a> unordered_multiset：： iterator

這是一種類型，提供可讀取 unordered_multiset 中元素的常數[正向迭代器](../standard-library/forward-iterator-tag-struct.md)。

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>範例

如需如何宣告及使用 **iterator** 的範例，請參閱 [begin](../standard-library/multiset-class.md#begin) 的範例。

## <a name="unordered_multisetkey_eq"></a><a name="key_eq"></a> unordered_multiset：： key_eq

取得儲存的比較函式物件。

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回儲存的比較函式物件

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_key_eq.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
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

## <a name="unordered_multisetkey_equal"></a><a name="key_equal"></a> unordered_multiset：： key_equal

比較函式的類型。

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Pred` 的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_key_equal.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
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

## <a name="unordered_multisetkey_type"></a><a name="key_type"></a> unordered_multiset：： key_type

排序索引鍵的類型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Key` 的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_key_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="unordered_multisetload_factor"></a><a name="load_factor"></a> unordered_multiset：： load_factor

計算每個值區的平均項目數。

```cpp
float load_factor() const;
```

### <a name="remarks"></a>備註

成員函式會傳回 `(float)` [unordered_multiset：： size](#size) `() / (float)` [unordered_multiset：： bucket_count](#bucket_count) `()` ，也就是每個值區的平均元素數。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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

## <a name="unordered_multisetlocal_iterator"></a><a name="local_iterator"></a> unordered_multiset：： local_iterator

值區迭代器的類型。

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>備註

此類型說明可做為值區之正向迭代器的物件。 在此將其說明為實作定義類型 `T4`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="unordered_multisetmax_bucket_count"></a><a name="max_bucket_count"></a> unordered_multiset：： max_bucket_count

取得 Bucket 最大數目。

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回目前允許的最大值區數目。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="unordered_multisetmax_load_factor"></a><a name="max_load_factor"></a> unordered_multiset：： max_load_factor

取得或設定每個 Bucket 最大項目數。

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>參數

*因素*\
新的最大載入因數。

### <a name="remarks"></a>備註

第一個成員函式會傳回儲存的最大載入因數。 第二個成員函式會以 *因數*取代儲存的最大載入因數。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="unordered_multisetmax_size"></a><a name="max_size"></a> unordered_multiset：： max_size

取得受控制序列的大小上限。

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>備註

成員函式會傳回物件可以控制的最長序列的長度。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_max_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
}
```

```Output
max_size() == 4294967295
```

## <a name="unordered_multisetoperator"></a><a name="op_eq"></a> unordered_multiset：： operator =

複製雜湊資料表。

```cpp
unordered_multiset& operator=(const unordered_multiset& right);

unordered_multiset& operator=(unordered_multiset&& right);
```

### <a name="parameters"></a>參數

*對*\
複製到 `unordered_multiset` 的 [unordered_multiset](../standard-library/unordered-multiset-class.md)。

### <a name="remarks"></a>備註

清除中的任何現有元素之後 `unordered_multiset` ，會 `operator=` 將 *右邊* 的內容複寫或移動到 `unordered_multiset` 。

### <a name="example"></a>範例

```cpp
// unordered_multiset_operator_as.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

int main( )
{
    using namespace std;
    unordered_multiset<int> v1, v2, v3;
    unordered_multiset<int>::iterator iter;

    v1.insert(10);

    cout << "v1 = " ;
    for (iter = v1.begin(); iter != v1.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    v2 = v1;
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    // move v1 into v2
    v2.clear();
    v2 = move(v1);
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;
}
```

## <a name="unordered_multisetpointer"></a><a name="pointer"></a> unordered_multiset：:p ointer

項目的指標類型。

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之項目的指標。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << "[" << *p << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetreference"></a><a name="reference"></a> unordered_multiset：： reference

項目的參考類型。

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>備註

此類型所說明的物件可做為受控制序列之元素的參考。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << "[" << ref << "] ";
        }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="unordered_multisetrehash"></a><a name="rehash"></a> unordered_multiset：： rehash

重建雜湊資料表。

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>參數

*nbuckets*\
要求的值區數目。

### <a name="remarks"></a>備註

成員函式會將值區的數目變更為至少 *nbuckets* ，並視需要重建雜湊資料表。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_rehash.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
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
[c] [b] [a]
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

## <a name="unordered_multisetsize"></a><a name="size"></a> unordered_multiset：： size

計算元素的數目。

```cpp
size_type size() const;
```

### <a name="remarks"></a>備註

成員函式會傳回受控制序列的長度。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="unordered_multisetsize_type"></a><a name="size_type"></a> unordered_multiset：： size_type

兩個項目之間不帶正負號距離的類型。

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>備註

此不帶正負號的整數類型所描述的物件可代表任何受控制序列的長度。 在此將其說明為實作定義類型 `T2`的同義字。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_size_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;
    Myset::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
}
```

```Output
size == 0
```

## <a name="unordered_multisetswap"></a><a name="swap"></a> unordered_multiset：： swap

交換兩個容器的內容。

```cpp
void swap(unordered_multiset& right);
```

### <a name="parameters"></a>參數

*對*\
要交換的容器。

### <a name="remarks"></a>備註

成員函式會交換和右邊的受控制序列 **`*this`** 。 *right* 如果[unordered_multiset：： get_allocator](#get_allocator) `() == right.get_allocator()` ，它會以常數時間來執行，只會在複製類型的預存特性物件時擲回例外狀況， `Tr` 而且不會使指定兩個受控制序列中元素的任何參考、指標或反覆運算器失效。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents "[f] [e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="unordered_multisetunordered_multiset"></a><a name="unordered_multiset"></a> unordered_multiset：： unordered_multiset

建構容器物件。

```cpp
unordered_multiset(
    const unordered_multiset& Right);

explicit unordered_multiset(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());

unordered_multiset(
    unordered_multiset&& Right);

unordered_set(
    initializer_list<Type> IList);

unordered_set(
    initializer_list<Typ> IList,
    size_type Bucket_count);

unordered_set(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    const Key& Key);

unordered_set(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    const Key& Key,
    const Allocator& Al);

template <class InputIterator>
unordered_multiset(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>參數

*InputIterator*\
迭代器類型。

*鋁*\
要儲存的配置器物件。

*壓縮*\
要儲存的比較函式物件。

*散 列*\
要儲存的雜湊函式物件。

*Bucket_count*\
Bucket 最小數目。

*對*\
要複製的容器。

*IList*\
要從中複製的 initializer_list。

### <a name="remarks"></a>備註

第一個函式會指定 *Right*所控制之序列的複本。 第二個建構函式會指定空白的受控制序列。 第三個建構函式會插入項目值序列 `[First, Last)`。 第四個函式會藉由 *向右*移動來指定序列的複本。

所有建構函式也會初始化數個儲存值。 若為複製的函式，則會從 *右邊*取得值。 否則：

值區的最小數目為引數 *Bucket_count*（如果有的話）。否則，它是以實值形式描述的預設值 `N0` 。

雜湊函式物件是引數 *雜湊*（如果有的話）。否則就是 `Hash()` 。

比較函式物件是引數 *Comp*（如果有的話）。否則就是 `Comp()` 。

配置器物件是引數 *Al*（如果有的話）。否則，就是 `Alloc()` 。

## <a name="unordered_multisetvalue_type"></a><a name="value_type"></a> unordered_multiset：： value_type

項目的類型。

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>備註

此類型描述受控制序列的項目。

### <a name="example"></a>範例

```cpp
// std__unordered_set__unordered_multiset_value_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="see-also"></a>另請參閱

[<unordered_set>](../standard-library/unordered-set.md)\
[容器](./stl-containers.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
