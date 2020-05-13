---
title: TRACING_SESSION_STATISTICS結構
description: C++構建見解 SDK TRACING_SESSION_OPTIONS結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96cff3a231fd515ec1c52a048b8350a63ba46a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323372"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`TRACING_SESSION_STATISTICS`結構描述收集的跟蹤的統計資訊。 停止跟蹤會話時設置其欄位。

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
| `MSVCEventsLost` | 丟棄的 MSVC 事件數。 |
| `MSVCBuffersLost` | 丟棄的 MSVC 事件緩衝區數。 |
| `SystemEventsLost` | 丟棄的系統事件數。 |
| `SystemBuffersLost` | 丟棄的系統事件緩衝區數。 |

## <a name="remarks"></a>備註

呼叫以下函數時,將填充此結構:

- [停止追蹤工作階段](../functions/stop-tracing-session.md)
- [停止追蹤工作階段A](../functions/stop-tracing-session-a.md)
- [停止追蹤工作階段W](../functions/stop-tracing-session-w.md)
- [停止並分析追蹤工作階段](../functions/stop-and-analyze-tracing-session.md)
- [停止並分析追蹤工作階段A](../functions/stop-and-analyze-tracing-session-a.md)
- [停止並分析追蹤工作階段W](../functions/stop-and-analyze-tracing-session-w.md)
- [停止並重新記錄追蹤工作階段](../functions/stop-and-relog-tracing-session.md)
- [停止並重新登入追蹤工作階段A](../functions/stop-and-relog-tracing-session-a.md)
- [停止並重新記錄追蹤工作階段W](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
