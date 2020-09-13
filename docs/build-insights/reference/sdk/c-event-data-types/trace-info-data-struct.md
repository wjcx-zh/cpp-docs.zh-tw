---
title: TRACE_INFO_DATA 結構
description: C + + Build Insights SDK TRACE_INFO_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 38683ff2c5c5165b5fe2a1969ccf80fbfca3693f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040453"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACE_INFO_DATA`結構描述要分析或 relogged 的追蹤。

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

| 名稱 | 描述 |
|--|--|
| `LogicalProcessorCount` | 收集追蹤之機器上的邏輯處理器數目。 |
| `TickFrequency` | 評估以刻度測量的持續時間時，每秒所使用的刻度數目。 |
| `StartTimestamp` | 此欄位會設定為啟動追蹤時所捕捉的刻度值。 |
| `StopTimestamp` | 此欄位會設定為停止追蹤時所捕捉的刻度值。 |

## <a name="remarks"></a>備註

`StartTimestamp`從減去 `StopTimestamp` 以取得整個追蹤期間所經過的滴答數。 用 `TickFrequency` 來將產生的值轉換成時間單位。 如需將刻度轉換成時間單位的範例，請參閱 [EVENT_DATA](event-data-struct.md)。

::: moniker-end
