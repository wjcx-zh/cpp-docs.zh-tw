---
title: OnTraceInfoFunc typedef
description: C++ BUILD Insights SDK OnTraceInfoFunc typedef 參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332345"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`OnTraceInfoFunc` typedef 是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)和[RELOG_CALLBACKS](relog-callbacks-struct.md)結構中所使用的其中一個函式簽章。

## <a name="syntax"></a>語法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>參數

*traceInfo*\
[TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md)物件，其中包含目前正在分析或 relogged 之追蹤的相關資訊。

*callbackCoNtext*\
在[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中為此回呼設定的內容值。

### <a name="return-value"></a>傳回值

控制接下來應發生之情況的[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
