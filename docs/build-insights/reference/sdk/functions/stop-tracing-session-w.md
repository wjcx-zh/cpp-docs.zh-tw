---
title: 停止追蹤工作階段W
description: C++生成見解 SDK 停止追蹤會話W 函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6582e477ac6b13319ab5ab0f77295517548f7068
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323529"
---
# <a name="stoptracingsessionw"></a>停止追蹤工作階段W

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`StopTracingSessionW`函數停止正在進行的跟蹤會話並生成原始跟蹤檔。 原始追蹤檔可以傳遞到[分析](analyze.md)、[分析](analyze-a.md)A 和[分析W](analyze-w.md)函數以啟動分析工作階段。 原始追蹤檔也可以傳遞到[Relog、RelogA](relog-a.md)和[RelogW](relog-w.md)函數以開始重新[Relog](relog.md)記錄作業階段。 調用的可執行`StopTracingSessionW`文件必須具有管理員許可權。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE StopTracingSessionW(
    const wchar_t*              sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>參數

*工作階段名稱*\
要停止的跟蹤會話的名稱。 使用與傳遞給[「開始追蹤工作階段](start-tracing-session.md)」、[開始追蹤會話A](start-tracing-session-a.md)或[「開始追蹤工作階段W」](start-tracing-session-w.md)的工作階段名稱相同的作業階段名稱。

*輸出記錄檔*\
應保存原始跟蹤的最終輸出日誌檔的路徑。

*統計*\
指向[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)物件的指標。 `StopTracingSessionW`返回之前,在此物件中寫入跟蹤集合統計資訊。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
