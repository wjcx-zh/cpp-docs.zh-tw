---
title: ANALYSIS_CALLBACKS 結構
description: C++ BUILD Insights SDK ANALYSIS_CALLBACKS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332527"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)物件時，會使用 `ANALYSIS_CALLBACKS` 結構。 它會指定在 Windows 事件追蹤（ETW）追蹤的分析或 relogging 期間所要呼叫的函數。

## <a name="syntax"></a>語法

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `OnStartActivity` | 呼叫以處理活動開始事件。 |
| `OnStopActivity` | 呼叫以處理活動停止事件。 |
| `OnSimpleEvent` | 呼叫以處理簡單事件。 |
| `OnTraceInfo` | 適用于分析會話，在每個分析階段開始時呼叫。 對於 relogging 會話，會在每個分析階段開始時呼叫，並在 relogging 階段的開頭再次呼叫。 只有在呼叫 OnBeginAnalysisPass 之後，才會呼叫這個函式。 |
| `OnBeginAnalysis` | 針對分析會話，在開始任何分析階段之前呼叫。 對於 relogging 會話，在分析階段開始之前，會呼叫兩次：一次是通知 relogging 會話的開頭，另一次則是宣佈分析階段的開始。 |
| `OnEndAnalysis` | 對於分析會話，會在所有分析通過結束後呼叫此函式。 針對 relogging 會話，當分析階段的所有分析通過結束時，會呼叫這個函式。 然後，它會在 relogging pass 結束後再次呼叫。 |
| `OnBeginAnalysisPass` | 在處理任何事件之前，于開始分析階段或 relogging 階段時呼叫。 |
| `OnEndAnalysisPass` | 在處理所有事件之後，于結束分析階段或 relogging 階段時呼叫。 |

## <a name="remarks"></a>備註

Relogging 會話的分析階段會視為 relogging 會話的一部分，而且可能包含多個分析通過。 基於這個理由，會在 relogging 會話開頭的資料列中呼叫兩次 `OnBeginAnalysis`。 `OnEndAnalysis` 是在分析階段結束時、開始 relogging 階段之前，以及在 relogging 階段結束時再次呼叫。 Relogging 階段一律包含單一的 relogging 階段。

分析器可以同時成為 relogging 會話的分析和 relogging 階段的一部分。 這些分析器可以追蹤 OnBeginAnalysis 和 `OnEndAnalysis` 呼叫配對，藉以判斷目前正在進行的階段。 沒有任何 `OnEndAnalysis` 呼叫的兩個 `OnBeginAnalysis` 呼叫表示分析階段正在進行中。 兩個 `OnBeginAnalysis` 呼叫和一個 `OnEndAnalysis` 呼叫表示 relogging 階段正在進行中。 兩個 OnBeginAnalysis 和兩個 `OnEndAnalysis` 呼叫表示兩個階段都已結束。

`ANALYSIS_CALLBACKS` 結構的所有成員都必須指向有效的函式。 如需有關已接受之函式簽章的詳細資訊，請參閱[OnAnalysisEventFunc](on-analysis-event-func-typedef.md)、 [OnTraceInfoFunc](on-trace-info-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。

::: moniker-end
