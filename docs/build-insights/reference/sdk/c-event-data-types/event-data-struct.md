---
title: EVENT_DATA 結構
description: C + + Build Insights SDK EVENT_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 468fc30d337e5cfc5ab90f7558904fc90588c3df
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041818"
---
# <a name="event_data-structure"></a>EVENT_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_DATA`結構描述從分析或 relogging 會話接收的事件。 這些會話是藉由呼叫 [分析](../functions/analyze.md)、 [AnalyzeA](../functions/analyze-a.md)、 [AnalyzeW](../functions/analyze-w.md)、重新 [發出、](../functions/relog.md) [RelogA](../functions/relog-a.md)或 [RelogW](../functions/relog-w.md) 函數來啟動。

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

| Name | 描述 |
|--|--|
| `EventId` | 識別事件的數位。 如需事件識別碼的清單，請參閱 [EVENT_ID](event-id-enum.md)。 |
| `EventInstanceId` | 可唯一識別追蹤內目前事件的數位。 分析或 relogging 相同的追蹤多次時，不會變更此值。 您可以使用此欄位來識別多個分析或 relogging 通過相同追蹤的相同事件。 |
| `TickFrequency` | 評估以刻度測量的持續時間時，每秒所使用的刻度數目。 |
| `StartTimestamp` | 當事件是 *活動*時，此欄位會設定為活動開始時所捕捉的刻度值。 如果這個事件是 *簡單的事件*，此欄位會設定為事件發生時所捕捉的刻度值。 |
| `StopTimestamp` | 當事件是 *活動*時，此欄位會設定為活動停止時所捕捉的刻度值。 如果這個活動尚未收到停止事件，此欄位會設定為零。 如果這個事件是 *簡單的事件*，此欄位會設定為零。 |
| `ExclusiveDurationTicks` | 如果此事件是 *活動*，則此欄位會設定為此活動中直接發生的刻度數目。 子活動中發生的刻度數目會被排除。 針對 *簡單事件*，此欄位會設為零。 |
| `CPUTicks` | 如果此事件是 *活動*，則此欄位會設定為此活動期間發生的 CPU 滴答數。 CPU 滴答和一般滴答不同。 只有當 CPU 在活動中執行程式碼時，才會計算 CPU 刻度。 當與活動相關聯的執行緒處於睡眠狀態時，不會計算 CPU 刻度。 針對 *簡單事件*，此欄位會設為零。 |
| `ExclusiveCPUTicks` | 這個欄位的意義與相同 `CPUTicks` ，不同之處在于，它不包含子活動中發生的 CPU 刻度。 針對 *簡單事件*，此欄位會設為零。 |
| `WallClockTimeResponsibilityTicks` | 如果此事件是 *活動*，此欄位會設定為表示此活動對整體時鐘時間的比重的滴答計數。 時鐘時間的責任刻度與一般滴答不同。 時鐘時間的責任刻度會考慮活動之間的平行處理原則。 例如，兩個平行活動的持續時間可能是50滴答和相同的開始和停止時間。 在此情況下，系統會將時鐘的時間責任指派為25個刻度。 針對 *簡單事件*，此欄位會設為零。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | 此欄位的意義與相同 `WallClockTimeResponsibilityTicks` ，不同之處在于它不包含子活動的時鐘時間責任刻度。 針對 *簡單事件*，此欄位會設為零。 |
| `Data` | 指向事件中儲存的其他資料。 所指向的資料類型會不同，視欄位而定 `EventId` 。 |
| `ProcessId` | 發生事件之進程的識別碼。 |
| `ThreadId` | 發生事件之執行緒的識別碼。 |
| `ProcessorIndex` | 發生事件的零索引 CPU 編號。 |
| `EventName` | ANSI 字串，其中包含所識別之實體的名稱 `EventId` 。 |
| `EventWideName` | 寬字元串，其中包含所識別之實體的名稱 `EventId` 。 |

## <a name="remarks"></a>備註

中的許多欄位 `EVENT_DATA` 包含滴答計數。 C + + Build Insights 使用視窗的效能計數器作為刻度的來源。 滴答計數必須與欄位一起使用 `TickFrequency` ，才能將它轉換成適當的時間單位，例如 seconds。 請參閱下列範例，以執行這種轉換。 `EVENT_DATA` 不包含活動一般滴答計數的欄位。 若要取得此值，請 `StartTimestamp` 從減去 `StopTimestamp` 。 `EVENT_DATA` 是一種結構，其目的是要供 C API 使用者使用。 針對 c + + API 使用者， [事件](../cpp-event-data-types/event.md) 等類別會自動進行轉換。

欄位的值 `EVENT_DATA` `Data` 取決於其欄位的值 `EventId` 。 `Data`下表說明的值。 下表可能遺漏某些實體識別碼。 在此情況下，此 `Data` 欄位會設定為 **`nullptr`** 或零。

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
