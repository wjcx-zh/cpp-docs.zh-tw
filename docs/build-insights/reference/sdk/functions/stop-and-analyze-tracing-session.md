---
title: StopAndAnalyzeTracingSession
description: C++ BUILD Insights SDK StopAndAnalyzeTracingSession 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b1c605bb63ac093f90128a03c37b186226130912
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332611"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndAnalyzeTracingSession` 函式會停止進行中的追蹤會話，並將產生的追蹤儲存在暫存檔案中。 接著會使用暫存檔做為輸入，立即開始分析會話。 呼叫此函式的可執行檔必須具有系統管理員許可權。

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

*sessionName*\
要停止之追蹤會話的名稱。 使用與傳遞至[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)相同的會話名稱。

*numberOfAnalysisPasses*\
要在追蹤上執行的分析傳遞數目。 追蹤會在每一次分析通過時，透過提供的分析器群組來傳遞。

*統計資料*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopAndAnalyzeTracingSession` 在傳回之前，會在此物件中寫入追蹤集合統計資料。

*analyzerGroup*\
用於分析的分析器群組。 呼叫[MakeStaticAnalyzerGroup](make-static-analyzer-group.md)以建立分析器群組。 如果您想要使用從[MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)取得的動態分析器群組，請先將其位址傳遞給 `MakeStaticAnalyzerGroup`，以將其封裝在靜態分析器群組內。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
