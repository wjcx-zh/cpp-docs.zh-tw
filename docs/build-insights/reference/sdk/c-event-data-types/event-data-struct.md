---
title: EVENT_DATA 結構
description: C++ BUILD Insights SDK EVENT_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857089"
---
# <a name="event_data-structure"></a>EVENT_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_DATA` 結構描述從分析或 relogging 會話接收到的事件。 這些會話會藉由呼叫[分析](../functions/analyze.md)、 [AnalyzeA](../functions/analyze-a.md)、 [AnalyzeW](../functions/analyze-w.md)、重新[發出、](../functions/relog.md) [RelogA](../functions/relog-a.md)或[RelogW](../functions/relog-w.md)函數來啟動。

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
| `EventId` | 識別事件的數位。 如需事件識別碼的清單，請參閱[EVENT_ID](event-id-enum.md)。 |
| `EventInstanceId` | 可唯一識別追蹤內目前事件的數位。 當分析或 relogging 相同的追蹤多次時，此值不會變更。 使用此欄位來識別多個分析或 relogging 通過相同追蹤的相同事件。 |
| `TickFrequency` | 評估以刻度測量的持續時間時，每秒所要使用的刻度數。 |
| `StartTimestamp` | 當事件是*活動*時，此欄位會設定為活動開始時所捕捉到的滴答值。 如果這個事件是*簡單事件*，此欄位會設定為事件發生時所捕捉到的滴答值。 |
| `StopTimestamp` | 當事件是*活動*時，此欄位會設定為活動停止時所捕捉到的滴答值。 如果尚未收到此活動的停止事件，此欄位會設定為零。 如果這個事件是*簡單事件*，此欄位會設定為零。 |
| `ExclusiveDurationTicks` | 如果此事件是*活動*，此欄位會設定為直接在此活動中發生的刻度數目。 排除子活動中發生的刻度數目。 對於*簡單事件*，此欄位會設定為零。 |
| `CPUTicks` | 如果此事件是*活動*，此欄位會設定為在此活動期間發生的 CPU 刻度數目。 CPU 刻度與一般滴答不同。 只有當 CPU 在活動中執行程式碼時，才會計算 CPU 刻度。 與活動相關聯的執行緒處於睡眠狀態時，不會計算 CPU 刻度。 對於*簡單事件*，此欄位會設定為零。 |
| `ExclusiveCPUTicks` | 此欄位與 `CPUTicks`的意義相同，不同之處在于它不會包含子活動中所發生的 CPU 刻度。 對於*簡單事件*，此欄位會設定為零。 |
| `WallClockTimeResponsibilityTicks` | 如果此事件是*活動*，此欄位會設定為表示此活動對整體時鐘時間之比重的滴答計數。 時鐘時間責任刻度與一般滴答不同。 時鐘時間責任刻度會考慮活動之間的平行處理。 例如，兩個平行活動的持續時間可能是50刻度和相同的開始和停止時間。 在此情況下，系統會將時鐘時間責任指派為25個刻度。 對於*簡單事件*，此欄位會設定為零。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | 此欄位與 `WallClockTimeResponsibilityTicks`的意義相同，不同之處在于它不會包含子活動的時鐘時間責任刻度。 對於*簡單事件*，此欄位會設定為零。 |
| `Data` | 指向事件中儲存的其他資料。 視 `EventId` 欄位而定，所指向的資料類型是不同的。 |
| `ProcessId` | 發生事件之進程的識別碼。 |
| `ThreadId` | 發生事件之執行緒的識別碼。 |
| `ProcessorIndex` | 發生事件之以零為索引的 CPU 編號。 |
| `EventName` | 包含 `EventId`所識別之機構名稱的 ANSI 字串。 |
| `EventWideName` | 寬字元串，包含 `EventId`所識別之實體的名稱。 |

## <a name="remarks"></a>備註

`EVENT_DATA` 中的許多欄位都包含滴答計數。 C++Build Insights 會使用 Window 的效能計數器作為刻度的來源。 滴答計數必須與 [`TickFrequency`] 欄位搭配使用，才能將它轉換成適當的時間單位，例如 [秒]。 請參閱下列範例，以執行這種轉換。 `EVENT_DATA` 不包含活動之一般滴答計數的欄位。 若要取得此值，請從 `StopTimestamp`減去 `StartTimestamp`。 `EVENT_DATA` 是要供 C API 使用者使用的結構。 針對C++ API 使用者，[事件](../cpp-event-data-types/event.md)之類的類別會自動進行轉換。

[`EVENT_DATA` `Data`] 欄位的值取決於其 [`EventId`] 欄位的值。 下表描述 `Data` 的值。 下表中可能遺漏一些實體識別碼。 在此情況下，`Data` 欄位會設為 `nullptr` 或零。

| `EventId` 值 | 所指向的類型 `Data` |
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

## <a name="tick-conversion-example"></a>刻度轉換範例

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
