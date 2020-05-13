---
title: 停止並分析追蹤工作階段
description: C++生成見解 SDK 停止和分析跟蹤會話函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c9bd4a092c22dfcdfb6d463b74207ec11ee6d64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323708"
---
# <a name="stopandanalyzetracingsession"></a>停止並分析追蹤工作階段

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`StopAndAnalyzeTracingSession`函數停止正在進行的跟蹤會話,並將生成的跟蹤保存在臨時檔中。 然後,使用臨時檔作為輸入立即啟動分析會話。 調用此函數的可執行文件必須具有管理員許可權。

## <a name="syntax"></a>語法

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>參數

*工作階段名稱*\
要停止的跟蹤會話的名稱。 使用與傳遞給[「開始追蹤工作階段](start-tracing-session.md)」、[開始追蹤會話A](start-tracing-session-a.md)或[「開始追蹤工作階段W」](start-tracing-session-w.md)的工作階段名稱相同的作業階段名稱。

*分析通道數*\
要在跟蹤上運行的分析數。 跟蹤通過每個分析傳遞一次通過提供的分析器組。

*統計*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopAndAnalyzeTracingSession`返回之前,在此物件中寫入跟蹤集合統計資訊。

*分析儀組*\
用於分析的分析器組。 呼叫[MakeStatic 分析器群組](make-static-analyzer-group.md)以建立分析器群組。 如果要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)獲得的動態分析器組,首先通過將地址`MakeStaticAnalyzerGroup`傳遞給將其封裝在靜態分析器組中。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
