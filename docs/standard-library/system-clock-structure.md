---
title: system_clock 結構
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 66710f94d96f069d6d388d6b49c76747c618a0d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557981"
---
# <a name="systemclock-structure"></a>system_clock 結構

代表以系統時鐘為基礎的「計時類型」。

## <a name="syntax"></a>語法

```cpp
struct system_clock;
```

## <a name="remarks"></a>備註

「計時類型」可用來取得目前的 UTC 時間。 此類型包含了 [duration](../standard-library/duration-class.md) 的具現化和類別樣板 [time_point](../standard-library/time-point-class.md)，並定義傳回時間的靜態成員函式 `now()`。

如果第一次呼叫 `now()` 傳回的值一律小於或等於後續呼叫 `now()` 所傳回的值，則時鐘具「單一性」。

如果時鐘具*單一性*且時鐘刻度之間的時間固定，則時鐘具「穩定性」。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`system_clock::duration`|`duration<rep, period>` 的同義字。|
|`system_clock::period`|與內含具現化 `duration` 時用來代表刻度期間的類型是同義字。|
|`system_clock::rep`|與 `duration` 內含具現化時用來代表時鐘刻度數目的類型是同義字。|
|`system_clock::time_point`|`time_point<Clock, duration>` 的同義字，其中 `Clock` 是計時類型本身的同義字，或與另一種根據相同 Epoch 且有相同巢狀 `duration` 類型的計時類型是同義字。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[from_time_t](#from_time_t)|靜態。 傳回最接近指定時間的 `time_point`。|
|[現在](#now)|靜態。 傳回目前時間。|
|[to_time_t](#to_time_t)|靜態。 傳回最接近指定 `time_point` 的 `time_t` 物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[system_clock::is_monotonic 常數](#is_monotonic_constant)|指定計時類型是否具單調性。|
|[system_clock::is_steady 常數](#is_steady_constant)|指定計時類型是否具穩定性。|

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t

靜態方法會傳回[time_point](../standard-library/time-point-class.md)估計最接近所表示的時間*Tm*。

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>參數

*Tm*<br/>
[time_t](../c-runtime-library/standard-types.md) 物件。

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic 常數

指定計時類型是否具單一性。

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>傳回值

在此實作中，`system_clock::is_monotonic`一律會傳回**false**。

### <a name="remarks"></a>備註

如果第一次呼叫 `now()` 傳回的值一律小於或等於後續呼叫 `now()` 所傳回的值，則時鐘具「單一性」。

## <a name="is_steady_constant"></a>  system_clock::is_steady 常數

指定計時類型是否具「穩定性」。

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>傳回值

在此實作中，`system_clock::is_steady`一律會傳回**false**。

### <a name="remarks"></a>備註

如果時鐘具[單一性](#is_monotonic_constant)且時鐘刻度之間的時間固定，則時鐘具「穩定性」。

## <a name="now"></a>  system_clock::now

靜態方法，會傳回目前的時間。

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>傳回值

[time_point](../standard-library/time-point-class.md) 物件，代表目前的時間。

## <a name="to_time_t"></a>  system_clock::to_time_t

靜態方法會傳回[time_t](../c-runtime-library/standard-types.md)估計最接近所表示的時間*時間*。

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>參數

*時間*<br/>
[time_point](../standard-library/time-point-class.md) 物件。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[steady_clock 結構](../standard-library/steady-clock-struct.md)<br/>
