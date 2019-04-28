---
title: concurrent_unordered_set 類別
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_set class
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
ms.openlocfilehash: 43bce15f001e0daee817d9dae345b5d0858f2baa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262537"
---
# <a name="concurrentunorderedset-class"></a>concurrent_unordered_set 類別

`concurrent_unordered_set`類別是並行安全容器，可控制不同長度序列的項目型別 k。序列的表示方式啟用並行安全附加、 項目存取、 迭代器存取及迭代器周遊作業。

## <a name="syntax"></a>語法

```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_set : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    false>>;
```

#### <a name="parameters"></a>參數

*K*<br/>
索引鍵類型。

*_Hasher*<br/>
雜湊函式物件類型。 這個引數是選擇性的，而且預設值是 `std::hash<K>`。

*key_equality*<br/>
相等比較函式物件類型。 這個引數是選擇性的，而且預設值是 `std::equal_to<K>`。

*_Allocator_type*<br/>
代表預存配置器物件，封裝有關配置和解除配置的記憶體供並行的未排序集合的詳細資訊的型別。 這個引數是選擇性的，而且預設值是 `std::allocator<K>`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
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
|`pointer`|項目的指標類型。|
|`reference`|項目的參考類型。|
|`size_type`|兩個項目之間不帶正負號距離的類型。|
|`value_type`|元素的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[concurrent_unordered_set](#ctor)|多載。 建構並行未排序的集合。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[hash_function](#hash_function)|傳回預存雜湊函式物件。|
|[insert](#insert)|多載。 將項目來加入`concurrent_unordered_set`物件。|
|[key_eq](#key_eq)|傳回儲存的相等比較函式物件。|
|[swap](#swap)|交換兩個內容`concurrent_unordered_set`物件。 這個方法不是並行安全。|
|[unsafe_erase](#unsafe_erase)|多載。 移除項目從`concurrent_unordered_set`位於指定位置。 這個方法不是並行安全。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|多載。 將另一個內容指派`concurrent_unordered_set`如下的物件。 這個方法不是並行安全。|

## <a name="remarks"></a>備註

如需詳細資訊`concurrent_unordered_set`類別，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_set`

## <a name="requirements"></a>需求

**標頭：** concurrent_unordered_set.h

**命名空間：** concurrency

##  <a name="begin"></a> begin

傳回迭代器，指向 並行容器中的第一個項目。 這個方法是並行安全。

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>傳回值

並行容器中第一個項目的迭代器。

##  <a name="cbegin"></a> cbegin

傳回指向並行容器中的第一個元素的 const 迭代器。 這個方法是並行安全。

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

並行容器中第一個項目的常數迭代器。

##  <a name="cend"></a> cend

傳回指向下一個位置定址，並行容器中的最後一個元素的 const 迭代器。 這個方法是並行安全。

```
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

Const 迭代器之後，並行容器中的最後一個元素的位置。

##  <a name="clear"></a> 清除

清除並行容器中的所有項目。 此函式不是並行安全。

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_set

建構並行未排序的集合。

```
explicit concurrent_unordered_set(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_set(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset);

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_set(
    concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>參數

*_Iterator*<br/>
輸入迭代器的類型。

*_Number_of_buckets*<br/>
這個未排序集合的 Bucket 初始數量。

*_Hasher*<br/>
這個未排序集合的雜湊函式。

*key_equality*<br/>
這個未排序集合的相等比較函式。

*_Allocator*<br/>
這個未排序集合的配置器。

*first*<br/>
*last*<br/>
*_Uset*<br/>
要從中複製或移動項目的來源 `concurrent_unordered_set` 物件。

### <a name="remarks"></a>備註

所有建構函式都會儲存配置器物件 `_Allocator` 並初始化未排序的集合。

第一個建構函式會指定空的初始集合，並明確指定要使用的 Bucket、雜湊函式、相等函式和配置器類型的數目。

第二個建構函式會指定未排序集合的配置器。

第三個建構函式指定的值提供的迭代器範圍 [ `_Begin`， `_End`)。

第四個和第五個建構函式會指定並行未排序之集合 `_Uset` 的複製作業。

最後一個建構函式會指定並行未排序之集合 `_Uset` 的移動作業。

##  <a name="count"></a> count

計算符合指定索引鍵的項目數目。 此函式是安全的並行存取。

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的索引鍵。

### <a name="return-value"></a>傳回值

出現在容器中的機碼次數時次數。

##  <a name="empty"></a> empty

測試項目是否不存在。 這個方法是並行安全。

```
bool empty() const;
```

### <a name="return-value"></a>傳回值

**真**並行容器是空的如果**false**否則。

### <a name="remarks"></a>備註

有並行插入存在時，並行容器是空的 zda bude 可能甚至讀取傳回值之前呼叫這個函式之後立即, 變更。

##  <a name="end"></a> 結束

傳回迭代器指向下一個位置定址，並行容器中的最後一個元素。 這個方法是並行安全。

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>傳回值

迭代器之後，並行容器中的最後一個元素的位置。

##  <a name="equal_range"></a> equal_range

尋找符合指定的索引鍵範圍。 此函式是安全的並行存取。

```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的索引鍵的值。

### <a name="return-value"></a>傳回值

A[配對](../../../standard-library/pair-structure.md)其中的第一個元素是開頭的迭代器，而第二個元素是迭代器範圍的結尾。

### <a name="remarks"></a>備註

就可能會造成額外的金鑰之後開始迭代器，以及結尾迭代器之前，要插入的並行插入。

##  <a name="find"></a> find

尋找符合指定之索引鍵的元素。 此函式是安全的並行存取。

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的索引鍵的值。

### <a name="return-value"></a>傳回值

迭代器，指向 比對提供的索引鍵的第一個元素的位置或迭代器`end()`如果沒有這類項目。

##  <a name="get_allocator"></a> get_allocator

傳回這個並行容器的預存配置器物件。 這個方法是並行安全。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

這個並行容器預存配置器物件。

##  <a name="hash_function"></a> hash_function

傳回預存雜湊函式物件。

```
hasher hash_function() const;
```

### <a name="return-value"></a>傳回值

儲存的雜湊函式物件。

##  <a name="insert"></a> insert

將項目來加入`concurrent_unordered_set`物件。

```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
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

*V*<br/>
插入至集合值的型別。

*value*<br/>
要插入的值。

*_Where*<br/>
要搜尋插入點的起始位置。

*first*<br/>
要插入之範圍的開頭。

*last*<br/>
要插入之範圍的結尾。

### <a name="return-value"></a>傳回值

迭代器和一個布林值包含一組。 請參閱 < 備註 > 一節，如需詳細資訊。

### <a name="remarks"></a>備註

第一個成員函式會判斷其索引鍵具有對等順序的序列中是否存在的項目 X `value`。 如果沒有，會建立這類項目 X，並將它與初始化`value`。 此函式接著會判斷迭代器`where`，其中指定 X。如果執行插入將會發生，則此函數會傳回`std::pair(where, true)`。 否則，它會傳回 `std::pair(where, false)`。

第二個成員函式會傳回 insert ( `value`)，並使用`_Where`做為起始的位置，在受控制序列中要搜尋插入點。

第三個成員函式會將元素值序列插入從範圍 [ `first`， `last`)。

最後兩個成員函式的行為與前兩個相同，不過 `value` 是用來建構插入的值。

##  <a name="key_eq"></a> key_eq

傳回儲存的相等比較函式物件。

```
key_equal key_eq() const;
```

### <a name="return-value"></a>傳回值

儲存的相等比較函式物件。

##  <a name="load_factor"></a> load_factor

計算並傳回目前的載入因數，容器。 載入因數是除以貯體數目的容器中的項目數。

```
float load_factor() const;
```

### <a name="return-value"></a>傳回值

容器的載入因數。

##  <a name="max_load_factor"></a> max_load_factor

取得或設定容器的最大載入因數。 最大載入因數是最大項目數，比可以先貯體中容器會增加其內部的資料表。

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>參數

`_Newmax`

### <a name="return-value"></a>傳回值

第一個成員函式會傳回儲存的最大載入因數。 第二個成員函式不會傳回值，但會擲回[out_of_range](../../../standard-library/out-of-range-class.md)例外狀況，如果提供的載入因數無效...

##  <a name="max_size"></a> max_size

傳回並行容器，取決於配置器的大小上限。 這個方法是並行安全。

```
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

可以插入到這個並行容器的項目數目上限。

### <a name="remarks"></a>備註

此上限值實際上可能會高於什麼容器可以實際保留的。

##  <a name="operator_eq"></a> 運算子 =

將另一個內容指派`concurrent_unordered_set`如下的物件。 這個方法不是並行安全。

```
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>參數

*_Uset*<br/>
來源 `concurrent_unordered_set` 物件。

### <a name="return-value"></a>傳回值

此參考`concurrent_unordered_set`物件。

### <a name="remarks"></a>備註

在清除並行未排序集合中的任何現有項目之後，`operator=` 會將 `_Uset` 的內容複製或移動至並行的未排序集合內。

##  <a name="rehash"></a> rehash

重建雜湊資料表。

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>參數

*_Buckets*<br/>
所需的貯體數目。

### <a name="remarks"></a>備註

此成員函式會將值區數目改變為至少 `_Buckets` ，並視需要重建雜湊資料表。 貯體數目必須是 2 的乘冪。 如果不 2 的乘冪，它會無條件進位到下一個最大 2 的乘冪。

它會擲回[out_of_range](../../../standard-library/out-of-range-class.md)如果貯體數目不正確的例外狀況 （0 或大於最大貯體數目）。

##  <a name="size"></a> 大小

傳回這個並行容器中的項目數目。 這個方法是並行安全。

```
size_type size() const;
```

### <a name="return-value"></a>傳回值

容器中的項目數目。

### <a name="remarks"></a>備註

有並行插入存在時，並行容器中的項目數可能會在呼叫這個函式之後立即變更，甚至會是在尚未讀取傳回值的情況下。

##  <a name="swap"></a> swap

交換兩個內容`concurrent_unordered_set`物件。 這個方法不是並行安全。

```
void swap(concurrent_unordered_set& _Uset);
```

### <a name="parameters"></a>參數

*_Uset*<br/>
要交換的 `concurrent_unordered_set` 物件。

##  <a name="unsafe_begin"></a> unsafe_begin

傳回特定值區此容器中的第一個元素的迭代器。

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
貯體的索引。

### <a name="return-value"></a>傳回值

迭代器，指向值區的開頭。

##  <a name="unsafe_bucket"></a> unsafe_bucket

傳回特定索引鍵會對應至這個容器中的值區索引。

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>參數

*KVal*<br/>
要搜尋的項目索引鍵。

### <a name="return-value"></a>傳回值

此容器中的索引鍵的貯體索引。

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

在此容器中會傳回目前的值區數目。

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>傳回值

目前在此容器中的貯體數目。

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

傳回在特定的貯體中，此容器的項目數目。

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
若要搜尋的貯體。

### <a name="return-value"></a>傳回值

目前在此容器中的貯體數目。

##  <a name="unsafe_cbegin"></a> unsafe_cbegin

傳回特定值區此容器中的第一個元素的迭代器。

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
貯體的索引。

### <a name="return-value"></a>傳回值

迭代器，指向值區的開頭。

##  <a name="unsafe_cend"></a> unsafe_cend

傳回迭代器，之後在特定的貯體中的最後一個元素的位置。

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
貯體的索引。

### <a name="return-value"></a>傳回值

迭代器，指向值區的開頭。

##  <a name="unsafe_end"></a> unsafe_end

在這個特定值區的容器中的最後一個元素會傳回迭代器。

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>參數

*_Bucket*<br/>
貯體的索引。

### <a name="return-value"></a>傳回值

指向值區結尾迭代器。

##  <a name="unsafe_erase"></a> unsafe_erase

移除項目從`concurrent_unordered_set`位於指定位置。 這個方法不是並行安全。

```
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
若要清除從迭代器位置。

*KVal*<br/>
要清除的索引鍵的值。

*first*<br/>
*last*<br/>
迭代器。

### <a name="return-value"></a>傳回值

前兩個成員函式會傳回迭代器，指定移除任何項目之外剩餘的第一個元素或[結束](#end)（)，如果沒有這類項目。 第三個成員函式會傳回它所移除的項目數目。

### <a name="remarks"></a>備註

第一個成員函式會移除所指向的項目`_Where`。 第二個成員函式範圍中移除的項目 [ `_Begin`， `_End`)。

第三個成員函式所分隔之範圍中移除的項目[equal_range](#equal_range)(KVal)。

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

在此容器中傳回值區的數目上限。

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>傳回值

此容器中的值區數目上限。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)
