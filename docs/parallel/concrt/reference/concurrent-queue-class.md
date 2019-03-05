---
title: concurrent_queue 類別
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: d5bbd361dc2dedc24c2a59050ffa680517186494
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304687"
---
# <a name="concurrentqueue-class"></a>concurrent_queue 類別


  `concurrent_queue` 類別是一種序列容器類別，允許以先進先出的方式存取其項目。 它會啟用一組有限的並行安全作業，例如 `push` 和 `try_pop` 等。

## <a name="syntax"></a>語法

```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在佇列中之項目的資料型別。

*_Ax*<br/>
代表預存配置器物件，封裝有關配置和解除配置之記憶體的並行佇列的詳細資訊的型別。 這個引數是選擇性的，而且預設值是 `allocator<T>`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`allocator_type`|代表並行佇列的配置器類別的類型。|
|`const_iterator`|表示非執行緒安全的型別`const`迭代器，透過並行佇列中的項目。|
|`const_reference`|提供的參考型別`const`供讀取和執行的並行佇列中儲存的項目`const`作業。|
|`difference_type`|提供的並行佇列中的兩個項目之間的帶正負號的距離的類型。|
|`iterator`|這種類型的並行佇列中的項目都代表非執行緒安全的迭代器。|
|`reference`|這種類型提供的並行佇列中預存項目的參考。|
|`size_type`|計算並行佇列中的項目數的類型。|
|`value_type`|代表並行佇列中儲存的資料類型的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[concurrent_queue](#ctor)|多載。 建構並行佇列。|
|[~ concurrent_queue 解構函式](#dtor)|終結的並行佇列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[clear](#clear)|清除並行佇列，並終結任何目前已加入佇列的項目。 這個方法不是並行安全。|
|[empty](#empty)|如果目前的並行佇列是空的測試會呼叫這個方法。 這個方法是並行安全的。|
|[get_allocator](#get_allocator)|傳回一份用來建構並行佇列的配置器。 這個方法是並行安全的。|
|[push](#push)|多載。 加入佇列的並行佇列在尾端項目。 這個方法是並行安全的。|
|[try_pop](#try_pop)|如果有的話，請清除佇列的佇列中的項目。 這個方法是並行安全的。|
|[unsafe_begin](#unsafe_begin)|多載。 傳回迭代器的型別`iterator`或`const_iterator`的並行佇列開頭。 這個方法不是並行安全。|
|[unsafe_end](#unsafe_end)|多載。 傳回迭代器的型別`iterator`或`const_iterator`並行佇列的結尾。 這個方法不是並行安全。|
|[unsafe_size](#unsafe_size)|傳回佇列中的項目數目。 這個方法不是並行安全。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`concurrent_queue`

## <a name="requirements"></a>需求

**標頭：** concurrent_queue.h

**命名空間：** concurrency

##  <a name="clear"></a> 清除

清除並行佇列，並終結任何目前已加入佇列的項目。 這個方法不是並行安全。

```
void clear();
```

##  <a name="ctor"></a> concurrent_queue

建構並行佇列。

```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>參數

*_InputIterator*<br/>
指定的值範圍的輸入迭代器類型。

*_Al*<br/>
搭配這個物件使用的配置器類別。

*_OtherQ*<br/>
要從中複製或移動項目的來源 `concurrent_queue` 物件。

*_Begin*<br/>
項目範圍中要複製的第一個項目位置。

*_End*<br/>
項目範圍之外要複製的第一個項目位置。

### <a name="remarks"></a>備註

所有建構函式會儲存配置器物件`_Al`和初始化佇列。

第一個建構函式指定空的初始佇列，並明確指定要使用的配置器類型。

第二個建構函式指定的並行佇列複本`_OtherQ`。

第三個建構函式會指定並行佇列 `_OtherQ` 的移動作業。

第四個建構函式指定的值提供的迭代器範圍 [ `_Begin`， `_End`)。

##  <a name="dtor"></a> ~concurrent_queue

終結的並行佇列。

```
~concurrent_queue();
```

##  <a name="empty"></a> empty

如果目前的並行佇列是空的測試會呼叫這個方法。 這個方法是並行安全的。

```
bool empty() const;
```

### <a name="return-value"></a>傳回值

**真**並行佇列是空的我們討論，目前如果**false**否則。

### <a name="remarks"></a>備註

雖然這個方法是並行安全方面的方法呼叫`push`， `try_pop`，和`empty`，它會檢查由呼叫執行緒的時間，傳回的值可能是不正確。

##  <a name="get_allocator"></a> get_allocator

傳回一份用來建構並行佇列的配置器。 這個方法是並行安全的。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

一份用來建構並行佇列的配置器。

##  <a name="push"></a> push

加入佇列的並行佇列在尾端項目。 這個方法是並行安全的。

```
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
要新增至佇列的項目。

### <a name="remarks"></a>備註

`push` 是並行安全的方法呼叫而言`push`， `try_pop`，和`empty`。

##  <a name="try_pop"></a> try_pop

如果有的話，請清除佇列的佇列中的項目。 這個方法是並行安全的。

```
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
若要儲存的清除佇列的項目位置的參考。

### <a name="return-value"></a>傳回值

**真**如果項目已經成功清除， **false**否則。

### <a name="remarks"></a>備註

如果項目已經成功清除，參數`_Dest`收到的清除佇列的值，保留在佇列中的原始值被損毀，以及此函數會傳回 **，則為 true**。 如果沒有任何項目來清除佇列，則此函數會傳回`false`而不封鎖和內容`_Dest`是未定義的參數。

`try_pop` 是並行安全的方法呼叫而言`push`， `try_pop`，和`empty`。

##  <a name="unsafe_begin"></a> unsafe_begin

傳回迭代器的型別`iterator`或`const_iterator`的並行佇列開頭。 這個方法不是並行安全。

```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>傳回值

迭代器的型別`iterator`或`const_iterator`並行佇列物件的開頭。

### <a name="remarks"></a>備註

迭代器`concurrent_queue`類別主要是偵錯時，執行速度很慢，以及反覆項目不是並行安全相對於其他佇列作業。

##  <a name="unsafe_end"></a> unsafe_end

傳回迭代器的型別`iterator`或`const_iterator`並行佇列的結尾。 這個方法不是並行安全。

```
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>傳回值

迭代器的型別`iterator`或`const_iterator`並行佇列的結尾。

### <a name="remarks"></a>備註

迭代器`concurrent_queue`類別主要是偵錯時，執行速度很慢，以及反覆項目不是並行安全相對於其他佇列作業。

##  <a name="unsafe_size"></a> unsafe_size

傳回佇列中的項目數目。 這個方法不是並行安全。

```
size_type unsafe_size() const;
```

### <a name="return-value"></a>傳回值

在並行佇列大小。

### <a name="remarks"></a>備註

`unsafe_size` 不是並行安全，而且可以產生不正確的結果，如果呼叫的方法呼叫同時`push`， `try_pop`，和`empty`。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
