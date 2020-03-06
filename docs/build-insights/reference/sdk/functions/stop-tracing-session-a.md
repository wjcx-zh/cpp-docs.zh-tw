---
title: StopTracingSessionA
description: C++ BUILD Insights SDK StopTracingSessionA 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 12f0c7a9665c47f36fb5e88d799673918017bb98
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332583"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`StopTracingSessionA` 函式會停止進行中的追蹤會話，並產生原始的追蹤檔案。 原始的追蹤檔案可以傳遞至[分析](analyze.md)、 [AnalzeA](analyze-a.md)和[AnalyzeW](analyze-w.md)函式，以啟動分析會話。 原始的追蹤檔案也可以傳遞至重新[RelogA](relog-a.md)和[RelogW](relog-w.md)函[式，以](relog.md)啟動 relogging 會話。 呼叫 `StopTracingSessionA` 的可執行檔必須具有系統管理員許可權。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>參數

*sessionName*\
要停止之追蹤會話的名稱。 使用與傳遞至[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)相同的會話名稱。

*outputLogFile*\
應儲存原始追蹤之最終輸出記錄檔的路徑。

*統計資料*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopTracingSessionA` 在傳回之前，會在此物件中寫入追蹤集合統計資料。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
