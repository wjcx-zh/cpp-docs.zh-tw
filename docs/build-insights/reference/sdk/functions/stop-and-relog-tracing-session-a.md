---
title: StopAndRelogTracingSessionA
description: C++ BUILD Insights SDK StopAndRelogTracingSessionA 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c9fe2ea47b378565d3ce9785b6f4cc3e541ebe80
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332702"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndRelogTracingSessionA` 函式會停止進行中的追蹤會話，並將產生的追蹤儲存在暫存檔案中。 然後，relogging 會話會立即開始使用暫存檔案作為輸入。 Relogging 會話所產生的最終 relogged 追蹤會儲存在呼叫者所指定的檔案中。 呼叫此函式的可執行檔必須具有系統管理員許可權。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>參數

*sessionName*\
要停止之追蹤會話的名稱。 使用與傳遞至[StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)或[StartTracingSessionW](start-tracing-session-w.md)相同的會話名稱。

*outputLogFile*\
要在其中寫入 relogging 會話所產生之 relogged 追蹤的檔案。

*統計資料*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopAndRelogTracingSessionA` 在傳回之前，會在此物件中寫入追蹤集合統計資料。

*analysisDescriptor*\
[RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)物件的指標。 使用此物件來設定 `StopAndRelogTracingSessionA`啟動的 relogging 會話。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
