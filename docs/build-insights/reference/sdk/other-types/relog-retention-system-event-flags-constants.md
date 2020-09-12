---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常數
description: C + + Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5444c1a6b8799b1de8eea228211a5f2d6de638f8
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041402"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS 常數

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_RETENTION_SYSTEM_EVENT_FLAGS`常數可用來描述要在 relogged 追蹤中保留的系統事件。 您可以使用它們來初始化 [RELOG_DESCRIPTOR](relog-descriptor-struct.md) 結構的 `SystemEventsRetentionFlags` 欄位。

## <a name="syntax"></a>語法

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>成員

| Name | 描述 |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | 將 CPU 範例系統事件保留在 relogged 追蹤中。 |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | 將所有系統事件保留在 relogged 追蹤中。 |

## <a name="remarks"></a>備註

::: moniker-end
