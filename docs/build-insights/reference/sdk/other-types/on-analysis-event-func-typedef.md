---
title: OnAnalysisEventFunc typedef
description: C++ BUILD Insights SDK OnAnalysisEventFunc typedef 參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d260f6060e759f315589abda82e31c2c2b95a65e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332429"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc typedef

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`OnAnalysisEventFunc` typedef 是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)結構中所使用的其中一個函式簽章。

## <a name="syntax"></a>語法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>參數

*eventStack*\
目前事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

*callbackCoNtext*\
在[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中為此回呼設定的內容值。

### <a name="return-value"></a>傳回值

控制接下來應發生之情況的[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
