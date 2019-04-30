---
title: completion_future 類別
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 663122c2d8cd430e921773e75dfd7975e4a41516
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405569"
---
# <a name="completionfuture-class"></a>completion_future 類別

代表未來對應至C++AMP 非同步處理操作。

### <a name="syntax"></a>語法

```
class completion_future;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[completion_future 建構函式](#ctor)|初始化 `completion_future` 類別的新執行個體。|
|[~ completion_future 解構函式](#dtor)|終結`completion_future`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|等候直到相關聯的非同步作業完成為止。|
|[then](#then)|鏈結的回呼函式物件`completion_future`執行相關聯的非同步作業完成時要執行的物件。|
|[to_task](#to_task)|傳回`task`對應至相關聯的非同步作業的物件。|
|[valid](#valid)|取得布林值，指出物件是否與非同步作業相關聯。|
|[wait](#wait)|封鎖直到相關聯的非同步作業完成為止。|
|[wait_for](#wait_for)|封鎖，直到相關聯的非同步作業完成或所指定的時間`_Rel_time`已過。|
|[wait_until](#wait_until)|封鎖直到相關聯的非同步作業完成或直到目前的時間超過指定的值`_Abs_time`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator std::shared_future\<void>](#operator_shared_future)|將隱含轉換`completion_future`物件至`std::shared_future`物件。|
|[operator=](#operator_eq)|將指定的內容複製`completion_future`到這個物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`completion_future`

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** concurrency

## <a name="ctor"></a> completion_future

初始化 `completion_future` 類別的新執行個體。

### <a name="syntax"></a>語法

```
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
`completion_future`複製或移動的物件。

### <a name="overloads-list"></a>多載清單

|名稱|描述|
|----------|-----------------|
|`completion_future();`|初始化的新執行個體`completion_future`類別|
|`completion_future(const completion_future& _Other);`|初始化的新執行個體`completion_future`藉由複製建構函式的類別。|
|`completion_future(completion_future&& _Other);`|初始化的新執行個體`completion_future`移動建構函式的類別。|

## <a name="get"></a> 取得

等候直到相關聯的非同步作業完成為止。 如果其中一個發生在非同步作業期間，會擲回的預存的例外狀況。

### <a name="syntax"></a>語法

```
void get() const;
```

## <a name="operator_shared_future"></a> operator std::shared_future<void>

將隱含轉換`completion_future`物件至`std::shared_future`物件。

### <a name="syntax"></a>語法

```
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>傳回值

`std::shared_future` 物件。

## <a name="operator_eq"></a> 運算子 =

將指定的內容複製`completion_future`到這個物件。

### <a name="syntax"></a>語法

```
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的物件。

### <a name="return-value"></a>傳回值

此參考`completion_future`物件。

## <a name="overloads-list"></a>多載清單

|名稱|描述|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|將指定的內容複製`completion_future`物件插入這個影片中，使用深層複本。|
|`completion_future& operator=(completion_future&& _Other);`|將指定的內容複製`completion_future`這個影片中，使用一個移動指派到的物件。|

## <a name="then"></a> 然後

鏈結的回呼函式物件`completion_future`執行相關聯的非同步作業完成時要執行的物件。

### <a name="syntax"></a>語法

```
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>參數

*_Functor*<br/>
回呼函式中。

*_Func*<br/>
回呼函式物件。

## <a name="to_task"></a> to_task

傳回`task`對應至相關聯的非同步作業的物件。

### <a name="syntax"></a>語法

```
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>傳回值

A`task`對應至相關聯的非同步作業的物件。

## <a name="valid"></a> 有效

取得布林值，該值會指出物件是否與非同步作業相關聯。

### <a name="syntax"></a>語法

```
bool valid() const;
```

### <a name="return-value"></a>傳回值

**真**的物件是否與非同步作業相關聯，否則**false**。

## <a name="wait"></a> 等候

封鎖直到相關聯的非同步作業完成為止。

### <a name="syntax"></a>語法

```
void wait() const;
```

## <a name="wait_for"></a> wait_for

封鎖，直到相關聯的非同步作業完成或所指定的時間`_Rel_time`已過。

### <a name="syntax"></a>語法

```
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>參數

*_Rep*<br/>
表示之刻度數的算術類型。

*_Period*<br/>
Std:: ratio 代表每刻度秒數。

*_Rel_time*<br/>
最大等待作業完成的時間量。

### <a name="return-value"></a>傳回值

會傳回：

- `std::future_status::deferred` 如果相關聯的非同步作業沒有在執行中。

- `std::future_status::ready` 如果關聯的非同步作業已完成。

- `std::future_status::timeout` 如果指定的時間期限。

## <a name="wait_until"></a> wait_until

封鎖直到相關聯的非同步作業完成或直到目前的時間超過指定的值`_Abs_time`。

### <a name="syntax"></a>語法

```
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>參數

*_Clock*<br/>
這個時點測量的時鐘。

*_Duration*<br/>
自啟動後的時間間隔`_Clock`的 epoch 之後，函式會逾時。

*_Abs_time*<br/>
之後，此函式會逾時的時間點。

### <a name="return-value"></a>傳回值

會傳回：

1. `std::future_status::deferred` 如果相關聯的非同步作業沒有在執行中。

1. `std::future_status::ready` 如果關聯的非同步作業已完成。

1. `std::future_status::timeout` 如果指定的時間期間已過。

## <a name="dtor"></a> ~completion_future

終結`completion_future`物件。

### <a name="syntax"></a>語法

```
~completion_future();
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
