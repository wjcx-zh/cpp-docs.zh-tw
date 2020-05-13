---
title: 活動類別
description: C++生成見解 SDK 活動類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ea04150aec9c0b2366d97e6e4c15de557a4f47c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325252"
---
# <a name="activity-class"></a>活動類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Activity`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配任何活動事件。 請參閱[事件表](../event-table.md)`Activity`以查看 類可以匹配的所有事件。

## <a name="syntax"></a>語法

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>備註

`Activity`類中的多個成員函數返回刻度計數。 C++生成見解使用 Windows 的性能計數器作為報價源。 刻度計數必須與刻度頻率一起使用,才能將其轉換為時間單位(如秒)。 可以`TickFrequency`調用[事件](event.md)基類中可用的成員函數以獲取刻度頻率。 [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)頁顯示了將刻度轉換為時間單位的範例。

如果不想自己將刻度轉換為時間單位,則`Activity`類提供以納秒為單位返回時間值的成員函數。 使用標準C++`chrono`庫將其轉換為其他時間單位。

## <a name="members"></a>成員

除了從[Event](event.md)基類繼承的成員`Activity`外, 該類還包含以下成員:

### <a name="constructor"></a>建構函式

[活動](#activity)

### <a name="functions"></a>函式

[CPUTicks](#cpu-ticks)\
[CPU時間](#cpu-time)\
[時間](#duration)\
[獨家CPUTicks](#exclusive-cpu-ticks)\
[獨家CPU時間](#exclusive-cpu-time)\
[獨家持續時間](#exclusive-duration)\
[獨家持續時間提示](#exclusive-duration-ticks)\
[獨家華爾街時間責任](#exclusive-wall-clock-time-responsibility)\
[獨家華爾街時間責任提示](#exclusive-wall-clock-time-responsibility-ticks)\
[開始時間戳](#start-timestamp)\
[停止時間戳](#stop-timestamp)\
[牆鐘時間責任](#wall-clock-time-responsibility)\
[牆鐘時間責任提示](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a> 活動

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
任何活動事件。

## <a name="cputicks"></a><a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>傳回值

在此活動期間發生的 CPU 刻度數。 CPU 刻度不同於常規刻度。 僅當 CPU 在活動中執行代碼時,才會計算 CPU 刻度。 當與活動關聯的線程處於睡眠狀態時,不會計算 CPU 刻度。

## <a name="cputime"></a><a name="cpu-time"></a>CPU時間

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>傳回值

CPU 在此活動中執行代碼的時間量。 如果在單獨的線程上執行子活動,則此值可能高於活動的持續時間。 該值以納秒為單位返回。

## <a name="duration"></a><a name="duration"></a>時間

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>傳回值

活動持續時間(以納秒為單位)。

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>獨家CPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>傳回值

與[CPUTick 相同](#cpu-ticks),但不包括子活動中發生的 CPU 刻度。

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>獨家CPU時間

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>傳回值

與[CPUTime](#cpu-time)相同,但不包括子活動的 CPU 時間。

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>獨家持續時間

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>傳回值

活動持續時間(以納秒為單位),不包括在子活動中花費的時間量。

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>獨家持續時間提示

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>傳回值

在此活動中發生的刻度數,不包括子活動中發生的刻度數。

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>獨家華爾街時間責任

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>傳回值

與["牆鐘時間責任"](#wall-clock-time-responsibility)相同,但不包括兒童活動的掛鐘時間責任。

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>獨家華爾街時間責任提示

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>傳回值

與["牆鐘時間責任"相同](#wall-clock-time-responsibility-ticks),但不包括兒童活動的掛鐘時間責任。

## <a name="starttimestamp"></a><a name="start-timestamp"></a>開始時間戳

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>傳回值

活動開始時捕獲的刻度值。

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>停止時間戳

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>傳回值

活動停止時捕獲的刻度值。

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>牆鐘時間責任

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>傳回值

此活動的掛鐘時間責任,以納秒為單位。 有關掛鐘時間責任的含義的詳細資訊,請參閱[「掛時鐘時間責任提示](#wall-clock-time-responsibility-ticks)」。

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>牆鐘時間責任提示

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>傳回值

表示此活動對總掛鐘時間的貢獻的刻度計數。 掛鐘時間責任刻度不同於常規刻度。 鐘點時間責任滴答聲考慮了活動之間的並行性。 兩個並行活動的持續時間可能為 50 個刻度,並且相同的開始和停止時間。 在這種情況下,兩者都被分配了 25 個刻度的掛鐘時間責任。

::: moniker-end
