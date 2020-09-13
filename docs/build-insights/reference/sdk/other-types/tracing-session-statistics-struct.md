---
title: TRACING_SESSION_STATISTICS 結構
description: C + + Build Insights SDK TRACING_SESSION_OPTIONS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5f6126fb469dc13b814b91942fe9f7bc480ba3f1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041181"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_STATISTICS`結構描述所收集追蹤的統計資料。 它的欄位會在停止追蹤會話時設定。

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

| 名稱 | 描述 |
|--|--|
| `MSVCEventsLost` | 已捨棄的 MSVC 事件數目。 |
| `MSVCBuffersLost` | 已卸載的 MSVC 事件緩衝區數目。 |
| `SystemEventsLost` | 已捨棄的系統事件數目。 |
| `SystemBuffersLost` | 已卸載的系統事件緩衝區數目。 |

## <a name="remarks"></a>備註

呼叫下列函式時，會填入此結構：

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
