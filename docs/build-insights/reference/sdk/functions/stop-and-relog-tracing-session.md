---
title: StopAndRelogTracingSession
description: C++ BUILD Insights SDK StopAndRelogTracingSession 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e99568f9b509b89ccd0f0711433dec9d96d904bc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332590"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndRelogTracingSession` 函式會停止進行中的追蹤會話，並將產生的追蹤儲存在暫存檔案中。 然後，relogging 會話會立即開始使用暫存檔案作為輸入。 Relogging 會話所產生的最終 relogged 追蹤會儲存在呼叫者所指定的檔案中。 呼叫此函式的可執行檔必須具有系統管理員許可權。

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

*sessionName*\
要停止之追蹤會話的名稱。 使用與傳遞至[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)相同的會話名稱。

*outputLogFile*\
要在其中寫入 relogging 會話所產生之 relogged 追蹤的檔案。

*統計資料*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopAndRelogTracingSession` 在傳回之前，會在此物件中寫入追蹤集合統計資料。

*numberOfAnalysisPasses*\
要在追蹤上執行的分析傳遞數目。 追蹤會在每一次分析通過時，透過提供的分析器群組來傳遞。

*systemEventsRetentionFlags*\
[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)位元遮罩，指定要保留在 relogged 追蹤中的系統 ETW 事件。

*analyzerGroup*\
用於 relogging 會話之分析階段的分析器群組。 呼叫[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)以建立分析器群組。 如果您想要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)取得的動態分析器群組，請先將其位址傳遞給 `MakeStaticAnalyzerGroup`，以將其封裝在靜態分析器群組內。

*reloggerGroup*\
Relogger 群組，可將事件 relogs 至*outputLogFile*中指定的追蹤檔案。 呼叫[MakeStaticReloggerGroup](make-static-relogger-group.md)以建立 relogger 群組。 如果您想要使用從[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)取得的動態 relogger 群組，請先將其位址傳遞給 `MakeStaticReloggerGroup`，以將其封裝在靜態 relogger 群組內。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

### <a name="remarks"></a>備註

輸入追蹤會透過分析器群組*numberOfAnalysisPasses*時間傳遞。 Relogging 階段沒有類似的選項。 在所有的分析傳遞完成之後，只會將 relogger 群組的透過數目傳遞給該追蹤一次。

不支援從 relogger 類別內 relogging 系統事件（例如 CPU 樣本）。 使用*systemEventsRetentionFlags*參數來決定要保留在輸出追蹤中的系統事件。

::: moniker-end
