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
ms.openlocfilehash: 1863f0908753fb05abb01cf1bd2e34dc6649e0a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228488"
---
# <a name="completion_future-class"></a>completion_future 類別

表示與 C++ AMP 非同步作業相對應的未來。

## <a name="syntax"></a>語法

```cpp
class completion_future;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[completion_future 的構造函式](#ctor)|初始化 `completion_future` 類別的新執行個體。|
|[~ completion_future 的析構函式](#dtor)|終結 `completion_future` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[get](#get)|等候相關聯的非同步作業完成。|
|[請](#then)|將回呼函式物件連結至 `completion_future` 物件，以在相關聯的非同步作業完成執行時執行。|
|[to_task](#to_task)|傳回 `task` 對應至相關聯非同步作業的物件。|
|[有效性](#valid)|取得布林值，指出物件是否與非同步作業相關聯。|
|[等候](#wait)|封鎖，直到相關聯的非同步作業完成為止。|
|[wait_for](#wait_for)|封鎖直到相關聯的非同步作業完成，或所指定的時間 `_Rel_time` 已過為止。|
|[wait_until](#wait_until)|封鎖直到相關聯的非同步作業完成，或直到目前的時間超過指定的值為止 `_Abs_time` 。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[運算子 std：： shared_future\<void>](#operator_shared_future)|隱含地將 `completion_future` 物件轉換成 `std::shared_future` 物件。|
|[operator =](#operator_eq)|將指定之物件的內容複寫 `completion_future` 到這個。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`completion_future`

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="completion_future"></a><a name="ctor"></a>completion_future

初始化 `completion_future` 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
`completion_future`要複製或移動的物件。

### <a name="overloads-list"></a>多載清單

|名稱|說明|
|----------|-----------------|
|`completion_future();`|初始化類別的新實例。 `completion_future`|
|`completion_future(const completion_future& _Other);`|藉由複製函式，初始化類別的新實例 `completion_future` 。|
|`completion_future(completion_future&& _Other);`|藉由移動函式，初始化類別的新實例 `completion_future` 。|

## <a name="get"></a><a name="get"></a>獲取

等候相關聯的非同步作業完成。 如果在非同步作業期間發現已儲存的例外狀況，則擲回。

### <a name="syntax"></a>語法

```cpp
void get() const;
```

## <a name="operator-stdshared_futurevoid"></a><a name="operator_shared_future"></a>運算子 std：： shared_future\<void>

隱含地將 `completion_future` 物件轉換成 `std::shared_future` 物件。

### <a name="syntax"></a>語法

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>傳回值

`std::shared_future` 物件。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將指定之物件的內容複寫 `completion_future` 到這個。

### <a name="syntax"></a>語法

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的來源物件。

### <a name="return-value"></a>傳回值

這個物件的參考 `completion_future` 。

## <a name="overloads-list"></a>多載清單

|名稱|說明|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|使用深層複製，將指定之物件的內容複寫 `completion_future` 到這個其中。|
|`completion_future& operator=(completion_future&& _Other);`|使用移動指派，將指定之物件的內容複寫 `completion_future` 到這個其中。|

## <a name="then"></a><a name="then"></a>請

將回呼函式物件連結至 `completion_future` 物件，以在相關聯的非同步作業完成執行時執行。

### <a name="syntax"></a>語法

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>參數

*_Functor*<br/>
回呼仿函數。

*_Func*<br/>
回呼函式物件。

## <a name="to_task"></a><a name="to_task"></a>to_task

傳回 `task` 對應至相關聯非同步作業的物件。

### <a name="syntax"></a>語法

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>傳回值

`task`對應至相關聯非同步作業的物件。

## <a name="valid"></a><a name="valid"></a>有效性

取得布林值，該值會指出物件是否與非同步作業相關聯。

### <a name="syntax"></a>語法

```cpp
bool valid() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果物件與非同步作業相關聯，則為，否則為 **`false`** 。

## <a name="wait"></a><a name="wait"></a>等候

封鎖，直到相關聯的非同步作業完成為止。

### <a name="syntax"></a>語法

```cpp
void wait() const;
```

## <a name="wait_for"></a><a name="wait_for"></a>wait_for

封鎖直到相關聯的非同步作業完成，或所指定的時間 `_Rel_time` 已過為止。

### <a name="syntax"></a>語法

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>參數

*_Rep*<br/>
表示刻度數目的算術類型。

*_Period*<br/>
Std：：比率，表示每個刻度所經過的秒數。

*_Rel_time*<br/>
等待作業完成的最長時間。

### <a name="return-value"></a>傳回值

傳回：

- `std::future_status::deferred`如果相關聯的非同步作業不在執行中，則為。

- `std::future_status::ready`如果相關聯的非同步作業已完成，則為。

- `std::future_status::timeout`如果指定的時間週期已過，則為。

## <a name="wait_until"></a><a name="wait_until"></a>wait_until

封鎖直到相關聯的非同步作業完成，或直到目前的時間超過指定的值為止 `_Abs_time` 。

### <a name="syntax"></a>語法

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>參數

*_Clock*<br/>
測量此時間點的時鐘。

*_Duration*<br/>
自開始 epoch 之後的時間間隔 `_Clock` ，在這之後，函數將會超時。

*_Abs_time*<br/>
函數將會超時的時間點。

### <a name="return-value"></a>傳回值

傳回：

1. `std::future_status::deferred`如果相關聯的非同步作業不在執行中，則為。

1. `std::future_status::ready`如果相關聯的非同步作業已完成，則為。

1. `std::future_status::timeout`如果指定的時間週期已過，則為。

## <a name="completion_future"></a><a name="dtor"></a>~ completion_future

終結 `completion_future` 物件。

### <a name="syntax"></a>語法

```cpp
~completion_future();
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間（C++ AMP）](concurrency-namespace-cpp-amp.md)
