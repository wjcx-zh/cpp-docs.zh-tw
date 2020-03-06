---
title: TRACE_INFO_DATA 結構
description: C++ BUILD Insights SDK TRACE_INFO_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333584"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACE_INFO_DATA` 結構描述正在分析或 relogged 的追蹤。

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
| `LogicalProcessorCount` | 收集追蹤的電腦上的邏輯處理器數目。 |
| `TickFrequency` | 評估以刻度測量的持續時間時，每秒所要使用的刻度數。 |
| `StartTimestamp` | 此欄位設定為啟動追蹤時所捕捉到的滴答值。 |
| `StopTimestamp` | 此欄位會設定為停止追蹤時所捕捉到的滴答值。 |

## <a name="remarks"></a>備註

從 `StopTimestamp` 減去 `StartTimestamp`，以取得整個追蹤期間經過的滴答數。 使用 `TickFrequency`，將產生的值轉換成時間單位。 如需將刻度轉換為時間單位的範例，請參閱[EVENT_DATA](event-data-struct.md)。

::: moniker-end
