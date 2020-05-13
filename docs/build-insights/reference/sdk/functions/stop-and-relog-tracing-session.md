---
title: 停止並重新記錄追蹤工作階段
description: C++生成見解 SDK 停止和重新記錄跟蹤會話函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323659"
---
# <a name="stopandrelogtracingsession"></a>停止並重新記錄追蹤工作階段

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`StopAndRelogTracingSession`函數停止正在進行的跟蹤會話,並將生成的跟蹤保存在臨時檔中。 然後,使用臨時檔作為輸入立即啟動重新記錄記錄工作階段。 重新記錄記錄工作階段產生的最終重新記錄追蹤將儲存在調用方指定的檔案中。 調用此函數的可執行文件必須具有管理員許可權。

## <a name="syntax"></a>語法

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>參數

*工作階段名稱*\
要停止的跟蹤會話的名稱。 使用與傳遞給[「開始追蹤工作階段](start-tracing-session.md)」、[開始追蹤會話A](start-tracing-session-a.md)或[「開始追蹤工作階段W」](start-tracing-session-w.md)的工作階段名稱相同的作業階段名稱。

*輸出記錄檔*\
用於寫入重新記錄作業階段生成的重新記錄追蹤的檔案。

*統計*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopAndRelogTracingSession`返回之前,在此物件中寫入跟蹤集合統計資訊。

*分析通道數*\
要在跟蹤上運行的分析數。 跟蹤通過每個分析傳遞一次通過提供的分析器組。

*系統事件保留旗標*\
指定要在重新記錄的追蹤中保留哪些系統 ETW 事件的[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)位掩碼。

*分析儀組*\
用於重新記錄會話分析階段的分析器組。 呼叫[MakeStatic 分析器群組](make-static-analyzer-group.md)以建立分析器群組。 如果要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)獲得的動態分析器組,首先通過將地址`MakeStaticAnalyzerGroup`傳遞給將其封裝在靜態分析器組中。

*重新記錄群組*\
重新記錄組,將事件重新記錄到*輸出日誌檔中*指定的跟蹤檔中。 呼叫[使靜態重新記錄組](make-static-relogger-group.md)創建重新記錄組。 如果你想使用從[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)獲得的動態重新記錄器組,首先通過將其地址`MakeStaticReloggerGroup`傳遞給將其封裝在靜態重新記錄器組中。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

### <a name="remarks"></a>備註

輸入跟蹤通過分析器組*編號分析傳遞次數分析。* 沒有類似的重新記錄通行證選項。 跟蹤在完成所有分析過程後,僅通過一次重新記錄組槽。

不支援重新記錄類中的系統事件(如 CPU 樣本)的重新記錄。 使用*系統事件保留標誌*參數決定要在輸出跟蹤中保留哪些系統事件。

::: moniker-end
