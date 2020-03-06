---
title: StartTracingSessionA
description: C++ BUILD Insights SDK StartTracingSessionA 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6c5069a2b521472ee4fd06ee313a66de5d7aa814
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332674"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`StartTracingSessionA` 函數會啟動追蹤會話。 呼叫此函式的可執行檔必須具有系統管理員許可權。

## <a name="syntax"></a>語法

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>參數

*sessionName*\
要啟動之追蹤會話的名稱。 呼叫[StopTracingSessionA](stop-tracing-session.md)或任何其他的 stop 追蹤函數時，請使用相同的名稱。

*選項*\
[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)物件的指標。 使用此物件來選取追蹤會話應收集的事件。

### <a name="return-value"></a>傳回值

來自[RESULT_CODE](../other-types/result-code-enum.md)列舉的結果碼。

::: moniker-end
