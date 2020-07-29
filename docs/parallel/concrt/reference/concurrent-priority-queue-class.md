---
title: concurrent_priority_queue 類別
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 024bd2a100b8a0b871d98a5e6001858b55977565
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230359"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue 類別

`concurrent_priority_queue` 類別允許多個執行緒同時推入和彈出項目。 項目會以優先權順序做為彈出依據，而優先權由函式提供的樣板引數決定。

## <a name="syntax"></a>語法

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>參數

*T*<br/>
要儲存在優先權佇列中之項目的資料類型。

*_Compare*<br/>
函式物件的類型，可用來比較兩個項目值做為排序鍵，以判斷其在優先權佇列中的相對順序。 這個引數是選用引數，且預設值是二元述詞 `less<T>`。

*_Ax*<br/>
代表預存配置器物件的類型，該物件會封裝有關配置和解除配置並行優先權佇列之記憶體的詳細資訊。 這個引數是選擇性的，而且預設值是 `allocator<T>`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|Name|說明|
|----------|-----------------|
|`allocator_type`|代表並行優先權佇列之配置器類別的類型。|
|`const_reference`|代表儲存在並行優先權佇列中的類型項目之常數參考的類型。|
|`reference`|代表儲存在並行優先權佇列中的類型項目參考的類型。|
|`size_type`|計算並行優先權佇列中項目數的類型。|
|`value_type`|代表並行優先權佇列中儲存之資料類型的類型。|

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|已多載。 建構並行優先權佇列。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[明確](#clear)|清除並行優先權中的所有項目。 這個方法不是並行安全的。|
|[empty](#empty)|測試呼叫這個方法時並行優先權佇列是否是空的。 這個方法是並行安全的。|
|[get_allocator](#get_allocator)|傳回用來建構並行優先權佇列之配置器的複本。 這個方法是並行安全的。|
|[push](#push)|已多載。 將項目加入至並行優先權佇列。 這個方法是並行安全的。|
|[size](#size)|傳回並行優先權佇列中的項目數。 這個方法是並行安全的。|
|[調換](#swap)|將兩個並行優先權佇列的內容交換。 這個方法不是並行安全的。|
|[try_pop](#try_pop)|如果佇列不是空的，則移除並傳回佇列中最高優先權的項目。 這個方法是並行安全的。|

### <a name="public-operators"></a>公用運算子

|Name|說明|
|----------|-----------------|
|[operator =](#operator_eq)|已多載。 將另一個物件的內容指派 `concurrent_priority_queue` 給這個物件。 這個方法不是並行安全的。|

## <a name="remarks"></a>備註

如需類別的詳細資訊 `concurrent_priority_queue` ，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`concurrent_priority_queue`

## <a name="requirements"></a>需求

**標頭：** concurrent_priority_queue。h

**命名空間：** 並行

## <a name="clear"></a><a name="clear"></a>明確

清除並行優先權中的所有項目。 這個方法不是並行安全的。

```cpp
void clear();
```

### <a name="remarks"></a>備註

`clear`不是並行安全。 當您呼叫這個方法時，您必須確定沒有任何其他執行緒在並行優先權佇列上叫用方法。 `clear`不會釋放記憶體。

## <a name="concurrent_priority_queue"></a><a name="ctor"></a>concurrent_priority_queue

建構並行優先權佇列。

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>參數

*_InputIterator*<br/>
輸入迭代器的類型。

*_Al*<br/>
搭配這個物件使用的配置器類別。

*_Init_capacity*<br/>
`concurrent_priority_queue` 物件的初始容量。

*_Begin*<br/>
要複製的元素範圍中第一個元素的位置。

*_End*<br/>
超出要複製之元素範圍的第一個元素的位置。

*_Src*<br/>
要從中複製或移動項目的來源 `concurrent_priority_queue` 物件。

### <a name="remarks"></a>備註

所有的函式都會儲存配置器物件 `_Al` 並初始化優先順序佇列。

第一個函式會指定空的初始優先順序佇列，並選擇性地指定配置器。

第二個函式會指定具有初始容量的優先順序佇列 `_Init_capacity` ，並選擇性地指定配置器。

第三個函式會指定反覆運算器範圍 [，）所提供的值 `_Begin` `_End` ，並選擇性地指定配置器。

第四個和第五個函式會指定優先順序佇列的複本 `_Src` 。

第六和第七個的函數會指定優先順序佇列的移動 `_Src` 。

## <a name="empty"></a><a name="empty"></a>空

測試呼叫這個方法時並行優先權佇列是否是空的。 這個方法是並行安全的。

```cpp
bool empty() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果在呼叫函數時，優先順序佇列是空的，則 **`false`** 為，否則為。

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

傳回用來建構並行優先權佇列之配置器的複本。 這個方法是並行安全的。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

用來建立物件的配置器複本 `concurrent_priority_queue` 。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將另一個物件的內容指派 `concurrent_priority_queue` 給這個物件。 這個方法不是並行安全的。

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
來源 `concurrent_priority_queue` 物件。

### <a name="return-value"></a>傳回值

這個物件的參考 `concurrent_priority_queue` 。

## <a name="push"></a><a name="push"></a>式

將項目加入至並行優先權佇列。 這個方法是並行安全的。

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>參數

*_Elem*<br/>
要加入至並行優先權佇列的元素。

## <a name="size"></a><a name="size"></a>容量

傳回並行優先權佇列中的項目數。 這個方法是並行安全的。

```cpp
size_type size() const;
```

### <a name="return-value"></a>傳回值

這個物件中的元素數目 `concurrent_priority_queue` 。

### <a name="remarks"></a>備註

傳回的大小保證會包含呼叫函式所新增的所有元素 `push` 。 不過，它可能不會反映暫止並行作業的結果。

## <a name="swap"></a><a name="swap"></a>調換

將兩個並行優先權佇列的內容交換。 這個方法不是並行安全的。

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>參數

*_Queue*<br/>
要交換內容的 `concurrent_priority_queue` 物件。

## <a name="try_pop"></a><a name="try_pop"></a>try_pop

如果佇列不是空的，則移除並傳回佇列中最高優先權的項目。 這個方法是並行安全的。

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>參數

*_Elem*<br/>
如果佇列不是空的，就會以最高優先順序的元素填入變數的參考。

### <a name="return-value"></a>傳回值

**`true`** 如果已彈出值，則 **`false`** 為，否則為。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)
