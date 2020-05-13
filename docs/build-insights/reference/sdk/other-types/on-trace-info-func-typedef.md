---
title: 在 TraceInfoFunc 類型定義
description: C++在TraceinfoFunc類型定義引用上構建見解 SDK。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b987d4db9852c2e52c148bb91015ad414c04d41b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329026"
---
# <a name="ontraceinfofunc-typedef"></a>在 TraceInfoFunc 類型定義

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

typedef`OnTraceInfoFunc`是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)和[RELOG_CALLBACKS](relog-callbacks-struct.md)結構中使用的函數簽名之一。

## <a name="syntax"></a>語法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>參數

*追蹤資訊*\
包含有關當前正在分析或重新記錄的跟蹤的資訊[TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md)物件。

*回檔內容*\
ANALYSIS_DESCRIPTOR[或](analysis-descriptor-struct.md)[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中為此回調設置的上下文值。

### <a name="return-value"></a>傳回值

控制接下來會發生什麼[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
