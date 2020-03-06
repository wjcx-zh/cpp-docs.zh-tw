---
title: TraceInfo 類別
description: C++ BUILD Insights SDK TraceInfo 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332940"
---
# <a name="traceinfo-class"></a>TraceInfo 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TraceInfo` 類別是用來存取有關正在分析或 relogged 之追蹤的實用屬性。

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

從 `StopTimestamp` 減去 `StartTimestamp`，以取得整個追蹤期間經過的滴答數。 使用 `TickFrequency`，將產生的值轉換成時間單位。 如需將刻度轉換成時間的範例，請參閱[EVENT_DATA](../c-event-data-types/event-data-struct.md)。

如果您不想要自行轉換刻度，`TraceInfo` 類別會提供一個成員函式，該函式會傳回以毫微秒為單位的追蹤持續時間。 使用標準C++ `chrono` 程式庫，將此值轉換成其他時間單位。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>期限

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>傳回值

活動的持續時間（以毫微秒為單位）。

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>傳回值

收集追蹤的電腦上的邏輯處理器數目。

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>傳回值

啟動追蹤時所捕捉到的滴答值。

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>傳回值

停止追蹤時所捕捉到的滴答值。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>傳回值

評估以刻度測量的持續時間時，每秒所要使用的刻度數。

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>參數

*資料*\
包含追蹤相關資訊的資料。

::: moniker-end
