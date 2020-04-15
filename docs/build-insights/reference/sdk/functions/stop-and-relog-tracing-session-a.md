---
title: 停止並重新登入追蹤工作階段A
description: C++生成見解 SDK 停止和重新log跟蹤會話A函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa70d50ba79a7829adb985ab4d884b5773b5d40f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323675"
---
# <a name="stopandrelogtracingsessiona"></a>停止並重新登入追蹤工作階段A

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`StopAndRelogTracingSessionA`函數停止正在進行的跟蹤會話,並將生成的跟蹤保存在臨時檔中。 然後,使用臨時檔作為輸入立即啟動重新記錄記錄工作階段。 重新記錄記錄工作階段產生的最終重新記錄追蹤將儲存在調用方指定的檔案中。 調用此函數的可執行文件必須具有管理員許可權。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>參數

*工作階段名稱*\
要停止的跟蹤會話的名稱。 使用與傳遞給[「開始追蹤工作階段](start-tracing-session.md)」、[開始追蹤會話A](start-tracing-session-a.md)或[「開始追蹤工作階段W」](start-tracing-session-w.md)的工作階段名稱相同的作業階段名稱。

*輸出記錄檔*\
用於寫入重新記錄作業階段生成的重新記錄追蹤的檔案。

*統計*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopAndRelogTracingSessionA`返回之前,在此物件中寫入跟蹤集合統計資訊。

*剖析描述子*\
指向[RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)物件的指標。 使用此物件可以設定`StopAndRelogTracingSessionA`由 啟動的重新記錄記錄工作階段。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
