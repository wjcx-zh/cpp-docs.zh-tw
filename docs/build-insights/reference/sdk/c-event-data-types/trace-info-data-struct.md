---
title: TRACE_INFO_DATA結構
description: C++生成見解 SDK TRACE_INFO_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325270"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

結構`TRACE_INFO_DATA`描述要分析或重新記錄的跟蹤。

## <a name="syntax"></a>語法

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `LogicalProcessorCount` | 收集跟蹤的計算機上的邏輯處理器數。 |
| `TickFrequency` | 評估以刻度為單位測量的持續時間時每秒使用的刻度數。 |
| `StartTimestamp` | 此欄位設置為在開始跟蹤時捕獲的刻度值。 |
| `StopTimestamp` | 此欄位設定為停止追蹤時捕獲的刻度值。 |

## <a name="remarks"></a>備註

從`StartTimestamp``StopTimestamp`中 減去以獲取整個跟蹤期間經過的刻度數。 用於`TickFrequency`將生成的值轉換為時間單位。 有關將刻度轉換為時間單位的範例,請參閱[EVENT_DATA](event-data-struct.md)。

::: moniker-end
