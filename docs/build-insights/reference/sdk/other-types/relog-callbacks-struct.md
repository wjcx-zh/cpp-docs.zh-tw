---
title: RELOG_CALLBACKS 結構
description: C++ BUILD Insights SDK RELOG_CALLBACKS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332338"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)物件時，會使用 `RELOG_CALLBACKS` 結構。 它會指定在 Windows 事件追蹤（ETW）追蹤 relogging 期間所要呼叫的函式。

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
| `OnStartActivity` | 呼叫以處理活動開始事件。 |
| `OnStopActivity` | 呼叫以處理活動停止事件。 |
| `OnSimpleEvent` | 呼叫以處理簡單事件。 |
| `OnTraceInfo` | 呼叫 `OnBeginReloggingPass` 之後，在 relogging 階段開始時呼叫一次。 |
| `OnBeginRelogging` | 開始 relogging 會話時呼叫，在 relogging 階段開始之前。 |
| `OnEndRelogging` | 結束 relogging 會話時，在 relogging 階段結束後呼叫。 |
| `OnBeginReloggingPass` | 在處理任何事件之前，于開始 relogging 階段時呼叫。 |
| `OnEndReloggingPass` | 在處理所有事件之後，于結束 relogging 階段時呼叫。 |

## <a name="remarks"></a>備註

`RELOG_CALLBACKS` 結構的所有成員都必須指向有效的函式。 如需有關已接受之函式簽章的詳細資訊，請參閱[OnRelogEventFunc](on-relog-event-func-typedef.md)、 [OnTraceInfoFunc](on-trace-info-func-typedef.md)和[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。

::: moniker-end
