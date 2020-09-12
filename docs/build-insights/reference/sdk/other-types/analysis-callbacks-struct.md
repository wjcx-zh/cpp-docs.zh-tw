---
title: ANALYSIS_CALLBACKS 結構
description: C + + Build Insights SDK ANALYSIS_CALLBACKS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a24755befdd446051ae376b49d3dca06c7bc3320
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041038"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_CALLBACKS`當初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)物件時，會使用此結構。 它會指定在 Windows (ETW) 追蹤的事件追蹤分析或 relogging 期間要呼叫的函式。

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

| Name | 描述 |
|--|--|
| `OnStartActivity` | 呼叫以處理活動開始事件。 |
| `OnStopActivity` | 呼叫以處理活動停止事件。 |
| `OnSimpleEvent` | 呼叫以處理簡單事件。 |
| `OnTraceInfo` | 針對分析會話，在每個分析階段開始時呼叫。 針對 relogging 會話，在每次分析階段開始時呼叫，並在 relogging 階段的開頭再次呼叫。 只有在呼叫 OnBeginAnalysisPass 之後，才會呼叫此函數。 |
| `OnBeginAnalysis` | 針對分析會話，在開始任何分析階段之前呼叫。 針對 relogging 會話，在分析階段開始之前呼叫兩次：一次是宣佈 relogging 會話的開頭，而再一次宣佈分析階段的開始。 |
| `OnEndAnalysis` | 針對分析會話，在所有分析行程結束之後，會呼叫此函數。 針對 relogging 會話，當分析階段的所有分析行程都已結束時，就會呼叫此函數。 然後，它會在 relogging 階段結束之後再次呼叫。 |
| `OnBeginAnalysisPass` | 在處理任何事件之前，于開始分析階段或 relogging 階段時呼叫。 |
| `OnEndAnalysisPass` | 在處理所有事件之後，于結束分析行程或 relogging 階段時呼叫。 |

## <a name="remarks"></a>備註

Relogging 會話的分析階段會被視為 relogging 會話的一部分，而且可能包含多個分析階段。 基於這個理由，在 `OnBeginAnalysis` relogging 會話開始時，會在資料列中呼叫兩次。 `OnEndAnalysis` 在分析階段結束時，會在開始 relogging 階段之前呼叫，然後在 relogging 階段結束時呼叫。 Relogging 階段一律包含單一 relogging 階段。

分析器可以是 relogging 會話的分析和 relogging 階段的一部分。 這些分析器可以藉由追蹤 OnBeginAnalysis 和呼叫配對，來判斷目前正在進行的階段 `OnEndAnalysis` 。 兩次 `OnBeginAnalysis` 沒有任何 `OnEndAnalysis` 呼叫的呼叫表示分析階段正在進行中。 兩個 `OnBeginAnalysis` 呼叫和一個 `OnEndAnalysis` 呼叫表示 relogging 階段正在進行中。 兩個 OnBeginAnalysis 和兩個 `OnEndAnalysis` 呼叫表示兩個階段都已結束。

結構的所有成員都 `ANALYSIS_CALLBACKS` 必須指向有效的函式。 如需有關接受的函式簽章的詳細資訊，請參閱 [OnAnalysisEventFunc](on-analysis-event-func-typedef.md)、 [OnTraceInfoFunc](on-trace-info-func-typedef.md)和 [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。

::: moniker-end
