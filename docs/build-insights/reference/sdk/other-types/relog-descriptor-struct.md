---
title: RELOG_DESCRIPTOR 結構
description: C + + Build Insights SDK RELOG_DESCRIPTOR 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 802e51ec4246f5ee95e3d204290743ffbd03be69
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041389"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

此 `RELOG_DESCRIPTOR` 結構會搭配 [RelogA](../functions/relog-a.md) 和 [RelogW](../functions/relog-w.md) 函數使用。 它說明如何 relogged Windows (ETW) 追蹤的事件追蹤。

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

| 名稱 | 描述 |
|--|--|
| `NumberOfAnalysisPasses` | 在 relogging 會話的分析階段期間，應該針對 ETW 追蹤進行的分析傳遞數目。 |
| `AnalysisCallbacks` | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)物件，指定要在 relogging 會話的分析階段中呼叫哪些函數。 |
| `RelogCallbacks` | [RELOG_CALLBACKS](relog-callbacks-struct.md)物件，指定要在 relogging 會話的 relogging 階段期間呼叫的函式。 |
| `SystemEventsRetentionFlags` | [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)位元遮罩，指定要保留在 relogged 追蹤中的系統 ETW 事件。 |
| `AnalysisContext` | 使用者提供的內容，以引數形式傳遞至指定的所有回呼函數 `AnalysisCallbacks` |
| `RelogContext` | 使用者提供的內容，以引數形式傳遞至指定的所有回呼函數 `RelogCallbacks` |

## <a name="remarks"></a>備註

在 relogging 會話期間，relogging ETW 事件的方式，是由使用者透過中指定的回呼函數控制 `RelogCallbacks` 。 不過，系統 ETW 事件（例如 CPU 範例）不會轉送至這些回呼函數。 使用 `SystemEventsRetentionFlags` 欄位來控制系統 ETW 事件的 relogging。

`AnalysisCallbacks`和 `RelogCallbacks` 結構只接受非成員函式的指標。 您可以藉由將其設定為物件指標來解決這項限制。 此物件指標會以引數的形式傳遞給您所有的非成員回呼函數。 使用這個指標可從您的非成員回呼函數中呼叫成員函式。

Relogging 會話的分析階段一律會在 relogging 階段之前執行。

::: moniker-end
