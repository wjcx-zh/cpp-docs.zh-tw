---
title: 上分析事件豐型
description: C++在分析事件豐體引用上構建見解 SDK。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eacd174279caff0db22586d5e40d3a866afc4459
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329120"
---
# <a name="onanalysiseventfunc-typedef"></a>上分析事件豐型

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

typedef`OnAnalysisEventFunc`是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)結構中使用的函數簽名之一。

## <a name="syntax"></a>語法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>參數

*事件堆疊*\
當前事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

*回檔內容*\
ANALYSIS_DESCRIPTOR[或](analysis-descriptor-struct.md)[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中為此回調設置的上下文值。

### <a name="return-value"></a>傳回值

控制接下來會發生什麼[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
