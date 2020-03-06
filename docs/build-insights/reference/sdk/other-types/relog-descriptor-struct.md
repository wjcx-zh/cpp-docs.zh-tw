---
title: RELOG_DESCRIPTOR 結構
description: C++ BUILD Insights SDK RELOG_DESCRIPTOR 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332324"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_DESCRIPTOR` 結構與[RelogA](../functions/relog-a.md)和[RelogW](../functions/relog-w.md)函數搭配使用。 說明如何 relogged Windows 事件追蹤（ETW）追蹤。

## <a name="syntax"></a>語法

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | 在 relogging 會話的分析階段期間，應該透過 ETW 追蹤來完成的分析傳遞數目。 |
| `AnalysisCallbacks` | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)物件，指定要在 relogging 會話的分析階段中呼叫的函式。 |
| `RelogCallbacks` | [RELOG_CALLBACKS](relog-callbacks-struct.md)物件，指定要在 relogging 會話的 relogging 階段中呼叫的函式。 |
| `SystemEventsRetentionFlags` | [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)位元遮罩，指定要保留在 relogged 追蹤中的系統 ETW 事件。 |
| `AnalysisContext` | 使用者提供的內容，它會當做引數傳遞給在中指定的所有回呼函數 `AnalysisCallbacks` |
| `RelogContext` | 使用者提供的內容，它會當做引數傳遞給在中指定的所有回呼函數 `RelogCallbacks` |

## <a name="remarks"></a>備註

Relogging 會話期間的 ETW 事件 relogging 是由使用者透過 `RelogCallbacks`中指定的回呼函數來控制。 不過，系統 ETW 事件（例如 CPU 範例）不會轉送到這些回呼函數。 使用 [`SystemEventsRetentionFlags`] 欄位來控制系統 ETW 事件的 relogging。

`AnalysisCallbacks` 和 `RelogCallbacks` 結構只接受非成員函式的指標。 您可以將其設定為物件指標，以避開這項限制。 這個物件指標會當做引數傳遞給您所有的非成員回呼函數。 使用這個指標，從您的非成員回呼函式中呼叫成員函式。

Relogging 會話的分析階段一律會在 relogging 階段之前執行。

::: moniker-end
