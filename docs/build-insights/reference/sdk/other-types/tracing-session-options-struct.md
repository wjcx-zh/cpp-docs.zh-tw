---
title: TRACING_SESSION_OPTIONS 結構
description: C++ BUILD Insights SDK TRACING_SESSION_OPTIONS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332205"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)結構時，會使用 `TRACING_SESSION_OPTIONS` 結構。 它會描述追蹤集合期間要捕獲的事件。

## <a name="syntax"></a>語法

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `SystemEventFlags` | 用來描述要捕捉之系統事件的位元遮罩。 如需詳細資訊，請參閱[TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md)。 |
| `MsvcEventFlags` | 用來描述要捕捉之 MSVC 事件的位元遮罩。 如需詳細資訊，請參閱[TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md)。 |

::: moniker-end
