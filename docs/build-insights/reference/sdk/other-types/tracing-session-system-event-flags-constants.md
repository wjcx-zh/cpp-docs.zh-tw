---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS常量
description: C++生成見解 SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS常量引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323277"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS常量

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

常`TRACING_SESSION_SYSTEM_EVENT_FLAGS`量用於描述在跟蹤期間要收集的系統事件。 使用它們初始化[TRACING_SESSION_OPTIONS](tracing-session-options-struct.md)結構`SystemEventFlags`的欄位。

## <a name="syntax"></a>語法

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>成員

| 名稱 | 這個旗標開啟的事件 |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | 默認情況下,C++生成見解 SDK 會啟動此標誌,即使未顯式指定也是如此。 它使C++生成見解所需的基本系統事件能夠正常運行。 此標誌啟用的事件提供有關進程、線程和圖像載入的資訊。 無法禁用這些事件。 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU 樣本 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | 此標誌將打開所有系統事件。 |

::: moniker-end
