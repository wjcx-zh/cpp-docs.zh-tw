---
title: 追蹤資訊類
description: C++生成見解 SDK 跟蹤資訊類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324166"
---
# <a name="traceinfo-class"></a>追蹤資訊類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

類`TraceInfo`用於訪問有關要分析或重新記錄的跟蹤的有用屬性。

## <a name="syntax"></a>語法

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>備註

`StartTimestamp`從中`StopTimestamp`減去 以獲取整個跟蹤期間經過的刻度數。 用於`TickFrequency`將生成的值轉換為時間單位。 有關將刻度轉換為時間的範例,請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

如果不想自己轉換刻度,`TraceInfo`類提供一個成員函數,以納秒為單位返回跟蹤持續時間。 使用標準C++`chrono`庫將此值轉換為其他時間單位。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

[追蹤資訊](#trace-info)

### <a name="functions"></a>函式

[持續時間](#duration)
[邏輯處理器計數](#logical-processor-count)
[開始時間戳](#start-timestamp)
[停止時間戳](#stop-timestamp)
[刻度頻率](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>時間

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>傳回值

活動持續時間(以納秒為單位)。

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>邏輯處理器計數

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>傳回值

收集跟蹤的計算機上的邏輯處理器數。

## <a name="starttimestamp"></a><a name="start-timestamp"></a>開始時間戳

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>傳回值

在開始跟蹤時捕獲的刻度值。

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>停止時間戳

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>傳回值

在停止追蹤時捕獲的刻度值。

## <a name="tickfrequency"></a><a name="tick-frequency"></a>滴答頻率

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>傳回值

評估以刻度為單位測量的持續時間時每秒使用的刻度數。

## <a name="traceinfo"></a><a name="trace-info"></a>追蹤資訊

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>參數

*資料*\
包含有關跟蹤的資訊的數據。

::: moniker-end
