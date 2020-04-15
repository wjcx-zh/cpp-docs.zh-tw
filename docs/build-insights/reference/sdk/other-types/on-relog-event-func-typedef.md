---
title: OnRelogEventFunc 類型def
description: C++在 RelogEventFunc 類型定義引用上生成見解 SDK。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329072"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc 類型def

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

typedef`OnRelogEventFunc`是[RELOG_CALLBACKS](relog-callbacks-struct.md)結構中使用的函數簽名之一。

## <a name="syntax"></a>語法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>參數

*事件堆疊*\
當前事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

*重新登入工作階段*\
調用[InjectEvent](../functions/inject-event.md)時使用的重新記錄會話指標。

*回檔內容*\
為RELOG_DESCRIPTOR[中為此](analysis-descriptor-struct.md)回調設置的上下文值。

### <a name="return-value"></a>傳回值

控制接下來會發生什麼[CALLBACK_CODE](callback-code-enum.md)值。

::: moniker-end
