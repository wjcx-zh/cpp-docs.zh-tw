---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS 常數
description: C++ BUILD Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS 常數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332352"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS 常數

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_SYSTEM_EVENT_FLAGS` 常數是用來描述追蹤期間要收集的系統事件。 使用它們來初始化[TRACING_SESSION_OPTIONS](tracing-session-options-struct.md)結構的 `SystemEventFlags` 欄位。

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

| 名稱 | 此旗標已開啟的事件 |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | 即使未明確指定， C++ BUILD Insights SDK 預設會啟用此旗標。 它可以讓C++ Build Insights 所需的基本系統事件正常運作。 此旗標所啟用的事件會提供處理常式、執行緒和映射載入的相關資訊。 您無法停用這些事件。 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU 範例 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | 這個旗標會開啟所有系統事件。 |

::: moniker-end
