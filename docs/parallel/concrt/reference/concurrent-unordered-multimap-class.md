---
title: concurrent_unordered_multimap 類別
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_multimap class
ms.assetid: 4dada5d7-15df-4382-b9c9-348e75b2f3c1
ms.openlocfilehash: fb03d368b7c9cced8961dbd77f22ab6bec40bc0d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230320"
---
# <a name="concurrent_unordered_multimap-class"></a>concurrent_unordered_multimap 類別

`concurrent_unordered_multimap` 類別是一種並行安全容器，可控制 `std::pair<const K, _Element_type>` 類型項目的不同長度序列。 序列的表示方式導致啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。

## <a name="syntax"></a>語法

```cpp
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_multimap : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
true>>;
```

### <a name="parameters"></a>參數

*K*<br/>
索引鍵類型。

*_Element_type*<br/>
對應的類型。

*_Hasher*<br/>
雜湊函式物件類型。 這個引數是選擇性的，而且預設值是 `std::hash<K>`。

*key_equality*<br/>
相等比較函式物件類型。 這個引數是選擇性的，而且預設值是 `std::equal_to<K>`。

*_Allocator_type*<br/>
代表預存配置器物件的類型，該物件會封裝並行向量之記憶體配置和解除配置的詳細資料。 這個引數是選擇性的，而且預設值是 `std::allocator<std::pair<K` 、 `_Element_type>>` 。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`allocator_type`|管理儲存體的配置器類型。|
|`const_iterator`|用於受控制序列的常數迭代器類型。|
|`const_local_iterator`|用於受控制序列的常數 Bucket 迭代器類型。|
|`const_pointer`|項目的常數指標類型。|
|`const_reference`|項目的常數參考類型。|
|`difference_type`|兩個項目之間帶正負號距離的類型。|
|`hasher`|雜湊函式的類型。|
|`iterator`|受控制序列之迭代器的類型。|
|`key_equal`|比較函式的類型。|
|`key_type`|排序索引鍵的類型。|
|`local_iterator`|用於受控制序列的 Bucket 迭代器類型。|
|`mapped_type`|與每個索引鍵關聯的對應值類型。|
|`pointer`|項目的指標類型。|
|`reference`|項目的參考類型。|
|`size_type`|兩個項目之間不帶正負號距離的類型。|
|`value_type`|項目的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[concurrent_unordered_multimap](#ctor)|已多載。 構造並行未排序的 multimap。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[hash_function](#hash_function)|傳回預存雜湊函式物件。|
|[insert](#insert)|已多載。 將元素加入至 `concurrent_unordered_multimap` 物件。|
|[key_eq](#key_eq)|傳回預存的相等比較函式物件。|
|[調換](#swap)|交換兩個 `concurrent_unordered_multimap` 物件的內容。 這個方法不是並行安全的。|
|[unsafe_erase](#unsafe_erase)|已多載。 從中的 `concurrent_unordered_multimap` 指定位置移除元素。 這個方法不是並行安全的。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[operator =](#operator_eq)|已多載。 將另一個物件的內容指派 `concurrent_unordered_multimap` 給這個物件。 這個方法不是並行安全的。|

## <a name="remarks"></a>備註

如需類別的詳細資訊 `concurrent_unordered_multimap` ，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_multimap`

## <a name="requirements"></a>需求

**標頭：** concurrent_unordered_map。h

**命名空間：** 並行

## <a name="begin"></a><a name="begin"></a>起點

傳回指向並行容器中第一個元素的反覆運算器。 這個方法是並行安全的。

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>傳回值

並行容器中第一個元素的反覆運算器。

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

傳回指向並行容器中第一個元素的 const 反覆運算器。 這個方法是並行安全的。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

並行容器中第一個元素的 const 反覆運算器。

## <a name="cend"></a><a name="cend"></a>cend

傳回常數反覆運算器，指向並行容器中最後一個元素後面的位置。 這個方法是並行安全的。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

在並行容器中最後一個元素後面的位置的常數反覆運算器。

## <a name="clear"></a><a name="clear"></a>明確

清除並行容器中的所有元素。 此函式不是並行保護。

```cpp
void clear();
```

## <a name="concurrent_unordered_multimap"></a><a name="ctor"></a>concurrent_unordered_multimap

構造並行未排序的 multimap。

```cpp
explicit concurrent_unordered_multimap(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multimap(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_multimap(
    concurrent_unordered_multimap&& _Umap);
```

### <a name="parameters"></a>參數

*_Iterator*<br/>
輸入迭代器的類型。

*_Number_of_buckets*<br/>
這個未排序多重對應的 Bucket 初始數量。

*_Hasher*<br/>
這個未排序多重對應的雜湊函式。

*key_equality*<br/>
這個未排序多重對應的相等比較函式。

*_Allocator*<br/>
這個未排序多重對應的配置器。

*_Begin*<br/>
要複製的元素範圍中第一個元素的位置。

*_End*<br/>
超出要複製之元素範圍的第一個元素的位置。

*_Umap*<br/>
`concurrent_unordered_multimap`要從中複製元素的來源物件。

### <a name="remarks"></a>備註

所有建構函式都會儲存配置器物件 `_Allocator` 並初始化未排序的多重對應。

第一個建構函式會指定空的初始多重對應，並明確指定要使用的 Bucket、雜湊函式、相等函式和配置器類型的數目。

第二個建構函式會為未排序多重對應指定配置器。

第三個函式會指定反覆運算器範圍 [，）所提供的值 `_Begin` `_End` 。

第四個和第五個建構函式會指定並行未排序之多重對應 `_Umap` 的複製作業。

最後一個建構函式會指定並行未排序之多重對應 `_Umap` 的移動作業。

## <a name="count"></a><a name="count"></a>計數

計算符合指定索引鍵的元素數目。 此函式為並行安全。

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的索引鍵。

### <a name="return-value"></a>傳回值

金鑰出現在容器中的次數。

## <a name="empty"></a><a name="empty"></a>空

測試項目是否不存在。 這個方法是並行安全的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果並行容器是空的，則為， **`false`** 否則為。

### <a name="remarks"></a>備註

如果並行插入存在，則在呼叫此函式之前，並行容器是否為空白可能會立即變更，甚至是在讀取傳回值之前。

## <a name="end"></a><a name="end"></a>成品

傳回反覆運算器，指向並行容器中最後一個元素後面的位置。 這個方法是並行安全的。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>傳回值

在並行容器中最後一個元素後面的位置的反覆運算器。

## <a name="equal_range"></a><a name="equal_range"></a>equal_range

尋找符合指定之索引鍵的範圍。 此函式為並行安全。

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的索引鍵值。

### <a name="return-value"></a>傳回值

一[組，其中第](../../../standard-library/pair-structure.md)一個專案是開始的反覆運算器，而第二個元素是範圍結尾的反覆運算器。

### <a name="remarks"></a>備註

並行插入可能會導致在開始反覆運算器之後和結束反覆運算器之前插入額外的索引鍵。

## <a name="find"></a><a name="find"></a>尋找

尋找符合指定之索引鍵的元素。 此函式為並行安全。

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的索引鍵值。

### <a name="return-value"></a>傳回值

反覆運算器，指向符合所提供之索引鍵之第一個專案的位置， `end()` 如果沒有這類元素存在，則為反覆運算器。

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

傳回此並行容器的預存配置器物件。 這個方法是並行安全的。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

此並行容器的預存配置器物件。

## <a name="hash_function"></a><a name="hash_function"></a>hash_function

傳回預存雜湊函式物件。

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>傳回值

儲存的雜湊函式物件。

## <a name="insert"></a><a name="insert"></a>插入

將元素加入至 `concurrent_unordered_multimap` 物件。

```cpp
iterator insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
iterator insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>參數

*_Iterator*<br/>
用來插入的迭代器類型。

*&*<br/>
插入對應中的數值型別。

*value*<br/>
要插入的值。

*_Where*<br/>
要搜尋插入點的起始位置。

*first*<br/>
要插入之範圍的開頭。

*last*<br/>
要插入之範圍的結尾。

### <a name="return-value"></a>傳回值

指向插入位置的迭代器。

### <a name="remarks"></a>備註

第一個成員函式會將 `value` 項目插入受控制的序列中，然後傳回指定所插入項目的迭代器。

第二個成員函式會傳回 insert （ `value` ），並使用 `_Where` 做為要搜尋插入點之受控制序列中的起始位置。

第三個成員函式會從範圍 [，）插入元素值的序列 `first` `last` 。

最後兩個成員函式的行為與前兩個相同，不過 `value` 是用來建構插入的值。

## <a name="key_eq"></a><a name="key_eq"></a>key_eq

傳回預存的相等比較函式物件。

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>傳回值

預存的相等比較函式物件。

## <a name="load_factor"></a><a name="load_factor"></a>load_factor

計算並傳回容器目前的載入因數。 負載因數是容器中的元素數目除以值區數目。

```cpp
float load_factor() const;
```

### <a name="return-value"></a>傳回值

容器的載入因數。

## <a name="max_load_factor"></a><a name="max_load_factor"></a>max_load_factor

取得或設定容器的最大載入因數。 最大載入因數是容器成長其內部資料表之前，可以在任何值區中的最大專案數。

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>參數

`_Newmax`

### <a name="return-value"></a>傳回值

第一個成員函式會傳回儲存的最大載入因數。 第二個成員函式不會傳回值，但如果提供的載入因數無效，則會擲回[out_of_range](../../../standard-library/out-of-range-class.md)例外狀況。

## <a name="max_size"></a><a name="max_size"></a>max_size

傳回配置器所決定的並行容器大小上限。 這個方法是並行安全的。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

可以插入此並行容器中的元素數目上限。

### <a name="remarks"></a>備註

此上限值實際上可能高於容器可以保存的內容。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將另一個物件的內容指派 `concurrent_unordered_multimap` 給這個物件。 這個方法不是並行安全的。

```cpp
concurrent_unordered_multimap& operator= (const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap& operator= (concurrent_unordered_multimap&& _Umap);
```

### <a name="parameters"></a>參數

*_Umap*<br/>
來源 `concurrent_unordered_multimap` 物件。

### <a name="return-value"></a>傳回值

這個物件的參考 `concurrent_unordered_multimap` 。

### <a name="remarks"></a>備註

在清除並行未排序的多重對應中的任何現有項目之後，`operator=` 會將 `_Umap` 的內容複製或移動至並行的未排序多重對應內。

## <a name="rehash"></a><a name="rehash"></a>rehash

重建雜湊資料表。

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>參數

*_Buckets*<br/>
所需的值區數目。

### <a name="remarks"></a>備註

此成員函式會將值區數目改變為至少 `_Buckets` ，並視需要重建雜湊資料表。 Bucket 的數目必須是2的乘冪。 如果不是2的乘冪，則會無條件進位到下一個最大的2乘冪。

如果 bucket 數目無效（0或大於最大值區數目），則會擲回[out_of_range](../../../standard-library/out-of-range-class.md)例外狀況。

## <a name="size"></a><a name="size"></a>容量

傳回這個並行容器中的項目數目。 這個方法是並行安全的。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

容器中的項目數目。

### <a name="remarks"></a>備註

有並行插入存在時，並行容器中的項目數可能會在呼叫這個函式之後立即變更，甚至會是在尚未讀取傳回值的情況下。

## <a name="swap"></a><a name="swap"></a>調換

交換兩個 `concurrent_unordered_multimap` 物件的內容。 這個方法不是並行安全的。

```cpp
void swap(concurrent_unordered_multimap& _Umap);
```

### <a name="parameters"></a>參數

*_Umap*<br/>
要交換的 `concurrent_unordered_multimap` 物件。

## <a name="unsafe_begin"></a><a name="unsafe_begin"></a>unsafe_begin

針對特定的值區，將反覆運算器傳回此容器中的第一個元素。

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>傳回值

指向值區開頭的反覆運算器。

## <a name="unsafe_bucket"></a><a name="unsafe_bucket"></a>unsafe_bucket

傳回特定索引鍵在此容器中對應的值區索引。

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的元素索引鍵。

### <a name="return-value"></a>傳回值

此容器中索引鍵的值區索引。

## <a name="unsafe_bucket_count"></a><a name="unsafe_bucket_count"></a>unsafe_bucket_count

傳回此容器中目前的 bucket 數目。

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>傳回值

此容器中目前的 bucket 數目。

## <a name="unsafe_bucket_size"></a><a name="unsafe_bucket_size"></a>unsafe_bucket_size

傳回此容器的特定 bucket 中的專案數。

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
要搜尋的值區。

### <a name="return-value"></a>傳回值

此容器中目前的 bucket 數目。

## <a name="unsafe_cbegin"></a><a name="unsafe_cbegin"></a>unsafe_cbegin

針對特定的值區，將反覆運算器傳回此容器中的第一個元素。

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>傳回值

指向值區開頭的反覆運算器。

## <a name="unsafe_cend"></a><a name="unsafe_cend"></a>unsafe_cend

將反覆運算器傳回至特定值區中最後一個元素後面的位置。

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>傳回值

指向值區開頭的反覆運算器。

## <a name="unsafe_end"></a><a name="unsafe_end"></a>unsafe_end

針對特定的值區，將反覆運算器傳回這個容器中的最後一個元素。

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
Bucket 索引。

### <a name="return-value"></a>傳回值

指向值區結尾的反覆運算器。

## <a name="unsafe_erase"></a><a name="unsafe_erase"></a>unsafe_erase

從中的 `concurrent_unordered_multimap` 指定位置移除元素。 這個方法不是並行安全的。

```cpp
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>參數

*_Where*<br/>
要清除的反覆運算器位置。

*KVal*<br/>
要清除的索引鍵值。

*first*<br/>
*last*<br/>
反覆運算.

### <a name="return-value"></a>傳回值

前兩個成員函式會傳回反覆運算器，指定移除任何元素之後剩餘的第一個元素， `concurrent_unordered_multimap::end` 如果沒有這類元素，則傳回（）。 第三個成員函式會傳回它所移除的元素數目。

### <a name="remarks"></a>備註

第一個成員函式會移除 `_Where` 所指向之受控制序列中的項目。 第二個成員函式會移除範圍 [，）中的元素 `_Begin` `_End` 。

第三個成員函式會移除範圍中以 `concurrent_unordered_multimap::equal_range` （KVal）分隔的元素。

## <a name="unsafe_max_bucket_count"></a><a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

傳回此容器中的最大值區數目。

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>傳回值

此容器中的 bucket 數目上限。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)
