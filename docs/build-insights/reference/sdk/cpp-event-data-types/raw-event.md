---
title: RawEvent 類別
description: C++ BUILD Insights SDK RawEvent 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333059"
---
# <a name="rawevent-class"></a>RawEvent 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`RawEvent` 類別是用來代表[EventStack](event-stack.md)中的一般事件。

## <a name="syntax"></a>語法

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>備註

`RawEvent` 類別中的數個成員函式會傳回滴答計數。 C++Build Insights 會使用 Windows 的效能計數器作為刻度的來源。 滴答計數必須搭配滴答頻率使用，才能將它轉換成時間單位（例如秒）。 您可以呼叫 `TickFrequency` 成員函式來取得滴答頻率。 如需如何將刻度轉換為時間單位的範例，請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)頁面。

如果您不想要自行轉換刻度，`RawEvent` 類別會提供以毫微秒傳回時間值的成員函式。 使用標準C++ `chrono` 程式庫，將毫微秒轉換成其他時間單位。

## <a name="members"></a>成員

### <a name="constructor"></a>建構函式

[RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[資料](#data)\
[持續時間](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[事件名稱](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>參數

*event*\
事件資料。

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

## <a name="data"></a>Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>傳回值

包含在此事件中之額外資料的指標。 如需如何解讀此欄位的詳細資訊，請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="duration"></a>期限

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>傳回值

活動的持續時間（以毫微秒為單位）。

## <a name="event-id"></a>EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>傳回值

識別事件種類的數位。 如需事件識別碼的清單，請參閱[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>傳回值

可唯一識別追蹤內事件的數位。 當分析或 relogging 相同的追蹤多次時，此值不會變更。 使用此值來識別多個分析或 relogging 傳遞相同追蹤中的相同事件。

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>傳回值

ANSI 字串，其中包含[EventId](#event-id)所識別之事件種類的名稱。

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>傳回值

寬字元串，包含[EventId](#event-id)所識別之事件種類的名稱。

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

## <a name="process-id"></a>進程

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>傳回值

發生事件之進程的識別碼。

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>傳回值

發生事件之邏輯處理器的以零為基底的索引。

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

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>傳回值

發生事件之執行緒的識別碼。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>傳回值

評估以這個事件的刻度測量的持續時間時，每秒所要使用的刻度數。

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

表示此活動對整體時鐘時間之比重的滴答計數。 時鐘時間責任刻度與一般滴答不同。 時鐘時間責任刻度會考慮活動之間的平行處理。 兩個平行活動的持續時間可能是50刻度和相同的開始和停止時間。 在這種情況下，會指派25個刻度的時鐘時間責任。

::: moniker-end
