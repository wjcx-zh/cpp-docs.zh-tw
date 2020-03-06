---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常數
description: C++ BUILD Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332317"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常數

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_RETENTION_SYSTEM_EVENT_FLAGS` 常數可用來描述要保留在 relogged 追蹤中的系統事件。 使用它們來初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)結構的 `SystemEventsRetentionFlags` 欄位。

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
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | 將 CPU 範例系統事件保留在 relogged 追蹤中。 |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | 將所有系統事件保留在 relogged 追蹤中。 |

## <a name="remarks"></a>備註

::: moniker-end
