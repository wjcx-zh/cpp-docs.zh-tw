---
title: Relog
description: C++生成見解 SDK 重新日誌函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323783"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Relog`函數用於從 Windows (ETW) 追蹤的事件追蹤讀取 MSVC 事件,並將它們寫入新的修改後的 ETW 追蹤中。

## <a name="syntax"></a>語法

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>參數

*TAnalyzer 群組成員*\
始終推導此參數。

*TReloggerGroup成員*\
始終推導此參數。

*輸入紀錄檔*\
要從中讀取事件的輸入 ETW 跟蹤。

*輸出記錄檔*\
寫入新事件的檔。

*分析通道數*\
在輸入跟蹤上運行的分析數。 跟蹤通過每個分析傳遞一次通過提供的分析器組。

*系統事件保留旗標*\
指定要在重新記錄的追蹤中保留哪些系統 ETW 事件的位掩碼。 有關詳細資訊,請參閱[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)。

*分析儀組*\
用於重新記錄會話分析階段的分析器組。 呼叫[MakeStatic 分析器群組](make-static-analyzer-group.md)以建立分析器群組。 要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)獲得的動態分析器組,首先通過將地址`MakeStaticAnalyzerGroup`傳遞給將其封裝在靜態分析器組中。

*重新記錄群組*\
重新記錄組,將事件重新記錄到*輸出日誌檔中*指定的跟蹤檔中。 呼叫[使靜態重新記錄組](make-static-relogger-group.md)創建重新記錄組。 要使用從[MakeDynamic ReloggerGroup](make-dynamic-relogger-group.md)獲得的動態重新記錄組,首先通過將其`MakeStaticReloggerGroup`位址傳遞給將其封裝在靜態重新記錄組中。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

### <a name="remark"></a>備註

輸入跟蹤通過分析器組*編號分析傳遞次數分析。* 沒有類似的重新記錄通行證選項。 跟蹤在完成所有分析過程後,僅通過一次重新記錄組槽。

不支援重新記錄類中的系統事件(如 CPU 樣本)的重新記錄。 使用*系統事件保留標誌*參數決定要在輸出跟蹤中保留哪些系統事件。

::: moniker-end
