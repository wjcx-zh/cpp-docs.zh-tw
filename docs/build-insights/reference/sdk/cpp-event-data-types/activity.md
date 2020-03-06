---
title: 活動類別
description: C++ BUILD Insights SDK 活動類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6de411c375b42e4acfb44bf0fac9d28ad57f1ca7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333556"
---
# <a name="activity-class"></a>活動類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`Activity` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對任何活動事件。 請參閱[事件資料表](../event-table.md)，以查看 `Activity` 類別可以比對的所有事件。

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

`Activity` 類別中的數個成員函式會傳回滴答計數。 C++Build Insights 會使用 Windows 的效能計數器作為刻度的來源。 滴答計數必須搭配滴答頻率使用，才能將它轉換成時間單位（例如秒）。 可以呼叫在[事件](event.md)基類中提供的 `TickFrequency` 成員函式，以取得滴答頻率。 [ [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) ] 頁面會顯示將刻度轉換為時間單位的範例。

如果您不想要自行將刻度轉換成時間單位，`Activity` 類別會提供以毫微秒傳回時間值的成員函式。 使用標準C++ `chrono` 程式庫，將它們轉換成其他時間單位。

## <a name="members"></a>成員

除了繼承自[事件](event.md)基類的成員之外，`Activity` 類別還包含下列成員：

### <a name="constructor"></a>建構函式

[活動](#activity)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[持續時間](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a>操作

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
任何活動事件。

## <a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>傳回值

在此活動期間發生的 CPU 刻度數目。 CPU 刻度與一般滴答不同。 只有當 CPU 在活動中執行程式碼時，才會計算 CPU 刻度。 與活動相關聯的執行緒處於睡眠狀態時，不會計算 CPU 刻度。

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>傳回值

CPU 在此活動內執行程式碼的時間量。 如果子活動是在不同的執行緒上執行，這個值可能會高於活動的持續時間。 值會以毫微秒傳回。

## <a name="duration"></a>期限

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>傳回值

活動的持續時間（以毫微秒為單位）。

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>傳回值

與[CPUTicks](#cpu-ticks)相同，但不包括子活動中發生的 CPU 刻度。

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>傳回值

與[CPUTime](#cpu-time)相同，不同之處在于不包含子活動的 CPU 時間。

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>傳回值

活動的持續時間（以毫微秒為單位），不包括在子活動中花費的時間量。

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>傳回值

在此活動中發生的刻度數目，不包括子活動中發生的滴答數。

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>傳回值

與[WallClockTimeResponsibility](#wall-clock-time-responsibility)相同，但不包括子活動的時鐘時間責任。

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>傳回值

與[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)相同，但不包括子活動的時鐘時間責任刻度。

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>傳回值

活動開始時所捕捉的滴答值。

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>傳回值

活動停止時所捕捉到的滴答值。

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>傳回值

此活動的時鐘時間責任（以毫微秒為單位）。 如需時鐘時間責任意義的詳細資訊，請參閱[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)。

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>傳回值

表示此活動對整體時鐘時間之比重的滴答計數。 時鐘時間責任刻度與一般滴答不同。 時鐘時間責任刻度會考慮活動之間的平行處理。 兩個平行活動的持續時間可能是50刻度，以及相同的開始和停止時間。 在這種情況下，會指派25個刻度的時鐘時間責任。

::: moniker-end
