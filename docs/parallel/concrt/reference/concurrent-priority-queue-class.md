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
ms.openlocfilehash: 5804675ffdaf6de2e73327103398316566b41627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160031"
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue 類別

`concurrent_priority_queue` 類別允許多個執行緒同時推入和彈出項目。 項目會以優先權順序做為彈出依據，而優先權由函式提供的樣板引數決定。

## <a name="syntax"></a>語法

```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在優先權佇列中之項目的資料類型。

*_Compare*<br/>
函式物件的類型，可用來比較兩個項目值做為排序鍵，以判斷其在優先權佇列中的相對順序。 這個引數是選用引數，且預設值是二元述詞 `less<T>`。

*_Ax*<br/>
代表預存配置器物件的類型，該物件會封裝有關配置和解除配置並行優先權佇列之記憶體的詳細資訊。 這個引數是選擇性的，而且預設值是 `allocator<T>`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`allocator_type`|代表並行優先權佇列之配置器類別的類型。|
|`const_reference`|代表儲存在並行優先權佇列中的類型項目之常數參考的類型。|
|`reference`|代表儲存在並行優先權佇列中的類型項目參考的類型。|
|`size_type`|計算並行優先權佇列中項目數的類型。|
|`value_type`|代表並行優先權佇列中儲存之資料類型的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|多載。 建構並行優先權佇列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[clear](#clear)|清除並行優先權中的所有項目。 這個方法不是並行安全。|
|[empty](#empty)|測試呼叫這個方法時並行優先權佇列是否是空的。 這個方法是並行安全的。|
|[get_allocator](#get_allocator)|傳回用來建構並行優先權佇列之配置器的複本。 這個方法是並行安全的。|
|[push](#push)|多載。 將項目加入至並行優先權佇列。 這個方法是並行安全的。|
|[size](#size)|傳回並行優先權佇列中的項目數。 這個方法是並行安全的。|
|[swap](#swap)|將兩個並行優先權佇列的內容交換。 這個方法不是並行安全。|
|[try_pop](#try_pop)|如果佇列不是空的，則移除並傳回佇列中最高優先權的項目。 這個方法是並行安全的。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|多載。 將另一個內容指派`concurrent_priority_queue`如下的物件。 這個方法不是並行安全。|

## <a name="remarks"></a>備註

如需詳細資訊`concurrent_priority_queue`類別，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`concurrent_priority_queue`

## <a name="requirements"></a>需求

**標頭：** concurrent_priority_queue.h

**命名空間：** concurrency

##  <a name="clear"></a> 清除

清除並行優先權中的所有項目。 這個方法不是並行安全。

```
void clear();
```

### <a name="remarks"></a>備註

`clear` 不是並行安全。 您必須確定，沒有其他執行緒所叫用並行優先權佇列上的方法時呼叫這個方法。 `clear` 不會釋放記憶體。

##  <a name="ctor"></a> concurrent_priority_queue

建構並行優先權佇列。

```
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

所有建構函式會儲存配置器物件`_Al`和初始化優先權佇列。

第一個建構函式會指定空的初始優先權佇列，並選擇性地指定的配置器。

第二個建構函式會指定優先順序佇列的初始容量，`_Init_capacity`並選擇性地指定配置器。

第三個建構函式指定的值提供的迭代器範圍 [ `_Begin`， `_End`)，並選擇性地指定配置器。

第四個和第五個建構函式會指定一份優先順序佇列`_Src`。

第六個和第七個建構函式指定的優先順序佇列移動`_Src`。

##  <a name="empty"></a> empty

測試呼叫這個方法時並行優先權佇列是否是空的。 這個方法是並行安全的。

```
bool empty() const;
```

### <a name="return-value"></a>傳回值

**真**優先順序佇列是空的目前呼叫的函式，如果**false**否則。

##  <a name="get_allocator"></a> get_allocator

傳回用來建構並行優先權佇列之配置器的複本。 這個方法是並行安全的。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

一份用來建構的配置器`concurrent_priority_queue`物件。

##  <a name="operator_eq"></a> 運算子 =

將另一個內容指派`concurrent_priority_queue`如下的物件。 這個方法不是並行安全。

```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
來源 `concurrent_priority_queue` 物件。

### <a name="return-value"></a>傳回值

此參考`concurrent_priority_queue`物件。

##  <a name="push"></a> push

將項目加入至並行優先權佇列。 這個方法是並行安全的。

```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>參數

*_Elem*<br/>
要加入至並行優先權佇列項目。

##  <a name="size"></a> 大小

傳回並行優先權佇列中的項目數。 這個方法是並行安全的。

```
size_type size() const;
```

### <a name="return-value"></a>傳回值

在此的項目數`concurrent_priority_queue`物件。

### <a name="remarks"></a>備註

在傳回的大小一定會包含新增的函式呼叫的所有項目`push`。 不過，它可能無法反映的暫止的並行作業的結果。

##  <a name="swap"></a> swap

將兩個並行優先權佇列的內容交換。 這個方法不是並行安全。

```
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>參數

*_Queue*<br/>
`concurrent_priority_queue`来交換內容的物件。

##  <a name="try_pop"></a> try_pop

如果佇列不是空的，則移除並傳回佇列中最高優先權的項目。 這個方法是並行安全的。

```
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>參數

*_Elem*<br/>
將會填入最高的優先順序項目，如果佇列是空的變數參考。

### <a name="return-value"></a>傳回值

**真**值已推出 (pop)，如果**false**否則。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)
