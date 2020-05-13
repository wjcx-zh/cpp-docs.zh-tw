---
title: EVENT_DATA結構
description: C++生成見解 SDK EVENT_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325601"
---
# <a name="event_data-structure"></a>EVENT_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

結構`EVENT_DATA`描述從分析或重新記錄會話接收的事件。 這些工作階段透過呼叫[分析](../functions/analyze.md),[分析A、](../functions/analyze-a.md)[分析W,](../functions/analyze-w.md)[重新紀錄](../functions/relog.md),[重新登入](../functions/relog-a.md)或[RelogW](../functions/relog-w.md)函數開始。

## <a name="syntax"></a>語法

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `EventId` | 標識事件的數位。 有關事件識別碼的清單,請參閱[EVENT_ID](event-id-enum.md)。 |
| `EventInstanceId` | 唯一標識跟蹤內當前事件的數位。 多次分析或重新記錄同一跟蹤時,此值不會更改。 使用此欄位可識別多個分析或通過同一跟蹤的重新記錄傳遞中的同一事件。 |
| `TickFrequency` | 評估以刻度為單位測量的持續時間時每秒使用的刻度數。 |
| `StartTimestamp` | 當事件為*活動*時,此欄位設置為活動啟動時捕獲的刻度值。 如果此事件是*簡單事件*,則此欄位設置為事件發生時捕獲的刻度值。 |
| `StopTimestamp` | 當事件為*活動*時,此欄位設置為活動停止時捕獲的刻度值。 如果尚未收到此活動的停止事件,則此欄位設置為零。 如果此事件是*簡單事件*,則此欄位設置為零。 |
| `ExclusiveDurationTicks` | 如果此事件是*活動*,則此欄位設置為此活動中直接發生的刻度數。 不包括子活動中發生的刻度數。 此欄位設定為 *「簡單事件*」為零。 |
| `CPUTicks` | 如果此事件是*活動*,則此欄位設置為在此活動期間發生的 CPU 刻度數。 CPU 刻度不同於常規刻度。 僅當 CPU 在活動中執行代碼時,才會計算 CPU 刻度。 當與活動關聯的線程處於睡眠狀態時,不會計算 CPU 刻度。 此欄位設定為 *「簡單事件*」為零。 |
| `ExclusiveCPUTicks` | 此欄位的含義與`CPUTicks`相同,只不過它不包括子活動中發生的 CPU 刻度。 此欄位設定為 *「簡單事件*」為零。 |
| `WallClockTimeResponsibilityTicks` | 如果此事件是*活動*,則此欄位設置為表示此活動對總掛鐘時間的貢獻的刻度計數。 掛鐘時間責任刻度不同於常規刻度。 鐘點時間責任滴答聲考慮了活動之間的並行性。 例如,兩個並行活動的持續時間可能為 50 個刻度,並且相同的開始和停止時間相同。 在這種情況下,兩者將被分配 25 個刻度的掛鐘時間責任。 此欄位設定為 *「簡單事件*」為零。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | 此欄位的含義與`WallClockTimeResponsibilityTicks`相同,只是不包括兒童活動的掛鐘時間責任刻度。 此欄位設定為 *「簡單事件*」為零。 |
| `Data` | 指向事件中存儲的其他數據。 指向的資料型態因欄位`EventId`而異 。 |
| `ProcessId` | 事件發生的進程的標識碼。 |
| `ThreadId` | 發生事件的線程的標識符。 |
| `ProcessorIndex` | 事件發生的零索引 CPU 編號。 |
| `EventName` | 包含識別`EventId`的實體名稱的 ANSI 字串。 |
| `EventWideName` | 包含識別`EventId`的實體名稱的寬字串。 |

## <a name="remarks"></a>備註

中的`EVENT_DATA`許多欄位包含刻度計數。 C++生成見解使用視窗的性能計數器作為報價源。 必須將刻度計數與`TickFrequency`欄位一起使用,將其轉換為適當的時間單位,如秒。 有關執行此轉換,請參閱下面的範例。 `EVENT_DATA`不包含活動常規刻度計數的欄位。 要取得此值,從`StartTimestamp``StopTimestamp`中減去 。 `EVENT_DATA`是一個結構,供 C API 使用者使用。 對於C++ API 使用者,像[事件](../cpp-event-data-types/event.md)這樣的類會自動進行時間轉換。

欄位的值`EVENT_DATA`取決於`EventId`其 欄位的`Data`值。 下表描述了`Data`的值。 下表中可能缺少某些實體標識符。 在這種情況下,欄位`Data`設置為`nullptr`或零。

| `EventId` 值 | 型態指向`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>滴答轉換範例

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
