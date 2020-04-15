---
title: RELOG_CALLBACKS結構
description: C++構建見解 SDK RELOG_CALLBACKS結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328965"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

在`RELOG_CALLBACKS`初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)物件時,將使用該結構。 它指定在重新記錄 Windows (ETW) 追蹤的事件追蹤期間調用哪些函數。

## <a name="syntax"></a>語法

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `OnStartActivity` | 調用以處理活動開始事件。 |
| `OnStopActivity` | 調用以處理活動停止事件。 |
| `OnSimpleEvent` | 調用 以處理簡單事件。 |
| `OnTraceInfo` | 調用一次在重新記錄通過開始,之後`OnBeginReloggingPass`已被調用。 |
| `OnBeginRelogging` | 在開始重新記錄作業階段時調用,在重新記錄通道開始之前。 |
| `OnEndRelogging` | 在結束重新記錄會話時調用,重新記錄通過結束後。 |
| `OnBeginReloggingPass` | 在處理任何事件之前,在開始重新記錄傳遞時調用。 |
| `OnEndReloggingPass` | 在處理所有事件後結束重新記錄傳遞時調用。 |

## <a name="remarks"></a>備註

`RELOG_CALLBACKS`結構的所有成員必須指向有效的函數。 有關接受的函數簽名的詳細資訊,請參閱[OnRelogEventFunc、OnTraceInfoFunc](on-relog-event-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。 [OnTraceInfoFunc](on-trace-info-func-typedef.md)

::: moniker-end
