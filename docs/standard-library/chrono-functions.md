---
title: '&lt;chrono&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 85fdd413354b3f310d3315a80cf7da983cf6621d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416771"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; 函式

## <a name="duration_cast"></a>duration_cast

將 `duration` 物件轉換為指定的類型。

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);

template <class ToDuration, class Rep, class Period>
constexpr ToDuration floor(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration ceil(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration round(const duration<Rep, Period>& d);
```

### <a name="return-value"></a>傳回值

`duration` 類型的 `To` 物件，代表時間間隔 `Dur`，如果必須符合目標類型則會截斷。

### <a name="remarks"></a>備註

如果 `To` 是 `duration` 的具現化，此函式不會參與多載解析。

## <a name="time_point_cast"></a>time_point_cast

將 [time_point](../standard-library/time-point-class.md) 物件轉換為指定的類型。

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);

template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
floor(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
ceil(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
round(const time_point<Clock, Duration>& tp);
```

### <a name="return-value"></a>傳回值

具有 `time_point` 類型之持續時間的 `To` 物件。

### <a name="remarks"></a>備註

除非 `To` 是 [duration](../standard-library/duration-class.md) 的具現化，否則此函式不會參與多載解析。
