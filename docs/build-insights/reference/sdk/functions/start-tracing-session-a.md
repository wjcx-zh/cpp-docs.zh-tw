---
title: 開始追蹤工作階段A
description: C++生成見解 SDK 開始跟蹤會話A 函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c184e214c7f55bb7eaa6eb03f21e792ef90fa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323770"
---
# <a name="starttracingsessiona"></a>開始追蹤工作階段A

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

函數`StartTracingSessionA`啟動跟蹤會話。 調用此函數的可執行文件必須具有管理員許可權。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>參數

*工作階段名稱*\
要啟動的跟蹤作業的名稱。 呼叫[停止追蹤作業階段A](stop-tracing-session.md)或任何其他停止追蹤函數時使用相同的名稱。

*選項*\
指向[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)物件的指標。 使用此物件可選擇要由跟蹤會話收集的事件。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)枚舉的結果代碼。

::: moniker-end
