---
title: RawEvent 類別
description: C++生成見解 SDK RawEvent 類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324376"
---
# <a name="rawevent-class"></a>RawEvent 類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`RawEvent`類用於表示[事件堆疊](event-stack.md)中的常規事件。

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

`RawEvent`類中的多個成員函數返回刻度計數。 C++生成見解使用 Windows 的性能計數器作為報價源。 刻度計數必須與刻度頻率一起使用,才能將其轉換為時間單位(如秒)。 可以`TickFrequency`調用成員函數以獲取滴答頻率。 有關如何將刻度轉換為時間單位的範例,請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)頁。

如果不想自己轉換刻度,`RawEvent`類提供以納秒為單位返回時間值的成員函數。 使用標準C++`chrono`庫將納秒轉換為其他時間單位。

## <a name="members"></a>成員

### <a name="constructor"></a>建構函式

[原始事件](#raw-event)

### <a name="functions"></a>函式

[CPUTicks](#cpu-ticks)\
[CPU時間](#cpu-time)\
[資料](#data)\
[時間](#duration)\
[事件 Id](#event-id)
[事件實體代碼](#event-instance-id)
[名稱](#event-name)\
[事件寬名稱](#event-wide-name)\
[獨家CPUTicks](#exclusive-cpu-ticks)\
[獨家CPU時間](#exclusive-cpu-time)\
[獨家持續時間](#exclusive-duration)\
[獨家持續時間提示](#exclusive-duration-ticks)\
[獨家華爾街時間責任](#exclusive-wall-clock-time-responsibility)\
[獨家華爾街時間責任提示](#exclusive-wall-clock-time-responsibility-ticks)\
[行程代碼](#process-id)\
[處理器索引](#processor-index)\
[開始時間戳](#start-timestamp)\
[停止時間戳](#stop-timestamp)\
[執行緒 Id](#thread-id)\
[滴答頻率](#tick-frequency)\
[牆鐘時間責任](#wall-clock-time-responsibility)\
[牆鐘時間責任提示](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>原始事件

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>參數

*事件*\
事件資料。

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

## <a name="data"></a><a name="data"></a>資料

```cpp
const void* Data() const;
```

### <a name="return-value"></a>傳回值

指向此事件中包含的額外數據的指標。 有關如何解釋此欄位的詳細資訊,請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

## <a name="duration"></a><a name="duration"></a>時間

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>傳回值

活動持續時間(以納秒為單位)。

## <a name="eventid"></a><a name="event-id"></a>事件 Id

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>傳回值

標識事件類型的數位。 有關事件識別碼的清單,請參閱[EVENT_ID](../c-event-data-types/event-id-enum.md)。

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>事件實例 Id

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>傳回值

唯一標識跟蹤內事件的數位。 多次分析或重新記錄同一跟蹤時,此值不會更改。 使用此值可識別多個分析或重新記錄通過同一跟蹤中的同一事件。

## <a name="eventname"></a><a name="event-name"></a>事件名稱

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>傳回值

包含[事件 Id](#event-id)識別的事件類型名稱的 ANSI 字串。

## <a name="eventwidename"></a><a name="event-wide-name"></a>事件寬名稱

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>傳回值

包含[事件 Id](#event-id)識別的事件類型名稱的寬字串。

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

## <a name="processid"></a><a name="process-id"></a>行程代碼

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>傳回值

事件發生的進程的標識碼。

## <a name="processorindex"></a><a name="processor-index"></a>處理器索引

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>傳回值

事件發生的邏輯處理器的零基索引。

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

## <a name="threadid"></a><a name="thread-id"></a>執行緒 Id

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>傳回值

發生事件的線程的標識符。

## <a name="tickfrequency"></a><a name="tick-frequency"></a>滴答頻率

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>傳回值

評估以此事件的刻度為單位的持續時間時,每秒使用的刻度數。

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

表示此活動對總掛鐘時間的貢獻的刻度計數。 掛鐘時間責任刻度不同於常規刻度。 鐘點時間責任滴答聲考慮了活動之間的並行性。 兩個並行活動的持續時間可能為 50 個刻度,並且相同的開始和停止時間相同。 在這種情況下,兩者都被分配了 25 個刻度的掛鐘時間責任。

::: moniker-end
