---
title: concurrent_vector 類別
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 9144fd0870bfb72e923a7271ffdd655e03a9bd57
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215838"
---
# <a name="concurrent_vector-class"></a>concurrent_vector 類別

`concurrent_vector` 類別是一種序列容器類別，允許以隨機方式存取任何項目。 它會啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。

## <a name="syntax"></a>語法

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>參數

*T*<br/>
要儲存在向量中之元素的資料類型。

*_Ax*<br/>
代表預存配置器物件的類型，該物件會封裝並行向量之記憶體配置和解除配置的詳細資料。 這個引數是選擇性的，而且預設值是 `allocator<T>`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`allocator_type`|類型，表示並行向量的配置器類別。|
|`const_iterator`|一種類型，提供可讀取 **`const`** 並行向量中元素的隨機存取反覆運算器。|
|`const_pointer`|一種類型，提供對 **`const`** 並行向量中之元素的指標。|
|`const_reference`|一種類型，提供 **`const`** 儲存在並行向量中以供讀取和執行作業之元素的參考 **`const`** 。|
|`const_reverse_iterator`|一種類型，提供可讀取並行向量中任何元素的隨機存取反覆運算器 **`const`** 。|
|`difference_type`|一種類型，提供並行向量中兩個元素之間的帶正負號距離。|
|`iterator`|一種類型，提供可讀取並行向量中任何元素的隨機存取反覆運算器。 使用 iterator 來修改元素並不是並行安全的。|
|`pointer`|一種類型，提供並行向量中專案的指標。|
|`reference`|一種類型，提供儲存在並行向量中之元素的參考。|
|`reverse_iterator`|一種類型，提供可讀取反轉並行向量中任何元素的隨機存取反覆運算器。 使用 iterator 來修改元素並不是並行安全的。|
|`size_type`|一種類型，可計算並行向量中的元素數目。|
|`value_type`|類型，表示儲存在並行向量中的資料類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[concurrent_vector](#ctor)|已多載。 構造並行向量。|
|[~ concurrent_vector 的析構函式](#dtor)|清除所有元素並終結這個並行向量。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[assign](#assign)|已多載。 清除並行向量的專案，並指派給它的兩個 `_N` 複本 `_Item` ，或是反覆運算器範圍 [，）指定的值 `_Begin` `_End` 。 這個方法不是並行安全的。|
|[at](#at)|已多載。 提供在並行向量中指定索引處之專案的存取權。 這種方法對於讀取作業而言是並行安全的，而且在成長向量時，只要確定值 `_Index` 小於並行向量的大小即可。|
|[返回](#back)|已多載。 傳回對 **`const`** 並行向量中最後一個元素的參考或參考。 如果並行向量是空的，則傳回值為未定義。 這個方法是並行安全的。|
|[起點](#begin)|已多載。 傳回類型的反覆運算器 `iterator` 或 `const_iterator` 並行向量的開頭。 這個方法是並行安全的。|
|[存儲](#capacity)|傳回並行向量可成長的最大大小，而不需要配置更多記憶體。 這個方法是並行安全的。|
|[cbegin](#cbegin)|將類型的反覆運算器傳回 `const_iterator` 至並行向量的開頭。 這個方法是並行安全的。|
|[cend](#cend)|將類型的反覆運算器傳回 `const_iterator` 至並行向量的結尾。 這個方法是並行安全的。|
|[明確](#clear)|清除並行向量中的所有元素。 這個方法不是並行安全的。|
|[crbegin](#crbegin)|將類型的反覆運算器傳回 `const_reverse_iterator` 至並行向量的開頭。 這個方法是並行安全的。|
|[crend](#crend)|將類型的反覆運算器傳回 `const_reverse_iterator` 至並行向量的結尾。 這個方法是並行安全的。|
|[empty](#empty)|測試呼叫這個方法時，並行向量是否為空白。 這個方法是並行安全的。|
|[成品](#end)|已多載。 傳回類型的反覆運算器 `iterator` 或 `const_iterator` 並行向量的結尾。 這個方法是並行安全的。|
|[前端](#front)|已多載。 傳回對 **`const`** 並行向量中第一個元素的參考或參考。 如果並行向量是空的，則傳回值為未定義。 這個方法是並行安全的。|
|[get_allocator](#get_allocator)|傳回用來建立並行向量的配置器複本。 這個方法是並行安全的。|
|[grow_by](#grow_by)|已多載。 以元素成長此並行向量 `_Delta` 。 這個方法是並行安全的。|
|[grow_to_at_least](#grow_to_at_least)|會成長此並行向量，直到至少有個 `_N` 元素為止。 這個方法是並行安全的。|
|[max_size](#max_size)|傳回並行向量可以保存的元素數目上限。 這個方法是並行安全的。|
|[push_back](#push_back)|已多載。 將指定的專案附加至並行向量的結尾。 這個方法是並行安全的。|
|[rbegin](#rbegin)|已多載。 傳回類型的反覆運算器 `reverse_iterator` 或 `const_reverse_iterator` 並行向量的開頭。 這個方法是並行安全的。|
|[rend](#rend)|已多載。 傳回類型的反覆運算器 `reverse_iterator` 或 `const_reverse_iterator` 並行向量的結尾。 這個方法是並行安全的。|
|[留成](#reserve)|配置足夠的空間來將並行向量成長為大小， `_N` 而不需要在稍後配置更多記憶體。 這個方法不是並行安全的。|
|[調整](#resize)|已多載。 將並行向量的大小變更為所要求的大小，並視需要刪除或加入元素。 這個方法不是並行安全的。|
|[shrink_to_fit](#shrink_to_fit)|壓縮並行向量的內部標記法，以減少分散程度並優化記憶體使用量。 這個方法不是並行安全的。|
|[size](#size)|傳回並行向量中的元素數目。 這個方法是並行安全的。|
|[調換](#swap)|交換兩個並行向量的內容。 這個方法不是並行安全的。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[操作\[\]](#operator_at)|已多載。 提供在並行向量中指定索引處之專案的存取權。 這個方法是讀取作業的並行安全，而且在成長向量時，只要確定值 `_Index` 小於並行向量的大小就可以了。|
|[operator =](#operator_eq)|已多載。 將另一個物件的內容指派 `concurrent_vector` 給這個物件。 這個方法不是並行安全的。|

## <a name="remarks"></a>備註

如需類別的詳細資訊 `concurrent_vector` ，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>需求

**標頭：** concurrent_vector。h

**命名空間：** 並行

## <a name="assign"></a><a name="assign"></a>值賦

清除並行向量的專案，並指派給它的兩個 `_N` 複本 `_Item` ，或是反覆運算器範圍 [，）指定的值 `_Begin` `_End` 。 這個方法不是並行安全的。

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>參數

*_InputIterator*<br/>
指定之反覆運算器的類型。

*_N*<br/>
要複製到並行向量中的專案數。

*_Item*<br/>
參考用來填滿並行向量的值。

*_Begin*<br/>
來源範圍中第一個元素的反覆運算器。

*_End*<br/>
在來源範圍的最後一個元素之後的反覆運算器。

### <a name="remarks"></a>備註

`assign`不是並行安全。 當您呼叫這個方法時，您必須確定沒有任何其他執行緒在並行向量上叫用方法。

## <a name="at"></a><a name="at"></a>在

提供在並行向量中指定索引處之專案的存取權。 這種方法對於讀取作業而言是並行安全的，而且在成長向量時，只要確定值 `_Index` 小於並行向量的大小即可。

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>參數

*_Index*<br/>
要抓取之元素的索引。

### <a name="return-value"></a>傳回值

指定索引處之專案的參考。

### <a name="remarks"></a>備註

傳回非參考的函式版本 `at` **`const`** 不能用來從不同執行緒同時寫入專案。 您應該使用不同的同步處理物件，將並行讀取和寫入作業同步至相同的資料元素。

`out_of_range`如果 `_Index` 大於或等於並行向量的大小，且 `range_error` 索引適用于向量的已中斷部分，則方法會擲回。 如需向量可能如何中斷的詳細資訊，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="back"></a><a name="back"></a>返回

傳回對 **`const`** 並行向量中最後一個元素的參考或參考。 如果並行向量是空的，則傳回值為未定義。 這個方法是並行安全的。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>傳回值

**`const`** 並行向量中最後一個元素的參考或參考。

## <a name="begin"></a><a name="begin"></a>起點

傳回類型的反覆運算器 `iterator` 或 `const_iterator` 並行向量的開頭。 這個方法是並行安全的。

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `iterator` 或 `const_iterator` 並行向量的開頭。

## <a name="capacity"></a><a name="capacity"></a>存儲

傳回並行向量可成長的最大大小，而不需要配置更多記憶體。 這個方法是並行安全的。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>傳回值

並行向量可以成長而不必配置更多記憶體的大小上限。

### <a name="remarks"></a>備註

不同于 c + + 標準程式庫 `vector` ， `concurrent_vector` 如果物件配置更多記憶體，則不會移動現有的元素。

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

將類型的反覆運算器傳回 `const_iterator` 至並行向量的開頭。 這個方法是並行安全的。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `const_iterator` ，指向並行向量的開頭。

## <a name="cend"></a><a name="cend"></a>cend

將類型的反覆運算器傳回 `const_iterator` 至並行向量的結尾。 這個方法是並行安全的。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `const_iterator` ，指向並行向量的結尾。

## <a name="clear"></a><a name="clear"></a>明確

清除並行向量中的所有元素。 這個方法不是並行安全的。

```cpp
void clear();
```

### <a name="remarks"></a>備註

`clear`不是並行安全。 當您呼叫這個方法時，您必須確定沒有任何其他執行緒在並行向量上叫用方法。 `clear`不會釋放內部陣列。 若要釋放內部陣列，請在之後呼叫函式 `shrink_to_fit` `clear` 。

## <a name="concurrent_vector"></a><a name="ctor"></a>concurrent_vector

構造並行向量。

```cpp
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>參數

*M*<br/>
來源向量的配置器類型。

*_InputIterator*<br/>
輸入迭代器的類型。

*_Al*<br/>
搭配這個物件使用的配置器類別。

*_Vector*<br/>
要從中複製或移動項目的來源 `concurrent_vector` 物件。

*_N*<br/>
`concurrent_vector` 物件的初始容量。

*_Item*<br/>
已建立之物件中的元素值。

*_Begin*<br/>
項目範圍中要複製的第一個項目位置。

*_End*<br/>
項目範圍之外要複製的第一個項目位置。

### <a name="remarks"></a>備註

所有的函式都會儲存配置器物件 `_Al` 並初始化向量。

第一個函式會指定空的初始向量，並明確指定配置器類型。 要使用的。

第二個和第三個函式會指定並行向量的複本 `_Vector` 。

第四個建構函式會指定移動並行向量 `_Vector`。

第五個函式會指定類別之預設值專案的指定數目（ `_N` ）重複 `T` 。

第六個函數會指定值的（ `_N` ）元素重複 `_Item` 。

最後一個函式會指定反覆運算器範圍 [，）所提供的值 `_Begin` `_End` 。

## <a name="concurrent_vector"></a><a name="dtor"></a>~ concurrent_vector

清除所有元素並終結這個並行向量。

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a><a name="crbegin"></a>crbegin

將類型的反覆運算器傳回 `const_reverse_iterator` 至並行向量的開頭。 這個方法是並行安全的。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `const_reverse_iterator` ，指向並行向量的開頭。

## <a name="crend"></a><a name="crend"></a>crend

將類型的反覆運算器傳回 `const_reverse_iterator` 至並行向量的結尾。 這個方法是並行安全的。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `const_reverse_iterator` ，指向並行向量的結尾。

## <a name="empty"></a><a name="empty"></a>空

測試呼叫這個方法時，並行向量是否為空白。 這個方法是並行安全的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果在呼叫函數時，向量是空的，則 **`false`** 為，否則為。

## <a name="end"></a><a name="end"></a>成品

傳回類型的反覆運算器 `iterator` 或 `const_iterator` 並行向量的結尾。 這個方法是並行安全的。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `iterator` 或 `const_iterator` 並行向量的結尾。

## <a name="front"></a><a name="front"></a>前端

傳回對 **`const`** 並行向量中第一個元素的參考或參考。 如果並行向量是空的，則傳回值為未定義。 這個方法是並行安全的。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>傳回值

**`const`** 並行向量中第一個元素的參考或參考。

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

傳回用來建立並行向量的配置器複本。 這個方法是並行安全的。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

用來建立物件的配置器複本 `concurrent_vector` 。

## <a name="grow_by"></a><a name="grow_by"></a>grow_by

以元素成長此並行向量 `_Delta` 。 這個方法是並行安全的。

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>參數

*_Delta*<br/>
要附加至物件的元素數目。

*_Item*<br/>
用來初始化新元素的值。

### <a name="return-value"></a>傳回值

附加至第一個專案的反覆運算器。

### <a name="remarks"></a>備註

如果 `_Item` 未指定，則會預設建立新的專案。

## <a name="grow_to_at_least"></a><a name="grow_to_at_least"></a>grow_to_at_least

會成長此並行向量，直到至少有個 `_N` 元素為止。 這個方法是並行安全的。

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>參數

*_N*<br/>
物件的新大小下限 `concurrent_vector` 。

### <a name="return-value"></a>傳回值

指向附加序列開頭的反覆運算器; `_N` 如果未附加任何元素，則為索引處的專案。

## <a name="max_size"></a><a name="max_size"></a>max_size

傳回並行向量可以保存的元素數目上限。 這個方法是並行安全的。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

物件可以保存的元素數目上限 `concurrent_vector` 。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將另一個物件的內容指派 `concurrent_vector` 給這個物件。 這個方法不是並行安全的。

```cpp
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>參數

*M*<br/>
來源向量的配置器類型。

*_Vector*<br/>
來源 `concurrent_vector` 物件。

### <a name="return-value"></a>傳回值

這個物件的參考 `concurrent_vector` 。

## <a name="operator"></a><a name="operator_at"></a>operator []

提供在並行向量中指定索引處之專案的存取權。 這個方法是讀取作業的並行安全，而且在成長向量時，只要確定值 `_Index` 小於並行向量的大小就可以了。

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>參數

*_Index*<br/>
要抓取之元素的索引。

### <a name="return-value"></a>傳回值

指定索引處之專案的參考。

### <a name="remarks"></a>備註

傳回 `operator []` 非參考的版本 **`const`** 不能用來從不同執行緒同時寫入專案。 您應該使用不同的同步處理物件，將並行讀取和寫入作業同步至相同的資料元素。

不會執行界限檢查，以確保在 `_Index` 並行向量中是有效的索引。

## <a name="push_back"></a><a name="push_back"></a>push_back

將指定的專案附加至並行向量的結尾。 這個方法是並行安全的。

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>參數

*_Item*<br/>
要附加的值。

### <a name="return-value"></a>傳回值

附加至專案的反覆運算器。

## <a name="rbegin"></a><a name="rbegin"></a>rbegin

傳回類型的反覆運算器 `reverse_iterator` 或 `const_reverse_iterator` 並行向量的開頭。 這個方法是並行安全的。

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `reverse_iterator` 或 `const_reverse_iterator` 並行向量的開頭。

## <a name="rend"></a><a name="rend"></a>rend

傳回類型的反覆運算器 `reverse_iterator` 或 `const_reverse_iterator` 並行向量的結尾。 這個方法是並行安全的。

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>傳回值

類型的反覆運算器 `reverse_iterator` 或 `const_reverse_iterator` 並行向量的結尾。

## <a name="reserve"></a><a name="reserve"></a>留成

配置足夠的空間來將並行向量成長為大小， `_N` 而不需要在稍後配置更多記憶體。 這個方法不是並行安全的。

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>參數

*_N*<br/>
要為其保留空間的元素數目。

### <a name="remarks"></a>備註

`reserve`不是並行安全。 當您呼叫這個方法時，您必須確定沒有任何其他執行緒在並行向量上叫用方法。 在方法傳回之後，並行向量的容量可能會大於所要求的保留區。

## <a name="resize"></a><a name="resize"></a>調整

將並行向量的大小變更為所要求的大小，並視需要刪除或加入元素。 這個方法不是並行安全的。

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>參數

*_N*<br/>
並行向量的新大小。

*初始值*<br/>
如果新的大小大於原始大小，則會將新項目的值加入至向量。 如果省略此值，則會為新物件指派其類型的預設值。

### <a name="remarks"></a>備註

如果容器的大小小於所要求的大小，則會將元素加入至向量，直到達到所要求的大小為止。 如果容器的大小大於所要求的大小，則會刪除最接近容器結尾的元素，直到容器達到大小為止 `_N` 。 如果容器現在的大小與所要求的大小相同，則不會採取任何動作。

`resize`不是並行安全。 當您呼叫這個方法時，您必須確定沒有任何其他執行緒在並行向量上叫用方法。

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a>shrink_to_fit

壓縮並行向量的內部標記法，以減少分散程度並優化記憶體使用量。 這個方法不是並行安全的。

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>備註

這個方法會在內部重新配置記憶體移動元素，使所有反覆運算器失效。 `shrink_to_fit`不是並行安全。 當您呼叫此函式時，您必須確定沒有任何其他執行緒在並行向量上叫用方法。

## <a name="size"></a><a name="size"></a>容量

傳回並行向量中的元素數目。 這個方法是並行安全的。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

這個物件中的元素數目 `concurrent_vector` 。

### <a name="remarks"></a>備註

傳回的大小保證會包含透過呼叫函式所附加的所有元素 `push_back` ，或在叫用此方法之前完成的作業。 不過，它也可能包含透過並行呼叫任何成長方法所配置但仍在進行中的元素。

## <a name="swap"></a><a name="swap"></a>調換

交換兩個並行向量的內容。 這個方法不是並行安全的。

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>參數

*_Vector*<br/>
要交換內容的 `concurrent_vector` 物件。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)
