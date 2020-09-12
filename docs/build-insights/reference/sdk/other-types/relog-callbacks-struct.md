---
title: RELOG_CALLBACKS 結構
description: C + + Build Insights SDK RELOG_CALLBACKS 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 55f63b05691e3d729ee42ed21049669b94053559
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041428"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_CALLBACKS`初始化[RELOG_DESCRIPTOR](relog-descriptor-struct.md)物件時，會使用此結構。 它會指定在 Windows (ETW) 追蹤的事件追蹤 relogging 期間要呼叫的函式。

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

| Name | 描述 |
|--|--|
| `OnStartActivity` | 呼叫以處理活動開始事件。 |
| `OnStopActivity` | 呼叫以處理活動停止事件。 |
| `OnSimpleEvent` | 呼叫以處理簡單事件。 |
| `OnTraceInfo` | 在 relogging 階段開始時呼叫一次，並在 `OnBeginReloggingPass` 呼叫之後呼叫。 |
| `OnBeginRelogging` | 開始 relogging 會話時呼叫，在 relogging 階段開始之前。 |
| `OnEndRelogging` | 在結束 relogging 會話時呼叫，在 relogging 階段結束之後。 |
| `OnBeginReloggingPass` | 在處理任何事件之前，于開始 relogging 階段時呼叫。 |
| `OnEndReloggingPass` | 在處理所有事件之後，于結束 relogging 階段時呼叫。 |

## <a name="remarks"></a>備註

結構的所有成員都 `RELOG_CALLBACKS` 必須指向有效的函式。 如需有關接受的函式簽章的詳細資訊，請參閱 [OnRelogEventFunc](on-relog-event-func-typedef.md)、 [OnTraceInfoFunc](on-trace-info-func-typedef.md)和 [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)。

::: moniker-end
