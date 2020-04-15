---
title: ANALYSIS_CALLBACKS結構
description: C++生成見解 SDK ANALYSIS_CALLBACKS結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323514"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

在`ANALYSIS_CALLBACKS`初始化[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)物件時,將使用該結構。 它指定在分析或重新記錄 Windows (ETW) 追蹤的事件跟蹤期間調用哪些函數。

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
| `OnStartActivity` | 調用以處理活動開始事件。 |
| `OnStopActivity` | 調用以處理活動停止事件。 |
| `OnSimpleEvent` | 調用 以處理簡單事件。 |
| `OnTraceInfo` | 對於分析會話,在每個分析傳遞開始時調用。 對於重新記錄會話,在每次分析傳遞開始時調用,在重新記錄傳遞開始時再次調用。 僅當調用 OnBegin 分析通點後,才調用此功能。 |
| `OnBeginAnalysis` | 對於分析會話,在開始任何分析傳遞之前調用。 對於重新記錄會話,在分析階段開始之前調用兩次:一次宣佈重新記錄會話的開始,再一次宣佈分析階段的開始。 |
| `OnEndAnalysis` | 對於分析會話,在結束所有分析過程後調用此函數。 對於重新記錄會話,當分析階段的所有分析通過都結束時,將調用此函數。 然後,在重新日誌記錄通過結束後再次調用它。 |
| `OnBeginAnalysisPass` | 在處理任何事件之前,在開始分析傳遞或重新日誌記錄傳遞時調用。 |
| `OnEndAnalysisPass` | 在處理所有事件後結束分析傳遞或重新記錄記錄傳遞時調用。 |

## <a name="remarks"></a>備註

重新記錄會話的分析階段被視為重新記錄會話的一部分,可能包含多個分析過程。 因此,`OnBeginAnalysis`在重新記錄會話開始時連續調用兩次。 `OnEndAnalysis`在分析階段結束時調用,在開始重新記錄階段之前,在重新記錄階段結束時再次調用。 重新記錄階段始終包含單個重新記錄記錄通道。

分析器有可能成為重新記錄會話分析和重新記錄階段的一部分。 這些分析器可以通過追蹤 OnBegin`OnEndAnalysis`分析和通話對來確定當前正在進行的階段。 兩`OnBeginAnalysis`次`OnEndAnalysis`沒有 調用的呼叫意味著分析階段正在進行。 兩`OnBeginAnalysis`個呼叫和`OnEndAnalysis`一個呼叫意味著重新記錄階段正在進行中。 兩個 OnBegin`OnEndAnalysis`分析和兩個呼叫意味著兩個階段都結束了。

`ANALYSIS_CALLBACKS`結構的所有成員必須指向有效的函數。 有關接受的功能簽名的詳細資訊,請參閱[OnAnalysisEventFunc、OnTraceInfoFunc](on-analysis-event-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。 [OnTraceInfoFunc](on-trace-info-func-typedef.md)

::: moniker-end
