---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS常量
description: C++生成見解 SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS常量引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323463"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS常量

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

常`RELOG_RETENTION_SYSTEM_EVENT_FLAGS`量用於描述要在重新記錄的跟蹤中保留哪些系統事件。 使用它們初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)`SystemEventsRetentionFlags`結構的欄位。

## <a name="syntax"></a>語法

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | 將 CPU 示例系統事件保持在已記錄的追蹤中。 |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | 將所有系統事件保留在已記錄的跟蹤中。 |

## <a name="remarks"></a>備註

::: moniker-end
