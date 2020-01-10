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
ms.openlocfilehash: 7f87ead486d635c933ad356f9868c22344601eda
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298614"
---
# <a name="concurrent_queue-class"></a>concurrent_queue 類別

`concurrent_queue` 類別是一種序列容器類別，允許以先進先出的方式存取其項目。 它會啟用一組有限的並行安全作業，例如 `push` 和 `try_pop` 等。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。

## <a name="syntax"></a>語法

```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在佇列中之元素的資料類型。

*_Ax*<br/>
代表預存配置器物件的類型，其會封裝此並行佇列之記憶體配置和解除配置的詳細資料。 這個引數是選擇性的，而且預設值是 `allocator<T>`。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公用 Typedefs

|Name|描述|
|----------|-----------------|
|`allocator_type`|代表並行佇列之配置器類別的類型。|
|`const_iterator`|一種類型，代表並行佇列中專案上的非安全線程 `const` 反覆運算器。|
|`const_reference`|一種類型，提供儲存在並行佇列中以供讀取和執行 `const` 作業之 `const` 元素的參考。|
|`difference_type`|一種類型，可在並行佇列中的兩個元素之間提供帶正負號的距離。|
|`iterator`|一種類型，代表並行佇列中專案上的非執行緒安全反覆運算器。|
|`reference`|一種類型，提供儲存在並行佇列中之專案的參考。|
|`size_type`|一種類型，可計算並行佇列中的元素數目。|
|`value_type`|類型，表示儲存在並行佇列中的資料類型。|

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[concurrent_queue](#ctor)|多載。 構造並行佇列。|
|[~ concurrent_queue 的析構函式](#dtor)|損毀並行佇列。|

### <a name="public-methods"></a>公用方法

|Name|描述|
|----------|-----------------|
|[clear](#clear)|清除並行佇列，終結任何目前已排入佇列的元素。 這個方法不是並行安全的。|
|[empty](#empty)|測試呼叫這個方法時，並行佇列是否為空白。 這個方法是並行安全的。|
|[get_allocator](#get_allocator)|傳回用來建立並行佇列之配置器的複本。 這個方法是並行安全的。|
|[push](#push)|多載。 將並行佇列結尾處的專案。 這個方法是並行安全的。|
|[try_pop](#try_pop)|從佇列中清除專案（如果有的話）。 這個方法是並行安全的。|
|[unsafe_begin](#unsafe_begin)|多載。 傳回 `iterator` 類型或 `const_iterator` 到並行佇列開頭的反覆運算器。 這個方法不是並行安全的。|
|[unsafe_end](#unsafe_end)|多載。 傳回 `iterator` 類型或 `const_iterator` 到並行佇列結尾的反覆運算器。 這個方法不是並行安全的。|
|[unsafe_size](#unsafe_size)|傳回佇列中的專案數。 這個方法不是並行安全的。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`concurrent_queue`

## <a name="requirements"></a>需求

**標頭：** concurrent_queue。h

**命名空間：** concurrency

##  <a name="clear"></a>明確

清除並行佇列，終結任何目前已排入佇列的元素。 這個方法不是並行安全的。

```
void clear();
```

##  <a name="ctor"></a>concurrent_queue

構造並行佇列。

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
指定值範圍之輸入反覆運算器的類型。

*_Al*<br/>
搭配這個物件使用的配置器類別。

*_OtherQ*<br/>
要從中複製或移動項目的來源 `concurrent_queue` 物件。

*_Begin*<br/>
項目範圍中要複製的第一個項目位置。

*_End*<br/>
項目範圍之外要複製的第一個項目位置。

### <a name="remarks"></a>備註

所有的函式都會儲存配置器物件 `_Al` 並初始化佇列。

第一個函式會指定空的初始佇列，並明確指定要使用的配置器類型。

第二個函式會指定並行佇列 `_OtherQ`的複本。

第三個建構函式會指定並行佇列 `_OtherQ` 的移動作業。

第四個函式會指定反覆運算器範圍 [`_Begin`，`_End`）所提供的值。

##  <a name="dtor"></a>~ concurrent_queue

損毀並行佇列。

```
~concurrent_queue();
```

##  <a name="empty"></a>空

測試呼叫這個方法時，並行佇列是否為空白。 這個方法是並行安全的。

```
bool empty() const;
```

### <a name="return-value"></a>傳回值

如果在我們查看的當時並行佇列是空的，**則為 true** ，否則為**false** 。

### <a name="remarks"></a>備註

雖然這個方法在並行處理方面是安全的，但對於 `push`、`try_pop`和 `empty`的方法呼叫而言，傳回的值可能會因呼叫執行緒檢查的時間而不正確。

##  <a name="get_allocator"></a>get_allocator

傳回用來建立並行佇列之配置器的複本。 這個方法是並行安全的。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>傳回值

用來建立並行佇列的配置器複本。

##  <a name="push"></a>式

將並行佇列結尾處的專案。 這個方法是並行安全的。

```
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>參數

*_Src*<br/>
要加入至佇列的專案。

### <a name="remarks"></a>備註

`push` 對於 `push`、`try_pop`和 `empty`方法的呼叫而言，是並行安全的。

##  <a name="try_pop"></a>try_pop

從佇列中清除專案（如果有的話）。 這個方法是並行安全的。

```
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
位置的參考，用來儲存已清除佇列的專案。

### <a name="return-value"></a>傳回值

如果已成功將專案取消佇列，**則為 true** ，否則為**false** 。

### <a name="remarks"></a>備註

如果專案已成功地清除佇列，參數 `_Dest` 會收到已清除佇列的值，保留在佇列中的原始值會終結，而此函數會傳回**true**。 如果沒有要清除佇列的專案，此函式會傳回 `false` 但不會封鎖，且 `_Dest` 參數的內容會是未定義的。

`try_pop` 對於 `push`、`try_pop`和 `empty`方法的呼叫而言，是並行安全的。

##  <a name="unsafe_begin"></a>unsafe_begin

傳回 `iterator` 類型或 `const_iterator` 到並行佇列開頭的反覆運算器。 這個方法不是並行安全的。

```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>傳回值

`iterator` 或 `const_iterator` 至並行佇列物件開頭的類型反覆運算器。

### <a name="remarks"></a>備註

`concurrent_queue` 類別的反覆運算器主要是用來進行偵錯工具，因為它們的速度很慢，而且反覆運算與其他佇列作業無關，而不是並行安全。

##  <a name="unsafe_end"></a>unsafe_end

傳回 `iterator` 類型或 `const_iterator` 到並行佇列結尾的反覆運算器。 這個方法不是並行安全的。

```
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>傳回值

`iterator` 或 `const_iterator` 至並行佇列結尾的類型反覆運算器。

### <a name="remarks"></a>備註

`concurrent_queue` 類別的反覆運算器主要是用來進行偵錯工具，因為它們的速度很慢，而且反覆運算與其他佇列作業無關，而不是並行安全。

##  <a name="unsafe_size"></a>unsafe_size

傳回佇列中的專案數。 這個方法不是並行安全的。

```
size_type unsafe_size() const;
```

### <a name="return-value"></a>傳回值

並行佇列的大小。

### <a name="remarks"></a>備註

`unsafe_size` 不是並行安全的，而且如果同時呼叫 `push`、`try_pop`和 `empty`方法時，就會產生不正確的結果。

## <a name="see-also"></a>請參閱

[concurrency 命名空間](concurrency-namespace.md)
