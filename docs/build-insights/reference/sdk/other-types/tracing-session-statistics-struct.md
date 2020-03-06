---
title: TRACING_SESSION_STATISTICS 結構
description: C++ BUILD Insights SDK TRACING_SESSION_OPTIONS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332198"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_STATISTICS` 結構描述所收集追蹤的統計資料。 其欄位會在停止追蹤會話時設定。

## <a name="syntax"></a>語法

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `MSVCEventsLost` | 已卸載的 MSVC 事件數目。 |
| `MSVCBuffersLost` | 已卸載的 MSVC 事件緩衝區數目。 |
| `SystemEventsLost` | 已卸載的系統事件數目。 |
| `SystemBuffersLost` | 已卸載的系統事件緩衝區數目。 |

## <a name="remarks"></a>備註

呼叫下列函數時，會填入此結構：

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
